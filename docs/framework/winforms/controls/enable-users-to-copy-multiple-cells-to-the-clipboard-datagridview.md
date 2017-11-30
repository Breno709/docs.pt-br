---
title: "Como habilitar usuários para copiarem várias células para a Área de Transferência a partir do controle DataGridView dos Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 703284572005ab262a7e9379b601d8144d8e9af1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a><span data-ttu-id="e4255-102">Como habilitar usuários para copiarem várias células para a Área de Transferência a partir do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4255-102">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e4255-103">Quando você habilita a cópia de célula, que os dados em seu <xref:System.Windows.Forms.DataGridView> controle facilmente acessível a outros aplicativos por meio de <xref:System.Windows.Forms.Clipboard>.</span><span class="sxs-lookup"><span data-stu-id="e4255-103">When you enable cell copying, you make the data in your <xref:System.Windows.Forms.DataGridView> control easily accessible to other applications through the <xref:System.Windows.Forms.Clipboard>.</span></span> <span data-ttu-id="e4255-104">Os valores das células selecionadas são convertidos em cadeias de caracteres e adicionados à área de transferência como valores de texto delimitado por tabulação para colar em aplicativos como Bloco de Notas e Excel, e como uma tabela formatada em HTML para colar em aplicativos como Word.</span><span class="sxs-lookup"><span data-stu-id="e4255-104">The values of the selected cells are converted to strings and added to the Clipboard as tab-delimited text values for pasting into applications like Notepad and Excel, and as an HTML-formatted table for pasting into applications like Word.</span></span>  
  
 <span data-ttu-id="e4255-105">É possível configurar a cópia de célula para copiar somente valores de célula, para incluir texto de cabeçalho de linha e coluna nos dados da área de transferência ou para incluir somente texto de cabeçalho quando os usuários selecionarem linhas ou colunas inteiras.</span><span class="sxs-lookup"><span data-stu-id="e4255-105">You can configure cell copying to copy cell values only, to include row and column header text in the Clipboard data, or to include header text only when users select entire rows or columns.</span></span>  
  
 <span data-ttu-id="e4255-106">Dependendo do modo de seleção, os usuários podem selecionar vários grupos de células desconectados.</span><span class="sxs-lookup"><span data-stu-id="e4255-106">Depending on the selection mode, users can select multiple disconnected groups of cells.</span></span> <span data-ttu-id="e4255-107">Quando um usuário copia as células para a área de transferência, linhas e colunas sem células selecionadas não são copiadas.</span><span class="sxs-lookup"><span data-stu-id="e4255-107">When a user copies cells to the Clipboard, rows and columns with no selected cells are not copied.</span></span> <span data-ttu-id="e4255-108">Todas as outras linhas ou colunas se tornam linhas e colunas na tabela de dados copiados para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="e4255-108">All other rows or columns become rows and columns in the table of data copied to the Clipboard.</span></span> <span data-ttu-id="e4255-109">Células não selecionadas nessas linhas ou colunas são copiadas como espaços reservados em branco para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="e4255-109">Unselected cells in these rows or columns are copied as blank placeholders to the Clipboard.</span></span>  
  
### <a name="to-enable-cell-copying"></a><span data-ttu-id="e4255-110">Habilitar cópia de célula</span><span class="sxs-lookup"><span data-stu-id="e4255-110">To enable cell copying</span></span>  
  
-   <span data-ttu-id="e4255-111">Definir a propriedade <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4255-111">Set the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a><span data-ttu-id="e4255-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4255-112">Example</span></span>  
 <span data-ttu-id="e4255-113">O exemplo de código completo a seguir demonstra como as células são copiadas para a Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="e4255-113">The following complete code example demonstrates how cells are copied to the Clipboard.</span></span> <span data-ttu-id="e4255-114">Este exemplo inclui um botão que copia as células selecionadas para a área de transferência usando o <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> método e exibe a área de transferência de conteúdo em uma caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="e4255-114">This example includes a button that copies the selected cells to the Clipboard using the <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> method and displays the Clipboard contents in a text box.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4255-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e4255-115">Compiling the Code</span></span>  
 <span data-ttu-id="e4255-116">Este código requer:</span><span class="sxs-lookup"><span data-stu-id="e4255-116">This code requires:</span></span>  
  
-   <span data-ttu-id="e4255-117">Referências aos assemblies N:System e N:System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e4255-117">References to the N:System and N:System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e4255-118">Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e4255-118">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e4255-119">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="e4255-119">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="e4255-120">Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="e4255-120">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4255-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4255-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>  
 [<span data-ttu-id="e4255-122">Seleção e uso da Área de Transferência com o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4255-122">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)