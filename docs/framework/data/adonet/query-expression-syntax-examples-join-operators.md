---
title: "Exemplos de sintaxe da expressão de consulta: Adição a operadores (LINQ to DataSet)"
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
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 28f2627e991d6761306d6655ad4b2e3c0f61ebfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a><span data-ttu-id="8ca70-102">Exemplos de sintaxe da expressão de consulta: Adição a operadores (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8ca70-102">Query Expression Syntax Examples: Join Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="8ca70-103">A junção é uma operação importante em consultas que usam fontes de dados de destino que não têm nenhuma relação navegável entre si, como, por exemplo, as tabelas do banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="8ca70-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="8ca70-104">Uma junção de duas fontes de dados é a associação de objetos em uma fonte de dados com objetos que compartilham um atributo comum em outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8ca70-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="8ca70-105">Para obter mais informações, consulte [visão geral de operadores de consulta padrão](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="8ca70-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="8ca70-106">Os exemplos neste tópico demonstram como usar os métodos <xref:System.Linq.Enumerable.GroupJoin%2A> e <xref:System.Linq.Enumerable.Join%2A> para consultar um <xref:System.Data.DataSet> usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="8ca70-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="8ca70-107">O `FillDataSet` método usado nesses exemplos é especificado em [carregar dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="8ca70-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="8ca70-108">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8ca70-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8ca70-109">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="8ca70-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="8ca70-110">Para obter mais informações, consulte [como: criar um LINQ to DataSet de projeto no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8ca70-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="groupjoin"></a><span data-ttu-id="8ca70-111">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="8ca70-111">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="8ca70-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ca70-112">Example</span></span>  
 <span data-ttu-id="8ca70-113">Este exemplo reproduz <xref:System.Linq.Enumerable.GroupJoin%2A> sobre as tabelas de `SalesOrderHeader` e de `SalesOrderDetail` para localizar o número de pedidos do cliente.</span><span class="sxs-lookup"><span data-stu-id="8ca70-113">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `SalesOrderHeader` and `SalesOrderDetail` tables to find the number of orders per customer.</span></span> <span data-ttu-id="8ca70-114">Um group join é o equivalente a um left outer join, que retorna cada elemento da primeira fonte de dados (esquerda), mesmo se nenhum elemento correlacionado estiver na outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8ca70-114">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="8ca70-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ca70-115">Example</span></span>  
 <span data-ttu-id="8ca70-116">Este exemplo reproduz <xref:System.Linq.Enumerable.GroupJoin%2A> sobre as tabelas de `Contact` e de `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="8ca70-116">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `Contact` and `SalesOrderHeader` tables.</span></span> <span data-ttu-id="8ca70-117">Um group join é o equivalente a um left outer join, que retorna cada elemento da primeira fonte de dados (esquerda), mesmo se nenhum elemento correlacionado estiver na outra fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="8ca70-117">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="8ca70-118">Join</span><span class="sxs-lookup"><span data-stu-id="8ca70-118">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="8ca70-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ca70-119">Example</span></span>  
 <span data-ttu-id="8ca70-120">Este exemplo reproduz uma união sobre as tabelas de `SalesOrderHeader` e de `SalesOrderDetail` para obter pedidos on-line de agosto.</span><span class="sxs-lookup"><span data-stu-id="8ca70-120">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="8ca70-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ca70-121">See Also</span></span>  
 [<span data-ttu-id="8ca70-122">Carregar dados em um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="8ca70-122">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="8ca70-123">LINQ para exemplos de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="8ca70-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="8ca70-124">Visão Geral de Operadores de Consulta Padrão</span><span class="sxs-lookup"><span data-stu-id="8ca70-124">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)