---
title: "Copiar e atualizar as expressões de registros (F #)"
description: "Saiba como escrever um 'Copiar e atualizar registro expression' que copia um existente atualizações de registro, campos de especificado e retorna o registro atualizado."
keywords: "visual f#, f#, programação funcional"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="copy-and-update-record-expressions"></a>Copiar e atualizar expressões de registro

Um *copiar e atualizar registro expressão* é uma expressão que copia um registro existente, atualiza campos especificados e retorna o registro atualizado.


## <a name="syntax"></a>Sintaxe

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Comentários
Os registros são imutáveis, por padrão, para que nenhuma atualização para um registro existente é possível. Para criar um registro atualizado em todos os campos de um registro precisa ser especificado novamente. Para simplificar essa tarefa uma *copiar e atualizar a expressão de registro* pode ser usado. Essa expressão usa um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e o campo ausente especificados pela expressão.
Isso pode ser útil quando você precisa copiar um registro existente e possivelmente alterar alguns dos valores de campo.

Veja, por exemplo, um registro recém-criada.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Se você atualizar somente no campo de registro de que você pode usar o *copiar e atualizar registro expressão* como a seguir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Consulte também
[Registros](records.md)

[Referência da Linguagem F#](index.md)
