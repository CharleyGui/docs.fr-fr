---
title: Entrée XPathDocument dans XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
ms.openlocfilehash: e19e0d18dc0f4aceb38bf006c3b9b80276455510
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709762"
---
# <a name="xpathdocument-input-to-xsltransform"></a>Entrée XPathDocument dans XslTransform
L'objet <xref:System.Xml.XPath.XPathDocument> est un cache en lecture seule, destiné à traiter des documents avec l'objet <xref:System.Xml.Xsl.XslTransform>. Sa structure est analogue au DOM (Document Object Model) XML, mais elle est particulièrement optimisée pour le traitement XSLT (Extensible Stylesheet Language for Transformations) et le modèle de données XPath (XML Path Language) en utilisant les fonctions d'optimisation sur l'objet <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).  
  
 L'exemple de code suivant crée un objet <xref:System.Xml.XPath.XPathDocument> en tant qu'entrée à transformer.  
  
```vb  
Dim xslt as XslTransform = new XslTransform()  
Xslt.Load(someStylesheet)  
Dim doc as XPathDocument = New XPathDocument("books.xml")  
Dim fs as StringWriter = new StringWriter()  
Xslt.Transform(doc, Nothing, fs, Nothing);  
```  
  
```csharp  
XslTransform xslt = new XslTransform();  
Xslt.Load(someStylesheet);  
XPathDocument doc = XPathDocument("books.xml");  
StringWriter fs = new StringWriter();  
Xslt.Transform(doc, null, fs, null);  
```  
  
## <a name="see-also"></a>Voir aussi

- [Implémentation du processeur XSLT par la classe XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
