---
title: "Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bea9be4db2730a67485ef9a504bbc69c096e76c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="70a73-102">Método ICorProfilerInfo2::SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="70a73-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="70a73-103">Especifica as funções implementada pelo criador de perfil a ser chamado nas versões atualizadas de "entrar", "Sair" e "tailcall" ganchos de funções gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="70a73-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a73-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70a73-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70a73-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70a73-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="70a73-106">[in] Um ponteiro para a implementação para ser usado como o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="70a73-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="70a73-107">[in] Um ponteiro para a implementação para ser usado como o [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="70a73-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="70a73-108">[in] Um ponteiro para a implementação para ser usado como o [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="70a73-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70a73-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="70a73-109">Remarks</span></span>  
 <span data-ttu-id="70a73-110">O `SetEnterLeaveFunctionHooks2` método é semelhante do [Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="70a73-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="70a73-111">Use o primeiro para especificar funções a serem usadas como as versões mais recentes dos retornos de chamada deixe/enter/tailcall e o segundo para especificar funções a serem usadas como as versões mais antigas de retornos de chamada de licença/enter/tailcall.</span><span class="sxs-lookup"><span data-stu-id="70a73-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="70a73-112">Apenas um conjunto de retornos de chamada pode estar ativo por vez.</span><span class="sxs-lookup"><span data-stu-id="70a73-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="70a73-113">Portanto, se um criador de perfil chama ambos `ICorProfilerInfo::SetEnterLeaveFunctionHooks` e `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` é usado.</span><span class="sxs-lookup"><span data-stu-id="70a73-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="70a73-114">O `SetEnterLeaveFunctionHooks2` método pode ser chamado somente a partir do criador de perfil [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="70a73-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70a73-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70a73-115">Requirements</span></span>  
 <span data-ttu-id="70a73-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70a73-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70a73-117">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="70a73-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="70a73-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70a73-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70a73-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70a73-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a73-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70a73-120">See Also</span></span>  
 [<span data-ttu-id="70a73-121">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="70a73-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="70a73-122">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="70a73-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)