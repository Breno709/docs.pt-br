---
title: 'Como: Executar uma consulta polimorfo'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3f2a51276568371c48647557f286ec60ac6531b7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-execute-a-polymorphic-query"></a>Como: Executar uma consulta polimorfo
Este tópico mostra como executar um polimórfico [!INCLUDE[esql](../../../../../includes/esql-md.md)] consultar usando o [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operador.  
  
### <a name="to-run-the-code-in-this-example"></a>Para executar o código nesse exemplo  
  
1.  Adicionar o [modelo School](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) ao seu projeto e configurar seu projeto para usar o Entity Framework. Para obter mais informações, consulte [como: usar o Assistente de modelo de dados de entidade](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Modificar o modelo conceitual para ter uma herança de tabela por hierrachy, seguindo as etapas em [passo a passo: mapeamento de herança - hierarquia por tabela](http://msdn.microsoft.com/library/49b685cf-9db8-4d6d-b885-8837ed238f55).  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo usa um operador de OFTYPE para obter e exibir uma coleção somente de `OnsiteCourses` de uma coleção de `Courses`.  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## <a name="see-also"></a>Consulte também  
 [Provedor EntityClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)
