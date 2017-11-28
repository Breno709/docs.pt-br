---
title: Hospedando novamente o designer de fluxo de trabalho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e5ca7eec49dec0e9b8896b31147a3cd40ffeef5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="3ac41-102">Hospedando novamente o designer de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3ac41-102">Rehosting the Workflow Designer</span></span>
<span data-ttu-id="3ac41-103">O [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] pode ser hospedado novamente em ambientes fora do [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] para criar, modificar e monitorar fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3ac41-103">The [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] can be rehosted in environments outside of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] for the purposes of creating, modifying, and monitoring workflows.</span></span>  
  
 <span data-ttu-id="3ac41-104">O tipo <xref:System.Activities.Presentation.WorkflowDesigner> é um wrapper da tela, da grade de propriedades e de outros elementos, e expõe um modelo de programação básico para manipular a maioria dos cenários nova hospedagem do designer.</span><span class="sxs-lookup"><span data-stu-id="3ac41-104">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="3ac41-105">Hospedar o <xref:System.Activities.Presentation.WorkflowDesigner> dentro de um aplicativo do [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] é um cenário comum de nova hospedagem para [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ac41-105">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application is a common rehosting scenario for [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ac41-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3ac41-106">In This Section</span></span>  
 [<span data-ttu-id="3ac41-107">Tarefa 1: Criar um novo aplicativo do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="3ac41-107">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
  
 [<span data-ttu-id="3ac41-108">Tarefa 2: Hospedar o Designer de Fluxo de Trabalho</span><span class="sxs-lookup"><span data-stu-id="3ac41-108">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)  
  
 [<span data-ttu-id="3ac41-109">Tarefa 3: Criar a caixa de ferramentas e os painéis de PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="3ac41-109">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)  
  
 [<span data-ttu-id="3ac41-110">Suporte para novos recursos do Workflow Foundation 4.5 no Designer de Fluxo de Trabalho hospedado novamente</span><span class="sxs-lookup"><span data-stu-id="3ac41-110">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)  
  
## <a name="see-also"></a><span data-ttu-id="3ac41-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ac41-111">See Also</span></span>  
 [<span data-ttu-id="3ac41-112">Personalizando a experiência de design de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3ac41-112">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)