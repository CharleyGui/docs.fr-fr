---
title: Extension du DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 4a1a7af0e841601542a30c7bd3f71395faa6cb57
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287790"
---
# <a name="extending-the-dom"></a><span data-ttu-id="31e2a-102">Extension du DOM</span><span class="sxs-lookup"><span data-stu-id="31e2a-102">Extending the DOM</span></span>

<span data-ttu-id="31e2a-103">Le .NET Framework Microsoft comprend un ensemble de classes de base qui fournit une implémentation du DOM (Document Objet Model) XML.</span><span class="sxs-lookup"><span data-stu-id="31e2a-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="31e2a-104">L'objet <xref:System.Xml.XmlNode> et ses classes dérivées proposent des méthodes et des propriétés qui permettent la navigation, l'interrogation et la modification du contenu et de la structure d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="31e2a-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="31e2a-105">Lors du chargement en mémoire de contenu XML à l'aide du DOM, les nœuds créés contiennent des informations telles que le nom de nœud, le type de nœud, etc.</span><span class="sxs-lookup"><span data-stu-id="31e2a-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="31e2a-106">Il peut arriver que vous ayez besoin d'informations spécifiques sur les nœuds que les classes de base ne fournissent pas.</span><span class="sxs-lookup"><span data-stu-id="31e2a-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="31e2a-107">Par exemple, il peut être utile de connaître le numéro de ligne et la position d'un nœud.</span><span class="sxs-lookup"><span data-stu-id="31e2a-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="31e2a-108">Dans ce cas, vous pouvez faire dériver de nouvelles classes de classes DOM existantes et ajouter des fonctionnalités complémentaires.</span><span class="sxs-lookup"><span data-stu-id="31e2a-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="31e2a-109">La dérivation de nouvelles classes est soumise à deux indications générales :</span><span class="sxs-lookup"><span data-stu-id="31e2a-109">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="31e2a-110">Il est recommandé de ne jamais faire dériver des classes de la classe <xref:System.Xml.XmlNode>.</span><span class="sxs-lookup"><span data-stu-id="31e2a-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="31e2a-111">Il est plutôt conseillé de dériver des classes à partir de la classe qui correspond au type de nœud auquel vous vous intéressez.</span><span class="sxs-lookup"><span data-stu-id="31e2a-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="31e2a-112">Par exemple, si vous souhaitez renvoyer des informations supplémentaires sur les nœuds d'attributs, vous pouvez dériver de la classe <xref:System.Xml.XmlAttribute>.</span><span class="sxs-lookup"><span data-stu-id="31e2a-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="31e2a-113">À l'exception des méthodes de création de nœud, il est recommandé, lors de la substitution d'une fonction, de toujours appeler une version de base de la fonction et ensuite d'ajouter le complément de traitement éventuellement requis.</span><span class="sxs-lookup"><span data-stu-id="31e2a-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="31e2a-114">Création de vos propres instances de nœud</span><span class="sxs-lookup"><span data-stu-id="31e2a-114">Creating Your Own Node Instances</span></span>

<span data-ttu-id="31e2a-115">La classe <xref:System.Xml.XmlDocument> contient des méthodes de création de nœud.</span><span class="sxs-lookup"><span data-stu-id="31e2a-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="31e2a-116">Quand un fichier XML est chargé, ces méthodes sont appelées afin de créer les nœuds.</span><span class="sxs-lookup"><span data-stu-id="31e2a-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="31e2a-117">Vous pouvez les substituer de sorte que les instances de nœud soient créées au moment du chargement d'un document.</span><span class="sxs-lookup"><span data-stu-id="31e2a-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="31e2a-118">Par exemple, si vous avez étendu la classe <xref:System.Xml.XmlElement>, la classe <xref:System.Xml.XmlDocument> est héritée et la méthode <xref:System.Xml.XmlDocument.CreateElement%2A> remplacée.</span><span class="sxs-lookup"><span data-stu-id="31e2a-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="31e2a-119">L'exemple suivant montre comment substituer la méthode <xref:System.Xml.XmlDocument.CreateElement%2A> afin de retourner votre implémentation de la classe <xref:System.Xml.XmlElement>.</span><span class="sxs-lookup"><span data-stu-id="31e2a-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

```vb
Class LineInfoDocument
    Inherits XmlDocument
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
        Return elem
    End Function 'CreateElement
End Class 'LineInfoDocument
```

```csharp
class LineInfoDocument : XmlDocument
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI)
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a><span data-ttu-id="31e2a-120">Extension d'une classe</span><span class="sxs-lookup"><span data-stu-id="31e2a-120">Extending a Class</span></span>

<span data-ttu-id="31e2a-121">Pour étendre une classe, faites-la dériver de l'une des classes DOM existantes.</span><span class="sxs-lookup"><span data-stu-id="31e2a-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="31e2a-122">Ensuite, vous pouvez substituer n'importe quelle méthode ou propriété virtuelle de cette classe de base ou ajouter la vôtre.</span><span class="sxs-lookup"><span data-stu-id="31e2a-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="31e2a-123">Dans l'exemple suivant, une nouvelle classe est créée ; elle implémente la classe <xref:System.Xml.XmlElement> et l'interface <xref:System.Xml.IXmlLineInfo>.</span><span class="sxs-lookup"><span data-stu-id="31e2a-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="31e2a-124">D'autres méthodes et propriétés sont définies pour permettre aux utilisateurs de recueillir des informations sur les lignes.</span><span class="sxs-lookup"><span data-stu-id="31e2a-124">Additional methods and properties are defined which allows users to gather line information.</span></span>

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

   Public ReadOnly Property LineNumber() As Integer
      Get
         Return lineNumber
      End Get
   End Property

   Public ReadOnly Property LinePosition() As Integer
      Get
         Return linePosition
      End Get
   End Property

   Public Function HasLineInfo() As Boolean
      Return True
   End Function
End Class ' End LineInfoElement class.
```

```csharp
class LineInfoElement : XmlElement, IXmlLineInfo {
   int lineNumber = 0;
   int linePosition = 0;
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {
       ( (LineInfoDocument)doc ).IncrementElementCount();
  }
  public void SetLineInfo( int linenum, int linepos ) {
      lineNumber = linenum;
      linePosition = linepos;
  }
  public int LineNumber {
     get {
       return lineNumber;
     }
  }
  public int LinePosition {
      get {
        return linePosition;
      }
  }
  public bool HasLineInfo() {
    return true;
  }
} // End LineInfoElement class.
```

### <a name="example"></a><span data-ttu-id="31e2a-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="31e2a-125">Example</span></span>

<span data-ttu-id="31e2a-126">L’exemple suivant dénombre les éléments d’un document XML :</span><span class="sxs-lookup"><span data-stu-id="31e2a-126">The following example counts the number of elements in an XML document:</span></span>

```vb
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

Class LineInfoElement
   Inherits XmlElement

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub 'New
End Class 'LineInfoElement
 _ 'End LineInfoElement class.

Public Class Test

   Private filename As [String] = "book.xml"

   Public Shared Sub Main()

      Dim doc As New LineInfoDocument()
      doc.Load(filename)
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())
   End Sub
End Class
```

```csharp
using System;
using System.Xml;
using System.IO;

class LineInfoDocument : XmlDocument {

  int elementCount;
  internal LineInfoDocument():base() {
    elementCount = 0;
  }

  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );
    return elem;
  }

  public void IncrementElementCount() {
     elementCount++;
  }

  public int GetCount() {
     return elementCount;
  }
} // End LineInfoDocument class.

class LineInfoElement:XmlElement {

    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){
      ((LineInfoDocument)doc).IncrementElementCount();
    }
} // End LineInfoElement class.

public class Test {

  const String filename = "book.xml";
  public static void Main() {

     LineInfoDocument doc =new LineInfoDocument();
     doc.Load(filename);
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());

  }
}
```

#### <a name="input"></a><span data-ttu-id="31e2a-127">Entrée</span><span class="sxs-lookup"><span data-stu-id="31e2a-127">Input</span></span>

<span data-ttu-id="31e2a-128">book.xml</span><span class="sxs-lookup"><span data-stu-id="31e2a-128">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="31e2a-129">Output</span><span class="sxs-lookup"><span data-stu-id="31e2a-129">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="31e2a-130">Gestionnaire d'événements de nœud</span><span class="sxs-lookup"><span data-stu-id="31e2a-130">Node Event Handler</span></span>

<span data-ttu-id="31e2a-131">L'implémentation .NET Framework du DOM comprend également un système d'événements qui vous permet de recevoir et de gérer des événements lors de la modification de nœuds dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="31e2a-131">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="31e2a-132">L'utilisation des classes <xref:System.Xml.XmlNodeChangedEventHandler> et <xref:System.Xml.XmlNodeChangedEventArgs> vous permet de capturer des événements `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved` et `NodeRemoving`.</span><span class="sxs-lookup"><span data-stu-id="31e2a-132">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="31e2a-133">Le processus de gestion d'événements fonctionne exactement de la même façon dans les classes dérivées que dans les classes DOM d'origine.</span><span class="sxs-lookup"><span data-stu-id="31e2a-133">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="31e2a-134">Pour plus d’informations sur la gestion des événements de nœud, consultez [Événements](../../events/index.md) et <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="31e2a-134">For more information regarding node event handling, see [Events](../../events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="31e2a-135">Attributs par défaut et méthode CreateElement</span><span class="sxs-lookup"><span data-stu-id="31e2a-135">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="31e2a-136">Lors de la substitution de la méthode <xref:System.Xml.XmlDocument.CreateElement%2A> dans une classe dérivée, les attributs par défaut ne sont pas ajoutés lorsque vous créez de nouveaux éléments pendant la modification du document.</span><span class="sxs-lookup"><span data-stu-id="31e2a-136">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="31e2a-137">Ce problème ne se pose que lors de la modification.</span><span class="sxs-lookup"><span data-stu-id="31e2a-137">This is only an issue while editing.</span></span> <span data-ttu-id="31e2a-138">Puisque la méthode <xref:System.Xml.XmlDocument.CreateElement%2A> est responsable de l'ajout d'attributs par défaut à un objet <xref:System.Xml.XmlDocument>, vous devez coder cette fonctionnalité dans la méthode <xref:System.Xml.XmlDocument.CreateElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="31e2a-138">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="31e2a-139">Si vous chargez un objet <xref:System.Xml.XmlDocument> qui comporte des attributs par défaut, ceux-ci sont gérés correctement.</span><span class="sxs-lookup"><span data-stu-id="31e2a-139">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="31e2a-140">Pour plus d'informations sur les attributs par défaut, voir [Création de nouveaux attributs pour des éléments du DOM](creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="31e2a-140">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="31e2a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31e2a-141">See also</span></span>

- [<span data-ttu-id="31e2a-142">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="31e2a-142">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
