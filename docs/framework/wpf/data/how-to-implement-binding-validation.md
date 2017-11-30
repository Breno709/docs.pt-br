---
title: "Como implementar validação de associação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec860cc9cc58febd98d8642c98a50ec296592d02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="3e9c8-102">Como implementar validação de associação</span><span class="sxs-lookup"><span data-stu-id="3e9c8-102">How to: Implement Binding Validation</span></span>
<span data-ttu-id="3e9c8-103">Este exemplo mostra como usar um <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> e um gatilho de estilo para fornecer comentários visuais para informar ao usuário quando um valor inválido for digitado, com base em uma regra de validação personalizada.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-103">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e9c8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e9c8-104">Example</span></span>  
 <span data-ttu-id="3e9c8-105">Conteúdo de texto de <xref:System.Windows.Controls.TextBox> no exemplo a seguir está associado ao `Age` propriedade (do tipo int) de um objeto de fonte de associação chamado `ods`.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-105">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="3e9c8-106">A associação é configurada para usar uma regra de validação chamada `AgeRangeRule` para que, se o usuário inserir caracteres não numéricos ou um valor menor que 21 ou maior que 130, um ponto de exclamação vermelho apareça ao lado da caixa de texto e uma dica de ferramenta com a mensagem de erro seja exibida quando o usuário move o mouse sobre a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-106">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="3e9c8-107">O exemplo a seguir mostra a implementação de `AgeRangeRule`, que herda de <xref:System.Windows.Controls.ValidationRule> e substitui o <xref:System.Windows.Controls.ValidationRule.Validate%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-107">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="3e9c8-108">O método Int32.Parse() é chamado no valor para verificar se ele não contém caracteres inválidos.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-108">The Int32.Parse() method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="3e9c8-109">O <xref:System.Windows.Controls.ValidationRule.Validate%2A> método retorna um <xref:System.Windows.Controls.ValidationResult> que indica se o valor é válido com base em se uma exceção for detectada durante a análise e se o valor de idade é fora os limites inferior e superior.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-109">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 <span data-ttu-id="3e9c8-110">O exemplo a seguir mostra personalizado <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` que cria um ponto de exclamação vermelho para notificar o usuário de um erro de validação.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-110">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="3e9c8-111">Modelos de controle são usados para redefinir a aparência de um controle.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-111">Control templates are used to redefine the appearance of a control.</span></span>  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 <span data-ttu-id="3e9c8-112">Conforme mostrado no exemplo a seguir, o <xref:System.Windows.Controls.ToolTip> que mostra a mensagem de erro é criada usando o estilo chamado `textBoxInError`.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-112">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="3e9c8-113">Se o valor de <xref:System.Windows.Controls.Validation.HasError%2A> é `true`, o gatilho define a dica de ferramenta do atual <xref:System.Windows.Controls.TextBox> para seu primeiro erro de validação.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-113">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="3e9c8-114">O <xref:System.Windows.Data.Binding.RelativeSource%2A> é definido como <xref:System.Windows.Data.RelativeSourceMode.Self>, fazendo referência ao elemento atual.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-114">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 <span data-ttu-id="3e9c8-115">Para ver o exemplo completo, consulte [Exemplo de validação de associação](http://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="3e9c8-115">For the complete example, see [Binding Validation Sample](http://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
 <span data-ttu-id="3e9c8-116">Observe que, se você não fornecer um personalizado <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> o modelo de erro padrão é exibido fornecer comentários visuais para o usuário quando há um erro de validação.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-116">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="3e9c8-117">Consulte “Validação de dados” na [Visão geral de associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-117">See "Data Validation" in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="3e9c8-118">Além disso, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece uma regra de validação interna que captura exceções que são geradas durante a atualização da propriedade de origem de associação.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-118">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="3e9c8-119">Para obter mais informações, consulte <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="3e9c8-119">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9c8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e9c8-120">See Also</span></span>  
 [<span data-ttu-id="3e9c8-121">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="3e9c8-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="3e9c8-122">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="3e9c8-122">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)