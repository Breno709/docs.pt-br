---
title: Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89be7e347556c8ec34296044f17fbfd4450bc127
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="2ce61-102">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2ce61-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="2ce61-103">Os controles do Windows Forms são componentes reutilizáveis que encapsulam a funcionalidade de interface do usuário e são usados em aplicativos Windows do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="2ce61-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="2ce61-104">O Windows Forms não só fornece vários controles prontos para usar como também proporciona a infraestrutura para desenvolver seus próprios controles.</span><span class="sxs-lookup"><span data-stu-id="2ce61-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="2ce61-105">É possível combinar os controles existentes, ampliar os controles existentes e fazer seus controles personalizados.</span><span class="sxs-lookup"><span data-stu-id="2ce61-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="2ce61-106">Esta seção fornece informações básicas e exemplos para ajudar a desenvolver controles do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2ce61-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ce61-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2ce61-107">In This Section</span></span>  
 [<span data-ttu-id="2ce61-108">Visão geral do uso de controles no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ce61-108">Overview of Using Controls in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="2ce61-109">Destaca os elementos essenciais do uso de controles em aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2ce61-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="2ce61-110">Variedades de Controles Personalizados</span><span class="sxs-lookup"><span data-stu-id="2ce61-110">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="2ce61-111">Descreve os diferentes tipos de controles personalizados, você pode criar com o <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="2ce61-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="2ce61-112">Noções básicas sobre o desenvolvimento de controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ce61-112">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 <span data-ttu-id="2ce61-113">Fala sobre os primeiros passos no desenvolvimento de um controle do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2ce61-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="2ce61-114">Propriedades em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ce61-114">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 <span data-ttu-id="2ce61-115">Mostra como adicionar propriedades aos controles do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2ce61-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="2ce61-116">Eventos em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ce61-116">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 <span data-ttu-id="2ce61-117">Descreve como manipular e definir eventos nos controles do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2ce61-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="2ce61-118">Atributos em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ce61-118">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="2ce61-119">Descreve os atributos que você pode aplicar a propriedades ou outros membros de seus controles e componentes personalizados.</span><span class="sxs-lookup"><span data-stu-id="2ce61-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="2ce61-120">Pintura e renderização de controle personalizado</span><span class="sxs-lookup"><span data-stu-id="2ce61-120">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="2ce61-121">Mostra como personalizar a aparência de seus controles.</span><span class="sxs-lookup"><span data-stu-id="2ce61-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="2ce61-122">Layout em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ce61-122">Layout in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 <span data-ttu-id="2ce61-123">Mostra como criar layouts para seus controles e formulários.</span><span class="sxs-lookup"><span data-stu-id="2ce61-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="2ce61-124">Multithreading em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ce61-124">Multithreading in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="2ce61-125">Mostra como implementar controles multithreaded.</span><span class="sxs-lookup"><span data-stu-id="2ce61-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2ce61-126">Referência</span><span class="sxs-lookup"><span data-stu-id="2ce61-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="2ce61-127">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="2ce61-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="2ce61-128">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="2ce61-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2ce61-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="2ce61-129">Related Sections</span></span>  
 [<span data-ttu-id="2ce61-130">Atributos de tempo de design para componentes</span><span class="sxs-lookup"><span data-stu-id="2ce61-130">Design-Time Attributes for Components</span></span>](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="2ce61-131">Lista atributos de metadados para aplicar a componentes e controles para que eles sejam exibidos corretamente em tempo de design em designers visuais.</span><span class="sxs-lookup"><span data-stu-id="2ce61-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="2ce61-132">Estendendo o suporte ao tempo de design</span><span class="sxs-lookup"><span data-stu-id="2ce61-132">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="2ce61-133">Descreve como implementar classes como editores e designers que oferecem suporte a tempo de design.</span><span class="sxs-lookup"><span data-stu-id="2ce61-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 [<span data-ttu-id="2ce61-134">Como licenciar componentes e controles</span><span class="sxs-lookup"><span data-stu-id="2ce61-134">How to: License Components and Controls</span></span>](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)  
 <span data-ttu-id="2ce61-135">Descreve como implementar licenciamento em seus controles e componentes.</span><span class="sxs-lookup"><span data-stu-id="2ce61-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="2ce61-136">Consulte também [Desenvolvendo controles do Windows Forms em tempo de design](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="2ce61-136">Also see [Developing Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span></span>