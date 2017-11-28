---
title: "Cenários do controle DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 919197d8fdb40f0e0fb7b91fecae38f4e0e061bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-scenarios-windows-forms"></a><span data-ttu-id="5f24e-102">Cenários do controle DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5f24e-102">DataGridView Control Scenarios (Windows Forms)</span></span>
<span data-ttu-id="5f24e-103">Com o <xref:System.Windows.Forms.DataGridView> controle, você pode exibir dados de uma variedade de fontes de dados de tabela.</span><span class="sxs-lookup"><span data-stu-id="5f24e-103">With the <xref:System.Windows.Forms.DataGridView> control, you can display tabular data from a variety of data sources.</span></span> <span data-ttu-id="5f24e-104">Para usos simples, você pode preencher manualmente um <xref:System.Windows.Forms.DataGridView> e manipular os dados diretamente por meio do controle.</span><span class="sxs-lookup"><span data-stu-id="5f24e-104">For simple uses, you can manually populate a <xref:System.Windows.Forms.DataGridView> and manipulate the data directly through the control.</span></span> <span data-ttu-id="5f24e-105">Normalmente, no entanto, você armazena seus dados em uma fonte de dados externa e associar o controle a ele por meio de um <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="5f24e-105">Typically, however, you will store your data in an external data source and bind the control to it through a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="5f24e-106">Este tópico descreve alguns dos cenários comuns que envolvem o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="5f24e-106">This topic describes some of the common scenarios that involve the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a><span data-ttu-id="5f24e-107">Cenário 1: Exibição de pequenas quantidades de dados</span><span class="sxs-lookup"><span data-stu-id="5f24e-107">Scenario 1: Displaying Small Amounts of Data</span></span>  
 <span data-ttu-id="5f24e-108">Você não precisa armazenar os dados em uma fonte de dados externa para exibi-lo no <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="5f24e-108">You do not have to store your data in an external data source to display it in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5f24e-109">Se estiver trabalhando com uma pequena quantidade de dados, você poderá preencher o controle por conta própria e manipular os dados por meio do controle.</span><span class="sxs-lookup"><span data-stu-id="5f24e-109">If you are working with a small amount of data, you can populate the control yourself and manipulate the data through the control.</span></span> <span data-ttu-id="5f24e-110">Isso é chamado de *modo não associado*.</span><span class="sxs-lookup"><span data-stu-id="5f24e-110">This is called *unbound mode*.</span></span> <span data-ttu-id="5f24e-111">Para obter mais informações, consulte [Como criar um controle DataGridView não associado dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="5f24e-111">For more information, see [How to: Create an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="5f24e-112">Principais aspectos do cenário</span><span class="sxs-lookup"><span data-stu-id="5f24e-112">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="5f24e-113">No modo não associado, você preenche o controle manualmente.</span><span class="sxs-lookup"><span data-stu-id="5f24e-113">In unbound mode, you populate the control manually.</span></span>  
  
-   <span data-ttu-id="5f24e-114">O modo não associado é especialmente adequado para pequenas quantidades de dados somente leitura.</span><span class="sxs-lookup"><span data-stu-id="5f24e-114">Unbound mode is particularly suited for small amounts of read-only data.</span></span>  
  
-   <span data-ttu-id="5f24e-115">O modo não associado também é adequado para tabelas preenchidas escassamente ou semelhantes a planilhas.</span><span class="sxs-lookup"><span data-stu-id="5f24e-115">Unbound mode is also suited for spreadsheet-like or sparsely populated tables.</span></span>  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a><span data-ttu-id="5f24e-116">Cenário 2: Exibindo e atualizando dados armazenados em uma fonte de dados externa</span><span class="sxs-lookup"><span data-stu-id="5f24e-116">Scenario 2: Viewing and Updating Data Stored in an External Data Source</span></span>  
 <span data-ttu-id="5f24e-117">Você pode usar o <xref:System.Windows.Forms.DataGridView> controlar como uma interface de usuário (UI) por meio do qual os usuários podem acessar os dados mantidos em uma fonte de dados como uma tabela de banco de dados ou uma coleção de objetos de negócios.</span><span class="sxs-lookup"><span data-stu-id="5f24e-117">You can use the <xref:System.Windows.Forms.DataGridView> control as a user interface (UI) through which users can access data kept in a data source such as a database table or a collection of business objects.</span></span> <span data-ttu-id="5f24e-118">Para obter mais informações, consulte [Como associar dados ao controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="5f24e-118">For more information, see [How to: Bind Data to the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="5f24e-119">Principais aspectos do cenário</span><span class="sxs-lookup"><span data-stu-id="5f24e-119">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="5f24e-120">O modo associado lhe permite se conectar a uma fonte de dados, gerar colunas automaticamente de acordo com as propriedades da fonte de dados ou colunas de banco de dados e preencher automaticamente o controle.</span><span class="sxs-lookup"><span data-stu-id="5f24e-120">Bound mode lets you connect to a data source, automatically generate columns based on the data source properties or database columns, and automatically populate the control.</span></span>  
  
-   <span data-ttu-id="5f24e-121">O modo associado é adequado para quando há um alto nível de interação do usuário com os dados.</span><span class="sxs-lookup"><span data-stu-id="5f24e-121">Bound mode is suited for heavy user interaction with data.</span></span> <span data-ttu-id="5f24e-122">Os dados podem ser formatados para exibição e dados especificados pelo usuário podem ser analisados para o formato esperado pela fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5f24e-122">Data can be formatted for display, and user-specified data can be parsed into the format expected by the data source.</span></span> <span data-ttu-id="5f24e-123">Erros de formatação de entrada de dados e erros de restrição de banco de dados podem ser detectados para que os usuários possam ser avisados e células com erros possam ser corrigidas.</span><span class="sxs-lookup"><span data-stu-id="5f24e-123">Data entry formatting errors and database constraint errors can be detected so that users can be warned and erroneous cells can be corrected.</span></span>  
  
-   <span data-ttu-id="5f24e-124">Funcionalidades adicionais, como a classificação, o congelamento e a reorganização de colunas permitem que os usuários exibam os dados da maneira que for mais conveniente para seu fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5f24e-124">Additional functionality such as column sorting, freezing, and reordering enable users to view data in the way most convenient for their workflow.</span></span>  
  
-   <span data-ttu-id="5f24e-125">O suporte para a área de transferência permite que os usuários copiem dados de seu aplicativo para outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="5f24e-125">Clipboard support enables users to copy data from your application into other applications.</span></span>  
  
## <a name="scenario-3-advanced-data"></a><span data-ttu-id="5f24e-126">Cenário 3: Dados avançados</span><span class="sxs-lookup"><span data-stu-id="5f24e-126">Scenario 3: Advanced Data</span></span>  
 <span data-ttu-id="5f24e-127">Se tiver necessidades especiais que o modelo de vinculação de dados padrão não atende, você pode gerenciar a interação entre o controle e seus dados com a implementação do *modo virtual*.</span><span class="sxs-lookup"><span data-stu-id="5f24e-127">If you have special needs that the standard data binding model does not address, you can manage the interaction between the control and your data by implementing *virtual mode*.</span></span> <span data-ttu-id="5f24e-128">Implementar o modo virtual significa implementar um ou mais manipuladores de eventos que permitem que o controle solicite informações sobre as células conforme essas informações forem necessárias.</span><span class="sxs-lookup"><span data-stu-id="5f24e-128">Implementing virtual mode means implementing one or more event handlers that let the control request information about cells as the information is needed.</span></span>  
  
 <span data-ttu-id="5f24e-129">Por exemplo, caso trabalhe com grandes quantidades de dados, você talvez queira implementar o modo virtual para garantir a eficiência máxima.</span><span class="sxs-lookup"><span data-stu-id="5f24e-129">For example, if you work with large amounts of data, you may want to implement virtual mode to ensure optimal efficiency.</span></span> <span data-ttu-id="5f24e-130">O modo virtual também é útil para manter os valores das colunas não associadas que você exibe em conjunto com colunas recuperadas de outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5f24e-130">Virtual mode is also useful for maintaining the values of unbound columns that you display along with columns retrieved from another data source.</span></span>  
  
 <span data-ttu-id="5f24e-131">Para obter mais informações sobre o modo virtual, consulte [Instruções passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="5f24e-131">For more information about virtual mode, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="5f24e-132">Principais aspectos do cenário</span><span class="sxs-lookup"><span data-stu-id="5f24e-132">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="5f24e-133">O modo virtual é adequado para exibir grandes quantidades de dados quando você precisar ajustar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="5f24e-133">Virtual mode is suited for displaying very large amounts of data when you need to fine-tune performance.</span></span>  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a><span data-ttu-id="5f24e-134">Cenário 4: Redimensionar automaticamente linhas e colunas</span><span class="sxs-lookup"><span data-stu-id="5f24e-134">Scenario 4: Automatically Resizing Rows and Columns</span></span>  
 <span data-ttu-id="5f24e-135">Quando exibe dados que são atualizados regularmente, você pode redimensionar automaticamente as linhas e colunas para garantir que todo o conteúdo esteja visível.</span><span class="sxs-lookup"><span data-stu-id="5f24e-135">When you display data that is regularly updated, you can automatically resize rows and columns to ensure that all content is visible.</span></span> <span data-ttu-id="5f24e-136">O <xref:System.Windows.Forms.DataGridView> controle oferece várias opções que permitem habilitar ou desabilitar manual redimensionamento, redimensionar programaticamente em horários específicos ou redimensionar automaticamente sempre que alterações de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5f24e-136">The <xref:System.Windows.Forms.DataGridView> control provides several options that let you enable or disable manual resizing, resize programmatically at specific times, or resize automatically whenever content changes.</span></span> <span data-ttu-id="5f24e-137">Para obter mais informações, consulte [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md) (Opções de dimensionamento no controle DataGridView dos Windows Forms).</span><span class="sxs-lookup"><span data-stu-id="5f24e-137">For more information, see [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="5f24e-138">Principais aspectos do cenário</span><span class="sxs-lookup"><span data-stu-id="5f24e-138">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="5f24e-139">O redimensionamento manual permite que os usuários ajustem as larguras e as alturas das células.</span><span class="sxs-lookup"><span data-stu-id="5f24e-139">Manual resizing enables users to adjust cell heights and widths.</span></span>  
  
-   <span data-ttu-id="5f24e-140">O redimensionamento automático permite que você mantenha os tamanhos das células, de modo que o conteúdo da célula nunca seja recortado.</span><span class="sxs-lookup"><span data-stu-id="5f24e-140">Automatic resizing enables you to maintain cell sizes so that cell content is never clipped.</span></span>  
  
-   <span data-ttu-id="5f24e-141">O redimensionando programático permite redimensionar células em momentos específicos para evitar a degradação do desempenho decorrente do redimensionamento automático contínuo.</span><span class="sxs-lookup"><span data-stu-id="5f24e-141">Programmatic resizing enables you to resize cells at specific times to avoid the performance penalty of continuous automatic resizing.</span></span>  
  
## <a name="scenario-5-simple-customization"></a><span data-ttu-id="5f24e-142">Cenário 5: Personalização simples</span><span class="sxs-lookup"><span data-stu-id="5f24e-142">Scenario 5: Simple Customization</span></span>  
 <span data-ttu-id="5f24e-143">O <xref:System.Windows.Forms.DataGridView> controle fornece várias maneiras de alterar sua aparência básica e seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="5f24e-143">The <xref:System.Windows.Forms.DataGridView> control provides many ways for you to alter its basic appearance and behavior.</span></span> <span data-ttu-id="5f24e-144">Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="5f24e-144">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="5f24e-145">Principais aspectos do cenário</span><span class="sxs-lookup"><span data-stu-id="5f24e-145">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="5f24e-146"><xref:System.Windows.Forms.DataGridViewCellStyle>objetos permitem que você forneça a cor, fonte, formatação e posicionamento informações em vários níveis e para elementos individuais do controle.</span><span class="sxs-lookup"><span data-stu-id="5f24e-146"><xref:System.Windows.Forms.DataGridViewCellStyle> objects let you provide color, font, formatting, and positioning information at multiple levels and for individual elements of the control.</span></span>  
  
-   <span data-ttu-id="5f24e-147">Os estilos das células podem ser dispostos em camadas e compartilhados por vários elementos, permitindo que você reutilize o código.</span><span class="sxs-lookup"><span data-stu-id="5f24e-147">Cell styles can be layered and shared by multiple elements, letting you reuse code.</span></span>  
  
## <a name="scenario-6-advanced-customization"></a><span data-ttu-id="5f24e-148">Cenário 6: Personalização avançada</span><span class="sxs-lookup"><span data-stu-id="5f24e-148">Scenario 6: Advanced Customization</span></span>  
 <span data-ttu-id="5f24e-149">O <xref:System.Windows.Forms.DataGridView> controle fornece várias maneiras para personalizar sua aparência e comportamento.</span><span class="sxs-lookup"><span data-stu-id="5f24e-149">The <xref:System.Windows.Forms.DataGridView> control provides many ways for you to customize its appearance and behavior.</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="5f24e-150">Principais aspectos do cenário</span><span class="sxs-lookup"><span data-stu-id="5f24e-150">Scenario Key Points</span></span>  
  
-   <span data-ttu-id="5f24e-151">Você pode fornecer seu próprio código de pintura da célula.</span><span class="sxs-lookup"><span data-stu-id="5f24e-151">You can provide your own cell painting code.</span></span> <span data-ttu-id="5f24e-152">Para obter mais informações, consulte [Como personalizar a aparência de células no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="5f24e-152">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="5f24e-153">Você pode fornecer sua própria pintura de linhas.</span><span class="sxs-lookup"><span data-stu-id="5f24e-153">You can provide your own row painting.</span></span> <span data-ttu-id="5f24e-154">Isso é útil, por exemplo, para criar linhas com conteúdo que se estende por várias colunas.</span><span class="sxs-lookup"><span data-stu-id="5f24e-154">This is useful, for example, to create rows with content that spans multiple columns.</span></span> <span data-ttu-id="5f24e-155">Para obter mais informações, consulte [Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="5f24e-155">For more information, see [How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="5f24e-156">Você pode implementar suas próprias classes de célula e de coluna para personalizar a aparência da célula.</span><span class="sxs-lookup"><span data-stu-id="5f24e-156">You can implement your own cell and column classes to customize cell appearance.</span></span> <span data-ttu-id="5f24e-157">Para obter mais informações, consulte [Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="5f24e-157">For more information, see [How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).</span></span>  
  
-   <span data-ttu-id="5f24e-158">Você pode implementar suas próprias classes de célula e de coluna para hospedar controles diferentes daqueles fornecidos pelos tipos de coluna internos.</span><span class="sxs-lookup"><span data-stu-id="5f24e-158">You can implement your own cell and column classes to host controls other than the ones provided by the built-in column types.</span></span> <span data-ttu-id="5f24e-159">Para obter mais informações, consulte [Como hospedar controles em células DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="5f24e-159">For more information, see [How to: Host Controls in Windows Forms DataGridView Cells](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f24e-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f24e-160">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="5f24e-161">Visão geral do controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="5f24e-161">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)