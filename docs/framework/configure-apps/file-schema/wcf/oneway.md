---
title: '&lt;Unidirecional&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 79dd5dd0ca383cebc5f08f3e12c6c6261d11a02a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltonewaygt"></a>&lt;Unidirecional&gt;
Permite que o roteamento de pacotes e o uso de métodos unidirecionais para uma associação personalizada.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<oneWay >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`packetRoutable`|Um valor booleano que especifica se o roteamento de pacotes está habilitado. O padrão é `false`.|  
|`MaxAcceptedChannels`|Um inteiro que especifica o número máximo de canais que podem ser aceitos.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<channelPoolSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|Um <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> objeto que contém as propriedades do pool de canal para o canal atual.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Para habilitar o roteamento de pacotes, uma camada de conversão unidirecional é necessária, que fornece este elemento. Um usuário pode criar uma associação personalizada que camadas essa ligação por um transporte de reconhecimento de sessão ou de solicitação-resposta para torná-lo pacote roteável. Esse elemento também é útil quando você deseja expor métodos unidirecionais de forma mais nativo. Mais transformações podem ser aplicadas por essa camada, como Duplex compostos e sistema de mensagens confiável.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)