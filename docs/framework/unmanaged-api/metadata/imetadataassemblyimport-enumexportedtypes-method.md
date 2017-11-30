---
title: "Método IMetaDataAssemblyImport::EnumExportedTypes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumExportedTypes
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76c73cc3d13089b4a38a47d523d8baa77f6eed12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="b9a4c-102">Método IMetaDataAssemblyImport::EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="b9a4c-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="b9a4c-103">Enumera os tipos exportados referenciados no manifesto do assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="b9a4c-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a4c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9a4c-104">Syntax</span></span>  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9a4c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9a4c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b9a4c-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="b9a4c-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b9a4c-107">Isso deve ser nulo quando o `EnumExportedTypes` método é chamado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="b9a4c-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="b9a4c-108">[out] A enumeração de `mdExportedType` tokens de metadados.</span><span class="sxs-lookup"><span data-stu-id="b9a4c-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b9a4c-109">[in] O número máximo de `mdExportedType` tokens que podem ser colocados no `rExportedTypes` matriz.</span><span class="sxs-lookup"><span data-stu-id="b9a4c-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b9a4c-110">[out] O número de `mdExportedType` tokens realmente realizada em `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="b9a4c-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9a4c-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b9a4c-111">Return Value</span></span>  
  
|<span data-ttu-id="b9a4c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9a4c-112">HRESULT</span></span>|<span data-ttu-id="b9a4c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9a4c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b9a4c-114">`EnumExportedTypes`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b9a4c-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b9a4c-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="b9a4c-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b9a4c-116">Nesse caso, `pcTokens` é definido como zero.</span><span class="sxs-lookup"><span data-stu-id="b9a4c-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9a4c-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9a4c-117">Requirements</span></span>  
 <span data-ttu-id="b9a4c-118">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9a4c-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9a4c-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b9a4c-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9a4c-120">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b9a4c-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9a4c-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9a4c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a4c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9a4c-122">See Also</span></span>  
 [<span data-ttu-id="b9a4c-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="b9a4c-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)