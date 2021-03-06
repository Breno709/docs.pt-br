---
title: "Método ICorDebug::SetUnmanagedHandler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.SetUnmanagedHandler
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c1b6da9db047321583de8c3c9238ed9ad4d4ec6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsetunmanagedhandler-method"></a>Método ICorDebug::SetUnmanagedHandler
Especifica o objeto do manipulador de eventos para eventos não gerenciados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCallback`  
 [in] Um ponteiro para um [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) objeto que representa o manipulador de eventos para eventos não gerenciados.  
  
## <a name="remarks"></a>Comentários  
 O manipulador de eventos de objeto para não gerenciado eventos devem ser definidos após uma chamada para [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) e antes de qualquer chamada para [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) ou [: DebugActiveProcess ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md). No entanto, para fins de legado não são necessário definir o objeto do manipulador de eventos para eventos não gerenciados até que o primeiro evento de depuração nativo seja gerado. Especificamente, se `ICorDebug::CreateProcess` definiu o sinalizador CREATE_SUSPENDED, depuração nativo não podem ser distribuídos eventos até que o thread principal seja retomado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
