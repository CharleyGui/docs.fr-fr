---
title: 'Procédure : transformer un fragment de nœud'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: 5c69a35497feced92a05e124307d3be584ab86b7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829438"
---
# <a name="how-to-transform-a-node-fragment"></a>Procédure : transformer un fragment de nœud
Lorsque vous transformez des données contenues dans un objet <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XPath.XPathDocument>, les transformations XSLT s'appliquent à l'ensemble du document. En d'autres termes, si vous passez dans un autre nœud que le nœud racine du document, cela n'empêche pas le processus de transformation d'accéder à tous les nœuds dans le document chargé. Pour transformer un fragment de nœud, vous devez créer un objet séparé contenant uniquement le fragment de nœud et transmettre cet objet à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-transform-a-node-fragment"></a>Pour transformer un fragment de nœud  
  
1. Créez un objet contenant le document source.  
  
2. Localisez le fragment de nœud que vous souhaitez transformer.  
  
3. Créez un objet distinct contenant uniquement le fragment de nœud.  
  
4. Transmettez le fragment de nœud à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant transforme un fragment de nœud et affiche les résultats sur la console.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Entrée  
  
##### <a name="booksxml"></a>books.xml  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Output  
 Le titre du livre est The Confidence Man.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md)
