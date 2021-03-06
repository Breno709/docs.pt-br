---
title: elemento &lt;synchronousReceive&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63923121ae96b85bd192899a8d8ad285a3ad5b2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsynchronousreceivegt-element"></a>elemento &lt;synchronousReceive&gt;
Este elemento de configuração é usado para especificar o comportamento de tempo de execução para receber mensagens em um cliente ou serviço de aplicativo. Ele não tem atributos ou elementos filho.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
\<endpointBehaviors >  
\<comportamento >  
\<synchronousReceive >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Use esse comportamento para instruir o ouvinte de canal para usar um síncrono receber, em vez do padrão assíncrono. [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]emite um novo thread para a bomba de cada canal aceito. Se houver muita canais, há a possibilidade de falta de threads.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
