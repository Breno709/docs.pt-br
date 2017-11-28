---
title: "FUNÇÃO (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 40c8f218238492bbbc4af543aa6f9a635454b359
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="function-entity-sql"></a><span data-ttu-id="b3c89-102">FUNÇÃO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b3c89-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="b3c89-103">Define uma função no escopo de um comando de consulta Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="b3c89-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3c89-104">Syntax</span></span>  
  
```  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a><span data-ttu-id="b3c89-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b3c89-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="b3c89-106">Nome da função.</span><span class="sxs-lookup"><span data-stu-id="b3c89-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="b3c89-107">Nome de um parâmetro em função.</span><span class="sxs-lookup"><span data-stu-id="b3c89-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="b3c89-108">Uma expressão válida de Entity SQL que é a função.</span><span class="sxs-lookup"><span data-stu-id="b3c89-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="b3c89-109">O comando na função pode atuar nos parâmetros de `parameter_name` passados para a função.</span><span class="sxs-lookup"><span data-stu-id="b3c89-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="b3c89-110">Nome de um tipo suportado.</span><span class="sxs-lookup"><span data-stu-id="b3c89-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="b3c89-111">COLEÇÃO ( <type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="b3c89-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="b3c89-112">Uma expressão que retorna uma coleção de tipos suportados, de linhas, ou de referências.</span><span class="sxs-lookup"><span data-stu-id="b3c89-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="b3c89-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="b3c89-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="b3c89-114">Uma expressão que retorna uma referência a um tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="b3c89-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="b3c89-115">LINHA **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="b3c89-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="b3c89-116">Uma expressão que retorna registros anônimos, tipados estrutural de um ou mais valores.</span><span class="sxs-lookup"><span data-stu-id="b3c89-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="b3c89-117">Para obter mais informações, consulte [linha](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b3c89-117">For more information, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3c89-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3c89-118">Remarks</span></span>  
 <span data-ttu-id="b3c89-119">Várias funções com o mesmo nome podem ser declarados embutidos, como as assinaturas de função são diferentes.</span><span class="sxs-lookup"><span data-stu-id="b3c89-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="b3c89-120">Para obter mais informações, consulte [a resolução de sobrecarga de função](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b3c89-120">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="b3c89-121">Uma função in-line pode ser chamado em um comando de Entity SQL somente após foi definida no comando.</span><span class="sxs-lookup"><span data-stu-id="b3c89-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="b3c89-122">No entanto, uma função in-line pode ser chamada dentro de outra função in-line tanto antes ou após a função chamada foi definido.</span><span class="sxs-lookup"><span data-stu-id="b3c89-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="b3c89-123">No exemplo a seguir, funciona a função B de chamadas de antes que a função B é definida:</span><span class="sxs-lookup"><span data-stu-id="b3c89-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="b3c89-124">Para obter mais informações, consulte [como: chamar uma função definida pelo usuário](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02).</span><span class="sxs-lookup"><span data-stu-id="b3c89-124">For more information, see [How to: Call a User-Defined Function](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02).</span></span>  
  
 <span data-ttu-id="b3c89-125">As funções podem também ser declaradas no próprio modelo.</span><span class="sxs-lookup"><span data-stu-id="b3c89-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="b3c89-126">As funções declaradas no modelo são executadas da mesma forma como as funções está embutido no comando.</span><span class="sxs-lookup"><span data-stu-id="b3c89-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="b3c89-127">Para obter mais informações, consulte [funções definidas pelo usuário](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b3c89-127">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3c89-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3c89-128">Example</span></span>  
 <span data-ttu-id="b3c89-129">O seguinte comando de Entity SQL define uma função `Products` que recebe um valor inteiro para filtrar os produtos retornados.</span><span class="sxs-lookup"><span data-stu-id="b3c89-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="b3c89-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3c89-130">Example</span></span>  
 <span data-ttu-id="b3c89-131">O seguinte comando de Entity SQL define uma função `StringReturnsCollection` que utiliza uma coleção de cadeias de caracteres para filtrar os contatos retornados.</span><span class="sxs-lookup"><span data-stu-id="b3c89-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="b3c89-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3c89-132">See Also</span></span>  
 [<span data-ttu-id="b3c89-133">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b3c89-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 <span data-ttu-id="b3c89-134">[Entity SQL Language](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="b3c89-134">[Entity SQL Language](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)</span></span>