---
title: Lista de atributos (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adfb980380bb787280715ca0185950657e174eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-list-visual-basic"></a>Lista de atributos (Visual Basic)
Especifica os atributos a serem aplicadas a um elemento de programação declarado. Vários atributos são separados por vírgulas. Esta é a sintaxe para um atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Partes  
 `attributemodifier`  
 Necessário para os atributos aplicados no início de um arquivo de origem. Pode ser [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) ou [módulo](../../../visual-basic/language-reference/modifiers/module-keyword.md).  
  
 `attributename`  
 Necessário. Nome do atributo.  
  
 `attributearguments`  
 Opcional. Lista de argumentos posicionais para este atributo. Vários argumentos são separados por vírgulas.  
  
 `attributeinitializer`  
 Opcional. Lista de inicializadores de variável ou propriedade para este atributo. Inicializadores múltiplos são separados por vírgulas.  
  
## <a name="remarks"></a>Comentários  
 Você pode aplicar um ou mais atributos para praticamente qualquer elemento de programação (tipos, procedimentos, propriedades e assim por diante). Atributos aparecem nos metadados do assembly, e eles podem ajudar você anotar o código ou especificar como usar um determinado elemento de programação. Você pode aplicar os atributos definidos pelo Visual Basic e o .NET Framework, e você pode definir seus próprios atributos.  

 Para obter mais informações sobre quando usar atributos, consulte [visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md). Para obter informações sobre nomes de atributo, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Regras  
  
-   **Posicionamento.** Você pode aplicar atributos para elementos de programação declarados mais. Para aplicar um ou mais atributos, você deve colocar um *bloco de atributo* no início da declaração do elemento. Cada entrada na lista de atributos especifica um atributo que você deseja aplicar, e o modificador e argumentos que você está usando para essa invocação do atributo.  
  
-   **Colchetes angulares.** Se você fornecer uma lista de atributos, você deve colocá-lo entre colchetes ("`<`"e"`>`").  
  
-   **Parte da declaração.** O atributo deve ser parte da declaração do elemento, não uma instrução separada. Você pode usar a sequência de continuação de linha (" `_`") para estender a instrução de declaração em várias linhas de código-fonte.  
  
-   **Modificadores.** Um modificador de atributo (`Assembly` ou `Module`) é necessário em cada atributo aplicado a um elemento de programação no início de um arquivo de origem. Modificadores de atributo não são permitidos em atributos aplicados aos elementos que não estão no início de um arquivo de origem.  
  
-   **Argumentos.** Todos os argumentos posicionais para um atributo devem preceder qualquer variável ou inicializadores de propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir se aplica a <xref:System.Runtime.InteropServices.DllImportAttribute> atributo a uma definição de uma `Function` procedimento.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute>indica que o procedimento atribuído representa um ponto de entrada em uma biblioteca de vínculo dinâmico (DLL) não gerenciada. O atributo fornece o nome da DLL como um argumento posicional e outras informações como inicializadores de variável.  
  
## <a name="see-also"></a>Consulte também  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [Módulo \<palavra-chave >](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
