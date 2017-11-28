---
title: COMO (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 773547b097bad80e82350b473b6e59d0d84aa6dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="like-entity-sql"></a><span data-ttu-id="1245f-102">COMO (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1245f-102">LIKE (Entity SQL)</span></span>
<span data-ttu-id="1245f-103">Determina se um elemento `String` de caracteres corresponde a um padrão especificado.</span><span class="sxs-lookup"><span data-stu-id="1245f-103">Determines whether a specific character `String` matches a specified pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1245f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1245f-104">Syntax</span></span>  
  
```  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1245f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1245f-105">Arguments</span></span>  
 `match`  
 <span data-ttu-id="1245f-106">Um [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressão que é avaliada como um `String`.</span><span class="sxs-lookup"><span data-stu-id="1245f-106">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression that evaluates to a `String`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="1245f-107">Um padrão para correspondência com o elemento `String` especificado.</span><span class="sxs-lookup"><span data-stu-id="1245f-107">A pattern to match to the specified `String`.</span></span>  
  
 `escape`  
 <span data-ttu-id="1245f-108">Um caractere de escape.</span><span class="sxs-lookup"><span data-stu-id="1245f-108">An escape character.</span></span>  
  
 <span data-ttu-id="1245f-109">NOT</span><span class="sxs-lookup"><span data-stu-id="1245f-109">NOT</span></span>  
 <span data-ttu-id="1245f-110">Especifica que o resultado de LIKE seja negado.</span><span class="sxs-lookup"><span data-stu-id="1245f-110">Specifies that the result of LIKE be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1245f-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1245f-111">Return Value</span></span>  
 <span data-ttu-id="1245f-112">`true` se `string` corresponde ao padrão; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="1245f-112">`true` if the `string` matches the pattern; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1245f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="1245f-113">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="1245f-114">expressões que usam o operador LIKE são avaliadas em grande parte da mesma maneira que as expressões que usam igualdade como os critérios de filtro.</span><span class="sxs-lookup"><span data-stu-id="1245f-114"> expressions that use the LIKE operator are evaluated in much the same way as expressions that use equality as the filter criteria.</span></span> <span data-ttu-id="1245f-115">No entanto, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressões que usam o operador LIKE podem incluir literais e caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="1245f-115">However, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator can include both literals and wildcard characters.</span></span>  
  
 <span data-ttu-id="1245f-116">A tabela a seguir descreve a sintaxe de `string` do padrão.</span><span class="sxs-lookup"><span data-stu-id="1245f-116">The following table describes the syntax of the pattern `string`.</span></span>  
  
|<span data-ttu-id="1245f-117">Caractere curinga</span><span class="sxs-lookup"><span data-stu-id="1245f-117">Wildcard Character</span></span>|<span data-ttu-id="1245f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1245f-118">Description</span></span>|<span data-ttu-id="1245f-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1245f-119">Example</span></span>|  
|------------------------|-----------------|-------------|  
|%|<span data-ttu-id="1245f-120">Qualquer `string` entre zero ou mais caracteres.</span><span class="sxs-lookup"><span data-stu-id="1245f-120">Any `string` of zero or more characters.</span></span>|<span data-ttu-id="1245f-121">`title like '%computer%'`Localiza todos os títulos com a palavra `"computer"` em qualquer lugar no título.</span><span class="sxs-lookup"><span data-stu-id="1245f-121">`title like '%computer%'` finds all titles with the word `"computer"` anywhere in the title.</span></span>|  
|<span data-ttu-id="1245f-122">_ (sublinhado)</span><span class="sxs-lookup"><span data-stu-id="1245f-122">_ (underscore)</span></span>|<span data-ttu-id="1245f-123">Qualquer caractere único.</span><span class="sxs-lookup"><span data-stu-id="1245f-123">Any single character.</span></span>|<span data-ttu-id="1245f-124">`firstname like '_ean'`Localiza todos os quatro letras nomes que terminam com `"ean`, "como Dean ou Sean.</span><span class="sxs-lookup"><span data-stu-id="1245f-124">`firstname like '_ean'` finds all four-letter first names that end with `"ean`," such as Dean or Sean.</span></span>|  
|<span data-ttu-id="1245f-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="1245f-125">[ ]</span></span>|<span data-ttu-id="1245f-126">Qualquer caractere único no intervalo ([a-f]) ou no conjunto ([abcdef]) especificado.</span><span class="sxs-lookup"><span data-stu-id="1245f-126">Any single character in the specified range ([a-f]) or set ([abcdef]).</span></span>|<span data-ttu-id="1245f-127">`lastname like '[C-P]arsen'`Localiza sobrenomes terminam com "arsen" e começando com qualquer caractere único entre C e P, como Carsen ou Larsen.</span><span class="sxs-lookup"><span data-stu-id="1245f-127">`lastname like '[C-P]arsen'` finds last names ending with "arsen" and beginning with any single character between C and P, such as Carsen or Larsen.</span></span>|  
|<span data-ttu-id="1245f-128">[^]</span><span class="sxs-lookup"><span data-stu-id="1245f-128">[^]</span></span>|<span data-ttu-id="1245f-129">Qualquer caractere único que não esteja no intervalo ([^a-f]) nem no conjunto ([^abcdef]) especificado.</span><span class="sxs-lookup"><span data-stu-id="1245f-129">Any single character not in the specified range ([^a-f]) or set ([^abcdef]).</span></span>|<span data-ttu-id="1245f-130">`lastname like 'de[^l]%'`Localiza todos os sobrenomes que começam com "de" e não incluem "l" como a seguinte letra.</span><span class="sxs-lookup"><span data-stu-id="1245f-130">`lastname like 'de[^l]%'` finds all last names that begin with "de" and do not include "l" as the following letter.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="1245f-131">O operador [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE e a cláusula ESCAPE não podem ser aplicados a valores de `System.DateTime` ou `System.Guid`.</span><span class="sxs-lookup"><span data-stu-id="1245f-131">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE operator and ESCAPE clause cannot be applied to `System.DateTime` or `System.Guid` values.</span></span>  
  
 <span data-ttu-id="1245f-132">LIKE dá suporte à correspondência de padrões ASCII e à correspondência de padrões Unicode.</span><span class="sxs-lookup"><span data-stu-id="1245f-132">LIKE supports ASCII pattern matching and Unicode pattern matching.</span></span> <span data-ttu-id="1245f-133">Quando todos os parâmetros são caracteres ASCII, a correspondência de padrões ASCII é executada.</span><span class="sxs-lookup"><span data-stu-id="1245f-133">When all parameters are ASCII characters, ASCII pattern matching is performed.</span></span> <span data-ttu-id="1245f-134">Se um ou mais dos argumentos são Unicode, todos os argumentos são convertidos em Unicode e a correspondência de padrões Unicode é executada.</span><span class="sxs-lookup"><span data-stu-id="1245f-134">If one or more of the arguments are Unicode, all arguments are converted to Unicode and Unicode pattern matching is performed.</span></span> <span data-ttu-id="1245f-135">Quando você usa Unicode com LIKE, espaços em branco à direita são significativos; no entanto, para não Unicode, os espaços em branco à direita não são significativos.</span><span class="sxs-lookup"><span data-stu-id="1245f-135">When you use Unicode with LIKE, trailing blanks are significant; however, for non-Unicode, trailing blanks are not significant.</span></span> <span data-ttu-id="1245f-136">A sintaxe de cadeia de caracteres padrão de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é o mesmo de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1245f-136">The pattern string syntax of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is the same as that of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1245f-137">Um padrão pode incluir caracteres regulares e caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="1245f-137">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="1245f-138">Durante a correspondência de padrões, os caracteres regulares devem corresponder exatamente aos caracteres especificados no caractere `string`.</span><span class="sxs-lookup"><span data-stu-id="1245f-138">During pattern matching, regular characters must exactly match the characters specified in the character `string`.</span></span> <span data-ttu-id="1245f-139">No entanto, os caracteres curinga podem ser correspondentes com fragmentos arbitrários da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1245f-139">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="1245f-140">Quando usado com caracteres curinga, o operador LIKE é mais flexível do que os operadores de comparação de cadeia de caracteres = e! =.</span><span class="sxs-lookup"><span data-stu-id="1245f-140">When it is used with wildcard characters, the LIKE operator is more flexible than the = and != string comparison operators.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1245f-141">Você pode usar extensões específicas ao provedor se o destino for um provedor específico.</span><span class="sxs-lookup"><span data-stu-id="1245f-141">You may use provider-specific extensions if you target a specific provider.</span></span> <span data-ttu-id="1245f-142">No entanto, esses construtores podem ser tratados de maneira diferente por outros provedores, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="1245f-142">However, such constructs may be treated differently by other providers, for example.</span></span> <span data-ttu-id="1245f-143">O SqlServer dá suporte aos padrões [first-last] e [^first-last], onde o primeiro padrão corresponde exatamente a um caractere entre o primeiro e o último, e o segundo padrão corresponde exatamente a um caractere que não esteja entre o primeiro e o último.</span><span class="sxs-lookup"><span data-stu-id="1245f-143">SqlServer supports [first-last] and [^first-last] patterns where the former matches exactly one character between first and last, and the latter matches exactly one character that is not between first and last.</span></span>  
  
### <a name="escape"></a><span data-ttu-id="1245f-144">Escape</span><span class="sxs-lookup"><span data-stu-id="1245f-144">Escape</span></span>  
 <span data-ttu-id="1245f-145">Ao usar a cláusula ESCAPE, você pode pesquisar cadeias de caracteres que incluam um ou mais dos caracteres curinga especiais descritos na tabela da seção anterior.</span><span class="sxs-lookup"><span data-stu-id="1245f-145">By using the ESCAPE clause, you can search for character strings that include one or more of the special wildcard characters described in the table in the previous section.</span></span> <span data-ttu-id="1245f-146">Por exemplo, suponha que vários documentos incluam o literal "100%" no título e que você deseje pesquisar em todos esses documentos.</span><span class="sxs-lookup"><span data-stu-id="1245f-146">For example, assume several documents include the literal "100%" in the title and you want to search for all of those documents.</span></span> <span data-ttu-id="1245f-147">Como o caractere de porcentagem (%)) é um caractere curinga, você deve escapar usando o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cláusula de ESCAPE para executar com êxito a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1245f-147">Because the percent (%) character is a wildcard character, you must escape it using the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE clause to successfully execute the search.</span></span> <span data-ttu-id="1245f-148">Veja a seguir um exemplo desse filtro.</span><span class="sxs-lookup"><span data-stu-id="1245f-148">The following is an example of this filter.</span></span>  
  
```  
"title like '%100!%%' escape '!'"  
```  
  
 <span data-ttu-id="1245f-149">Nesta expressão de pesquisa, o caractere curinga de porcentagem (%) que segue imediatamente o caractere de ponto de exclamação (!) é tratado como um literal, não como um caractere curinga.</span><span class="sxs-lookup"><span data-stu-id="1245f-149">In this search expression, the percent wildcard character (%) immediately following the exclamation point character (!) is treated as a literal, instead of as a wildcard character.</span></span> <span data-ttu-id="1245f-150">Você pode usar qualquer caractere como um caractere de escape, exceto para o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] caracteres curingas e o quadrado colchete (`[ ]`) caracteres.</span><span class="sxs-lookup"><span data-stu-id="1245f-150">You can use any character as an escape character except for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wildcard characters and the square bracket (`[ ]`) characters.</span></span> <span data-ttu-id="1245f-151">No exemplo anterior, o caractere de ponto de exclamação (!) é o caractere de escape.</span><span class="sxs-lookup"><span data-stu-id="1245f-151">In the previous example, the exclamation point (!) character is the escape character.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1245f-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1245f-152">Example</span></span>  
 <span data-ttu-id="1245f-153">Os dois seguintes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consultas usam LIKE e ESCAPE operadores para determinar se uma cadeia de caracteres específica corresponde a um padrão especificado.</span><span class="sxs-lookup"><span data-stu-id="1245f-153">The following two [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries use the LIKE and ESCAPE operators to determine whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="1245f-154">A primeira consulta procura o `Name` que começa com os caracteres `Down_`.</span><span class="sxs-lookup"><span data-stu-id="1245f-154">The first query searches for the `Name` that starts with the characters `Down_`.</span></span> <span data-ttu-id="1245f-155">Essa consulta usa a opção ESCAPE porque o sublinhado (`_`) é um caractere curinga.</span><span class="sxs-lookup"><span data-stu-id="1245f-155">This query uses the ESCAPE option because the underscore (`_`) is a wildcard character.</span></span> <span data-ttu-id="1245f-156">Sem especificar a opção de ESCAPE, a consulta procura qualquer `Name` valores que começam com a palavra `Down` seguido de qualquer caractere único que não seja o caractere de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="1245f-156">Without specifying the ESCAPE option, the query would search for any `Name` values that start with the word `Down` followed by any single character other than the underscore character.</span></span> <span data-ttu-id="1245f-157">As consultas são baseadas no modelo de vendas do AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1245f-157">The queries are based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1245f-158">Para compilar e executar essa consulta, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="1245f-158">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1245f-159">Siga o procedimento [como: executar uma consulta que retorna resultados de PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1245f-159">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="1245f-160">Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="1245f-160">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIKE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#like)]  
  
## <a name="see-also"></a><span data-ttu-id="1245f-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1245f-161">See Also</span></span>  
 [<span data-ttu-id="1245f-162">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1245f-162">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)