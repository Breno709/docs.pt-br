---
title: "Visão geral dos primitivos de sincronização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58fb520365d0a80a8f8bc46e3fdbd23483fdf07f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-synchronization-primitives"></a>Visão geral dos primitivos de sincronização
<a name="top"></a>O .NET Framework fornece uma variedade de primitivos de sincronização para controlar as interações de threads e evitar condições de corrida. Eles podem ser divididos em três categorias: operações interliconectadas, sinalização e bloqueio.  
  
 As categorias não estão claramente definidas nem organizadas. Alguns mecanismos de sincronização têm características de várias categorias; eventos que liberam um único thread em um momento são funcionalmente como bloqueios; a versão de qualquer bloqueio pode ser considerada como um sinal; e operações interconectadas podem ser usadas para construir bloqueios. No entanto, as categorias ainda são úteis.  
  
 É importante lembrar que a sincronização de threads é cooperativa. Se um thread ignora um mecanismo de sincronização e acessa diretamente o recurso protegido, esse mecanismo de sincronização não pode ser eficaz.  
  
 Esta visão geral contém as seguintes seções:  
  
-   [Bloqueio](#locking)  
  
-   [Sinalização](#signaling)  
  
-   [Tipos de sincronização leve](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Operações interconectadas](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>Bloqueio  
 Bloqueios oferecem controle de um recurso para um thread por vez, ou para um número especificado de threads. Um thread que solicita um bloqueio exclusivo quando o bloqueio está sendo usado permanece bloqueado até o bloqueio ficar disponível.  
  
### <a name="exclusive-locks"></a>Bloqueios exclusivos  
 A forma mais simples de bloqueio é a instrução `lock` em C# e a instrução `SyncLock` no Visual Basic, que controla o acesso a um bloco de código. Tal bloco é normalmente chamado de seção crítica. O `lock` instrução é implementada usando o <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> métodos e usa `try…catch…finally` bloco para garantir que o bloqueio seja liberado.  
  
 Em geral, usando o `lock` ou `SyncLock` instrução para proteger pequenos blocos de código, nunca abrangendo mais de um único método, é a melhor maneira de usar o <xref:System.Threading.Monitor> classe. Embora eficiente, o <xref:System.Threading.Monitor> classe é propenso a deadlocks e bloqueios órfãos.  
  
#### <a name="monitor-class"></a>Classe Monitor  
 O <xref:System.Threading.Monitor> classe fornece funcionalidade adicional, que pode ser usada em conjunto com o `lock` instrução:  
  
-   O <xref:System.Threading.Monitor.TryEnter%2A> método permite que um thread que está bloqueado, aguardando recursos desista após um intervalo especificado. Ele retorna um valor booliano que indica êxito ou falha, que pode ser usado para detectar e evitar deadlocks potenciais.  
  
-   O <xref:System.Threading.Monitor.Wait%2A> método é chamado por um thread em uma seção crítica. Ele fornece controle de recursos e blocos até que o recurso esteja disponível novamente.  
  
-   O <xref:System.Threading.Monitor.Pulse%2A> e <xref:System.Threading.Monitor.PulseAll%2A> métodos permitem que um thread que está prestes a liberar o bloqueio ou chamar <xref:System.Threading.Monitor.Wait%2A> para colocar um ou mais threads na fila de pronto, para que eles podem adquirir o bloqueio.  
  
 Tempos limite na <xref:System.Threading.Monitor.Wait%2A> sobrecargas do método permitem que os threads de espera pular para a fila de pronta.  
  
 O <xref:System.Threading.Monitor> classe pode fornecer o bloqueio em vários domínios de aplicativo se o objeto usado para o bloqueio é derivado de <xref:System.MarshalByRefObject>.  
  
 <xref:System.Threading.Monitor>tem afinidade de thread. Ou seja, um thread que inseriu o monitor deve sair chamando <xref:System.Threading.Monitor.Exit%2A> ou <xref:System.Threading.Monitor.Wait%2A>.  
  
 O <xref:System.Threading.Monitor> classe não é pode ser instanciado. Seus métodos são estáticos (`Shared` no Visual Basic) e afetam um objeto de bloqueio que pode ser instanciado.  
  
 Para obter uma visão conceitual, consulte [Monitores](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
#### <a name="mutex-class"></a>Classe Mutex  
 Solicitação de threads um <xref:System.Threading.Mutex> chamando uma sobrecarga de seu <xref:System.Threading.WaitHandle.WaitOne%2A> método. Sobrecargas com tempos limite são fornecidas para permitir que os threads desistam da espera. Ao contrário de <xref:System.Threading.Monitor> classe mutex pode ser local ou global. Global mutexes, também chamados de mutexes nomeados, são visíveis em todo o sistema operacional e podem ser usados para sincronizar threads em vários domínios de aplicativos ou processos. Locais mutexes derivam <xref:System.MarshalByRefObject>e pode ser usado nos limites do domínio de aplicativo.  
  
 Além disso, <xref:System.Threading.Mutex> deriva <xref:System.Threading.WaitHandle>, que significa que ele pode ser usado com os mecanismos de sinalização fornecidos pelo <xref:System.Threading.WaitHandle>, como o <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, e <xref:System.Threading.WaitHandle.SignalAndWait%2A> métodos.  
  
 Como <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> tem afinidade de thread. Ao contrário de <xref:System.Threading.Monitor>, um <xref:System.Threading.Mutex> é um objeto pode ser instanciado.  
  
 Para obter uma visão conceitual, consulte [Mutexes](../../../docs/standard/threading/mutexes.md).  
  
#### <a name="spinlock-class"></a>Classe de SpinLock  
 Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar o <xref:System.Threading.SpinLock> classe quando necessários para a sobrecarga <xref:System.Threading.Monitor> degrada o desempenho. Quando <xref:System.Threading.SpinLock> encontra uma seção crítica bloqueada, ele simplesmente gira em um loop até que o bloqueio esteja disponível. Se o bloqueio for mantido por um período muito curto, a rotação pode fornecer melhor desempenho do que o bloqueio. No entanto, se o bloqueio é mantido por mais de algumas dezenas de ciclos de <xref:System.Threading.SpinLock> executa tão bem como <xref:System.Threading.Monitor>, mas usará mais ciclos de CPU e, portanto, pode degradar o desempenho de outros processos ou threads.  
  
### <a name="other-locks"></a>Outros bloqueios  
 Os bloqueios não precisam ser exclusivos. Normalmente é útil permitir que um número limitado de threads acesse simultaneamente um recurso. Semaphores e bloqueios de leitor-gravador são criados para controlar esse tipo de acesso a recursos em pool.  
  
#### <a name="readerwriterlock-class"></a>Classe ReaderWriterLock  
 O <xref:System.Threading.ReaderWriterLockSlim> classe trata o caso em que um thread que as alterações de dados, o gravador, deve ter acesso exclusivo a um recurso. Quando o gravador não está ativo, qualquer número de leitores pode acessar o recurso (por exemplo, ao chamar o <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A> método). Quando um thread solicita acesso exclusivo (por exemplo, ao chamar o <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A> método), bloco de solicitações do leitor subsequentes até que todos os leitores existentes abandonaram o bloqueio e o gravador tem entrando e saindo do bloqueio.  
  
 <xref:System.Threading.ReaderWriterLockSlim>tem afinidade de thread.  
  
 Para obter uma visão conceitual, consulte [Bloqueios de leitor-gravador](../../../docs/standard/threading/reader-writer-locks.md).  
  
#### <a name="semaphore-class"></a>Classe Semaphore  
 O <xref:System.Threading.Semaphore> classe permite que um número especificado de threads para acessar um recurso. Threads adicionais solicitam o bloqueio de um recurso até que um thread libere o semaphore.  
  
 Como o <xref:System.Threading.Mutex> classe <xref:System.Threading.Semaphore> deriva de <xref:System.Threading.WaitHandle>. Além disso, como <xref:System.Threading.Mutex>, um <xref:System.Threading.Semaphore> pode ser local ou global. Ele pode ser usado nos limites do domínio de aplicativo.  
  
 Ao contrário de <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, e <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Semaphore> não tem afinidade de thread. Isso significa que ele pode ser usado em cenários onde um thread adquire o semaphore e o outro o libera.  
  
 Para obter uma visão conceitual, consulte [Semaphore e SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>é um semáforo leve para sincronização dentro de um limite de processo único.  
  
 [Voltar ao início](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>Sinalização  
 A maneira mais simples de espera para um sinal de outro thread é chamar o <xref:System.Threading.Thread.Join%2A> método, que bloqueia até que o outro thread seja concluída. <xref:System.Threading.Thread.Join%2A>tem duas sobrecargas que permitem que o thread bloqueado interromper a espera após um intervalo especificado tiver decorrido.  
  
 Identificadores de espera fornecem um conjunto mais avançado de recursos de espera e sinalização.  
  
### <a name="wait-handles"></a>Identificadores de espera  
 Identificadores de espera derivam o <xref:System.Threading.WaitHandle> classe, que por sua vez, deriva de <xref:System.MarshalByRefObject>. Assim, os identificadores de espera podem ser usados para sincronizar as atividades de threads entre limites de domínio de aplicativo.  
  
 Bloco de threads em espera manipula chamando o método de instância <xref:System.Threading.WaitHandle.WaitOne%2A> ou um dos métodos estáticos <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, ou <xref:System.Threading.WaitHandle.SignalAndWait%2A>. Como eles são liberados depende de qual método foi chamado e do tipo de identificadores de espera.  
  
 Para obter uma visão conceitual, consulte [Identificadores de espera](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489).  
  
#### <a name="event-wait-handles"></a>Identificadores de espera de eventos  
 Identificadores de espera de eventos incluem a <xref:System.Threading.EventWaitHandle> classe e suas classes derivadas, <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent>. Threads são liberadas de um identificador de espera de eventos quando o identificador de espera do evento é sinalizado chamando seu <xref:System.Threading.EventWaitHandle.Set%2A> método ou usando o <xref:System.Threading.WaitHandle.SignalAndWait%2A> método.  
  
 Os identificadores de espera de eventos são automaticamente redefinidos, como uma borboleta que permite que apenas um thread seja sinalizado de cada vez, ou deverão ser redefinidos manualmente, como uma entrada que é fechada até ser sinalizada e, em seguida, aberta até que alguém a feche. Como seus nomes sugerem, <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent> representar o primeiro e último, respectivamente. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>é um evento leve para sincronização dentro de um limite de processo único.  
  
 Um <xref:System.Threading.EventWaitHandle> pode representar qualquer tipo de evento e pode ser local ou global. As classes derivadas <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent> sempre são locais.  
  
 Identificadores de espera de eventos não têm afinidade de thread. Qualquer thread pode sinalizar um identificador de espera de eventos.  
  
 Para uma visão conceitual, consulte [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
#### <a name="mutex-and-semaphore-classes"></a>Classes Mutex e Semaphore  
 Porque o <xref:System.Threading.Mutex> e <xref:System.Threading.Semaphore> derivam de <xref:System.Threading.WaitHandle>, eles podem ser usados com os métodos estáticos de <xref:System.Threading.WaitHandle>. Por exemplo, um thread pode usar o <xref:System.Threading.WaitHandle.WaitAll%2A> método para aguardar até que todas as três condições a seguir forem verdadeiras: um <xref:System.Threading.EventWaitHandle> é sinalizado, uma <xref:System.Threading.Mutex> é liberado e um <xref:System.Threading.Semaphore> é liberado. Da mesma forma, um thread pode usar o <xref:System.Threading.WaitHandle.WaitAny%2A> método para aguardar até que qualquer uma dessas condições for verdadeira.  
  
 Para uma <xref:System.Threading.Mutex> ou <xref:System.Threading.Semaphore>, sendo sinalizado significa que está sendo liberado. Se o tipo é usado como o primeiro argumento do <xref:System.Threading.WaitHandle.SignalAndWait%2A> método, ele será liberado. No caso de um <xref:System.Threading.Mutex>, que tem afinidade de thread, uma exceção é gerada se o thread de chamada não possui o mutex. Conforme observado anteriormente, os semaphores não têm afinidade de thread.  
  
#### <a name="barrier"></a>Barreira  
 O <xref:System.Threading.Barrier> classe fornece uma maneira de sincronizar cyclically vários threads para que todos os blocos no mesmo ponto e aguarde até que todos os outros segmentos concluir. Uma barreira é útil quando um ou mais threads requerem os resultados de outro thread para poderem prosseguir para a próxima fase de um algoritmo. Para saber mais, consulte [Barreira](../../../docs/standard/threading/barrier.md).  
  
 [Voltar ao início](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>Tipos de sincronização leve  
 Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], você pode usar primitivos de sincronização que fornecem desempenho rápido, evitando a dispendiosa dependência de objetos do kernel do Win32, como identificadores de espera, sempre que possível. Em geral, você deve usar esses tipos quando os tempos de espera são curtos e somente quando os tipos de sincronização originais foram usados e considerados insatisfatórios. Os tipos leves não podem ser usados em cenários que exigem a comunicação entre processos.  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>é uma versão leve do <xref:System.Threading.Semaphore?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>é uma versão leve do <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType>representa um evento que se torna sinalizado quando sua contagem é zero.  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType>permite que vários threads sincronizar uns com os outros sem a necessidade de controle por um thread mestre. Uma barreira impede cada thread de continuar até que todos os threads atinjam um ponto especificado.  
  
 [Voltar ao início](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], você pode usar o <xref:System.Threading.SpinWait?displayProperty=nameWithType> estrutura quando um thread precisa aguardar um evento deve ser sinalizado ou uma condição a ser atendida, mas quando o tempo de espera real deve ser menor do que o tempo de espera necessário usando um identificador de espera ou otherwi Se o bloqueio do thread atual. Usando <xref:System.Threading.SpinWait>, você pode especificar um curto período de tempo para girar enquanto aguardava o e, em seguida, gerar (por exemplo, por espera ou suspensão) somente se a condição não foi atendida no tempo especificado.  
  
 [Voltar ao início](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>Operações interconectadas  
 As operações integradas são operações atômicas simples realizadas em um local de memória por métodos estáticos a <xref:System.Threading.Interlocked> classe. Essas operações atômicas incluem adição, incremento e decremento, troca, troca condicional (dependendo de uma comparação) e operações de leitura de valores de 64 bits em plataformas de 32 bits.  
  
> [!NOTE]
>  A garantia de atomicidade é limitada às operações individuais; quando várias operações devem ser executadas como uma unidade, um mecanismo de sincronização da mais alta granularidade deve ser usado.  
  
 Embora nenhuma dessas operações sejam bloqueios ou sinais, eles podem ser usadas para construir sinais e bloqueios. Como são nativas do sistema operacional Windows, as operações interconectadas são extremamente rápidas.  
  
 Operações interconectadas podem ser usadas com garantias de memória volátil para gravar aplicativos que apresentam simultaneidade eficiente sem bloqueio. No entanto, elas exigem programação sofisticada, de baixo nível, para a maioria das finalidades, portanto, bloqueios simples são uma opção melhor.  
  
 Para obter uma visão conceitual, consulte [Operações interconectadas](../../../docs/standard/threading/interlocked-operations.md).  
  
## <a name="see-also"></a>Consulte também  
 [Sincronizando dados para multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [Monitores](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [Mutexes](../../../docs/standard/threading/mutexes.md)  
 [Semaphore e SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Identificadores de espera](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [Operações interconectadas](../../../docs/standard/threading/interlocked-operations.md)  
 [Bloqueios de leitor-gravador](../../../docs/standard/threading/reader-writer-locks.md)  
 [Barreira](../../../docs/standard/threading/barrier.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
