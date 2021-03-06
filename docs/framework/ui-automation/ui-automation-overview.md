---
title: "Visão geral de automação da interface do usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
caps.latest.revision: "35"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d86c70ec4421bc716b12044bac30f8f925c375f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-overview"></a>Visão geral de automação da interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]é a nova estrutura de acessibilidade para [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)], disponível em todos os sistemas operacionais que oferecem suporte a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]fornece acesso programático à maioria [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] fornecem informações sobre os leitores de tela de elementos na área de trabalho, permitindo que produtos de tecnologia assistencial, como o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] para os usuários finais e manipular o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] por meio diferente de entrada padrão. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]também permite que scripts de teste automatizado interagir com o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]não permitir a comunicação entre processos iniciados por diferentes usuários por meio de **executar como** comando.  
  
 Aplicativos de cliente de automação de interface do usuário podem ser gravados com a garantia de que eles funcionarão em vários frameworks. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core esconde as diferenças nos frameworks subjacentes várias partes da [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Por exemplo, o `Content` propriedade de um [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] botão, o `Caption` propriedade de um [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] botão e o `ALT` propriedade de uma imagem HTML são mapeadas para uma única propriedade, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] exibição.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]fornece a funcionalidade completa no [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)], e [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 Provedores de automação de interface do usuário oferecem algum suporte para [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] aplicativos de cliente, por meio de um serviço interno de ponte.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Provedores e clientes  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tem quatro componentes principais, conforme mostrado na tabela a seguir.  
  
|Componente|Descrição|  
|---------------|-----------------|  
|Provedor [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] (UIAutomationProvider e UIAutomationTypes. dll)|Um conjunto de definições de interface que são implementadas por provedores de automação de interface do usuário, objetos que fornecem informações sobre [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos e respondem a entrada programática.|  
|Cliente API (UIAutomationClient. dll e UIAutomationTypes. dll)|Um conjunto de tipos para código gerenciado que permite que aplicativos de cliente de automação de interface do usuário obter informações sobre o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] e enviem dados de entrada para controles.|  
|UIAutomationCore|O código subjacente (às vezes chamado de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core) que gerencia a comunicação entre clientes e provedores.|  
|UIAutomationClientsideProviders|Um conjunto de provedores de automação de interface do usuário para controles padrão herdados. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controles têm suporte nativo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Esse suporte está automaticamente disponível para aplicativos cliente.|  
  
 Do ponto de vista do desenvolvedor de software, há duas maneiras de usar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: para criar suporte para controles personalizados (usando a API de provedor) e criar aplicativos que usam o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] principal para se comunicar com [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos (usando a API de cliente). Dependendo de seu foco, consulte a diferentes partes da documentação. Você pode aprender mais sobre os conceitos e adquirir conhecimento prático nas seções a seguir.  
  
|Seção|Assunto|Público-alvo|  
|-------------|--------------------|--------------|  
|[Fundamentos de automação de interface do usuário](../../../docs/framework/ui-automation/index.md) (Esta seção)|Ampla visão geral dos conceitos.|Todos os.|  
|[UI Automation Providers for Managed Code](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md) (Provedores da Automação da Interface do Usuário para código gerenciado)|Visões gerais e tópicos de instruções para ajudá-lo a usar a API de provedor.|Desenvolvedores de controle.|  
|[UI Automation Clients for Managed Code](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md) (Clientes da Automação da Interface do Usuário para código gerenciado)|Visões gerais e tópicos de instruções para ajudá-lo a usar a API do cliente.|Desenvolvedores de aplicativos do cliente.|  
|[UI Automation Control Patterns](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) (Padrões de controle da Automação da Interface do Usuário)|Informações sobre como os padrões de controle devem ser implementados por provedores e qual funcionalidade está disponível para clientes.|Todos os.|  
|[UI Automation Text Pattern](../../../docs/framework/ui-automation/ui-automation-text-pattern.md) (Padrão de texto da Automação da Interface do Usuário)|Informações sobre como o padrão de controle de texto deve ser implementado pelos provedores, e qual funcionalidade está disponível para clientes.|Todos os.|  
|[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)|Informações sobre as propriedades e padrões de controle suportados pelos diferentes tipos de controle.|Todos os.|  
  
 A seguinte tabela lista [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] namespaces, as DLLs que contêm-los e o público que usa.  
  
|Namespace|DLLs referenciados|Público-alvo|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Desenvolvedores de cliente de automação de interface do usuário; usado para localizar <xref:System.Windows.Automation.AutomationElement> de registro de objetos, para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos e trabalhar com [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] padrões de controle.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Os desenvolvedores de provedores de automação de interface do usuário para estruturas de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Os desenvolvedores de provedores de automação de interface do usuário para estruturas de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]; usado para implementar o padrão de controle TextPattern.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Os desenvolvedores de provedores de automação de interface do usuário para [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Modelo de automação de interface do usuário  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]expõe cada parte do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] para aplicativos cliente como um <xref:System.Windows.Automation.AutomationElement>. Elementos estão contidos em uma estrutura de árvore, com a área de trabalho como o elemento raiz. Os clientes podem filtrar a exibição bruta da árvore como um modo de exibição de controle ou conteúdo. Aplicativos também podem criar exibições personalizadas.  
  
 <xref:System.Windows.Automation.AutomationElement>objetos expõem propriedades comuns a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos representam. Uma dessas propriedades é o tipo de controle, que define sua aparência e funcionalidade básicas como uma única entidade reconhecível: por exemplo, um botão ou caixa de seleção.  
  
 Além disso, os elementos expõem os padrões de controle que fornecem propriedades específicas para seus tipos de controle. Padrões de controle também expõem métodos que permitem que os clientes para obter mais informações sobre o elemento e para fornecer entrada.  
  
> [!NOTE]
>  Não há uma correspondência entre tipos de controle e padrões de controle. Um padrão de controle pode ser suportado por vários tipos de controle e um controle pode oferecer suporte a vários padrões de controle, cada um deles expõe diferentes aspectos de seu comportamento. Por exemplo, uma caixa de combinação tem pelo menos dois padrões de controle: uma que representa sua capacidade de expandir e recolher e outra que representa o mecanismo de seleção. Para obter informações específicas, consulte [tipos de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]também fornece informações para aplicativos de cliente por meio de eventos. Ao contrário de [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)], [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos não são baseados em um mecanismo de difusão. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]os clientes se registrar para notificações de evento específico e pode solicitar que específico [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações de padrão de controle e propriedades passado para seus manipuladores de eventos. Além disso, um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento contém uma referência ao elemento que o gerou. Provedores podem melhorar o desempenho gerando eventos seletivamente, dependendo se todos os clientes estão escutando.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Visão geral de propriedades de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)  
 [Visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md)  
 [Visão geral de segurança de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
