---
title: "Como verificar se cadeias de caracteres estão em um formato de email válido"
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
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, e-mail strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- e-mail [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
caps.latest.revision: "30"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03623cc4086981dc321aafe3020dcd571b74d9bc
ms.sourcegitcommit: 9c4b8d457ffb8d134c9d55c6d7682a0f22e2b9a8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2017
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Como verificar se cadeias de caracteres estão em um formato de email válido
O exemplo a seguir usa uma expressão regular para verificar se uma cadeia de caracteres está no formato de email válido.  
  
## <a name="example"></a>Exemplo  
 O exemplo define um método `IsValidEmail`, que retornará `true` se a cadeia de caracteres contiver um endereço de email válido e `false` se não contiver, mas não realiza outra ação.  
  
 Para verificar se o endereço de email é válido, o método `IsValidEmail` chama o método <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> com o padrão da expressão regular `(@)(.+)$` para separar o nome de domínio do endereço de email. O terceiro parâmetro é um representante <xref:System.Text.RegularExpressions.MatchEvaluator>, que representa o método que processa e substitui o texto correspondente. O padrão da expressão regular é interpretado da seguinte maneira.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`(@)`|Coincida o caractere @. Este é o primeiro grupo de captura.|  
|`(.+)`|Coincida uma ou mais ocorrências de qualquer caractere. Este é o segundo grupo de captura.|  
|`$`|Encerre a correspondência ao final da cadeia de caracteres.|  
  
 O nome de domínio com o caractere @ é passado para o método `DomainMapper`, que usa a classe <xref:System.Globalization.IdnMapping> para converter caracteres Unicode fora do intervalo de caracteres US-ASCII em Punycode. O método também define o sinalizador `invalid` como `True`, caso o método <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> detecte algum caractere inválido no nome do domínio. O método retorna o nome de domínio Punycode precedido pelo símbolo @ para o método `IsValidEmail`.  
  
 Em seguida, o método `IsValidEmail` chama o método <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> para verificar se o endereço está adequado para um padrão de expressão regular.  
  
 O método `IsValidEmail` não realiza a autenticação para validar o endereço de email. Ele simplesmente determina se o formato é válido para um endereço de email. Além disso, o método `IsValidEmail` não verifica se o nome de domínio primário é um nome de domínio válido listado no [IANA Root Zone Database](https://www.iana.org/domains/root/db) (Banco de dados de zona raiz da IANA), o que exigiria uma operação de pesquisa. Em vez disso, a expressão regular apenas verifica se o nome de domínio primário consiste entre dois e vinte e quatro caracteres ASCII, com caracteres alfanuméricos sendo os primeiros e os últimos e o restante dos caracteres sendo alfanuméricos ou um hífen (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 Neste exemplo, o padrão de expressão regular ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` é interpretado como mostrado na tabela a seguir. A expressão regular é compilada com o sinalizador <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.  
  
|Padrão|Descrição|  
|-------------|-----------------|  
|`^`|Comece a correspondência no início da cadeia de caracteres.|  
|`(?(")`|Determine se o primeiro caractere é aspas. `(?(")` é o início de um construtor de alternância.|  
|`(?("")("".+?(?<!\\)""@)`|Se o primeiro caractere for aspas, coincida as aspas iniciais seguidas de pelo menos uma ocorrência de qualquer caractere, seguido de uma marca de aspas finais. Fechar aspas não deve ser precedida por um caractere de barra invertida (\\). `(?<!` é o início de uma asserção lookbehind negativa de largura zero. A cadeia de caracteres deve terminar com um sinal de arroba (@).|  
|`&#124;(([0-9a-z]`|Se o primeiro caractere não for aspas, coincida qualquer caractere alfabético de a até z ou de A até Z (a comparação não diferencia maiúsculas de minúsculas) ou qualquer caractere numérico entre 0 e 9.|  
|`(\.(?!\.))`|Se o próximo caractere for um ponto final, coincida com ele. Se ele não for um ponto final, observe o próximo caractere e continue a correspondência. `(?!\.)` é uma asserção lookahead negativa de largura zero que impede dois pontos finais consecutivos de serem exibidos na parte local de um endereço de email.|  
|``&#124;[-!#\$%&'\*\+/=\?\^`{}\&#124;~\w]``|Se o próximo caractere não for um ponto final, corresponda qualquer caractere da palavra ou um dos seguintes caracteres: -!#$%'*+=?^`{}&#124;~.|  
|``((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^`{}\&#124;~\w])*``|Coincida o padrão de alternância (um ponto final seguido de um não ponto final ou um de um número de caracteres) zero ou mais vezes.|  
|`@`|Coincida o caractere @.|  
|`(?<=[0-9a-z])`|Continue a correspondência se o caractere que precede o caractere @ for de A a Z, de a até z ou de 0 a 9. O constructo `(?<=[0-9a-z])` define uma asserção lookbehind positiva de largura zero.|  
|`(?(\[)`|Verifique se o caractere que segue @ é um colchete de abertura.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|Se ele for um colchete de abertura, coincida o colchete de abertura seguido de um endereço IP (quatro conjuntos de um a três dígitos, com cada conjunto separado por um ponto final) e um colchete de fechamento.|  
|`&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`|Se o caractere que segue @ não é um colchete de abertura, corresponde a um caractere alfanumérico com um valor de A-Z, a-z ou 0-9, seguido por zero ou mais ocorrências de um hífen, seguido por zero ou um caractere alfanumérico com um valor de A-Z, a-z ou 0-9 , seguido por um período. Esse padrão pode ser repetido uma ou mais vezes e deve ser seguido pelo nome de domínio primário.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|O nome de domínio primário deve começar e terminar com um caractere alfanumérico (a-z, A-Z e 0-9). Ele também pode incluir de zero a 22 caracteres ASCII que são alfanuméricos ou hifens.|  
|`$`|Encerre a correspondência ao final da cadeia de caracteres.|  
  
> [!NOTE]
>  Em vez de usar uma expressão regular para validar um endereço de email, você pode usar a classe <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType>. Para determinar se um endereço de email é válido, passe-o para o construtor de classe <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Os métodos `IsValidEmail` e `DomainMapper` podem ser incluídos em uma biblioteca de métodos de utilitário de expressão regular ou como métodos estáticos privados ou de instância na classe do aplicativo.  
  
 Para incluí-los em uma biblioteca de expressões regulares, seja copiar e colar o código em um projeto de Biblioteca de classes do Visual Studio, ou copiar e colá-lo em um arquivo de texto e compilá-lo a partir da linha de comando com um comando semelhante ao seguinte (supondo que o nome do arquivo de código de origem seja RegexUtilities.cs ou RegexUtilities.vb:  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 Também é possível usar o método <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> para incluir essa expressão regular em uma biblioteca de expressões regulares.  
  
 Se eles forem usados em uma biblioteca de expressões regulares, você poderá informá-los usando um código como o seguinte:  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 Supondo que você criou uma biblioteca de classes denominada RegexUtilities.dll que inclui sua expressão regular de validação de email, você poderá compilar esse exemplo de qualquer uma das seguintes maneiras:  
  
-   No Visual Studio, criando um Aplicativo de Console e adicionando uma referência ao RegexUtilities.dll para o seu projeto.  
  
-   Na linha de comando, copiando e colando o código-fonte em um arquivo de texto e compilando-o com um comando semelhante ao seguinte (supondo que o nome do arquivo de código-fonte seja Example.cs ou Example.vb:  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Expressões regulares do .NET Framework](../../../docs/standard/base-types/regular-expressions.md)
