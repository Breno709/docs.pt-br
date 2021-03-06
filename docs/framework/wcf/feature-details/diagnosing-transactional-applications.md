---
title: Diagnosticando aplicativos transacionais
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0826881bac88f2bfa933ae71b798186dafc55303
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="diagnosing-transactional-applications"></a>Diagnosticando aplicativos transacionais
Este tópico descreve como usar o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] recurso de gerenciamento e diagnóstico para solucionar problemas de um aplicativo transacional.  
  
## <a name="performance-counters"></a>Contadores de desempenho  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um conjunto padrão de contadores de desempenho para medir o desempenho do seu aplicativo transacional. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Contadores de desempenho](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
 Contadores de desempenho têm como escopo três níveis diferentes: de serviço, ponto de extremidade e operação, conforme descrito nas tabelas a seguir.  
  
### <a name="service-performance-counters"></a>Contadores de desempenho de serviço  
  
|Contador de desempenho|Descrição|  
|-------------------------|-----------------|  
|Fluxo de transações|O número de transações que fluíram para operações neste serviço. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o serviço.|  
|Fluxo de transações por segundo|O número de transações que fluíram para operações neste serviço dentro de cada segundo. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o serviço.|  
|Operações Transacionadas Confirmadas|O número de operações realizadas executada, cuja transação foi concluída com resultados confirmados neste serviço. O trabalho feito nessas operações é totalmente confirmado. Os recursos são atualizados de acordo com o trabalho feito na operação.|  
|Operações Transacionadas Confirmadas por Segundo|O número de operações realizadas executada, cuja transação foi concluída com resultados confirmados neste serviço dentro de cada segundo. O trabalho feito nessas operações é totalmente confirmado. Os recursos são atualizados de acordo com o trabalho feito na operação.|  
|Operações de transação abortadas|O número de operações realizadas executada, cuja transação foi concluída com resultados anulados neste serviço. Trabalho feito nessas operações é revertido. Os recursos são revertidos ao seu estado anterior.|  
|Operações Transacionadas Anuladas por Segundo|O número de operações realizadas executada, cuja transação foi concluída com resultados anulados neste serviço dentro de cada segundo. Trabalho feito nessas operações é revertido. Os recursos são revertidos ao seu estado anterior.|  
|Operações Transacionadas em Dúvida|O número de operações realizadas executada, cuja transação foi concluída com resultados em dúvida neste serviço. Trabalho com resultados em dúvida está em um estado indeterminado. Os recursos são mantidos com resultado pendente.|  
|Operações Transacionadas em Dúvida por Segundo|O número de operações realizadas executada, cuja transação tiver sido concluído com resultados em dúvida neste serviço em cada segundo. Trabalho com resultados em dúvida está em um estado indeterminado. Os recursos são mantidos com resultado pendente.|  
  
### <a name="endpoint-performance-counters"></a>Contadores de desempenho de ponto de extremidade  
  
|Contador de desempenho|Descrição|  
|-------------------------|-----------------|  
|Fluxo de transações|O número de transações que fluíram para operações neste ponto de extremidade. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o ponto de extremidade.|  
|Fluxo de transações por segundo|O número de transações que fluíram para operações neste ponto de extremidade dentro de cada segundo. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o ponto de extremidade.|  
  
### <a name="operation-performance-counters"></a>Contadores de desempenho de operação  
  
|Contador de desempenho|Descrição|  
|-------------------------|-----------------|  
|Fluxo de transações|O número de transações que fluíram para operações neste ponto de extremidade. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o ponto de extremidade.|  
|Fluxo de transações por segundo|O número de transações que fluíram para operações neste ponto de extremidade dentro de cada segundo. Esse contador é incrementado sempre que uma transação está presente na mensagem que é enviada para o ponto de extremidade.|  
  
## <a name="windows-management-instrumentation"></a>Instrumentação de gerenciamento do Windows  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]expõe dados de inspeção de um serviço em tempo de execução por meio de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provedor do Windows Management Instrumentation (WMI). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Acessando dados do WMI, consulte [usando o Windows Management Instrumentation para diagnóstico](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 Um número de propriedades somente leitura do WMI indicar as configurações aplicadas de transação para um serviço. As tabelas a seguir listam todas essas configurações.  
  
 Em um serviço, o `ServiceBehaviorAttribute` tem as seguintes propriedades.  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boolean|Especifica se o objeto de serviço será reciclado quando a transação atual seja concluída.|  
|TransactionAutoCompleteOnSessionClose|Boolean|Especifica se as transações pendentes a são concluídos quando fecha a sessão atual.|  
|TransactionIsolationLevel|Uma cadeia de caracteres que contém um valor válido de <xref:System.Transactions.IsolationLevel> enumeração.|Especifica o nível de isolamento de transação que oferece suporte a esse serviço.|  
|TransactionTimeout|<xref:System.DateTime>|Especifica o período no qual uma transação deve ser concluída.|  
  
 O `ServiceTimeoutsBehavior` tem a propriedade a seguir.  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|Especifica o período no qual uma transação deve ser concluída.|  
  
 Em uma associação, o `TransactionFlowBindingElement` tem as seguintes propriedades.  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|transactionProtocol|Uma cadeia de caracteres que contém um valor válido de <xref:System.ServiceModel.TransactionProtocol> tipo.|Especifica o protocolo de transação a ser usado em uma transação de fluxo.|  
|TransactionFlow|Boolean|Especifica se o fluxo de transação de entrada está habilitado.|  
  
 Em uma operação, o `OperationBehaviorAttribute` tem as seguintes propriedades:  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|TransactionAutoComplete|Boolean|Especifica se deve confirmar a transação atual automaticamente se nenhuma exceção não tratada ocorrer.|  
|TransactionScopeRequired|Boolean|Especifica se a operação exige uma transação.|  
  
 Em uma operação, o `TransactionFlowAttribute` tem as seguintes propriedades.  
  
|Nome|Tipo|Descrição|  
|----------|----------|-----------------|  
|TransactionFlowOption|Uma cadeia de caracteres que contém um valor válido de <xref:System.ServiceModel.TransactionFlowOption> enumeração.|Especifica a extensão para qual transação fluxo é necessário.|  
  
## <a name="tracing"></a>Rastreamento  
 Rastreamentos permitem monitorar e analisar falhas em seus aplicativos transacionais. Você pode habilitar rastreamento usando das seguintes maneiras:  
  
-   Padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rastreamento  
  
     Esse tipo de rastreamento é o mesmo que rastreamento qualquer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Rastreamento de WS-AtomicTransaction  
  
     Rastreamento de WS-AtomicTransaction pode ser habilitado usando o [o utilitário de configuração do WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Tal rastreamento fornece informações sobre o estado de transações e participantes dentro de um sistema. Para habilitar o rastreamento de modelo de serviço interno também, você pode definir o `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` chave do registro para um valor válido do <xref:System.Diagnostics.SourceLevels> enumeração. Você pode habilitar a mensagem de log da mesma maneira que outras [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos.  
  
-   `System.Transactions`rastreamento  
  
     Ao usar o protocolo OleTransactions, mensagens de protocolo não podem ser rastreadas. O suporte de rastreamento de <xref:System.Transactions> fornece infraestrutura (que usa OleTransactions) permite aos usuários visualizar eventos que ocorreram nas transações. Para habilitar o rastreamento para uma <xref:System.Transactions> aplicativo, incluem o seguinte código no `App.config` arquivo de configuração.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     Isso também permite que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rastreamento, como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também utiliza o <xref:System.Transactions> infraestrutura.  
  
## <a name="see-also"></a>Consulte também  
 [Administração e diagnósticos](../../../../docs/framework/wcf/diagnostics/index.md)  
 [Configurando o rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Utilitário de configuração de WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
