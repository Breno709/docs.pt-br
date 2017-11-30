---
title: CallbackBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9df9629e280a2aec6acf93773e09384e763280ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="61c90-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="61c90-102">CallbackBehavior</span></span>
<span data-ttu-id="61c90-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="61c90-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61c90-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61c90-104">Syntax</span></span>  
  
```  
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="61c90-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="61c90-105">Methods</span></span>  
 <span data-ttu-id="61c90-106">A classe CallbackBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="61c90-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="61c90-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="61c90-107">Properties</span></span>  
 <span data-ttu-id="61c90-108">A classe CallbackBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="61c90-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="61c90-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="61c90-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="61c90-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="61c90-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="61c90-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="61c90-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="61c90-112">Quando for verdadeiro, a sessão é fechada automaticamente quando um serviço fecha uma sessão duplex.</span><span class="sxs-lookup"><span data-stu-id="61c90-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="61c90-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="61c90-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="61c90-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="61c90-114">Data type: string</span></span>  
<span data-ttu-id="61c90-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="61c90-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="61c90-116">Especifica se o serviço oferece suporte a um thread, vários threads ou chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="61c90-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="61c90-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="61c90-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="61c90-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="61c90-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="61c90-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="61c90-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="61c90-120">Um valor que especifica se deve enviar dados de serialização desconhecidos na conexão.</span><span class="sxs-lookup"><span data-stu-id="61c90-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="61c90-121">includeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="61c90-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="61c90-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="61c90-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="61c90-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="61c90-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="61c90-124">Quando habilitada, detalhes sobre exceções no retorno de chamada são anexados às falhas retornadas ao serviço.</span><span class="sxs-lookup"><span data-stu-id="61c90-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="61c90-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="61c90-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="61c90-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="61c90-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="61c90-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="61c90-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="61c90-128">O número máximo de itens permitidos em um objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="61c90-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="61c90-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="61c90-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="61c90-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="61c90-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="61c90-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="61c90-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="61c90-132">Especifica se deve usar o contexto de sincronização atual para escolher o thread de execução.</span><span class="sxs-lookup"><span data-stu-id="61c90-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="61c90-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="61c90-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="61c90-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="61c90-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="61c90-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="61c90-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="61c90-136">Especifica se o sistema ou o aplicativo reforça o processamento de cabeçalho MustUnderstand SOAP.</span><span class="sxs-lookup"><span data-stu-id="61c90-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61c90-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61c90-137">Requirements</span></span>  
  
|<span data-ttu-id="61c90-138">MOF</span><span class="sxs-lookup"><span data-stu-id="61c90-138">MOF</span></span>|<span data-ttu-id="61c90-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="61c90-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="61c90-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="61c90-140">Namespace</span></span>|<span data-ttu-id="61c90-141">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="61c90-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61c90-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61c90-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>