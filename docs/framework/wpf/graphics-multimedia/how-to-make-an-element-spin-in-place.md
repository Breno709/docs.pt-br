---
title: Como criar um giro do elemento in-loco
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e7dac2b1afb9d0ed385f3c25c2e30a93ea8a24f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="b335c-102">Como criar um giro do elemento in-loco</span><span class="sxs-lookup"><span data-stu-id="b335c-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="b335c-103">Este exemplo mostra como fazer um elemento girar usando um <xref:System.Windows.Media.RotateTransform> e um <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="b335c-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="b335c-104">O exemplo a seguir se aplica a <xref:System.Windows.Media.RotateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade do elemento.</span><span class="sxs-lookup"><span data-stu-id="b335c-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="b335c-105">O exemplo usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a <xref:System.Windows.Media.RotateTransform.Angle%2A> do <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="b335c-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="b335c-106">Para fazer com que o elemento girar em vigor, o exemplo define o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade do elemento para o ponto (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="b335c-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b335c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b335c-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="b335c-108">Para o exemplo completo, que inclui mais exemplos de transformação, consulte [exemplo de transformações 2D](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="b335c-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b335c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b335c-109">See Also</span></span>  
 [<span data-ttu-id="b335c-110">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="b335c-110">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="b335c-111">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="b335c-111">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)