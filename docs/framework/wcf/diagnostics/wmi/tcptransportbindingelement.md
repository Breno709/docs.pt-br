---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e230cbccee211fbda219000fbbd2cda5275776b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe TcpTransportBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe TcpTransportBindingElement tem as seguintes propriedades:  
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  
 Tipo de dados: TcpConnectionPoolSettings  
  
 Tipo de acesso: somente leitura  
  
 As configurações de pool de conexão.  
  
### <a name="listenbacklog"></a>ListenBacklog  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de solicitações de conexão em fila que podem estar pendentes.  
  
### <a name="portsharingenabled"></a>portSharingEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booleano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.  
  
### <a name="teredoenabled"></a>teredoEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booleano que especifica se Teredo (uma tecnologia para endereçar cliente que estão atrás de firewalls) está habilitado.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
