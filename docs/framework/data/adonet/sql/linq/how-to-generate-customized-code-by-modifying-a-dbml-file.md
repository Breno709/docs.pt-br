---
title: "Como gerar código personalizado modificando um arquivo DBML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c9a2b382c84548d3226fe68531961e0f53033e7d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Como gerar código personalizado modificando um arquivo DBML
Você pode gerar [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou código-fonte c# de um arquivo de metadados do banco de dados markup language (. dbml). Essa abordagem fornece uma oportunidade para personalizar o arquivo .dbml padrão antes de você gerar o código de mapeamento do aplicativo. Esse é um recurso avançado.  
  
 As etapas nesse processo são as seguintes:  
  
1.  Gere um arquivo .dbml.  
  
2.  Use um editor para modificar o arquivo .dbml. Observe que o arquivo dbml deve validar o arquivo de definição (. xsd) de esquema para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] arquivos dbml. Para obter mais informações, consulte [geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
3.  Gere o código-fonte de [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C#.  
  
 Os exemplos a seguir usam a ferramenta de linha de comando SQLMetal. Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir gera um arquivo .dbml do banco de dados de exemplo Northwind. Como a origem para os metadados de banco de dados, você pode usar o nome do banco de dados ou o nome do arquivo .mdf.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir gera arquivo de código-fonte do [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C# de um arquivo .dbml.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Consulte também  
 [Geração de código em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [SqlMetal.exe (Ferramenta de Geração de Código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Criando o modelo de objeto](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
