---
title: "Registrar um Módulo Provedor do Lado do Cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
caps.latest.revision: "8"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 638e7b07c159bf1daf91428a1b95a4e83f61dace
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="94fc5-102">Registrar um Módulo Provedor do Lado do Cliente</span><span class="sxs-lookup"><span data-stu-id="94fc5-102">Register a Client-Side Provider Assembly</span></span>
> [!NOTE]
>  <span data-ttu-id="94fc5-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="94fc5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="94fc5-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="94fc5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="94fc5-105">Este tópico mostra como registrar uma DLL que contém os provedores de automação de interface do usuário do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="94fc5-105">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94fc5-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94fc5-106">Example</span></span>  
 <span data-ttu-id="94fc5-107">O exemplo a seguir mostra como registrar um assembly que contém um provedor para uma janela do console.</span><span class="sxs-lookup"><span data-stu-id="94fc5-107">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="94fc5-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94fc5-108">See Also</span></span>  
 [<span data-ttu-id="94fc5-109">Criar um provedor de automação de interface do usuário do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="94fc5-109">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)