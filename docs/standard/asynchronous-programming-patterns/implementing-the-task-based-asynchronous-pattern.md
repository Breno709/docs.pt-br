---
title: "Implementando o padrão assíncrono baseado em tarefa"
ms.date: 06/14/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: fab6bd41-91bd-44ad-86f9-d8319988aa78
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e61b0c94b1512509008d67017389fa11f938999
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>Implementando o padrão assíncrono baseado em tarefa
Você pode implementar o Padrão Assíncrono baseado em Tarefas (TAP) de três formas: usando os compiladores C# e Visual Basic no Visual Studio, manualmente ou por meio de uma combinação dos métodos de compilador e manual. As seções a seguir discutem cada método em detalhes. Você pode usar o padrão de toque para implementar operações assíncronas vinculada à computação e vinculada a e/S. O [cargas de trabalho](#workloads) seção descreve cada tipo de operação.

## <a name="generating-tap-methods"></a>Gerando métodos de toque

### <a name="using-the-compilers"></a>Usando os compiladores
Começando com [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], qualquer método que é atribuído com o `async` palavra-chave (`Async` no Visual Basic) é considerado um método assíncrono e os compiladores c# e Visual Basic executam as transformações necessárias para implementar o método de forma assíncrona usando o toque. Um método assíncrono deve retornar um objeto <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ou um objeto <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Para o último, o corpo da função deve retornar um `TResult`, e o compilador garante que esse resultado é disponibilizado por meio do objeto de tarefa resultante. Da mesma forma, quaisquer exceções que passem para o corpo do método sem tratamento são empacotadas na tarefa de saída e fazem com que a tarefa resultante termine no estado <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType>. A exceção é quando uma <xref:System.OperationCanceledException> (ou um tipo derivado) passa sem tratamento e, nesse caso, a tarefa resultante termina no estado <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType>.

### <a name="generating-tap-methods-manually"></a>Gerar métodos toque manualmente
Você pode implementar o padrão TAP manualmente para obter maior controle sobre a implementação. O compilador depende da área de superfície pública exposta no namespace <xref:System.Threading.Tasks?displayProperty=nameWithType> e dos tipos de suporte no namespace <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>. Para implementar o TAP você mesmo, crie um objeto <xref:System.Threading.Tasks.TaskCompletionSource%601>, execute a operação assíncrona e quando ela estiver concluída, chame o método <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A> ou <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A>, ou a versão `Try` de um desses métodos. Quando você implementa um método do TAP manualmente, deverá concluir a tarefa resultante quando a operação assíncrona representada for concluída. Por exemplo:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>Abordagem híbrida
 Você pode achá-la útil para implementar o padrão TAP manualmente, mas também para delegar a lógica principal para a implementação para o compilador. Por exemplo, talvez você queira usar a abordagem híbrida quando quiser verificar argumentos fora de um método assíncrono gerado pelo compilador para que as exceções possam escapar para o chamador direto do método, em vez de serem expostas por meio do objeto <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>:

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 Outro caso em que tal delegação é útil é quando você está implementando a otimização de caminho rápido e deseja retornar uma tarefa armazenada em cache.

## <a name="workloads"></a>Cargas de trabalho
Você pode implementar operações assíncronas associadas ao cálculo e associadas à E/S como métodos do TAP. No entanto, quando os métodos do TAP forem expostos publicamente de uma biblioteca, eles deverão receber somente cargas de trabalho que envolvem operações associadas à E/S (eles também podem envolver cálculos, mas não devem ser puramente computacionais). Se um método é vinculada à computação puramente, ele deve ser exposto apenas como uma implementação síncrona. O código que consome pode, em seguida, escolha se deseja encapsular uma invocação do método síncrono em uma tarefa para descarregar o trabalho para outro thread ou para obter paralelismo. E se um método é associado a e/s, ele deve ser exposto apenas como uma implementação assíncrona.

### <a name="compute-bound-tasks"></a>Tarefas de computação associados
A classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> é totalmente adequada para representar operações que exigem vários recursos computacionais. Por padrão, ela aproveita o suporte especial dentro da classe <xref:System.Threading.ThreadPool> para fornecer execução eficiente e fornece também controle significativo sobre quando, onde e como executar cálculos assíncronos.

Você pode gerar tarefas associadas ao cálculo de uma das seguintes maneiras:

- No .NET Framework 4, use o método <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>, que aceita um delegado (geralmente um <xref:System.Action%601> ou um <xref:System.Func%601>) a ser executado de forma assíncrona. Se você fornecer um delegado <xref:System.Action%601>, o método retornará um objeto <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> que representa a execução assíncrona desse delegado. Se você fornecer um delegado <xref:System.Func%601>, o método retornará um objeto <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Sobrecargas do método <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> aceitam um token de cancelamento (<xref:System.Threading.CancellationToken>), opções de criação de tarefas (<xref:System.Threading.Tasks.TaskCreationOptions>) e um agendador de tarefas (<xref:System.Threading.Tasks.TaskScheduler>), que fornecem controle refinado sobre o planejamento e a execução da tarefa. Uma instância de fábrica que tem como destino o agendador de tarefas atual está disponível como uma propriedade estática (<xref:System.Threading.Tasks.Task.Factory%2A>) da classe <xref:System.Threading.Tasks.Task>; por exemplo: `Task.Factory.StartNew(…)`.

- No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e versões posteriores (incluindo o .NET Core e .NET padrão), use estático <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> método como um atalho para <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Você pode usar <xref:System.Threading.Tasks.Task.Run%2A> para iniciar com facilidade uma tarefa associada ao cálculo que tem como destino o pool de threads. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e versões posteriores, esse é o mecanismo preferido para iniciar uma tarefa vinculada à computação. Use `StartNew` diretamente somente quando desejar um controle mais refinado sobre a tarefa.

- Use os construtores do tipo `Task` ou o método `Start` se desejar gerar e agendar a tarefa separadamente. Métodos públicos devem retornar somente as tarefas que já foram iniciadas.

- Use as sobrecargas do método <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Esse método cria uma nova tarefa que é agendada quando outra tarefa for concluída. Algumas das sobrecargas <xref:System.Threading.Tasks.Task.ContinueWith%2A> aceitam um token de cancelamento, opções de continuação e um agendador de tarefas para obter melhor controle sobre o agendamento e a execução da tarefa de continuação.

- Use o <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> métodos. Esses métodos criam uma nova tarefa que é agendada quando todos ou nenhum dos conjuntos de tarefas for concluído. Esses métodos também fornecem sobrecargas para controlar o agendamento e execução dessas tarefas.

Nas tarefas associadas ao cálculo, o sistema pode impedir a execução de uma tarefa agendada se ele receber uma solicitação de cancelamento antes de iniciar a execução da tarefa. Assim, se você fornecer um token de cancelamento (objeto <xref:System.Threading.CancellationToken>), poderá passar esse token para o código assíncrono que monitora o token. Também é possível fornecer o token para um dos métodos mencionados anteriormente, tais como `StartNew` ou `Run` para que o tempo de execução da `Task` também possa monitorar o token.

Por exemplo, considere um método assíncrono que renderiza uma imagem. O corpo da tarefa pode sondar o token de cancelamento para que o código possa sair antecipadamente se uma solicitação de cancelamento chegar durante a renderização. Além disso, se a solicitação de cancelamento chegar antes do início da renderização, você desejará impedir a operação de renderização:

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

Tarefas associadas ao cálculo terminarão em um estado <xref:System.Threading.Tasks.TaskStatus.Canceled> se pelo menos uma das seguintes condições for verdadeira:

- Uma solicitação de cancelamento chega por meio do objeto <xref:System.Threading.CancellationToken>, que é fornecido como um argumento para o método de criação (por exemplo, `StartNew` ou `Run`) antes das transições de tarefas para o estado <xref:System.Threading.Tasks.TaskStatus.Running>.

- Uma exceção <xref:System.OperationCanceledException> ficará sem tratamento dentro do corpo dessa tarefa, se a exceção contiver o mesmo <xref:System.Threading.CancellationToken> que é passado para a tarefa e se o token mostrar que o cancelamento foi solicitado.

Se outra exceção ficar sem tratamento dentro do corpo da tarefa, a tarefa terminará no estado <xref:System.Threading.Tasks.TaskStatus.Faulted> e quaisquer tentativas de aguardar a tarefa ou acessar seu resultado fará com que uma exceção seja lançada.

### <a name="io-bound-tasks"></a>Tarefas vinculada à e/S
Para criar uma tarefa cujo backup não deve ser feito diretamente por um thread para a totalidade de sua execução, use o tipo <xref:System.Threading.Tasks.TaskCompletionSource%601>. Esse tipo expõe uma propriedade <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> que retorna uma instância <xref:System.Threading.Tasks.Task%601> associada. O ciclo de vida dessa tarefa é controlado por métodos <xref:System.Threading.Tasks.TaskCompletionSource%601>, tais como <xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>, <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> e suas variantes `TrySet`.

Digamos que você deseja criar uma tarefa que será concluída após um período de tempo especificado. Por exemplo, talvez você queira atrasar uma atividade na interface do usuário. A classe <xref:System.Threading.Timer?displayProperty=nameWithType> já oferece a capacidade de invocar de forma assíncrona um delegado após um período especificado e usando <xref:System.Threading.Tasks.TaskCompletionSource%601> você pode colocar uma frente <xref:System.Threading.Tasks.Task%601> no cronômetro, por exemplo:

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

Começando com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], o método <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> é fornecido para essa finalidade e você pode usá-lo dentro de outro método assíncrono, por exemplo, para implementar um loop de sondagem assíncrono:

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

A classe <xref:System.Threading.Tasks.TaskCompletionSource%601> não tem uma equivalente não genérica. No entanto, <xref:System.Threading.Tasks.Task%601> deriva de <xref:System.Threading.Tasks.Task>, de modo que você pode usar o objeto <xref:System.Threading.Tasks.TaskCompletionSource%601> genérico para métodos de associação de E/S que simplesmente retornam uma tarefa. Para fazer isso, é possível usar uma fonte com um `TResult` fictício (<xref:System.Boolean> é uma boa opção padrão, mas se você estiver preocupado sobre o usuário que fará downcast da <xref:System.Threading.Tasks.Task> para uma <xref:System.Threading.Tasks.Task%601>, poderá, em vez disso, usar um tipo `TResult` particular). Por exemplo, o método `Delay` no exemplo anterior retorna a hora atual com o deslocamento resultante (`Task<DateTimeOffset>`). Se esse valor de resultado for desnecessário, o método poderia então ser codificado da seguinte maneira (observe a alteração de tipo de retorno e a alteração de argumento para <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A>):

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>Mistas tarefas associadas à computação e vinculada a e/S
Os métodos assíncronos não estão limitados apenas a operações associadas ao cálculo ou associadas à E/S, mas podem representar uma mistura das duas. Na verdade, várias operações assíncronas são geralmente combinadas em operações mistas maiores. Por exemplo, o método `RenderAsync` em um exemplo anterior executou uma operação que exige muitos recursos computacionais para renderizar uma imagem com base em algumas entradas `imageData`. Essa `imageData` poderia ser proveniente de um serviço da web que você acessa de forma assíncrona:

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

Esse exemplo também demonstra como um token de cancelamento único pode ser encadeado por meio de várias operações assíncronas. Para obter mais informações, consulte a seção uso cancelamento [consumindo o padrão assíncrono baseado em tarefa](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

## <a name="see-also"></a>Consulte também
 [TAP (Padrão Assíncrono Baseado em Tarefa)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Consumindo o padrão assíncrono baseado em tarefa](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)  
 [Interoperabilidade com outros tipos e padrões assíncronos](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)  
