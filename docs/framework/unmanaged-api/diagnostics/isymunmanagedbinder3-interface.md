---
title: Interface ISymUnmanagedBinder3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3 Interface
helpviewer_keywords: ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c93275fc32e68f49618d93bdd0b54f1970121ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder3-interface"></a>Interface ISymUnmanagedBinder3
Estende a interface de associador de símbolo. Obter essa interface chamando `QueryInterface` em um objeto que implementa o `ISymUnmanagedBinder` interface.  
  
> [!IMPORTANT]
>  É um risco de segurança para abrir um arquivo de programa (PDB) de banco de dados de uma fonte não confiável.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|Permite que o usuário implementa ou fornecer por meio do retorno de chamada ou uma `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` para obter as informações de diretório de depuração da memória|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Interface ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [Interface ISymUnmanagedBinder2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
