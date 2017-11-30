---
title: Adicionando colunas a um DataTable
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6107c21ed04c9c39d69c5c784244d8f6bf9560e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="66b55-102">Adicionando colunas a um DataTable</span><span class="sxs-lookup"><span data-stu-id="66b55-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="66b55-103">Um <xref:System.Data.DataTable> contém uma coleção de <xref:System.Data.DataColumn> objetos referenciados pelo **colunas** propriedade da tabela.</span><span class="sxs-lookup"><span data-stu-id="66b55-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="66b55-104">Esta coleção de colunas, junto com quaisquer restrições, define o esquema, ou a estrutura, da tabela.</span><span class="sxs-lookup"><span data-stu-id="66b55-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="66b55-105">Criar **DataColumn** objetos dentro de uma tabela usando o **DataColumn** construtor, ou chamando o **adicionar** método o **colunas**propriedade da tabela, que é um <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="66b55-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="66b55-106">O **adicionar** método aceita opcional **ColumnName**, **DataType**, e **expressão** argumentos e cria um novo  **DataColumn** como um membro da coleção.</span><span class="sxs-lookup"><span data-stu-id="66b55-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="66b55-107">Ele também aceita um existente **DataColumn** do objeto e adiciona-o à coleção e retorna uma referência ao adicionado **DataColumn** se solicitado.</span><span class="sxs-lookup"><span data-stu-id="66b55-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="66b55-108">Porque **DataTable** objetos não são específicos para qualquer fonte de dados, os tipos do .NET Framework são usados ao especificar o tipo de dados de um **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="66b55-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="66b55-109">O exemplo a seguir adiciona quatro colunas para um **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="66b55-109">The following example adds four columns to a **DataTable**.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 <span data-ttu-id="66b55-110">No exemplo, observe que as propriedades para o **CustID** coluna estão definidas para não permitir **DBNull** valores e para restringir os valores exclusivos.</span><span class="sxs-lookup"><span data-stu-id="66b55-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="66b55-111">No entanto, se você definir o **CustID** coluna como coluna de chave primária da tabela, o **AllowDBNull** propriedade será definida automaticamente **false** e o **Unique** propriedade será definida automaticamente **true**.</span><span class="sxs-lookup"><span data-stu-id="66b55-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="66b55-112">Para obter mais informações, consulte [definindo chaves primárias](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="66b55-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="66b55-113">Se um nome de coluna não for fornecido para uma coluna, a coluna recebe um nome padrão incremental da coluna*N,* começando com "Coluna1", quando ele é adicionado para o **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="66b55-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="66b55-114">É recomendável que você evite a convenção de nomenclatura de "coluna*N*" quando você fornece um nome de coluna, porque o nome que você fornecer pode entrar em conflito com um nome de coluna padrão existente no **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="66b55-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="66b55-115">Se o nome fornecido já existir, será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="66b55-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="66b55-116">Se você estiver usando <xref:System.Xml.Linq.XElement> como <xref:System.Data.DataColumn.DataType%2A> de um <xref:System.Data.DataColumn> no <xref:System.Data.DataTable>, a serialização XML não funcionará quando você ler dados.</span><span class="sxs-lookup"><span data-stu-id="66b55-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="66b55-117">Por exemplo, se você escreve um <xref:System.Xml.XmlDocument> usando o método `DataTable.WriteXml`, na serialização para XML há um nó pai adicional no <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="66b55-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="66b55-118">Para resolver esse problema, use o tipo <xref:System.Data.SqlTypes.SqlXml> em vez de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="66b55-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="66b55-119">`ReadXml` e `WriteXml` funcionam corretamente com <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="66b55-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b55-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66b55-120">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="66b55-121">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="66b55-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="66b55-122">DataTables</span><span class="sxs-lookup"><span data-stu-id="66b55-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="66b55-123">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="66b55-123">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>