---
title: "Método ISymUnmanagedMethod::GetSequencePoints"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 071cbb6c33b56cb4fb409ab634a89f589db5bab8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>Método ISymUnmanagedMethod::GetSequencePoints
Obtém todos os pontos de sequência dentro desse método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cPoints`  
 [in] Um `ULONG32` que recebe o tamanho do `offsets`, `documents`, `lines`, `columns`, `endLines`, e `endColumns` matrizes.  
  
 `pcPoints`  
 [out] Um ponteiro para um `ULONG32` que recebe o comprimento do buffer necessário para conter os pontos de sequência.  
  
 `offsets`  
 [in] Uma matriz na qual deseja armazenar o Microsoft intermediate language (MSIL) desloca desde o início do método para os pontos de sequência.  
  
 `documents`  
 [in] Uma matriz na qual deseja armazenar os documentos em que os pontos de sequência estão localizados.  
  
 `lines`  
 [in] Uma matriz na qual deseja armazenar as linhas nos documentos em que os pontos de sequência estão localizados.  
  
 `columns`  
 [in] Uma matriz na qual deseja armazenar as colunas nos documentos em que os pontos de sequência estão localizados.  
  
 `endLines`  
 [in] A matriz de linhas nos documentos em que a sequência de pontos finais.  
  
 `endColumns`  
 [in] A matriz de colunas nos documentos em que a sequência de pontos finais.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
