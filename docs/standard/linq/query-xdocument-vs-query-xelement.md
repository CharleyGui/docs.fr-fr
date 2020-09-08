---
title: Interroger un XDocument et interroger un XElement-LINQ to XML
description: Écrivez des requêtes légèrement différentes pour les documents XML chargés par XDocument. Load et XElement. Load.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 96d706bcc1871c9e420bafd984d08ca9616b5c18
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553707"
---
# <a name="query-an-xdocument-vs-query-an-xelement-linq-to-xml"></a><span data-ttu-id="60a0e-103">Interroger une requête `XDocument` et un `XElement` (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="60a0e-103">Query an `XDocument` vs. query an `XElement` (LINQ to XML)</span></span>

<span data-ttu-id="60a0e-104">La requête que vous écrivez lorsque vous chargez un document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> diffère légèrement de ce que vous écrivez lorsque vous chargez via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="60a0e-104">The query you write when you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> differs slighty from what you write when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>

## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="60a0e-105">Comparaison de `XDocument.Load` et `XElement.Load`</span><span class="sxs-lookup"><span data-stu-id="60a0e-105">Comparison of `XDocument.Load` and `XElement.Load`</span></span>

<span data-ttu-id="60a0e-106">Lorsque vous chargez un document XML dans <xref:System.Xml.Linq.XElement> par le biais de <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, l'objet <xref:System.Xml.Linq.XElement> à la racine de l'arborescence XML contient l'élément racine du document chargé.</span><span class="sxs-lookup"><span data-stu-id="60a0e-106">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="60a0e-107">Toutefois, lorsque vous chargez le même document XML dans un objet <xref:System.Xml.Linq.XDocument> par le biais de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, la racine de l'arborescence est un nœud <xref:System.Xml.Linq.XDocument> et l'élément racine du document chargé est le nœud <xref:System.Xml.Linq.XElement> enfant autorisé de l'objet <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="60a0e-107">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="60a0e-108">Les axes de LINQ to XML opèrent par rapport au nœud racine.</span><span class="sxs-lookup"><span data-stu-id="60a0e-108">The LINQ to XML axes operate relative to the root node.</span></span>

## <a name="example-load-an-xml-tree-using-xelementload-then-query-for-child-elements"></a><span data-ttu-id="60a0e-109">Exemple : charger une arborescence XML à l’aide `XElement.Load` de, puis interroger des éléments enfants</span><span class="sxs-lookup"><span data-stu-id="60a0e-109">Example: Load an XML tree using `XElement.Load`, then query for child elements</span></span>

<span data-ttu-id="60a0e-110">Ce premier exemple charge une arborescence XML à l'aide de <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="60a0e-110">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="60a0e-111">Il interroge ensuite les éléments enfants de la racine de l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="60a0e-111">It then queries for the child elements of the root of the tree.</span></span>

```csharp
// Create a simple document and write it to a file
File.WriteAllText("Test.xml", @"<Root>
    <Child1>1</Child1>
    <Child2>2</Child2>
    <Child3>3</Child3>
</Root>");

Console.WriteLine("Querying tree loaded with XElement.Load");
Console.WriteLine("----");
XElement doc = XElement.Load("Test.xml");
IEnumerable<XElement> childList =
    from el in doc.Elements()
    select el;
foreach (XElement e in childList)
    Console.WriteLine(e);
```

```vb
' Create a simple document and  write it to a file
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _
    "    <Child1>1</Child1>" + Environment.NewLine + _
    "    <Child2>2</Child2>" + Environment.NewLine + _
    "    <Child3>3</Child3>" + Environment.NewLine + _
    "</Root>")

Console.WriteLine("Querying tree loaded with XElement.Load")
Console.WriteLine("----")
Dim doc As XElement = XElement.Load("Test.xml")
Dim childList As IEnumerable(Of XElement) = _
        From el In doc.Elements() _
        Select el
For Each e As XElement In childList
    Console.WriteLine(e)
Next
```

<span data-ttu-id="60a0e-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="60a0e-112">This example produces the following output:</span></span>

```output
Querying tree loaded with XElement.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```

## <a name="example-load-an-xml-tree-using-xdocumentload-then-query-for-child-elements"></a><span data-ttu-id="60a0e-113">Exemple : charger une arborescence XML à l’aide `XDocument.Load` de, puis interroger des éléments enfants</span><span class="sxs-lookup"><span data-stu-id="60a0e-113">Example: Load an XML tree using `XDocument.Load`, then query for child elements</span></span>

<span data-ttu-id="60a0e-114">L’exemple suivant fait la même chose que l’exemple ci-dessus, mais l’arborescence XML a été chargée dans un <xref:System.Xml.Linq.XDocument> , plutôt que dans un <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="60a0e-114">The next example does the same as the one above, but the XML tree has been loaded into an <xref:System.Xml.Linq.XDocument>, rather than an <xref:System.Xml.Linq.XElement>.</span></span>

```csharp
// Create a simple document and write it to a file
File.WriteAllText("Test.xml", @"<Root>
    <Child1>1</Child1>
    <Child2>2</Child2>
    <Child3>3</Child3>
</Root>");

Console.WriteLine("Querying tree loaded with XDocument.Load");
Console.WriteLine("----");
XDocument doc = XDocument.Load("Test.xml");
IEnumerable<XElement> childList =
    from el in doc.Elements()
    select el;
foreach (XElement e in childList)
    Console.WriteLine(e);
```

```vb
' Create a simple document and  write it to a file
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _
    "    <Child1>1</Child1>" + Environment.NewLine + _
    "    <Child2>2</Child2>" + Environment.NewLine + _
    "    <Child3>3</Child3>" + Environment.NewLine + _
    "</Root>")

Console.WriteLine("Querying tree loaded with XDocument.Load")
Console.WriteLine("----")
Dim doc As XDocument = XDocument.Load("Test.xml")
Dim childList As IEnumerable(Of XElement) = _
        From el In doc.Elements() _
        Select el
For Each e As XElement In childList
    Console.WriteLine(e)
Next
```

<span data-ttu-id="60a0e-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="60a0e-115">This example produces the following output:</span></span>

```output
Querying tree loaded with XDocument.Load
----
<Root>
  <Child1>1</Child1>
  <Child2>2</Child2>
  <Child3>3</Child3>
</Root>
```

<span data-ttu-id="60a0e-116">Notez que la même requête a retourné le nœud `Root` au lieu des trois nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="60a0e-116">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>

<span data-ttu-id="60a0e-117">L'une des solutions à ce problème consiste à utiliser la propriété <xref:System.Xml.Linq.XDocument.Root%2A> avant d'accéder aux méthodes d'axe, comme suit :</span><span class="sxs-lookup"><span data-stu-id="60a0e-117">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>

```csharp
// Create a simple document and write it to a file
File.WriteAllText("Test.xml", @"<Root>
    <Child1>1</Child1>
    <Child2>2</Child2>
    <Child3>3</Child3>
</Root>");

Console.WriteLine("Querying tree loaded with XDocument.Load");
Console.WriteLine("----");
XDocument doc = XDocument.Load("Test.xml");
IEnumerable<XElement> childList =
    from el in doc.Root.Elements()
    select el;
foreach (XElement e in childList)
    Console.WriteLine(e);
```

```vb
' Create a simple document and  write it to a file
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _
    "    <Child1>1</Child1>" + Environment.NewLine + _
    "    <Child2>2</Child2>" + Environment.NewLine + _
    "    <Child3>3</Child3>" + Environment.NewLine + _
    "</Root>")

Console.WriteLine("Querying tree loaded with XDocument.Load")
Console.WriteLine("----")
Dim doc As XDocument = XDocument.Load("Test.xml")
Dim childList As IEnumerable(Of XElement) = _
        From el In doc.Root.Elements() _
        Select el
For Each e As XElement In childList
    Console.WriteLine(e)
Next
```

<span data-ttu-id="60a0e-118">Cette requête s'exécute maintenant de la même manière que la requête sur l'arborescence enracinée dans <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="60a0e-118">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span>

<span data-ttu-id="60a0e-119">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="60a0e-119">This example produces the following output:</span></span>

```output
Querying tree loaded with XDocument.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```
