---
title: "Escapes de caracteres em expressões regulares"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unescaped characters
- replacement patterns
- characters, escapes
- regular expressions, character escapes
- escape characters
- .NET Framework regular expressions, character escapes
- constructs, character escapes
ms.assetid: f49cc9cc-db7d-4058-8b8a-422bc08b29b0
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0149bd97b997da8b29e225a7a1aeda17a6ffa226
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="character-escapes-in-regular-expressions"></a>Escapes de caracteres em expressões regulares
A barra invertida (\\) em uma expressão regular indica um dos seguintes:  
  
-   O caractere que segue é um caractere especial, conforme mostrado na tabela na seção a seguir. Por exemplo, `\b` é uma âncora que indica que uma correspondência da expressão regular deve começar em um limite de palavra, `\t` representa uma guia e `\x020` representa um espaço.  
  
-   Um caractere que, caso contrário, seria interpretado como um constructo de linguagem sem escape deve ser interpretado literalmente. Por exemplo, uma chave (`{`) começa a definição de um quantificador, mas uma barra invertida seguido por uma chave (`\{`) indica que o mecanismo de expressão regular deve corresponder a chave. Da mesma forma, uma barra invertida marca o início de uma construção de linguagem com caracteres de escape, mas duas barras invertidas (`\\`) indica que o mecanismo de expressão regular deve corresponder a barra invertida.  
  
> [!NOTE]
>  Escapes de caracteres são reconhecidos em padrões de expressão regulares, mas não em padrões de substituição.  
  
## <a name="character-escapes-in-net"></a>Escapes de caracteres em .NET  
 A tabela a seguir lista os escapes de caracteres com suporte das expressões regulares em .NET.  
  
|Caractere ou sequência|Descrição|  
|---------------------------|-----------------|  
|Todos os caracteres, exceto os seguintes:<br /><br /> . $ ^ { [ ( &#124; ) * + ? \|Caracteres diferentes dos listados na coluna **Caractere ou sequência** não têm significado especial em expressões regulares; eles correspondem a si mesmos.<br /><br /> Os caracteres incluídos na coluna **Caractere ou sequência** são elementos especiais na linguagem de expressão regular. Para associá-las em uma expressão regular, eles devem ser ignorados ou incluídos em um [caractere positivo grupo](../../../docs/standard/base-types/character-classes-in-regular-expressions.md). Por exemplo, a expressão regular `\$\d+` ou `[$]\d+` corresponde a "$1200".|  
|`\a`|Corresponde a um caractere de sino (alarme), `\u0007`.|  
|`\b`|Em um `[` *grupo caractere* `]` caracteres de classe, corresponde a uma tecla backspace, `\u0008`.  (Consulte [Classes de caracteres](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Fora de uma classe de caractere, `\b` é uma âncora que coincide com um limite de palavra. (Consulte [âncoras](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)|  
|`\t`|Corresponde a uma guia, `\u0009`.|  
|`\r`|Corresponde a um retorno de carro `\u000D`. Observe que `\r` não é equivalente ao caractere de nova linha, `\n`.|  
|`\v`|Corresponde a uma tabulação vertical, `\u000B`.|  
|`\f`|Corresponde a um avanço de página, `\u000C`.|  
|`\n`|Corresponde a uma nova linha, `\u000A`.|  
|`\e`|Corresponde a um escape `\u001B`.|  
|`\` *nnn*|Corresponde a um caractere ASCII, onde  *nnn*  consiste em dois ou três dígitos que representam o código de caracteres octal. Por exemplo, `\040` representa um caractere de espaço. Esse constructo é interpretado como referência inversa se tiver apenas um dígito (por exemplo, `\2`) ou se corresponder ao número de um grupo de captura. (Consulte [construtores](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)|  
|`\x` *nn*|Corresponde a um caractere ASCII, onde  *nn*  é um código de caractere hexadecimal com dois dígitos.|  
|`\c`*X*|Corresponde a um caractere de controle ASCII, onde X é a letra de caractere de controle. Por exemplo, `\cC` é CTRL-C.|  
|`\u` *nnnn*|Corresponde a uma unidade de código UTF-16 cujo valor é  *nnnn*  hexadecimal. **Observação:** o caractere de escape Perl 5 que é usado para especificar Unicode não é suportado pelo .NET. O caractere de escape Perl 5 tem o formato `\x{`  *####*  `…}`, onde  *####*  `…` é uma série de dígitos hexadecimais. Em vez disso, use `\u`  *nnnn* .|  
|`\`|Quando seguido por um caractere que não é reconhecido como um caractere com escape, corresponde a esse caractere. Por exemplo, `\*` corresponde a um asterisco (*) e é igual a `\x2A`.|  
  
## <a name="an-example"></a>Um Exemplo  
 O exemplo a seguir ilustra o uso de escapes de caracteres em uma expressão regular. Ele analisa uma cadeia de caracteres que contém os nomes das maiores cidades do mundo e suas populações em 2009. Cada nome de cidade é separada da sua população por uma tabulação (`\t`) ou uma barra vertical (&#124; ou `\u007c`). Cidades individuais e suas populações são separadas umas das outras por um retorno de carro e uma alimentação de linha.  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 A expressão regular `\G(.+)[\t|\u007c](.+)\r?\n` é interpretada conforme mostrado na tabela a seguir.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`\G`|Inicia a correspondência onde a última correspondência terminou.|  
|`(.+)`|Corresponde qualquer caractere uma ou mais vezes. Este é o primeiro grupo de captura.|  
|`[\t\u007c]`|Corresponde a uma guia (`\t`) ou uma barra vertical (&#124;).|  
|`(.+)`|Corresponde qualquer caractere uma ou mais vezes. Este é o segundo grupo de captura.|  
|`\r?\n`|Corresponde a zero ou uma ocorrência de um retorno de carro, seguida por uma nova linha.|  
  
## <a name="see-also"></a>Consulte também  
 [Linguagem de expressão regular – referência rápida](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)