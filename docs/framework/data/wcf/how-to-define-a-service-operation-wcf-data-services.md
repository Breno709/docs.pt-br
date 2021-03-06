---
title: "Como: definir uma operação de serviço (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03dc0b774fe6c3e077fa539fc14c7df4a1fb448d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Como: definir uma operação de serviço (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]expor os métodos que são definidos no servidor como operações de serviço. Operações de serviço é permitir que um serviço de dados fornecer acesso por meio de um URI para um método que é definido no servidor. Para definir uma operação de serviço, se aplicam a [`WebGet]` ou `[WebInvoke]` atributo ao método. Para dar suporte a operadores de consulta, a operação de serviço deve retornar um <xref:System.Linq.IQueryable%601> instância. Operações de serviço podem acessar a fonte de dados por meio de <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> propriedade o <xref:System.Data.Services.DataService%601>. Para obter mais informações, consulte [operações de serviço](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 O exemplo neste tópico define uma operação de serviço chamada `GetOrdersByCity` que retorna um filtrado <xref:System.Linq.IQueryable%601> instância de `Orders` e relacionados `Order_Details` objetos. O exemplo acessa o <xref:System.Data.Objects.ObjectContext> instância que é a fonte de dados para o serviço de dados de exemplo Northwind. Esse serviço é criado quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Para definir uma operação de serviço no serviço de dados Northwind  
  
1.  No projeto do serviço de dados Northwind, abra o arquivo Northwind.svc.  
  
2.  Na classe `Northwind`, defina um método de operação de serviço chamado `GetOrdersByCity` da seguinte maneira:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  No `InitializeService` método o `Northwind` de classe, adicione o código a seguir para habilitar o acesso à operação de serviço:  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>A consulta a operação do serviço GetOrdersByCity  
  
-   Em um navegador da Web, digite um dos seguintes URIs para invocar a operação de serviço que é definida no exemplo a seguir:  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir implementa uma operação de serviço chamada `GetOrderByCity` no serviço de dados Northwind. Essa operação usa o ADO.NET Entity Framework para retornar um conjunto de `Orders` e relacionados `Order_Details` objetos como um <xref:System.Linq.IQueryable%601> instância com base no nome da cidade fornecido.  
  
> [!NOTE]
>  Operadores de consulta têm suporte nesse ponto de extremidade de operação de serviço porque o método retorna um <xref:System.Linq.IQueryable%601> instância.  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>Consulte também  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)
