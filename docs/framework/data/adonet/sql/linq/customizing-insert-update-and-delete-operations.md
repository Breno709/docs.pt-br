---
title: "Personalizando a inserção, atualiazação, e as operações de exclusão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e48ac307087d5b90567c720d0c215ac0d52ccb6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="460db-102">Personalizando a inserção, atualiazação, e as operações de exclusão</span><span class="sxs-lookup"><span data-stu-id="460db-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="460db-103">Por padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gerencia dinâmico SQL para implementar à leitura, inserção, atualiazação, e as operações de exclusão.</span><span class="sxs-lookup"><span data-stu-id="460db-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="460db-104">Na prática, no entanto, você personaliza normalmente seu aplicativo atender às suas necessidades comerciais.</span><span class="sxs-lookup"><span data-stu-id="460db-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="460db-105">Se você estiver usando [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], você pode usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para personalizar a inserção, atualização e exclusão de ações.</span><span class="sxs-lookup"><span data-stu-id="460db-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="460db-106">Tópicos desta seção descreve as técnicas que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece personalizando à leitura, inserção, atualiazação, e as operações de exclusão em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460db-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="460db-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="460db-107">In This Section</span></span>  
 [<span data-ttu-id="460db-108">Personalizando operações: Visão geral</span><span class="sxs-lookup"><span data-stu-id="460db-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="460db-109">Descreve as diversas técnicas que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece personalizando à leitura, inserção, atualiazação, e as operações de exclusão.</span><span class="sxs-lookup"><span data-stu-id="460db-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="460db-110">Inserir, atualizar e excluir operações</span><span class="sxs-lookup"><span data-stu-id="460db-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="460db-111">Descreve os processos de opção de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para manipular dados de base de dados.</span><span class="sxs-lookup"><span data-stu-id="460db-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="460db-112">Responsabilidades do desenvolvedor em Substituir o comportamento padrão</span><span class="sxs-lookup"><span data-stu-id="460db-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="460db-113">Descreve a função do desenvolvedor em implementar os requisitos não aplicadas por [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="460db-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="460db-114">Adicionando lógica comercial usando métodos parciais</span><span class="sxs-lookup"><span data-stu-id="460db-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="460db-115">Descreve como usar os métodos parciais para substituir métodos gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="460db-115">Describes how to use partial methods to override autogenerated methods.</span></span>