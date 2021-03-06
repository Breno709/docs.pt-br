---
title: "Informações do chamador (F #)"
description: "Descreve como usar atributos de argumento de informações do chamador para obter informações do chamador de um método."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 04/25/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 533d2f0429ddb31e6d1dd7efca2f0760069a2945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="caller-information"></a>Informações do chamador

Ao usar atributos de informações do chamador, você pode obter informações sobre o chamador de um método. Você pode obter o caminho do arquivo do código-fonte, o número da linha no código-fonte e o nome do membro do chamador. Essas informações são úteis para fins de rastreamento, depuração e criação de ferramentas de diagnóstico.

Para obter essas informações, você deve usar os atributos que são aplicadas aos parâmetros opcionais, cada qual com um valor padrão. A tabela a seguir lista os atributos de informações do chamador que são definidos no [CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:

|Atributo|Descrição|Tipo|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|O caminho completo do arquivo de origem que contém o chamador. Esse é o caminho do arquivo no momento da compilação.|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Número da linha no arquivo fonte no qual o método é chamado.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Nome do método ou da propriedade do chamador. Consulte a seção de nomes de membro neste tópico.|`String`|

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como você pode usar esses atributos para um chamador de rastreamento.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices

type Tracer() =
    member __.DoTrace(msg: string,
                      [<CallerMemberName>] ?memberName: string,
                      [<CallerFilePath>] ?path: string
                      [<CallerLineNumber>] ?line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        match (memberName, path, line) with
        | Some m, Some p, Some l ->
            Trace.WriteLine(sprintf "Member name: %s" m)
            Trace.WriteLine(sprintf "Source file path: %s" p)
            Trace.WriteLine(sprintf "Source line number: %d" l)
        | _,_,_ -> ()
```

## <a name="remarks"></a>Comentários

Atributos de informações do chamador só podem ser aplicados a parâmetros opcionais. Você deve fornecer um valor explícito para cada parâmetro opcional. Os atributos de informações do chamador com que o compilador gravar o valor apropriado para cada parâmetro opcional decorado com um atributo de informações do chamador.

Os valores de informações do chamador são emitidos como literais em linguagem intermediária (IL) em tempo de compilação. Diferentemente de resultados do [StackTrace](/dotnet/api/system.diagnostics.stacktrace) propriedade para exceções, os resultados não são afetadas por ofuscação.

Você pode fornecer explicitamente os argumentos opcionais para controlar as informações do chamador ou ocultá-las.

## <a name="member-names"></a>Nomes de membros

Você pode usar o [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atributo para evitar especificar o nome do membro como um `String` argumento para o método chamado. Usando essa técnica, você evitar o problema de refatoração Renomear não altera o `String` valores. Esse benefício é especialmente útil para as seguintes tarefas:

* Usar rotinas de rastreamento e diagnóstico.
* Implementando o [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface quando a associação de dados. Essa interface permite que a propriedade de um objeto notifique um controle associado sobre a alteração da propriedade de modo que o controle possa exibir as informações atualizadas. Sem o [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atributo, você deve especificar o nome da propriedade como um literal.

O gráfico a seguir mostra o membro nomes que são retornados quando você usa o atributo CallerMemberName.

|As chamadas ocorrem em|Resultado de nome de membro|
|-------------------|------------------|
|Método, propriedade ou evento|O nome do método, da propriedade ou do evento em que a chamada foi originada.|
|Construtor|A cadeia de caracteres “.ctor”|
|Construtor estático|A cadeia de caracteres “.cctor”|
|Destruidor|A cadeia de caracteres "Finalize"|
|Operadores usuário ou conversões definidos pelo usuário|O nome gerado para o membro, por exemplo, “op_Addition”.|
|Construtor de atributos|O nome do membro ao qual o atributo se aplica. Se o atributo é qualquer elemento dentro de um membro (como um parâmetro, um valor de retorno, ou um parâmetro de tipo genérico), esse resultado é o nome do membro associado a esse elemento.|
|Nenhum membro contentor (por exemplo, nível de assembly ou atributos que são aplicadas aos tipos)|O valor padrão do parâmetro opcional.|

## <a name="see-also"></a>Consulte também
 [Atributos](attributes.md)  
 [Argumentos nomeados](parameters-and-arguments.md#named-arguments)  
 [Parâmetros opcionais](parameters-and-arguments.md#optional-parameters)  
