---
title: "Método ICorDebugHeapValue3::GetThreadOwningMonitorLock"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a2198e54c764fde0248563b040ac98984001888
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>Método ICorDebugHeapValue3::GetThreadOwningMonitorLock
Retorna o thread gerenciado que possui o bloqueio de monitor nesse objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppThread`  
 [out] O thread gerenciado que possui o bloqueio de monitor nesse objeto.  
  
 `pAcquisitionCount`  
 [out] O número de vezes que esse thread precisa liberar o bloqueio antes de retornar para sendo sem proprietário.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|S_FALSE|Nenhum thread gerenciado possui o bloqueio de monitor nesse objeto.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 Se um thread gerenciado possui o bloqueio de monitor nesse objeto:  
  
-   O método retorna S_OK.  
  
-   O objeto de thread é válido até que o thread será encerrado.  
  
 Se nenhum thread gerenciado possui o bloqueio de monitor nesse objeto `ppThread` e `pAcquisitionCount` foram modificados, e o método retornará S_FALSE.  
  
 Se `ppThread` ou `pAcquisitionCount` não é um ponteiro válido, o resultado é indefinido.  
  
 Se ocorrer um erro, de modo que ele não pode ser determinado que, se houver, thread possui o bloqueio de monitor nesse objeto, o método retorna um HRESULT que indica falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
