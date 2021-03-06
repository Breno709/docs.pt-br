---
title: "Numérico e operadores de comparação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56558e790b8aee300da0a75ade7c0ac451a0eca1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="numeric-and-comparison-operators"></a>Numérico e operadores de comparação
Aritmética e operadores de comparação funciona como esperado em Common Language Runtime (CLR) exceto como segue:  
  
-   O SQL não suporta o operador de módulo em números de ponto flutuante.  
  
-   O SQL não oferece suporte a aritmética não-verificada.  
  
-   Operadores de incremento e de redução causam efeitos colaterais quando você usa os em expressões que não podem ser replicadas no SQL e, portanto, não são suportados.  
  
## <a name="supported-operators"></a>Operadores suportados  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece suporte aos seguintes operadores.  
  
-   Operadores aritméticos básicos:  
  
    -   `+`  
  
    -   `-` (subtração)  
  
    -   `*`  
  
    -   `/`  
  
    -   Divisão de inteiro do Visual Basic (`\`)  
  
    -   `%` (Visual Basic) `Mod`  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (negação unária)  
  
-   Operadores de comparação básicos:  
  
    -   `=` Visual Basic e C# `==`  
  
    -   `<>` Visual Basic e C# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Consulte também  
 [Funções e tipos de dados](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [Operadores do C#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [Operadores](../../../../../visual-basic/language-reference/operators/index.md)
