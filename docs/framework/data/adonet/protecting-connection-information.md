---
title: "Protegendo informações de conexão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31196697a606b3edbc0b3aa00b01e5eacb66cb03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="protecting-connection-information"></a><span data-ttu-id="cfc77-102">Protegendo informações de conexão</span><span class="sxs-lookup"><span data-stu-id="cfc77-102">Protecting Connection Information</span></span>
<span data-ttu-id="cfc77-103">A proteção do acesso à fonte de dados é essencial para a segurança do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfc77-103">Protecting access to your data source is one of the most important goals when securing an application.</span></span> <span data-ttu-id="cfc77-104">Uma cadeia de conexão apresenta uma vulnerabilidade potencial se não estiver protegida.</span><span class="sxs-lookup"><span data-stu-id="cfc77-104">A connection string presents a potential vulnerability if it is not secured.</span></span> <span data-ttu-id="cfc77-105">Armazenar as informações de conexão em texto sem formatação ou persistir-la na memória pode comprometer seu sistema inteiro.</span><span class="sxs-lookup"><span data-stu-id="cfc77-105">Storing connection information in plain text or persisting it in memory risks compromising your entire system.</span></span> <span data-ttu-id="cfc77-106">Cadeias de caracteres de Conexão inseridas no seu código-fonte podem ser lida usando o [Ildasm.exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para exibir o Microsoft intermediate language (MSIL) em um assembly compilado.</span><span class="sxs-lookup"><span data-stu-id="cfc77-106">Connection strings embedded in your source code can be read using the [Ildasm.exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) in a compiled assembly.</span></span>  
  
 <span data-ttu-id="cfc77-107">As vulnerabilidades de segurança envolvendo cadeias de conexão podem surgir com base no tipo de autenticação usado, em como as cadeias de conexão são persistidas na memória e no disco e nas técnicas usadas para construí-los em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cfc77-107">Security vulnerabilities involving connection strings can arise based on the type of authentication used, how connection strings are persisted in memory and on disk, and the techniques used to construct them at run time.</span></span>  
  
## <a name="use-windows-authentication"></a><span data-ttu-id="cfc77-108">Use a Autenticação do Windows</span><span class="sxs-lookup"><span data-stu-id="cfc77-108">Use Windows Authentication</span></span>  
 <span data-ttu-id="cfc77-109">Para ajudar a limitar o acesso a sua fonte de dados, você deverá proteger as informações de conexão como a identificação do usuário, senha e nome da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cfc77-109">To help limit access to your data source, you must secure connection information such as user ID, password, and data source name.</span></span> <span data-ttu-id="cfc77-110">Para evitar a exposição de informações do usuário, é recomendável usar a autenticação do Windows (também conhecido como *segurança integrada*) sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="cfc77-110">In order to avoid exposing user information, we recommend using Windows authentication (sometimes referred to as *integrated security*) wherever possible.</span></span> <span data-ttu-id="cfc77-111">A autenticação do Windows é especificada em uma cadeia de conexão usando as palavras-chave `Integrated Security` ou `Trusted_Connection`, eliminando a necessidade de usar uma identificação de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="cfc77-111">Windows authentication is specified in a connection string by using the `Integrated Security` or `Trusted_Connection` keywords, eliminating the need to use a user ID and password.</span></span> <span data-ttu-id="cfc77-112">Ao usar a autenticação do Windows, os usuários são autenticados pelo Windows e o acesso ao servidor e os recursos de banco de dados são determinados concedendo permissões a usuários e grupos do Windows.</span><span class="sxs-lookup"><span data-stu-id="cfc77-112">When using Windows authentication, users are authenticated by Windows, and access to server and database resources is determined by granting permissions to Windows users and groups.</span></span>  
  
 <span data-ttu-id="cfc77-113">Para situações onde não é possível usar a autenticação do Windows, você deverá ter cuidado adicional porque as credenciais do usuário são expostas na cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="cfc77-113">For situations where it is not possible to use Windows authentication, you must use extra care because user credentials are exposed in the connection string.</span></span> <span data-ttu-id="cfc77-114">Em um aplicativo do ASP.NET, você pode configurar uma conta do Windows como uma identidade fixa que é usada para se conectar a bancos de dados e outros recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="cfc77-114">In an ASP.NET application, you can configure a Windows account as a fixed identity that is used to connect to databases and other network resources.</span></span> <span data-ttu-id="cfc77-115">Você habilitar a representação no elemento identity no **Web. config** de arquivo e especifique um nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="cfc77-115">You enable impersonation in the identity element in the **web.config** file and specify a user name and password.</span></span>  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 <span data-ttu-id="cfc77-116">A conta de identidade fixa deve ser uma conta de privilégios baixos que tem concedidas somente as permissões necessárias no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cfc77-116">The fixed identity account should be a low-privilege account that has been granted only necessary permissions in the database.</span></span> <span data-ttu-id="cfc77-117">Além disso, você deve criptografar o arquivo de configuração de modo que o nome de usuário e a senha não sejam expostos em texto não criptografado.</span><span class="sxs-lookup"><span data-stu-id="cfc77-117">In addition, you should encrypt the configuration file so that the user name and password are not exposed in clear text.</span></span>  
  
## <a name="do-not-use-universal-data-link-udl-files"></a><span data-ttu-id="cfc77-118">Não use arquivos UDL (Universal Data Link)</span><span class="sxs-lookup"><span data-stu-id="cfc77-118">Do Not Use Universal Data Link (UDL) files</span></span>  
 <span data-ttu-id="cfc77-119">Evite armazenar cadeias de conexão para um <xref:System.Data.OleDb.OleDbConnection> em um arquivo UDL (Universal Data Link).</span><span class="sxs-lookup"><span data-stu-id="cfc77-119">Avoid storing connection strings for an <xref:System.Data.OleDb.OleDbConnection> in a Universal Data Link (UDL) file.</span></span> <span data-ttu-id="cfc77-120">UDLs são armazenados em texto não criptografado e não podem ser criptografados.</span><span class="sxs-lookup"><span data-stu-id="cfc77-120">UDLs are stored in clear text and cannot be encrypted.</span></span> <span data-ttu-id="cfc77-121">Um arquivo UDL é um recurso externo com base em arquivo para o seu aplicativo e ele não poderá ser protegido ou criptografado usando o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cfc77-121">A UDL file is an external file-based resource to your application, and it cannot be secured or encrypted using the .NET Framework.</span></span>  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a><span data-ttu-id="cfc77-122">Evite ataques de injeção com construtores de cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="cfc77-122">Avoid Injection Attacks with Connection String Builders</span></span>  
 <span data-ttu-id="cfc77-123">Um ataque de injeção de cadeia de conexão pode ocorrer quando a concatenação dinâmica de cadeia de caracteres é usada para criar cadeias de conexão com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="cfc77-123">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings based on user input.</span></span> <span data-ttu-id="cfc77-124">Se a entrada do usuário não for validada e o texto mal-intencionado ou caracteres não forem escapados, um invasor poderá acessar dados confidenciais ou outros recursos no servidor.</span><span class="sxs-lookup"><span data-stu-id="cfc77-124">If the user input is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="cfc77-125">Para resolver esse problema, o ADO.NET 2.0 introduziu novas classes de construtor de cadeia de conexão para validar a sintaxe da cadeia de conexão e garantir que os parâmetros adicionais não sejam introduzidos.</span><span class="sxs-lookup"><span data-stu-id="cfc77-125">To address this problem, ADO.NET 2.0 introduced new connection string builder classes to validate connection string syntax and ensure that additional parameters are not introduced.</span></span> <span data-ttu-id="cfc77-126">Para obter mais informações, consulte [construtores de cadeia de Conexão](../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="cfc77-126">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
## <a name="use-persist-security-infofalse"></a><span data-ttu-id="cfc77-127">Use segurança de persistência Info=False</span><span class="sxs-lookup"><span data-stu-id="cfc77-127">Use Persist Security Info=False</span></span>  
 <span data-ttu-id="cfc77-128">O valor padrão para `Persist Security Info` é falso; nós recomendamos usar esta opção em todas as cadeias de conexão.</span><span class="sxs-lookup"><span data-stu-id="cfc77-128">The default value for `Persist Security Info` is false; we recommend using this default in all connection strings.</span></span> <span data-ttu-id="cfc77-129">Configurar `Persist Security Info` como `true` ou `yes` permite informações confidenciais de segurança, incluindo a identificação de usuário e a senha, para serem obtidas de uma conexão depois que ela tiver sido aberta.</span><span class="sxs-lookup"><span data-stu-id="cfc77-129">Setting `Persist Security Info` to `true` or `yes` allows security-sensitive information, including the user ID and password, to be obtained from a connection after it has been opened.</span></span> <span data-ttu-id="cfc77-130">Quando `Persist Security Info` for definido como `false` ou `no`, as informações de segurança serão descartadas após serem usadas para abrir a conexão, garantindo que uma fonte não confiável não tenha acesso a informações confidenciais de segurança.</span><span class="sxs-lookup"><span data-stu-id="cfc77-130">When `Persist Security Info` is set to `false` or `no`, security information is discarded after it is used to open the connection, ensuring that an untrusted source does not have access to security-sensitive information.</span></span>  
  
## <a name="encrypt-configuration-files"></a><span data-ttu-id="cfc77-131">Criptografe arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="cfc77-131">Encrypt Configuration Files</span></span>  
 <span data-ttu-id="cfc77-132">Você também pode armazenar cadeias de conexão em arquivos de configuração, o que elimina a necessidade de inseri-las no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfc77-132">You can also store connection strings in configuration files, which eliminates the need to embed them in your application's code.</span></span> <span data-ttu-id="cfc77-133">Os arquivos de configuração são arquivos XML padrão para os quais o .NET Framework definiu um conjunto comum de elementos.</span><span class="sxs-lookup"><span data-stu-id="cfc77-133">Configuration files are standard XML files for which the .NET Framework has defined a common set of elements.</span></span> <span data-ttu-id="cfc77-134">Cadeias de caracteres de Conexão nos arquivos de configuração normalmente são armazenadas dentro de  **\<connectionStrings >** elemento no **App. config** para um aplicativo do Windows, ou o  **Web. config** arquivo para um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cfc77-134">Connection strings in configuration files are typically stored inside the **\<connectionStrings>** element in the **app.config** for a Windows application, or the **web.config** file for an ASP.NET application.</span></span> <span data-ttu-id="cfc77-135">Para obter mais informações sobre os conceitos básicos de armazenar, recuperar e criptografar cadeias de caracteres de conexão de arquivos de configuração, consulte [cadeias de caracteres de Conexão e arquivos de configuração](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="cfc77-135">For more information on the basics of storing, retrieving and encrypting connection strings from configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc77-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfc77-136">See Also</span></span>  
 <span data-ttu-id="cfc77-137">[Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="cfc77-137">[Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)</span></span>  
 [<span data-ttu-id="cfc77-138">Criptografando informações de configuração usando configuração protegida</span><span class="sxs-lookup"><span data-stu-id="cfc77-138">Encrypting Configuration Information Using Protected Configuration</span></span>](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)  
 <span data-ttu-id="cfc77-139">[PAVE Security in Native and .NET Framework Code](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784) (PAVE Segurança no código nativo e do .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="cfc77-139">[PAVE Security in Native and .NET Framework Code](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784)</span></span>  
 <span data-ttu-id="cfc77-140">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="cfc77-140">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>