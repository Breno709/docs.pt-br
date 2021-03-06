---
title: Aplicativos multithread (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 19a4fe40e27a9edf8515e2734914aaf02d5e48b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="multithreaded-applications-visual-basic"></a>Aplicativos multithread (Visual Basic)
Com o Visual Basic, você pode escrever aplicativos que executam várias tarefas ao mesmo tempo. Tarefas com o potencial de atrasar outras tarefas podem ser executadas em threads separados, um processo conhecido como *multithreading* ou *free threading*.  
  
 Aplicativos que usam multithreading são mais responsivos a entradas do usuário porque a interface do usuário permanece ativa, enquanto tarefas com uso intensivo do processador são executadas em threads separados. O multithreading também é útil quando você cria aplicativos escalonáveis, porque você pode adicionar threads conforme a carga de trabalho aumenta.  
  
## <a name="creating-and-using-threads"></a>Criando e usando threads  
 Se precisar de mais controle sobre o comportamento dos threads de seu aplicativo, você pode gerenciar os threads por conta própria. No entanto, observe que escrever aplicativos multi-threaded corretamente pode ser difícil: o aplicativo pode parar de responder ou passar por erros transitórios causados por condições de corrida. Para obter mais informações, veja [Componentes thread-safe](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).  
  
 Você cria um novo thread declarando uma variável do tipo <xref:System.Threading.Thread> e chamando o construtor, fornecendo o nome do procedimento ou método que deseja executar no novo thread. O código a seguir fornece um exemplo.  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### <a name="starting-and-stopping-threads"></a>Iniciando e parando threads  
 Para iniciar a execução de um novo thread, use o método <xref:System.Threading.Thread.Start%2A>, conforme mostrado no código a seguir.  
  
```vb  
newThread.Start()  
```  
  
 Para interromper a execução de um thread, use o método <xref:System.Threading.Thread.Abort%2A>, conforme mostrado no código a seguir.  
  
```vb  
newThread.Abort()  
```  
  
 Além de iniciar e parar threads, você também pode pausar threads chamando o método <xref:System.Threading.Thread.Sleep%2A> ou <xref:System.Threading.Thread.Suspend%2A>, retomar um thread suspenso usando o método <xref:System.Threading.Thread.Resume%2A> e destruir um thread usando o método <xref:System.Threading.Thread.Abort%2A>  
  
### <a name="thread-methods"></a>Métodos de thread  
 A tabela a seguir mostra alguns dos métodos que você pode usar para controlar segmentos individuais.  
  
|Método|Ação|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|Faz com que um thread comece a ser executado.|  
|<xref:System.Threading.Thread.Sleep%2A>|Pausa um thread por um período especificado.|  
|<xref:System.Threading.Thread.Suspend%2A>|Pausa um thread quando ele atinge um ponto de segurança.|  
|<xref:System.Threading.Thread.Abort%2A>|Para um thread quando ele atinge um ponto de segurança.|  
|<xref:System.Threading.Thread.Resume%2A>|Reinicia um thread suspenso|  
|<xref:System.Threading.Thread.Join%2A>|Faz com que o thread atual aguarde até que outro thread seja finalizado. Se for usado com um valor de tempo limite, este método retorna `True` se o thread terminar no tempo alocado.|  
  
### <a name="safe-points"></a>Pontos de segurança  
 A maioria desses métodos são autoexplicativos, mas o conceito de *pontos de segurança* pode ser novidade para você. Pontos de segurança são locais no código em que é seguro para o Common Language Runtime executar a *coleta de lixo* automática, que é o processo de liberar variáveis não utilizadas e recuperar memória. Quando você chama o método <xref:System.Threading.Thread.Abort%2A> ou <xref:System.Threading.Thread.Suspend%2A> de um thread, o Common Language Runtime analisa o código e determina o local apropriado para o thread parar a execução.  
  
### <a name="thread-properties"></a>Propriedades da Thread  
 Threads também contêm diversas propriedades úteis, como mostrado na tabela a seguir:  
  
|Propriedade|Valor|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Contém o valor `True` se um thread estiver ativo.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Obtém ou define um valor booliano que indica se um thread é ou deve ser um thread de segundo plano. Threads de segundo plano são como threads de primeiro plano, mas um thread de segundo plano não impede que um processo pare. Após todos os threads de primeiro plano que pertencem a um processo serem parados, o Common Language Runtime finaliza o processo chamando o método <xref:System.Threading.Thread.Abort%2A> em threads em segundo plano que ainda estão ativos.|  
|<xref:System.Threading.Thread.Name%2A>|Obtém ou define o nome de um thread. Usado com mais frequência para descobrir threads individuais quando você depura.|  
|<xref:System.Threading.Thread.Priority%2A>|Obtém ou define um valor usado pelo sistema operacional para priorizar agendamento de threads.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Contém um valor que descreve o estado ou estados de um thread.|  
  
## <a name="thread-priorities"></a>Prioridades do thread  
 Cada thread tem uma propriedade de prioridade que determina quanto tempo do processador ele tem para ser executado. O sistema operacional aloca frações de tempo maiores para segmentos de maior prioridade e frações de tempo mais curtas para segmentos de menor prioridade. Novos segmentos são criados com o valor de `Normal`, mas você pode alterar a propriedade <xref:System.Threading.Thread.Priority%2A> para qualquer valor na enumeração <xref:System.Threading.ThreadPriority>.  
  
 Consulte <xref:System.Threading.ThreadPriority> para obter uma descrição detalhada sobre as várias prioridades de thread.  
  
## <a name="foreground-and-background-threads"></a>Threads em primeiro plano e em segundo plano  
 Um *thread de primeiro plano* é executado indefinidamente, enquanto um *thread de segundo plano* para assim que o último thread do primeiro plano parar. Você pode usar a propriedade <xref:System.Threading.Thread.IsBackground%2A> para determinar ou alterar o status em segundo plano de um thread.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread>  
 [Sincronização de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Parâmetros e valores de retorno para procedimentos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)  
 [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)
