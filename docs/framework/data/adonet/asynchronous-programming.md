---
title: "Programação assíncrona"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-ado
ms.topic: article
ms.assetid: 85da7447-7125-426e-aa5f-438a290d1f77
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fb500b203555c9174727cd4e9f69eeb5f1df87db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-programming"></a><span data-ttu-id="25108-102">Programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="25108-102">Asynchronous Programming</span></span>

<span data-ttu-id="25108-103">Este tópico discute o suporte à programação assíncrona no provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] (SqlClient) incluindo os aprimoramentos feitos para dar suporte à funcionalidade de programação assíncrona que foi introduzida no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25108-103">This topic discusses support for asynchronous programming in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] (SqlClient) including enhancements made to support asynchronous programming functionality that was introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="legacy-asynchronous-programming"></a><span data-ttu-id="25108-104">Programação assíncrona herdada</span><span class="sxs-lookup"><span data-stu-id="25108-104">Legacy Asynchronous Programming</span></span>  
 <span data-ttu-id="25108-105">Antes do [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], a programação assíncrona com SqlClient foi feita com os seguintes métodos e a propriedade de conexão de `Asynchronous Processing=true`:</span><span class="sxs-lookup"><span data-stu-id="25108-105">Prior to [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], asynchronous programming with SqlClient was done with the following methods and the `Asynchronous Processing=true` connection property:</span></span>  
  
1.  <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="25108-106">Essa funcionalidade é mantida em SqlClient no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25108-106">This functionality remains in SqlClient in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 <span data-ttu-id="25108-107">A partir do [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], esses métodos não exigem `Asynchronous Processing=true` na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="25108-107">Beginning in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], these methods no longer require `Asynchronous Processing=true` in the connection string.</span></span>  
  
## <a name="asynchronous-programming-features-added-in-includenetv45includesnet-v45-mdmd"></a><span data-ttu-id="25108-108">Recursos de programação assíncrona adicionados no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25108-108">Asynchronous Programming Features Added in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]</span></span>  
 <span data-ttu-id="25108-109">O novo recurso de programação assíncrona fornece uma técnica simples para tornar o código assíncrono.</span><span class="sxs-lookup"><span data-stu-id="25108-109">The new asynchronous programming feature provides a simple technique to make code asynchronous.</span></span>  
  
 <span data-ttu-id="25108-110">Para obter mais informações sobre o recurso de programação assíncrona que foi apresentado no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], consulte:</span><span class="sxs-lookup"><span data-stu-id="25108-110">For more information about the asynchronous programming feature that was introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], see:</span></span>  
  
- [<span data-ttu-id="25108-111">Programação assíncrona em c#</span><span class="sxs-lookup"><span data-stu-id="25108-111">Asynchronous programming in C#</span></span>](../../../csharp/async.md)

- [<span data-ttu-id="25108-112">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25108-112">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)

- [<span data-ttu-id="25108-113">Usando os métodos assíncronos novo do SqlDataReader no .net 4.5 (parte 1)</span><span class="sxs-lookup"><span data-stu-id="25108-113">Using SqlDataReader’s new async methods in .Net 4.5 (Part 1)</span></span>](https://blogs.msdn.microsoft.com/adonet/2012/04/20/using-sqldatareaders-new-async-methods-in-net-4-5/)

- [<span data-ttu-id="25108-114">Usando os métodos assíncronos novo do SqlDataReader no .net 4.5 (parte 2)</span><span class="sxs-lookup"><span data-stu-id="25108-114">Using SqlDataReader’s new async methods in .Net 4.5 (Part 2)</span></span>](https://blogs.msdn.microsoft.com/adonet/2012/07/15/using-sqldatareaders-new-async-methods-in-net-4-5-part-2-examples/)
 
 <span data-ttu-id="25108-115">Quando sua interface de usuário não tem resposta ou o servidor não escala, é provável que você precise que seu código seja mais assíncrono.</span><span class="sxs-lookup"><span data-stu-id="25108-115">When your user interface is unresponsive or your server does not scale, it is likely that you need your code to be more asynchronous.</span></span>  <span data-ttu-id="25108-116">Escrever código assíncrono tradicionalmente envolve instalar um retorno de chamada (também chamado de continuação) para expressar a lógica que ocorre depois que a operação assíncrona é concluída.</span><span class="sxs-lookup"><span data-stu-id="25108-116">Writing asynchronous code has traditionally involved installing a callback (also called continuation) to express the logic that occurs after the asynchronous operation finishes.</span></span> <span data-ttu-id="25108-117">Isso complica a estrutura de código assíncrona em comparação com o código síncrono.</span><span class="sxs-lookup"><span data-stu-id="25108-117">This complicates the structure of asynchronous code as compared with synchronous code.</span></span>  
  
 <span data-ttu-id="25108-118">Agora você pode chamar os métodos assíncronos sem usar retornos de chamada e sem dividir seu código em vários métodos ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="25108-118">You can now call into asynchronous methods without using callbacks, and without splitting your code across multiple methods or lambda expressions.</span></span>  
  
 <span data-ttu-id="25108-119">O modificador `async` especifica que um método é assíncrono.</span><span class="sxs-lookup"><span data-stu-id="25108-119">The `async` modifier specifies that a method is asynchronous.</span></span> <span data-ttu-id="25108-120">Ao chamar um método `async`, uma tarefa é retornada.</span><span class="sxs-lookup"><span data-stu-id="25108-120">When calling an `async` method, a task is returned.</span></span> <span data-ttu-id="25108-121">Quando o `await` operador é aplicado a uma tarefa, o método atual será encerrado imediatamente.</span><span class="sxs-lookup"><span data-stu-id="25108-121">When the `await` operator is applied to a task, the current method exits immediately.</span></span> <span data-ttu-id="25108-122">Quando a tarefa é concluída, a execução é retomada no mesmo método.</span><span class="sxs-lookup"><span data-stu-id="25108-122">When the task finishes, execution resumes in the same method.</span></span>
  
> [!WARNING]
>  <span data-ttu-id="25108-123">As chamadas assíncronas não têm suporte se um aplicativo também usa a palavra-chave da cadeia de conexão `Context Connection`.</span><span class="sxs-lookup"><span data-stu-id="25108-123">Asynchronous calls are not supported if an application also uses the `Context Connection` connection string keyword.</span></span>  
  
 <span data-ttu-id="25108-124">Chamar um método de `async` não atribui nenhum thread adicional.</span><span class="sxs-lookup"><span data-stu-id="25108-124">Calling an `async` method does not allocate any additional threads.</span></span> <span data-ttu-id="25108-125">Ele pode usar o thread de E/S de conclusão existente brevemente na extremidade.</span><span class="sxs-lookup"><span data-stu-id="25108-125">It may use the existing I/O completion thread briefly at the end.</span></span>  
  
 <span data-ttu-id="25108-126">Os métodos a seguir foram adicionados no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] para dar suporte à programação assíncrona:</span><span class="sxs-lookup"><span data-stu-id="25108-126">The following methods were added in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] to support asynchronous programming:</span></span>  
  
-   <xref:System.Data.Common.DbConnection.OpenAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteDbDataReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbDataReader.GetFieldValueAsync%2A>  
  
-   <xref:System.Data.Common.DbDataReader.IsDBNullAsync%2A>  
  
-   <xref:System.Data.Common.DbDataReader.NextResultAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbDataReader.ReadAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlConnection.OpenAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteXmlReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.NextResultAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.ReadAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="25108-127">Outros membros assíncronos foram adicionados para oferecer suporte a [SqlClient Streaming oferece suporte a](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md).</span><span class="sxs-lookup"><span data-stu-id="25108-127">Other asynchronous members were added to support [SqlClient Streaming Support](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md).</span></span>  
  
### <a name="synchronous-to-asynchronous-connection-open"></a><span data-ttu-id="25108-128">Conexão síncrona para assíncrona aberta</span><span class="sxs-lookup"><span data-stu-id="25108-128">Synchronous to Asynchronous Connection Open</span></span>  
 <span data-ttu-id="25108-129">Você pode atualizar um aplicativo existente para usar o novo recurso assíncrono.</span><span class="sxs-lookup"><span data-stu-id="25108-129">You can upgrade an existing application to use the new asynchronous feature.</span></span> <span data-ttu-id="25108-130">Por exemplo, suponha que um aplicativo tenha um algoritmo síncrono de conexão e bloqueie o thread de interface de usuário sempre que se conecta ao banco de dados e, uma vez conectado, o aplicativo chama um procedimento armazenado que sinaliza outros usuários da pessoa que acabou de se conectar.</span><span class="sxs-lookup"><span data-stu-id="25108-130">For example, assume an application has a synchronous connection algorithm and blocks the UI thread every time it connects to the database and, once connected, the application calls a stored procedure that signals other users of the one who just signed in.</span></span>  
  
```csharp
using SqlConnection conn = new SqlConnection("…");  
{  
   conn.Open();  
   using (SqlCommand cmd = new SqlCommand("StoredProcedure_Logon", conn))  
   {  
      cmd.ExecuteNonQuery();  
   }  
}  
```  
  
 <span data-ttu-id="25108-131">Quando convertidos para usar a nova funcionalidade assíncrona, o programa seria parecido com isso:</span><span class="sxs-lookup"><span data-stu-id="25108-131">When converted to use the new asynchronous functionality, the program would look like:</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class A {  
  
   static async Task<int> Method(SqlConnection conn, SqlCommand cmd) {  
      await conn.OpenAsync();  
      await cmd.ExecuteNonQueryAsync();  
      return 1;  
   }  
  
   public static void Main() {  
      using (SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI")) {  
         SqlCommand command = new SqlCommand("select top 2 * from orders", conn);  
  
         int result = A.Method(conn, command).Result;  
  
         SqlDataReader reader = command.ExecuteReader();  
         while (reader.Read())  
            Console.WriteLine(String.Format("{0}", reader[0]));  
      }  
   }  
}  
```  
  
### <a name="adding-the-new-asynchronous-feature-in-an-existing-application-mixing-old-and-new-patterns"></a><span data-ttu-id="25108-132">Adicionando o novo recurso assíncrono em um aplicativo existente (misturando padrões novos e antigos)</span><span class="sxs-lookup"><span data-stu-id="25108-132">Adding the New Asynchronous Feature in an Existing Application (Mixing Old and New Patterns)</span></span>  
 <span data-ttu-id="25108-133">Também é possível adicionar o novo recurso assíncrono (SqlConnection::OpenAsync) sem modificar a lógica assíncrona existente.</span><span class="sxs-lookup"><span data-stu-id="25108-133">It is also possible to add new asynchronous capability (SqlConnection::OpenAsync) without changing the existing asynchronous logic.</span></span> <span data-ttu-id="25108-134">Por exemplo, se um aplicativo no momento usa:</span><span class="sxs-lookup"><span data-stu-id="25108-134">For example, if an application currently uses:</span></span>  
  
```csharp
AsyncCallback productList = new AsyncCallback(ProductList);  
SqlConnection conn = new SqlConnection("…");  
conn.Open();  
SqlCommand cmd = new SqlCommand("SELECT * FROM [Current Product List]", conn);  
IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);  
```  
  
 <span data-ttu-id="25108-135">Você pode começar a usar o novo padrão assíncrono sem substancialmente alterar o algoritmo existente.</span><span class="sxs-lookup"><span data-stu-id="25108-135">You can begin to use the new asynchronous pattern without substantially changing the existing algorithm.</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class A {  
   static void ProductList(IAsyncResult result) { }  
  
   public static void Main() {  
      // AsyncCallback productList = new AsyncCallback(ProductList);  
      // SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");  
      // conn.Open();  
      // SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);  
      // IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);  
  
      AsyncCallback productList = new AsyncCallback(ProductList);  
      SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");  
      conn.OpenAsync().ContinueWith((task) => {  
         SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);  
         IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);  
      }, TaskContinuationOptions.OnlyOnRanToCompletion);  
   }  
}  
```  
  
### <a name="using-the-base-provider-model-and-the-new-asynchronous-feature"></a><span data-ttu-id="25108-136">Usando o modelo de provedor base e o novo recurso assíncrono</span><span class="sxs-lookup"><span data-stu-id="25108-136">Using the Base Provider Model and the New Asynchronous Feature</span></span>  
 <span data-ttu-id="25108-137">Você pode precisar criar uma ferramenta que seja capaz de se conectar a bancos de dados diferentes e executar consultas.</span><span class="sxs-lookup"><span data-stu-id="25108-137">You may need to create a tool that is able to connect to different databases and execute queries.</span></span> <span data-ttu-id="25108-138">Você pode usar o modelo de provedor base e o novo recurso assíncrono.</span><span class="sxs-lookup"><span data-stu-id="25108-138">You can use the base provider model and the new asynchronous feature.</span></span>  
  
 <span data-ttu-id="25108-139">O controlador MSDTC deve ser habilitado no servidor para usar transações distribuídas.</span><span class="sxs-lookup"><span data-stu-id="25108-139">The Microsoft Distributed Transaction Controller (MSDTC) must be enabled on the server to use distributed transactions.</span></span> <span data-ttu-id="25108-140">Para obter informações sobre como habilitar o MSDTC, consulte [como habilitar o MSDTC em um servidor Web](http://msdn.microsoft.com/library/dd327979.aspx).</span><span class="sxs-lookup"><span data-stu-id="25108-140">For information on how to enable MSDTC, see [How to Enable MSDTC on a Web Server](http://msdn.microsoft.com/library/dd327979.aspx).</span></span>  
  
```csharp
using System;  
using System.Data.Common;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class A {  
   static async Task PerformDBOperationsUsingProviderModel(string connectionString, string providerName) {  
      DbProviderFactory factory = DbProviderFactories.GetFactory(providerName);  
      using (DbConnection connection = factory.CreateConnection()) {  
         connection.ConnectionString = connectionString;  
         await connection.OpenAsync();  
  
         DbCommand command = connection.CreateCommand();  
         command.CommandText = "SELECT * FROM AUTHORS";  
  
         using (DbDataReader reader = await command.ExecuteReaderAsync()) {  
            while (await reader.ReadAsync()) {  
               for (int i = 0; i < reader.FieldCount; i++) {  
                  // Process each column as appropriate  
                  object obj = await reader.GetFieldValueAsync<object>(i);  
                  Console.WriteLine(obj);  
               }  
            }  
         }  
      }  
   }  
  
   public static void Main()   
   {  
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();  
       // replace these with your own values  
       builder.DataSource = "your_server";  
       builder.InitialCatalog = "pubs";  
       builder.IntegratedSecurity = true;  
       string provider = "System.Data.SqlClient";  
  
       Task task = PerformDBOperationsUsingProviderModel(builder.ConnectionString, provider);  
       task.Wait();  
   }  
}  
```  
  
### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="25108-141">Usando transações do SQL e o novo recurso assíncrono</span><span class="sxs-lookup"><span data-stu-id="25108-141">Using SQL Transactions and the New Asynchronous Feature</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class Program {  
   static void Main() {  
      string connectionString =  
          "Persist Security Info=False;Integrated Security=SSPI;database=Northwind;server=(local)";  
      Task task = ExecuteSqlTransaction(connectionString);  
      task.Wait();  
   }  
  
   static async Task ExecuteSqlTransaction(string connectionString) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         await connection.OpenAsync();  
  
         SqlCommand command = connection.CreateCommand();  
         SqlTransaction transaction = null;  
  
         // Start a local transaction.  
         transaction = await Task.Run<SqlTransaction>(  
             () => connection.BeginTransaction("SampleTransaction")  
             );  
  
         // Must assign both transaction object and connection  
         // to Command object for a pending local transaction  
         command.Connection = connection;  
         command.Transaction = transaction;  
  
         try {  
            command.CommandText =  
                "Insert into Region (RegionID, RegionDescription) VALUES (555, 'Description')";  
            await command.ExecuteNonQueryAsync();  
  
            command.CommandText =  
                "Insert into Region (RegionID, RegionDescription) VALUES (556, 'Description')";  
            await command.ExecuteNonQueryAsync();  
  
            // Attempt to commit the transaction.  
            await Task.Run(() => transaction.Commit());  
            Console.WriteLine("Both records are written to database.");  
         }  
         catch (Exception ex) {  
            Console.WriteLine("Commit Exception Type: {0}", ex.GetType());  
            Console.WriteLine("  Message: {0}", ex.Message);  
  
            // Attempt to roll back the transaction.  
            try {  
               transaction.Rollback();  
            }  
            catch (Exception ex2) {  
               // This catch block will handle any errors that may have occurred  
               // on the server that would cause the rollback to fail, such as  
               // a closed connection.  
               Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());  
               Console.WriteLine("  Message: {0}", ex2.Message);  
            }  
         }  
      }  
   }  
}  
```  
  
### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a><span data-ttu-id="25108-142">Usando transações do SQL e o novo recurso assíncrono</span><span class="sxs-lookup"><span data-stu-id="25108-142">Using SQL Transactions and the New Asynchronous Feature</span></span>  
 <span data-ttu-id="25108-143">Em um aplicativo da empresa, você poderá precisar adicionar transações distribuídas em alguns cenários, para habilitar transações entre vários servidores de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="25108-143">In an enterprise application, you may need to add distributed transactions in some scenarios, to enable transactions between multiple database servers.</span></span> <span data-ttu-id="25108-144">Você pode usar o namespace System.Transactions e inscrever uma transação distribuída, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="25108-144">You can use the System.Transactions namespace and enlist a distributed transaction, as follows:</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
using System.Transactions;  
  
class Program {  
   public static void Main()   
   {  
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();  
       // replace these with your own values  
       builder.DataSource = "your_server";  
       builder.InitialCatalog = "your_data_source";  
       builder.IntegratedSecurity = true;  
  
       Task task = ExecuteDistributedTransaction(builder.ConnectionString, builder.ConnectionString);  
       task.Wait();  
   }  
  
   static async Task ExecuteDistributedTransaction(string connectionString1, string connectionString2) {  
      using (SqlConnection connection1 = new SqlConnection(connectionString1))  
      using (SqlConnection connection2 = new SqlConnection(connectionString2)) {  
         using (CommittableTransaction transaction = new CommittableTransaction()) {  
            await connection1.OpenAsync();  
            connection1.EnlistTransaction(transaction);  
  
            await connection2.OpenAsync();  
            connection2.EnlistTransaction(transaction);  
  
            try {  
               SqlCommand command1 = connection1.CreateCommand();  
               command1.CommandText = "Insert into RegionTable1 (RegionID, RegionDescription) VALUES (100, 'Description')";  
               await command1.ExecuteNonQueryAsync();  
  
               SqlCommand command2 = connection2.CreateCommand();  
               command2.CommandText = "Insert into RegionTable2 (RegionID, RegionDescription) VALUES (100, 'Description')";  
               await command2.ExecuteNonQueryAsync();  
  
               transaction.Commit();  
            }  
            catch (Exception ex) {  
               Console.WriteLine("Exception Type: {0}", ex.GetType());  
               Console.WriteLine("  Message: {0}", ex.Message);  
  
               try {  
                  transaction.Rollback();  
               }  
               catch (Exception ex2) {  
                  Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());  
                  Console.WriteLine("  Message: {0}", ex2.Message);  
               }  
            }  
         }  
      }  
   }  
}  
```  
  
### <a name="cancelling-an-asynchronous-operation"></a><span data-ttu-id="25108-145">Cancelando uma operação assíncrona</span><span class="sxs-lookup"><span data-stu-id="25108-145">Cancelling an Asynchronous Operation</span></span>  
 <span data-ttu-id="25108-146">Você pode cancelar uma solicitação assíncrona usando o <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="25108-146">You can cancel an asynchronous request by using the <xref:System.Threading.CancellationToken>.</span></span>  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading;  
using System.Threading.Tasks;  
  
namespace Samples {  
   class CancellationSample {  
      public static void Main(string[] args) {  
         CancellationTokenSource source = new CancellationTokenSource();  
         source.CancelAfter(2000); // give up after 2 seconds  
         try {  
            Task result = CancellingAsynchronousOperations(source.Token);  
            result.Wait();  
         }  
         catch (AggregateException exception) {  
            if (exception.InnerException is SqlException) {  
               Console.WriteLine("Operation canceled");  
            }  
            else {  
               throw;  
            }  
         }  
      }  
  
      static async Task CancellingAsynchronousOperations(CancellationToken cancellationToken) {  
         using (SqlConnection connection = new SqlConnection("Server=(local);Integrated Security=true")) {  
            await connection.OpenAsync(cancellationToken);  
  
            SqlCommand command = new SqlCommand("WAITFOR DELAY '00:10:00'", connection);  
            await command.ExecuteNonQueryAsync(cancellationToken);  
         }  
      }  
   }  
}  
```  
  
### <a name="asynchronous-operations-with-sqlbulkcopy"></a><span data-ttu-id="25108-147">Operações assíncronas com SqlBulkCopy</span><span class="sxs-lookup"><span data-stu-id="25108-147">Asynchronous Operations with SqlBulkCopy</span></span>  
 <span data-ttu-id="25108-148">Os recursos assíncronos também foram acrescentados a <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> com <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25108-148">Asynchronous capabilities were also added to <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> with <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.Odbc;  
using System.Data.SqlClient;  
using System.Linq;  
using System.Text;  
using System.Threading;  
using System.Threading.Tasks;  
  
namespace SqlBulkCopyAsyncCodeSample {  
   class Program {  
      static string selectStatment = "SELECT * FROM [pubs].[dbo].[titles]";  
      static string createDestTableStatement =  
          @"CREATE TABLE {0} (  
            [title_id] [varchar](6) NOT NULL,  
            [title] [varchar](80) NOT NULL,  
            [type] [char](12) NOT NULL,  
            [pub_id] [char](4) NULL,  
            [price] [money] NULL,  
            [advance] [money] NULL,  
            [royalty] [int] NULL,  
            [ytd_sales] [int] NULL,  
            [notes] [varchar](200) NULL,  
            [pubdate] [datetime] NOT NULL)";  
  
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo;Integrated Security=true"  
      // static string connectionString = @"Server=(localdb)\V11.0;Database=Demo";  
      static string connectionString = @"Server=(local);Database=Demo;Integrated Security=true";  
  
      // static string odbcConnectionString = @"Driver={SQL Server};Server=(localdb)\V11.0;UID=oledb;Pwd=1Password!;Database=Demo";  
      static string odbcConnectionString = @"Driver={SQL Server};Server=(local);Database=Demo;Integrated Security=true";  
  
      // static string marsConnectionString = @"Server=(localdb)\V11.0;Database=Demo;MultipleActiveResultSets=true;";  
      static string marsConnectionString = @"Server=(local);Database=Demo;MultipleActiveResultSets=true;Integrated Security=true";  
  
      // Replace the Server name with your actual sql azure server name and User ID/Password  
      static string azureConnectionString = @"Server=SqlAzure;User ID=myUserID;Password=myPassword;Database=Demo";  
  
      static void Main(string[] args) {  
         SynchronousSqlBulkCopy();  
         AsyncSqlBulkCopy().Wait();  
         MixSyncAsyncSqlBulkCopy().Wait();  
         AsyncSqlBulkCopyNotifyAfter().Wait();  
         AsyncSqlBulkCopyDataRows().Wait();  
         // AsyncSqlBulkCopySqlServerToSqlAzure().Wait();  
         // AsyncSqlBulkCopyCancel().Wait();  
         AsyncSqlBulkCopyMARS().Wait();  
      }  
  
      // 3.1.1 Synchronous bulk copy in .NET 4.5  
      private static void SynchronousSqlBulkCopy() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            conn.Open();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               cmd.ExecuteNonQuery();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  bcp.WriteToServer(dt);  
               }  
            }  
         }  
  
      }  
  
      // 3.1.2 Asynchrounous bulk copy in .NET 4.5  
      private static async Task AsyncSqlBulkCopy() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            await conn.OpenAsync();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               await cmd.ExecuteNonQueryAsync();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  await bcp.WriteToServerAsync(dt);  
               }  
            }  
         }  
      }  
  
      // 3.2 Add new Async.NET capabilities in an existing application (Mixing synchronous and asynchornous calls)  
      private static async Task MixSyncAsyncSqlBulkCopy() {  
         using (OdbcConnection odbcconn = new OdbcConnection(odbcConnectionString)) {  
            odbcconn.Open();  
            using (OdbcCommand odbccmd = new OdbcCommand(selectStatment, odbcconn)) {  
               using (OdbcDataReader odbcreader = odbccmd.ExecuteReader()) {  
                  using (SqlConnection conn = new SqlConnection(connectionString)) {  
                     await conn.OpenAsync();  
                     string temptable = "temptable";//"[#" + Guid.NewGuid().ToString("N") + "]";  
                     SqlCommand createCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), conn);  
                     await createCmd.ExecuteNonQueryAsync();  
                     using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                        bcp.DestinationTableName = temptable;  
                        await bcp.WriteToServerAsync(odbcreader);  
                     }  
                  }  
               }  
            }  
         }  
      }  
  
      // 3.3 Using the NotifyAfter property  
      private static async Task AsyncSqlBulkCopyNotifyAfter() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            await conn.OpenAsync();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               await cmd.ExecuteNonQueryAsync();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  bcp.NotifyAfter = 5;  
                  bcp.SqlRowsCopied += new SqlRowsCopiedEventHandler(OnSqlRowsCopied);  
                  await bcp.WriteToServerAsync(dt);  
               }  
            }  
         }  
      }  
  
      private static void OnSqlRowsCopied(object sender, SqlRowsCopiedEventArgs e) {  
         Console.WriteLine("Copied {0} so far...", e.RowsCopied);  
      }  
  
      // 3.4 Using the new SqlBulkCopy Async.NET capabilities with DataRow[]  
      private static async Task AsyncSqlBulkCopyDataRows() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            await conn.OpenAsync();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
               DataRow[] rows = dt.Select();  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               await cmd.ExecuteNonQueryAsync();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  await bcp.WriteToServerAsync(rows);  
               }  
            }  
         }  
      }  
  
      // 3.5 Copying data from SQL Server to SQL Azure in .NET 4.5  
      //private static async Task AsyncSqlBulkCopySqlServerToSqlAzure() {  
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))  
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {  
      //      await srcConn.OpenAsync();  
      //      await destConn.OpenAsync();  
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatment, srcConn)) {  
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync()) {  
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {  
      //               await destCmd.ExecuteNonQueryAsync();  
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {  
      //                  bcp.DestinationTableName = temptable;  
      //                  await bcp.WriteToServerAsync(reader);  
      //               }  
      //            }  
      //         }  
      //      }  
      //   }  
      //}  
  
      // 3.6 Cancelling an Asynchronous Operation to SQL Azure  
      //private static async Task AsyncSqlBulkCopyCancel() {  
      //   CancellationTokenSource cts = new CancellationTokenSource();  
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))  
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {  
      //      await srcConn.OpenAsync(cts.Token);  
      //      await destConn.OpenAsync(cts.Token);  
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatment, srcConn)) {  
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync(cts.Token)) {  
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {  
      //               await destCmd.ExecuteNonQueryAsync(cts.Token);  
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {  
      //                  bcp.DestinationTableName = temptable;  
      //                  await bcp.WriteToServerAsync(reader, cts.Token);  
      //                  //Cancel Async SqlBulCopy Operation after 200 ms  
      //                  cts.CancelAfter(200);  
      //               }  
      //            }  
      //         }  
      //      }  
      //   }  
      //}  
  
      // 3.7 Using Async.Net and MARS  
      private static async Task AsyncSqlBulkCopyMARS() {  
         using (SqlConnection marsConn = new SqlConnection(marsConnectionString)) {  
            await marsConn.OpenAsync();  
  
            SqlCommand titlesCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[titles]", marsConn);  
            SqlCommand authorsCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[authors]", marsConn);  
            //With MARS we can have multiple active results sets on the same connection  
            using (SqlDataReader titlesReader = await titlesCmd.ExecuteReaderAsync())  
            using (SqlDataReader authorsReader = await authorsCmd.ExecuteReaderAsync()) {  
               await authorsReader.ReadAsync();  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               using (SqlConnection destConn = new SqlConnection(connectionString)) {  
                  await destConn.OpenAsync();  
                  using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {  
                     await destCmd.ExecuteNonQueryAsync();  
                     using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {  
                        bcp.DestinationTableName = temptable;  
                        await bcp.WriteToServerAsync(titlesReader);  
                     }  
                  }  
               }  
            }  
         }  
      }  
   }  
}  
```  
  
## <a name="asynchronously-using-multiple-commands-with-mars"></a><span data-ttu-id="25108-149">Usando vários comandos de modo assíncrono com o MARS</span><span class="sxs-lookup"><span data-stu-id="25108-149">Asynchronously Using Multiple Commands with MARS</span></span>  
 <span data-ttu-id="25108-150">O exemplo abre uma conexão única para o **AdventureWorks** banco de dados.</span><span class="sxs-lookup"><span data-stu-id="25108-150">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="25108-151">Usando um objeto <xref:System.Data.SqlClient.SqlCommand>, um <xref:System.Data.SqlClient.SqlDataReader> é criado.</span><span class="sxs-lookup"><span data-stu-id="25108-151">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="25108-152">À medida que o leitor é usado, um segundo <xref:System.Data.SqlClient.SqlDataReader> é aberto, usando dados do primeiro <xref:System.Data.SqlClient.SqlDataReader> como entrada para a cláusula WHERE para o segundo leitor.</span><span class="sxs-lookup"><span data-stu-id="25108-152">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25108-153">O exemplo a seguir usa o exemplo **AdventureWorks** banco de dados incluído com [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25108-153">The following example uses the sample **AdventureWorks** database included with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="25108-154">A cadeia de conexão fornecida no código de exemplo presume que o banco de dados esteja instalado e disponível no computador local.</span><span class="sxs-lookup"><span data-stu-id="25108-154">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="25108-155">Modifique a cadeia de conexão conforme o necessário para seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="25108-155">Modify the connection string as necessary for your environment.</span></span>  
  
```csharp
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class Class1 {  
   static void Main() {  
      Task task = MultipleCommands();  
      task.Wait();  
   }  
  
   static async Task MultipleCommands() {  
      // By default, MARS is disabled when connecting to a MARS-enabled.  
      // It must be enabled in the connection string.  
      string connectionString = GetConnectionString();  
  
      int vendorID;  
      SqlDataReader productReader = null;  
      string vendorSQL =  
        "SELECT VendorId, Name FROM Purchasing.Vendor";  
      string productSQL =  
        "SELECT Production.Product.Name FROM Production.Product " +  
        "INNER JOIN Purchasing.ProductVendor " +  
        "ON Production.Product.ProductID = " +  
        "Purchasing.ProductVendor.ProductID " +  
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
      using (SqlConnection awConnection =  
        new SqlConnection(connectionString)) {  
         SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
         SqlCommand productCmd =  
           new SqlCommand(productSQL, awConnection);  
  
         productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
         await awConnection.OpenAsync();  
         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {  
            while (await vendorReader.ReadAsync()) {  
               Console.WriteLine(vendorReader["Name"]);  
  
               vendorID = (int)vendorReader["VendorId"];  
  
               productCmd.Parameters["@VendorId"].Value = vendorID;  
               // The following line of code requires a MARS-enabled connection.  
               productReader = await productCmd.ExecuteReaderAsync();  
               using (productReader) {  
                  while (await productReader.ReadAsync()) {  
                     Console.WriteLine("  " +  
                       productReader["Name"].ToString());  
                  }  
               }  
            }  
         }  
      }  
   }  
  
   private static string GetConnectionString() {  
      // To avoid storing the connection string in your code, you can retrive it from a configuration file.  
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
   }  
}  
```  
  
## <a name="asynchronously-reading-and-updating-data-with-mars"></a><span data-ttu-id="25108-156">Lendo e atualizando dados de modo assíncrono com o MARS</span><span class="sxs-lookup"><span data-stu-id="25108-156">Asynchronously Reading and Updating Data with MARS</span></span>  
 <span data-ttu-id="25108-157">O MARS permite que uma conexão seja usada para operações de leitura e operações de DML com mais de uma operação pendente.</span><span class="sxs-lookup"><span data-stu-id="25108-157">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="25108-158">Este recurso elimina a necessidade de um aplicativo tratar erros de conexões ocupadas.</span><span class="sxs-lookup"><span data-stu-id="25108-158">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="25108-159">Além disso, o MARS pode substituir o usuário de cursores de servidor, que geralmente consome mais recursos.</span><span class="sxs-lookup"><span data-stu-id="25108-159">In addition, MARS can replace the user of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="25108-160">Por fim, porque várias operações podem operar em uma única conexão, eles podem compartilhar o mesmo contexto de transação, eliminando a necessidade de usar **sp_getbindtoken** e **sp_bindsession** armazenado do sistema procedimentos.</span><span class="sxs-lookup"><span data-stu-id="25108-160">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>  
  
 <span data-ttu-id="25108-161">O aplicativo de console a seguir demonstra como usar dois objetos <xref:System.Data.SqlClient.SqlDataReader> com três objetos <xref:System.Data.SqlClient.SqlCommand> e um único objeto <xref:System.Data.SqlClient.SqlConnection> com o MARS ativado.</span><span class="sxs-lookup"><span data-stu-id="25108-161">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="25108-162">O primeiro objeto de comando recupera uma lista de fornecedores cuja avaliação de crédito é 5.</span><span class="sxs-lookup"><span data-stu-id="25108-162">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="25108-163">O segundo objeto de comando usa a ID do fornecedor fornecido de um <xref:System.Data.SqlClient.SqlDataReader> para carregar o segundo <xref:System.Data.SqlClient.SqlDataReader> com todos os produtos para o fornecedor específico.</span><span class="sxs-lookup"><span data-stu-id="25108-163">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="25108-164">Cada registro de produto é visitado pelo segundo <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="25108-164">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="25108-165">Um cálculo é executado para determinar qual o novo **OnOrderQty** deve ser.</span><span class="sxs-lookup"><span data-stu-id="25108-165">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="25108-166">O terceiro objeto de comando, em seguida, é usado para atualizar o **ProductVendor** tabela com o novo valor.</span><span class="sxs-lookup"><span data-stu-id="25108-166">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="25108-167">Este processo inteiro ocorre em uma única transação, que é revertida no final.</span><span class="sxs-lookup"><span data-stu-id="25108-167">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25108-168">O exemplo a seguir usa o exemplo **AdventureWorks** banco de dados incluído com [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25108-168">The following example uses the sample **AdventureWorks** database included with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="25108-169">A cadeia de conexão fornecida no código de exemplo presume que o banco de dados esteja instalado e disponível no computador local.</span><span class="sxs-lookup"><span data-stu-id="25108-169">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="25108-170">Modifique a cadeia de conexão conforme o necessário para seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="25108-170">Modify the connection string as necessary for your environment.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class Program {  
   static void Main() {  
      Task task = ReadingAndUpdatingData();  
      task.Wait();  
   }  
  
   static async Task ReadingAndUpdatingData() {  
      // By default, MARS is disabled when connecting to a MARS-enabled host.  
      // It must be enabled in the connection string.  
      string connectionString = GetConnectionString();  
  
      SqlTransaction updateTx = null;  
      SqlCommand vendorCmd = null;  
      SqlCommand prodVendCmd = null;  
      SqlCommand updateCmd = null;  
  
      SqlDataReader prodVendReader = null;  
  
      int vendorID = 0;  
      int productID = 0;  
      int minOrderQty = 0;  
      int maxOrderQty = 0;  
      int onOrderQty = 0;  
      int recordsUpdated = 0;  
      int totalRecordsUpdated = 0;  
  
      string vendorSQL =  
          "SELECT VendorID, Name FROM Purchasing.Vendor " +  
          "WHERE CreditRating = 5";  
      string prodVendSQL =  
          "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
          "FROM Purchasing.ProductVendor " +  
          "WHERE VendorID = @VendorID";  
      string updateSQL =  
          "UPDATE Purchasing.ProductVendor " +  
          "SET OnOrderQty = @OrderQty " +  
          "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
      using (SqlConnection awConnection =  
        new SqlConnection(connectionString)) {  
         await awConnection.OpenAsync();  
         updateTx = await Task.Run(() => awConnection.BeginTransaction());  
  
         vendorCmd = new SqlCommand(vendorSQL, awConnection);  
         vendorCmd.Transaction = updateTx;  
  
         prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
         prodVendCmd.Transaction = updateTx;  
         prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
         updateCmd = new SqlCommand(updateSQL, awConnection);  
         updateCmd.Transaction = updateTx;  
         updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
         updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
         updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {  
            while (await vendorReader.ReadAsync()) {  
               Console.WriteLine(vendorReader["Name"]);  
  
               vendorID = (int)vendorReader["VendorID"];  
               prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
               prodVendReader = await prodVendCmd.ExecuteReaderAsync();  
  
               using (prodVendReader) {  
                  while (await prodVendReader.ReadAsync()) {  
                     productID = (int)prodVendReader["ProductID"];  
  
                     if (prodVendReader["OnOrderQty"] == DBNull.Value) {  
                        minOrderQty = (int)prodVendReader["MinOrderQty"];  
                        onOrderQty = minOrderQty;  
                     }  
                     else {  
                        maxOrderQty = (int)prodVendReader["MaxOrderQty"];  
                        onOrderQty = (int)(maxOrderQty / 2);  
                     }  
  
                     updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
                     updateCmd.Parameters["@ProductID"].Value = productID;  
                     updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
                     recordsUpdated = await updateCmd.ExecuteNonQueryAsync();  
                     totalRecordsUpdated += recordsUpdated;  
                  }  
               }  
            }  
         }  
         Console.WriteLine("Total Records Updated: ", totalRecordsUpdated.ToString());  
         await Task.Run(() => updateTx.Rollback());  
         Console.WriteLine("Transaction Rolled Back");  
      }  
   }  
  
   private static string GetConnectionString() {  
      // To avoid storing the connection string in your code, you can retrive it from a configuration file.  
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="25108-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25108-171">See Also</span></span>  
 <span data-ttu-id="25108-172">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="25108-172">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>