---
title: Como baixar um arquivo no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc67d28b870f86c6464e86f7682f71e6e36ea9e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Como baixar um arquivo no Visual Basic
O método <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> pode ser usado para baixar um arquivo remoto e armazená-lo em um local específico. Se o parâmetro `ShowUI` for definido como `True`, uma caixa de diálogo será exibida mostrando o andamento do download e permitindo que os usuários cancelem a operação. Por padrão, os arquivos existentes com o mesmo nome não são sobrescritos. Se você deseja sobrescrever os arquivos existentes, defina o parâmetro `overwrite` como `True`.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome da unidade não é válido (<xref:System.ArgumentException>).  
  
-   A autenticação necessária não foi fornecida (<xref:System.UnauthorizedAccessException> ou <xref:System.Security.SecurityException>).  
  
-   O servidor não responde dentro do `connectionTimeout` especificado (<xref:System.TimeoutException>).  
  
-   A solicitação foi negada pelo site (<xref:System.Net.WebException>).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo. Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic. Verifique todas as entradas antes de usar os dados no seu aplicativo. O conteúdo do arquivo pode não ser esperado, e os métodos para ler o arquivo podem falhar.  
  
### <a name="to-download-a-file"></a>Para baixar um arquivo  
  
-   Use o método `DownloadFile` para baixar o arquivo, especificando o local do arquivo de destino como uma cadeia de caracteres ou URI e especificando o local no qual armazenar o arquivo. Este exemplo baixa o arquivo `WineList.txt` de `http://www.cohowinery.com/downloads` e salva-o em `C:\Documents and Settings\All Users\Documents`:  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Para baixar um arquivo, especificando um intervalo de tempo limite  
  
-   Use o método `DownloadFile` para baixar o arquivo, especificando o local do arquivo de destino como uma cadeia de caracteres ou URI, especificando o local no qual armazenar o arquivo e especificando o intervalo de tempo limite, em milissegundos (o padrão é 1000). Este exemplo baixa o arquivo `WineList.txt` de `http://www.cohowinery.com/downloads` e salva-o em `C:\Documents and Settings\All Users\Documents`, especificando um intervalo de tempo limite de 500 milissegundos:  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Para baixar um arquivo, fornecendo um nome de usuário e senha  
  
-   Use o método `DownLoadFile` para baixar o arquivo, especificando o local do arquivo de destino como uma cadeia de caracteres ou URI, especificando o local no qual armazenar o arquivo e especificando o nome de usuário e a senha. Este exemplo baixa o arquivo `WineList.txt` de `http://www.cohowinery.com/downloads` e salva em `C:\Documents and Settings\All Users\Documents`, com o nome de usuário `anonymous` e uma senha em branco.  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  O protocolo FTP usado pelo método `DownLoadFile` envia informações, incluindo senhas, em texto sem formatação e não deve ser usado para transmitir informações confidenciais.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Network>  
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>  
 [Como Carregar um Arquivo](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)  
 [Como analisar demarcadores de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
