---
title: XmlDataDocument inseriu a XslTransform
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 813c240ca0115015158988e1226d25890cde6939
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xmldatadocument-input-to-xsltransform"></a>XmlDataDocument inseriu a XslTransform
> [!NOTE]
>  A classe <xref:System.Xml.Xsl.XslTransform> está obsoleta no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Você pode executar a linguagem XSL Transformations (XSLT) usando a classe <xref:System.Xml.Xsl.XslCompiledTransform>. Consulte [usando a classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [migrar da classe de XslTransform o](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para obter mais informações.  
  
 Microsoft [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementa o modelo de objeto (DOM) de documento XML para fornecer acesso a dados em documentos XML e classes adicionais para leitura, para escrever, e navegar em documentos XML. O <xref:System.Xml.XmlDataDocument>, encontrado na <xref:System.Xml> namespace, fornece acesso relacional a dados com sua capacidade de sincronizar com os dados relacionais a <xref:System.Data.DataSet>. Você pode exibir simultaneamente e manipular XML estruturada através da representação relacional de <xref:System.Data.DataSet> manipular XML ou semi-confiáveis estruturada através da representação DOM de <xref:System.Xml.XmlDataDocument>. Portanto <xref:System.Xml.XmlDataDocument> cruza os limites de XML e de mundos relacionais.  
  
 Se os dados são armazenados em uma estrutura relacional e você deseja que ele seja entrada para uma transformação XSLT, você pode carregar os dados relacionais em <xref:System.Data.DataSet> e associá-los com <xref:System.Xml.XmlDataDocument>. 
          <xref:System.Xml.XPath.XPathNavigator>, entrada a <xref:System.Xml.Xsl.XslTransform>, é implementado em <xref:System.Xml.XmlDataDocument> através da interface de <xref:System.Xml.XPath.IXPathNavigable> . Colocando dados relacionais, carregando na <xref:System.Data.DataSet>, e usando sincronizar dentro de <xref:System.Xml.XmlDataDocument>, os dados relacionais agora podem ter as transformações XSLT executadas neles.  
  
 Para obter mais informações sobre como aplicar uma transformação de dados relacional, consulte [aplicando uma transformação XSLT para um conjunto de dados](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.XmlDataDocument>  
 [Sincronização de DataSet e XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [Transformações XSLT com a classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Classe XslTransform implementa do processador XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [XPathNavigator nas transformações](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator nas transformações](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Entrada XPathDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Entrada de XmlDocument inseriu a XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
