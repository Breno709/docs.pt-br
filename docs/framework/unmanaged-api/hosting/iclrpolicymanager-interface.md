---
title: Interface ICLRPolicyManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager
helpviewer_keywords: ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce37f9beb0901eaf1bc98f5af3f8f99a7fedf1c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanager-interface"></a>Interface ICLRPolicyManager
Fornece métodos que permitem que o host especificar ações de política a ser executada no caso de falhas e tempos limite.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|Especifica a ação de política, que o common language runtime (CLR) deve ser executada quando ocorre a falha especificada.|  
|[Método SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|Especifica a ação de política que CLR deve ser executada quando a operação especificada expire.|  
|[Método SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|Especifica a ação de política que CLR deve ser executada quando ocorre a operação especificada.|  
|[Método SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|Define um valor de tempo limite para a operação especificada.|  
|[Método SetTimeoutAndAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|Define um valor de tempo limite para a operação especificada e especifica a ação de política que CLR deve ser executada quando ocorre a operação.|  
|[Método SetUnhandledExceptionPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|Especifica o comportamento do CLR quando ocorre uma exceção sem tratamento.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumeração EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [Enumeração EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [Enumeração EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
