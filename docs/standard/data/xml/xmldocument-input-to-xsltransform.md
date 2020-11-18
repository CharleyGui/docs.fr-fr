---
title: Entrée XmlDocument dans XslTransform
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: 0afee2d706b95117971c02b57a5570427e0fbd3d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827553"
---
# <a name="xmldocument-input-to-xsltransform"></a>Entrée XmlDocument dans XslTransform
La classe <xref:System.Xml.XmlDocument> permet de modifier un document XML. Si le document XML doit être modifié ou édité avant d'être envoyé à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>, chargez le XML dans un objet <xref:System.Xml.XmlDocument>, éditez-le, puis envoyez-le à l'objet <xref:System.Xml.Xsl.XslTransform>.  
  
> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](migrating-from-the-xsltransform-class.md).  
  
 L'objet <xref:System.Xml.XmlDocument> implémentant l'interface <xref:System.Xml.XPath.IXPathNavigable>, le document peut être passé à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> après la modification.  
  
 En raison de la capacité d'édition de l'objet <xref:System.Xml.XmlDocument>, l'utilisation de la classe <xref:System.Xml.XmlDocument> comme entrée pour une transformation est plus lente que l'utilisation d'un objet <xref:System.Xml.XPath.XPathDocument> pour les transformations XSLT (Extensible Stylesheet Language for Transformations) car l'objet <xref:System.Xml.XPath.XPathDocument> est optimisé pour les requêtes XPath (XML Path Language) dues au stockage interne.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment un objet <xref:System.Xml.XmlDocument> peut être fourni à l'objet <xref:System.Xml.Xsl.XslTransform>, dont la sortie est envoyée à un objet <xref:System.Xml.XmlReader>.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- [Transformations XSLT avec la classe XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Implémentation du processeur XSLT par la classe XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [XPathNavigator dans les transformations](xpathnavigator-in-transformations.md)
- [XPathNodeIterator dans les transformations](xpathnodeiterator-in-transformations.md)
- [Entrée XPathDocument dans XslTransform](xpathdocument-input-to-xsltransform.md)
- [Entrée XmlDataDocument dans XslTransform](xmldatadocument-input-to-xsltransform.md)
