---
title: "Método IHostMemoryManager::VirtualAlloc"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc80de55efa8740497bdd455a24e3dafc518db6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="f9e3c-102">Método IHostMemoryManager::VirtualAlloc</span><span class="sxs-lookup"><span data-stu-id="f9e3c-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="f9e3c-103">Serve como um wrapper lógico para a função Win32 correspondente.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="f9e3c-104">A implementação do Win32 de `VirtualAlloc` reserva ou confirma uma região de páginas no espaço de endereço virtual do processo de chamada.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e3c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9e3c-105">Syntax</span></span>  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9e3c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9e3c-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="f9e3c-107">[in] Um ponteiro para o endereço inicial da região para alocar.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="f9e3c-108">[in] O tamanho, em bytes, da região.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="f9e3c-109">[in] O tipo de alocação de memória.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="f9e3c-110">[in] Proteção de memória para a região de páginas a serem alocados.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="f9e3c-111">[in] Um [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valor que indica o impacto de uma falha de alocação.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="f9e3c-112">[out] Ponteiro para o endereço inicial da memória alocada, ou nulo se a solicitação não pôde ser atendida.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9e3c-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f9e3c-113">Return Value</span></span>  
  
|<span data-ttu-id="f9e3c-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9e3c-114">HRESULT</span></span>|<span data-ttu-id="f9e3c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9e3c-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9e3c-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9e3c-116">S_OK</span></span>|<span data-ttu-id="f9e3c-117">`VirtualAlloc`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="f9e3c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9e3c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9e3c-119">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9e3c-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9e3c-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9e3c-121">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-121">The call timed out.</span></span>|  
|<span data-ttu-id="f9e3c-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9e3c-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9e3c-123">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9e3c-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9e3c-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9e3c-125">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9e3c-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9e3c-126">E_FAIL</span></span>|<span data-ttu-id="f9e3c-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9e3c-128">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9e3c-129">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f9e3c-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f9e3c-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f9e3c-131">Não havia memória suficiente disponível para concluir a solicitação de alocação</span><span class="sxs-lookup"><span data-stu-id="f9e3c-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9e3c-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9e3c-132">Remarks</span></span>  
 <span data-ttu-id="f9e3c-133">Reservar uma região no espaço de endereço de seu processo chamando `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="f9e3c-134">O `pAddress` parâmetro contém o endereço de início do bloco de memória que você deseja.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="f9e3c-135">Este parâmetro normalmente é definido como null.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-135">This parameter is typically set to null.</span></span> <span data-ttu-id="f9e3c-136">O sistema operacional mantém um registro de intervalos de endereços livres disponíveis para o processo.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="f9e3c-137">Um `pAddress` valor NULL instrui o sistema para reservar a região onde desejar.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="f9e3c-138">Como alternativa, você pode fornecer um endereço inicial específico para o bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="f9e3c-139">Em ambos os casos, o parâmetro de saída `ppMem` é retornado como um ponteiro para a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="f9e3c-140">A função retorna um valor HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="f9e3c-141">O Win32 `VirtualAlloc` função não tem um `ppMem` parâmetro e retorna o ponteiro para a memória alocada em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="f9e3c-142">Para obter mais informações, consulte a documentação da plataforma Windows.</span><span class="sxs-lookup"><span data-stu-id="f9e3c-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e3c-143">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9e3c-143">Requirements</span></span>  
 <span data-ttu-id="f9e3c-144">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9e3c-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9e3c-145">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f9e3c-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9e3c-146">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f9e3c-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9e3c-147">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9e3c-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e3c-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9e3c-148">See Also</span></span>  
 [<span data-ttu-id="f9e3c-149">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="f9e3c-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)