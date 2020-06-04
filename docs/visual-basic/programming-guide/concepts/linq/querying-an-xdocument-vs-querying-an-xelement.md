---
title: Comparaison de l'interrogation d'un XDocument et d'un Interrogation d’un XElement
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 3cd79c8f2cde101de43a9b9e983709e2e0d11814
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396296"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="6517f-102">Interrogation d’un XDocument et interrogation d’un XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6517f-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="6517f-103">Lorsque vous chargez un document par le biais de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, vous remarquerez que vous devez écrire des requêtes de manière légèrement différente comparé au chargement par le biais de <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6517f-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="6517f-104">Comparaison de XDocument.Load et XElement.Load</span><span class="sxs-lookup"><span data-stu-id="6517f-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="6517f-105">Lorsque vous chargez un document XML dans <xref:System.Xml.Linq.XElement> par le biais de <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, l'objet <xref:System.Xml.Linq.XElement> à la racine de l'arborescence XML contient l'élément racine du document chargé.</span><span class="sxs-lookup"><span data-stu-id="6517f-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="6517f-106">Toutefois, lorsque vous chargez le même document XML dans un objet <xref:System.Xml.Linq.XDocument> par le biais de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, la racine de l'arborescence est un nœud <xref:System.Xml.Linq.XDocument> et l'élément racine du document chargé est le nœud <xref:System.Xml.Linq.XElement> enfant autorisé de l'objet <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="6517f-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="6517f-107">Les axes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] opèrent relativement au nœud racine.</span><span class="sxs-lookup"><span data-stu-id="6517f-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="6517f-108">Ce premier exemple charge une arborescence XML à l'aide de <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="6517f-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="6517f-109">Il interroge ensuite les éléments enfants de la racine de l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="6517f-109">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="6517f-110">Comme prévu, cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6517f-110">As expected, this example produces the following output:</span></span>  
  
```console
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="6517f-111">L'exemple suivant est identique au précédent, hormis le fait que l'arborescence XML est chargée dans un objet <xref:System.Xml.Linq.XDocument> au lieu d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6517f-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="6517f-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6517f-112">This example produces the following output:</span></span>  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="6517f-113">Notez que la même requête a retourné le nœud `Root` au lieu des trois nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="6517f-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="6517f-114">L'une des solutions à ce problème consiste à utiliser la propriété <xref:System.Xml.Linq.XDocument.Root%2A> avant d'accéder aux méthodes d'axe, comme suit :</span><span class="sxs-lookup"><span data-stu-id="6517f-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="6517f-115">Cette requête s'exécute maintenant de la même manière que la requête sur l'arborescence enracinée dans <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6517f-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="6517f-116">L'exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6517f-116">The example produces the following output:</span></span>  
  
```console
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6517f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6517f-117">See also</span></span>

- [<span data-ttu-id="6517f-118">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6517f-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
