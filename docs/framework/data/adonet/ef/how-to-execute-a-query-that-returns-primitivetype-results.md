---
title: 'Como: Executar uma consulta que retorna resultados de PrimitiveType'
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
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d8a38d732023cd30812a4ae2fa00b99345556a78
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a>Como: Executar uma consulta que retorna resultados de PrimitiveType
Este tópico mostra como executar um comando em um modelo conceitual usando <xref:System.Data.EntityClient.EntityCommand>, e como recuperar <xref:System.Data.Metadata.Edm.PrimitiveType> resultados usando <xref:System.Data.EntityClient.EntityDataReader>.  
  
### <a name="to-run-the-code-in-this-example"></a>Para executar o código nesse exemplo  
  
1.  Adicionar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) ao seu projeto e configurar seu projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Para obter mais informações, consulte [como: usar o Assistente de modelo de dados de entidade](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo executa uma consulta que retorna um resultado de <xref:System.Data.Metadata.Edm.PrimitiveType> . Se você passar a seguinte consulta como um argumento a função de `ExecutePrimitiveTypeQuery` , a função exibe o custo de tabela médio de qualquer `Products`:  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 Se você passar uma consulta parametrizada, como o exemplo a seguir, objetos de <xref:System.Data.EntityClient.EntityParameter> à propriedade de <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> em <xref:System.Data.EntityClient.EntityCommand> objeto.  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Provedor EntityClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
