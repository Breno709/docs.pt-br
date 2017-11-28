---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 496967bc3638344d2b39d428b85270b575b325ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="8ff10-102">Elemento personalizado para SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="8ff10-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="8ff10-103">Define as configurações em uma seção de configuração personalizada que é definida por um</span><span class="sxs-lookup"><span data-stu-id="8ff10-103">Defines settings in a custom configuration section that is defined by a</span></span> <section> <span data-ttu-id="8ff10-104">elemento e usa o <xref:System.Configuration.SingleTagSectionHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="8ff10-104">element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="8ff10-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8ff10-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="8ff10-106">&nbsp;&nbsp;*\<sectionName >*</span><span class="sxs-lookup"><span data-stu-id="8ff10-106">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="8ff10-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ff10-107">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="8ff10-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="8ff10-108">Attributes</span></span>

<span data-ttu-id="8ff10-109">Atributos e valores de atributo são definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="8ff10-109">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="8ff10-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="8ff10-110">Parent element</span></span>

|     | <span data-ttu-id="8ff10-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ff10-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8ff10-112">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="8ff10-112">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="8ff10-113">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ff10-113">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8ff10-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8ff10-114">Child elements</span></span>

<span data-ttu-id="8ff10-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8ff10-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="8ff10-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ff10-116">Remarks</span></span>

<span data-ttu-id="8ff10-117">O  **\<sectionName >** é um elemento personalizado definido por um [  **\<seção >** ](~/docs/framework/configure-apps/file-schema/section-element.md) marca no [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="8ff10-117">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="8ff10-118">O sistema de configuração retorna um <xref:System.Collections.IDictionary> objeto quando você chamar <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ff10-118">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="8ff10-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ff10-119">Example</span></span>

<span data-ttu-id="8ff10-120">O exemplo a seguir declara um elemento personalizado chamado  **\<sampleSection >** que contém as configurações de leitura pelo <xref:System.Configuration.SingleTagSectionHandler> classe:</span><span class="sxs-lookup"><span data-stu-id="8ff10-120">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="8ff10-121">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="8ff10-121">Configuration file</span></span>

<span data-ttu-id="8ff10-122">Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ff10-122">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ff10-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ff10-123">See also</span></span>

[<span data-ttu-id="8ff10-124">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8ff10-124">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)