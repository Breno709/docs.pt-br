---
title: Interface ICLRStrongName
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName
helpviewer_keywords: ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b8859cf507fb81f07b85b055380ba86aae471b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongname-interface"></a>Interface ICLRStrongName
Fornece funções estáticas globais de básicas para assinar assemblies com nomes fortes. Todos os `ICLRStrongName` métodos retornam os HRESULTs COM padrão.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Obtém um hash do arquivo de assembly especificado, usando o algoritmo de hash especificado.|  
|[Método GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Obtém um hash do arquivo de assembly especificado como uma cadeia de caracteres Unicode, usando o algoritmo de hash especificado.|  
|[Método GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.|  
|[Método GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Gera um hash com base no conteúdo do arquivo especificado.|  
|[Método GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Gera um hash com base no conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.|  
|[Método GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Gera um hash com base no conteúdo do arquivo com o identificador de arquivo especificado, usando o algoritmo de hash especificado.|  
|[Método StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|Determina se os dois assemblies diferem somente por suas assinaturas de nome forte.|  
|[Método StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Libera a memória que foi alocada com uma chamada anterior para um método de nome forte, como [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), ou [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[Método StrongNameGetBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.|  
|[Método StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Obtém uma representação binária da imagem do assembly no endereço de memória especificado.|  
|[Método StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Obtém a chave pública de um par de chaves pública/privada.|  
|[Método StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Obtém o tamanho do buffer necessário para um hash, usando o algoritmo de hash especificado.|  
|[Método StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Exclui o contêiner de chave especificado.|  
|[Método StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Cria um novo par de chaves pública/privada para uso de nome forte.|  
|[Método StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Gera um novo par de chaves pública/privada com o tamanho da chave especificado para o uso de nome forte.|  
|[Método StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Importa um par de chaves pública/privada para um contêiner.|  
|[Método StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Gera uma assinatura de nome forte para o assembly especificado.|  
|[Método StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Gera uma assinatura de nome forte para o assembly especificado, com base nos sinalizadores especificados.|  
|[Método StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Retorna o tamanho da assinatura de nome forte.|  
|[Método StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.|  
|[Método StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.|  
|[Método StrongNameSignatureVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Verifica se um assembly que já foi mapeado para a memória é válido para a chave pública associada.|  
|[Método StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Cria um token de nome forte do arquivo de assembly especificado.|  
|[Método StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Cria um token de nome forte do arquivo de assembly especificado e retorna a chave pública.|  
|[Método StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Obtém um token que representa uma chave pública.|  
  
## <a name="remarks"></a>Comentários  
 Você pode obter uma instância do `ICLRStrongName` chamando o [Iclrruntimeinfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) usando o método `CLSID_CLRStrongName` e `IID_ICLRStrongName` como parâmetros.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
