---
title: "Método ICorProfilerInfo3::RequestProfilerDetach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.RequestProfilerDetach Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d155c68f1b7743e0a888c78f6eeecf967c16570
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a><span data-ttu-id="f385f-102">Método ICorProfilerInfo3::RequestProfilerDetach</span><span class="sxs-lookup"><span data-stu-id="f385f-102">ICorProfilerInfo3::RequestProfilerDetach Method</span></span>
<span data-ttu-id="f385f-103">Instrui o tempo de execução para desanexar o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f385f-103">Instructs the runtime to detach the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f385f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f385f-104">Syntax</span></span>  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f385f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f385f-105">Parameters</span></span>  
 `dwExpectedCompletionMilliseconds`  
 <span data-ttu-id="f385f-106">[in] O período de tempo, em milissegundos, o common language runtime (CLR) deve esperar antes de verificar para ver se é seguro descarregar o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f385f-106">[in] The length of time, in milliseconds, the common language runtime (CLR) should wait before checking to see whether it is safe to unload the profiler.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f385f-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f385f-107">Return Value</span></span>  
 <span data-ttu-id="f385f-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="f385f-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f385f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f385f-109">HRESULT</span></span>|<span data-ttu-id="f385f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f385f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f385f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f385f-111">S_OK</span></span>|<span data-ttu-id="f385f-112">A solicitação de desanexar é válida e o procedimento desanexar agora continua em outro thread.</span><span class="sxs-lookup"><span data-stu-id="f385f-112">The detach request is valid, and the detach procedure is now continuing on another thread.</span></span> <span data-ttu-id="f385f-113">Quando a desanexação esteja totalmente concluída, um `ProfilerDetachSucceeded` evento é emitido.</span><span class="sxs-lookup"><span data-stu-id="f385f-113">When the detach is fully complete, a `ProfilerDetachSucceeded` event is issued.</span></span>|  
|<span data-ttu-id="f385f-114">E_ CORPROF_E_CALLBACK3_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="f385f-114">E_ CORPROF_E_CALLBACK3_REQUIRED</span></span>|<span data-ttu-id="f385f-115">O criador de perfil falhou uma [IUnknown:: QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) tentativa para o [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) interface, que ele deve implementar para dar suporte à operação de desanexação.</span><span class="sxs-lookup"><span data-stu-id="f385f-115">The profiler failed an [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) attempt for the [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) interface, which it must implement to support the detach operation.</span></span> <span data-ttu-id="f385f-116">Desanexar não foi tentada.</span><span class="sxs-lookup"><span data-stu-id="f385f-116">Detach was not attempted.</span></span>|  
|<span data-ttu-id="f385f-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span><span class="sxs-lookup"><span data-stu-id="f385f-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span></span>|<span data-ttu-id="f385f-118">Desconexão é impossível porque o criador de perfil definir sinalizadores imutáveis na inicialização.</span><span class="sxs-lookup"><span data-stu-id="f385f-118">Detachment is impossible because the profiler set immutable flags at startup.</span></span> <span data-ttu-id="f385f-119">Não foi tentada a desconexão; o criador de perfil ainda totalmente está anexado.</span><span class="sxs-lookup"><span data-stu-id="f385f-119">Detachment was not attempted; the profiler is still fully attached.</span></span>|  
|<span data-ttu-id="f385f-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span><span class="sxs-lookup"><span data-stu-id="f385f-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span></span>|<span data-ttu-id="f385f-121">Desconexão é impossível porque o criador de perfil usado instrumentado código Microsoft intermediate language (MSIL) ou inseridas `enter` / `leave` ganchos.</span><span class="sxs-lookup"><span data-stu-id="f385f-121">Detachment is impossible because the profiler used instrumented Microsoft intermediate language (MSIL) code, or inserted `enter`/`leave` hooks.</span></span> <span data-ttu-id="f385f-122">Não foi tentada a desconexão; o criador de perfil ainda totalmente está anexado.</span><span class="sxs-lookup"><span data-stu-id="f385f-122">Detachment was not attempted; the profiler is still fully attached.</span></span><br /><br /> <span data-ttu-id="f385f-123">**Observação** instrumentado MSIL é o código é um código que é fornecido pelo criador de perfil usando o [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f385f-123">**Note** Instrumented MSIL is code is code that is provided by the profiler using the [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>|  
|<span data-ttu-id="f385f-124">CORPROF_E_RUNTIME_UNINITIALIZED</span><span class="sxs-lookup"><span data-stu-id="f385f-124">CORPROF_E_RUNTIME_UNINITIALIZED</span></span>|<span data-ttu-id="f385f-125">O tempo de execução não foi inicializado ainda no aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f385f-125">The runtime has not been initialized yet in the managed application.</span></span> <span data-ttu-id="f385f-126">(Ou seja, o tempo de execução não foi totalmente carregado.) Esse código de erro pode ser retornado quando desconexão for solicitado dentro o retorno de chamada de criador de perfil [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f385f-126">(That is, the runtime has not been fully loaded.) This error code may be returned when detachment is requested inside the profiler callback's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) method.</span></span>|  
|<span data-ttu-id="f385f-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="f385f-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span></span>|<span data-ttu-id="f385f-128">`RequestProfilerDetach`foi chamado em um momento sem suporte.</span><span class="sxs-lookup"><span data-stu-id="f385f-128">`RequestProfilerDetach` was called at an unsupported time.</span></span> <span data-ttu-id="f385f-129">Isso ocorre se o método for chamado em um thread gerenciado, mas não de dentro um [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) método ou de dentro um [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) método que não pode tolerar uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f385f-129">This occurs if the method is called on a managed thread but not from within an [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) method or from within an [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) method that cannot tolerate a garbage collection.</span></span> <span data-ttu-id="f385f-130">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="f385f-130">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f385f-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="f385f-131">Remarks</span></span>  
 <span data-ttu-id="f385f-132">Durante o procedimento de desanexação, o thread de desanexar (o thread criado especificamente para desanexar o criador de perfil), ocasionalmente, verifica se todos os threads abandonaram o código do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f385f-132">During the detach procedure, the detach thread (the thread created specifically for detaching the profiler) occasionally checks whether all threads have exited the profiler’s code.</span></span> <span data-ttu-id="f385f-133">O criador de perfil deve fornecer uma estimativa de quanto tempo isso levará por meio de `dwExpectedCompletionMilliseconds` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f385f-133">The profiler should provide an estimate of how long this should take through the `dwExpectedCompletionMilliseconds` parameter.</span></span> <span data-ttu-id="f385f-134">Um bom valor para usar é a quantidade normal de tempo que o criador de perfil gasta em nenhum dado `ICorProfilerCallback*` método; esse valor não deve ser menor do que a metade da quantidade máxima de tempo de espera que o criador de perfil para gastar.</span><span class="sxs-lookup"><span data-stu-id="f385f-134">A good value to use is the typical amount of time the profiler spends inside any given `ICorProfilerCallback*` method; this value should not be less than half of the maximum amount of time the profiler expects to spend.</span></span>  
  
 <span data-ttu-id="f385f-135">O thread de desanexar usa `dwExpectedCompletionMilliseconds` para decidir quanto tempo antes de verificar se código de retorno de chamada do criador de perfil foi retirado todas as pilhas de suspensão.</span><span class="sxs-lookup"><span data-stu-id="f385f-135">The detach thread uses `dwExpectedCompletionMilliseconds` to decide how long to sleep before checking whether profiler callback code has been popped off all stacks.</span></span> <span data-ttu-id="f385f-136">Embora os detalhes da seguinte algoritmo podem mudar em versões futuras do CLR, ele ilustra uma maneira `dwExpectedCompletionMilliseconds` pode ser usado para determinar quando é seguro descarregar o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="f385f-136">Although the details of the following algorithm may change in future releases of the CLR, it illustrates one way `dwExpectedCompletionMilliseconds` can be used when determining when it is safe to unload the profiler.</span></span> <span data-ttu-id="f385f-137">O thread de desanexar primeiro ficará suspenso por `dwExpectedCompletionMilliseconds` milissegundos.</span><span class="sxs-lookup"><span data-stu-id="f385f-137">The detach thread first sleeps for `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="f385f-138">Se, após a ativação do estado de suspensão, o CLR encontrá-código de retorno de chamada do criador de perfil ainda estiver presente, o thread de desanexar entra em suspensão novamente, desta vez para duas vezes `dwExpectedCompletionMilliseconds` milissegundos.</span><span class="sxs-lookup"><span data-stu-id="f385f-138">If, after awakening from the sleep, the CLR finds that profiler callback code is still present, the detach thread sleeps again, this time for two times `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="f385f-139">Se, após a ativação do modo de suspensão Este segundo, o thread de desanexar encontrá-código de retorno de chamada do criador de perfil ainda estiver presente, ele ficará suspenso por 10 minutos antes de verificar novamente.</span><span class="sxs-lookup"><span data-stu-id="f385f-139">If, after awakening from this second sleep, the detach thread finds that profiler callback code is still present, it sleeps for 10 minutes before checking again.</span></span> <span data-ttu-id="f385f-140">O thread de desanexar continua a verificar novamente a cada 10 minutos.</span><span class="sxs-lookup"><span data-stu-id="f385f-140">The detach thread continues to recheck every 10 minutes.</span></span>  
  
 <span data-ttu-id="f385f-141">Se o criador de perfil especifica `dwExpectedCompletionMilliseconds` como 0 (zero), o CLR usa um valor padrão de 5000, o que significa que ele executará uma verificação depois de 5 segundos, depois de 10 segundos, e, em seguida, a cada 10 minutos depois disso.</span><span class="sxs-lookup"><span data-stu-id="f385f-141">If the profiler specifies `dwExpectedCompletionMilliseconds` as 0 (zero), the CLR uses a default value of 5000, which means that it will perform a check after 5 seconds, again after 10 seconds, and then every 10 minutes thereafter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f385f-142">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f385f-142">Requirements</span></span>  
 <span data-ttu-id="f385f-143">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f385f-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f385f-144">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f385f-144">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f385f-145">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f385f-145">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f385f-146">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f385f-146">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f385f-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f385f-147">See Also</span></span>  
 [<span data-ttu-id="f385f-148">Interface ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="f385f-148">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="f385f-149">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f385f-149">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="f385f-150">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f385f-150">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)