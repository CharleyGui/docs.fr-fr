---
title: Extraction de données XML à l’aide de XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
ms.openlocfilehash: e639931204a416c3cde87044730364a4f387799a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287764"
---
# <a name="extract-xml-data-using-xpathnavigator"></a><span data-ttu-id="39072-102">Extraction de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="39072-102">Extract XML Data Using XPathNavigator</span></span>
<span data-ttu-id="39072-103">Il existe différentes manières de représenter un document XML dans Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39072-103">There are several different ways to represent an XML document in the Microsoft .NET Framework.</span></span> <span data-ttu-id="39072-104">Ce peut être à l'aide d'une chaîne (<xref:System.String>) ou des classes <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="39072-104">This includes using a <xref:System.String>, or by using the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, or <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="39072-105">Pour faciliter les déplacements entre ces différentes représentations d'un document XML, la classe <xref:System.Xml.XPath.XPathNavigator> offre diverses méthodes et propriétés d'extraction du XML en tant qu'objet <xref:System.String>, <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="39072-105">To facilitate moving between these different representations of an XML document, the <xref:System.Xml.XPath.XPathNavigator> class provides a number of methods and properties for extracting the XML as a <xref:System.String>, <xref:System.Xml.XmlReader> object or <xref:System.Xml.XmlWriter> object.</span></span>  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a><span data-ttu-id="39072-106">Conversion d’un objet XPathNavigator en une chaîne</span><span class="sxs-lookup"><span data-stu-id="39072-106">Convert an XPathNavigator to a String</span></span>  
 <span data-ttu-id="39072-107">La propriété <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> de la classe <xref:System.Xml.XPath.XPathNavigator> permet d'obtenir le balisage de l'entièreté du document XML ou d'un seul nœud et de ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="39072-107">The <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class is used to get the markup of the entire XML document or just the markup of a single node and its child nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39072-108">La propriété <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> n'obtient le balisage que des nœuds enfants d'un nœud.</span><span class="sxs-lookup"><span data-stu-id="39072-108">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property gets the markup of just the child nodes of a node.</span></span>  
  
 <span data-ttu-id="39072-109">L'exemple de code suivant montre comment enregistrer en tant qu'objet <xref:System.Xml.XPath.XPathNavigator> l'entièreté d'un document XML contenu dans un objet <xref:System.String>, de même qu'un nœud unique et ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="39072-109">The following code example shows how to save an entire XML document contained in an <xref:System.Xml.XPath.XPathNavigator> object as a <xref:System.String>, as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("input.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Save the entire input.xml document to a string.  
Dim xml As String = navigator.OuterXml  
  
' Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element)  
Dim root As String = navigator.OuterXml  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Save the entire input.xml document to a string.  
string xml = navigator.OuterXml;  
  
// Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element);  
string root = navigator.OuterXml;  
```  
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a><span data-ttu-id="39072-110">Conversion d’un objet XPathNavigator en un objet XmlReader</span><span class="sxs-lookup"><span data-stu-id="39072-110">Convert an XPathNavigator to an XmlReader</span></span>  
 <span data-ttu-id="39072-111">La méthode <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> permet de transmettre l'ensemble du contenu d'un document XML ou un seul nœud et ses nœuds enfants à un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="39072-111">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlReader> object.</span></span>  
  
 <span data-ttu-id="39072-112">Lorsque l'objet <xref:System.Xml.XmlReader> est créé avec le nœud actuel et ses nœuds enfants, la propriété <xref:System.Xml.XmlReader> de l'objet <xref:System.Xml.XmlReader.ReadState%2A> est définie sur <xref:System.Xml.ReadState.Initial>.</span><span class="sxs-lookup"><span data-stu-id="39072-112">When the <xref:System.Xml.XmlReader> object is created with the current node and its child nodes, the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.Initial>.</span></span> <span data-ttu-id="39072-113">Lorsque la méthode <xref:System.Xml.XmlReader> de l'objet <xref:System.Xml.XmlReader.Read%2A> est appelée pour la première fois, le <xref:System.Xml.XmlReader> est déplacé vers le nœud actuel du <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="39072-113">When the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.Read%2A> method is called for the first time, the <xref:System.Xml.XmlReader> is moved to the current node of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="39072-114">Le nouvel objet <xref:System.Xml.XmlReader> poursuit la lecture jusqu’à la fin de l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="39072-114">The new <xref:System.Xml.XmlReader> object continues to read until the end of the XML tree is reached.</span></span> <span data-ttu-id="39072-115">À ce stade, la méthode <xref:System.Xml.XmlReader.Read%2A> retourne `false` et la propriété <xref:System.Xml.XmlReader> de l'objet <xref:System.Xml.XmlReader.ReadState%2A> est définie sur <xref:System.Xml.ReadState.EndOfFile>.</span><span class="sxs-lookup"><span data-stu-id="39072-115">At this point, the <xref:System.Xml.XmlReader.Read%2A> method returns `false` and the <xref:System.Xml.XmlReader> object's <xref:System.Xml.XmlReader.ReadState%2A> property is set to <xref:System.Xml.ReadState.EndOfFile>.</span></span>  
  
 <span data-ttu-id="39072-116">La position de l'objet <xref:System.Xml.XPath.XPathNavigator> n'est pas modifiée par la création ou le déplacement de l'objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="39072-116">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation or movement of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="39072-117">La méthode <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> n'est valide que lorsque vous êtes positionné sur un élément ou un nœud racine.</span><span class="sxs-lookup"><span data-stu-id="39072-117">The <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> method is only valid when positioned on an element or root node.</span></span>  
  
 <span data-ttu-id="39072-118">L'exemple suivant montre comment obtenir un objet <xref:System.Xml.XmlReader> contenant l'entièreté du document XML dans un objet <xref:System.Xml.XPath.XPathDocument>, de même qu'un nœud unique et ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="39072-118">The following example shows how to get an <xref:System.Xml.XmlReader> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlReader.  
Dim xml As XmlReader = navigator.ReadSubtree()  
  
While xml.Read()  
    Console.WriteLine(xml.ReadInnerXml())  
End While  
  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlReader = navigator.ReadSubtree()  
  
While book.Read()  
    Console.WriteLine(book.ReadInnerXml())  
End While  
  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlReader.  
XmlReader xml = navigator.ReadSubtree();  
  
while (xml.Read())  
{  
    Console.WriteLine(xml.ReadInnerXml());  
}  
  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlReader book = navigator.ReadSubtree();  
  
while (book.Read())  
{  
    Console.WriteLine(book.ReadInnerXml());  
}  
  
book.Close();  
```  
  
 <span data-ttu-id="39072-119">L'exemple prend le fichier `books.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="39072-119">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a><span data-ttu-id="39072-120">Conversion d’un objet XPathNavigator en un objet XmlWriter</span><span class="sxs-lookup"><span data-stu-id="39072-120">Converting an XPathNavigator to an XmlWriter</span></span>  
 <span data-ttu-id="39072-121">La méthode <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> permet de transmettre l'ensemble du contenu d'un document XML ou un seul nœud et ses nœuds enfants à un objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="39072-121">The <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> method is used to stream the entire contents of an XML document or just a single node and its child nodes to an <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="39072-122">La position de l'objet <xref:System.Xml.XPath.XPathNavigator> n'est pas modifiée par la création de l'objet <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="39072-122">The <xref:System.Xml.XPath.XPathNavigator> object's position is unchanged by the creation of the <xref:System.Xml.XmlWriter> object.</span></span>  
  
 <span data-ttu-id="39072-123">L'exemple suivant montre comment obtenir un objet <xref:System.Xml.XmlWriter> contenant l'entièreté du document XML dans un objet <xref:System.Xml.XPath.XPathDocument>, de même qu'un nœud unique et ses nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="39072-123">The following example shows how to get an <xref:System.Xml.XmlWriter> object containing the entire XML document in an <xref:System.Xml.XPath.XPathDocument> object as well as a single node and its child nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlWriter.  
Dim xml As XmlWriter = XmlWriter.Create("newbooks.xml")  
navigator.WriteSubtree(xml)  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlWriter = XmlWriter.Create("book.xml")  
navigator.WriteSubtree(book)  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlWriter.  
XmlWriter xml = XmlWriter.Create("newbooks.xml");  
navigator.WriteSubtree(xml);  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlWriter book = XmlWriter.Create("book.xml");  
navigator.WriteSubtree(book);  
book.Close();  
```  
  
 <span data-ttu-id="39072-124">L'exemple prend comme entrée le fichier `books.xml` mentionné précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="39072-124">The example takes the `books.xml` file found earlier in this topic as input.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39072-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39072-125">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="39072-126">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="39072-126">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="39072-127">Navigation dans la collection de nœuds à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="39072-127">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="39072-128">Navigation entre les nœuds d'attribut et d'espace de noms à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="39072-128">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="39072-129">Accès à des données XML fortement typées à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="39072-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
