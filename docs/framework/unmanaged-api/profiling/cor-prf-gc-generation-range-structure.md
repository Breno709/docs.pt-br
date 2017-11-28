---
title: Estrutura COR_PRF_GC_GENERATION_RANGE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_GENERATION_RANGE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords: COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e2fd546a88f34906ab37e36377f67c26e80b2799
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfgcgenerationrange-structure"></a><span data-ttu-id="ae7e5-102">Estrutura COR_PRF_GC_GENERATION_RANGE</span><span class="sxs-lookup"><span data-stu-id="ae7e5-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="ae7e5-103">Descreve um intervalo (ou seja, um bloco) de memória que está passando por coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ae7e5-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae7e5-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="ae7e5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ae7e5-105">Members</span></span>  
  
|<span data-ttu-id="ae7e5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ae7e5-106">Member</span></span>|<span data-ttu-id="ae7e5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae7e5-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="ae7e5-108">Um valor de [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeração que especifica a geração para o qual o bloco de memória pertence.</span><span class="sxs-lookup"><span data-stu-id="ae7e5-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="ae7e5-109">A ID de um objeto que especifica o local de início do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="ae7e5-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="ae7e5-110">Um ponteiro para um inteiro que especifica o tamanho da parte usado do bloco de memória (ou seja, a quantidade de memória usada dentro do bloco).</span><span class="sxs-lookup"><span data-stu-id="ae7e5-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="ae7e5-111">Um ponteiro para um inteiro que especifica o tamanho do bloco de memória (ou seja, a quantidade de memória reservada para o bloco).</span><span class="sxs-lookup"><span data-stu-id="ae7e5-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae7e5-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae7e5-112">Remarks</span></span>  
 <span data-ttu-id="ae7e5-113">O `rangeLength` valor é garantido para ser preciso apenas se [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) ou [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), ambos que usam o `COR_PRF_GC_GENERATION_RANGE` estrutura, é chamado a partir de [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ou [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="ae7e5-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae7e5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae7e5-114">Requirements</span></span>  
 <span data-ttu-id="ae7e5-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae7e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae7e5-116">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="ae7e5-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ae7e5-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae7e5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae7e5-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae7e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7e5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae7e5-119">See Also</span></span>  
 [<span data-ttu-id="ae7e5-120">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="ae7e5-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)