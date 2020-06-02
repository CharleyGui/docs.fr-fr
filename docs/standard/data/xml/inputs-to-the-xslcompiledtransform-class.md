---
title: Entrées dans la classe XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
ms.openlocfilehash: 1452bc19940a33aeebaccf3041857a07c976964d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287647"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>Entrées dans la classe XslCompiledTransform
La méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> accepte trois types d'entrées pour le document source : un objet qui implémente l'interface <xref:System.Xml.XPath.IXPathNavigable>, un objet <xref:System.Xml.XmlReader> qui lit le document source ou un string URI.  
  
> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslCompiledTransform> conserve l'espace blanc par défaut. Elle respecte ainsi la [section 3.4 de la recommandation du W3C sur XSLT 1.0](https://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>Interface IXPathNavigable  
 L'interface <xref:System.Xml.XPath.IXPathNavigable> est implémentée dans les classes <xref:System.Xml.XmlNode> et <xref:System.Xml.XPath.XPathDocument>. Ces classes représentent un cache en mémoire de données XML.  
  
- La classe <xref:System.Xml.XmlNode> se base sur le DOM (Document Object Model) et comprend des fonctionnalités de modification.  
  
- La classe <xref:System.Xml.XPath.XPathDocument> est une banque de données en lecture seule basé sur le modèle de données XPath. <xref:System.Xml.XPath.XPathDocument> est la classe recommandée pour la transformation XSLT. Elle offre des performances plus rapides par rapport à la classe <xref:System.Xml.XmlNode>.  
  
> [!NOTE]
> Les transformations s'appliquent à l'ensemble du document. En d'autres termes, si vous passez dans un autre nœud que le nœud racine du document, cela n'empêche pas le processus de transformation d'accéder à tous les nœuds dans le document chargé. Pour transformer un fragment de nœud, vous devez créer un objet contenant uniquement le fragment de nœud et transférer cet objet à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. Pour plus d’informations, consultez [Procédure : transformation d'un fragment de nœud](how-to-transform-a-node-fragment.md).  
  
 L'exemple suivant utilise la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> pour transformer le fichier books.xml en fichier books.html à l'aide de la feuille de style transform.xsl. Vous trouverez les fichiers books.xml et transform.xsl dans la rubrique [Procédure : effectuer une transformation XSLT à l'aide d'un assembly](how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>Objet XmlReader  
 La méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> charge à partir du nœud actuel de l'objet <xref:System.Xml.XmlReader> via tous ses enfants. Vous pouvez donc utiliser une partie d'un document comme document de contexte. Après les retours de la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>, l'objet <xref:System.Xml.XmlReader> est positionné sur le nœud suivant après la fin du document de contexte. Si la fin du document est atteinte, l'objet <xref:System.Xml.XmlReader> est positionné à la fin du fichier.  
  
 L'exemple suivant utilise la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> pour transformer le fichier books.xml en fichier books.html à l'aide de la feuille de style transform.xsl. Vous trouverez les fichiers books.xml et transform.xsl dans la rubrique [Procédure : effectuer une transformation XSLT à l'aide d'un assembly](how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>String URI  
 Vous pouvez également spécifier l'URI du document source comme entrée XSLT. Un objet <xref:System.Xml.XmlResolver> permet de résoudre l'URI. Vous pouvez spécifier l'objet <xref:System.Xml.XmlResolver> à utiliser en le transférant à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. Si aucun objet <xref:System.Xml.XmlResolver> n'est spécifié, la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> utilise un objet <xref:System.Xml.XmlUrlResolver> par défaut sans informations d'identification.  
  
 L'exemple suivant utilise la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> pour transformer le fichier books.xml en fichier books.html à l'aide de la feuille de style transform.xsl. Vous trouverez les fichiers books.xml et transform.xsl dans la rubrique [Procédure : effectuer une transformation XSLT à l'aide d'un assembly](how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Pour plus d’informations, consultez [Résolution de ressources externes lors du traitement XSLT](resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Voir aussi

- [Transformations XSLT](xslt-transformations.md)
