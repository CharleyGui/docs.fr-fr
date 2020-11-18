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
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="35134-102">Entrée XmlDocument dans XslTransform</span><span class="sxs-lookup"><span data-stu-id="35134-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="35134-103">La classe <xref:System.Xml.XmlDocument> permet de modifier un document XML.</span><span class="sxs-lookup"><span data-stu-id="35134-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="35134-104">Si le document XML doit être modifié ou édité avant d'être envoyé à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>, chargez le XML dans un objet <xref:System.Xml.XmlDocument>, éditez-le, puis envoyez-le à l'objet <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="35134-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35134-105">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="35134-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="35134-106">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="35134-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="35134-107">Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="35134-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="35134-108">L'objet <xref:System.Xml.XmlDocument> implémentant l'interface <xref:System.Xml.XPath.IXPathNavigable>, le document peut être passé à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> après la modification.</span><span class="sxs-lookup"><span data-stu-id="35134-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="35134-109">En raison de la capacité d'édition de l'objet <xref:System.Xml.XmlDocument>, l'utilisation de la classe <xref:System.Xml.XmlDocument> comme entrée pour une transformation est plus lente que l'utilisation d'un objet <xref:System.Xml.XPath.XPathDocument> pour les transformations XSLT (Extensible Stylesheet Language for Transformations) car l'objet <xref:System.Xml.XPath.XPathDocument> est optimisé pour les requêtes XPath (XML Path Language) dues au stockage interne.</span><span class="sxs-lookup"><span data-stu-id="35134-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35134-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="35134-110">Example</span></span>  
 <span data-ttu-id="35134-111">L'exemple de code suivant montre comment un objet <xref:System.Xml.XmlDocument> peut être fourni à l'objet <xref:System.Xml.Xsl.XslTransform>, dont la sortie est envoyée à un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="35134-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="35134-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35134-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="35134-113">Transformations XSLT avec la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="35134-113">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="35134-114">Implémentation du processeur XSLT par la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="35134-114">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="35134-115">XPathNavigator dans les transformations</span><span class="sxs-lookup"><span data-stu-id="35134-115">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="35134-116">XPathNodeIterator dans les transformations</span><span class="sxs-lookup"><span data-stu-id="35134-116">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="35134-117">Entrée XPathDocument dans XslTransform</span><span class="sxs-lookup"><span data-stu-id="35134-117">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="35134-118">Entrée XmlDataDocument dans XslTransform</span><span class="sxs-lookup"><span data-stu-id="35134-118">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
