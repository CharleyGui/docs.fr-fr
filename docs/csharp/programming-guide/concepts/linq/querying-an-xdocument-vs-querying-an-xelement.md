---
title: Interrogation d’un XDocument et interrogation d’un XElement (C#)
description: En savoir plus sur les différences entre l’interrogation d’un XDocument et l’interrogation d’un XElement. Passez en revue les exemples de code qui illustrent ces différences.
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 0c81768f06148308a639f96f4041e464b24edd33
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300317"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="d5517-104">Interrogation d’un XDocument et interrogation d’un XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="d5517-104">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="d5517-105">Lorsque vous chargez un document par le biais de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, vous remarquerez que vous devez écrire des requêtes de manière légèrement différente comparé au chargement par le biais de <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d5517-105">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="d5517-106">Comparaison de XDocument.Load et XElement.Load</span><span class="sxs-lookup"><span data-stu-id="d5517-106">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="d5517-107">Lorsque vous chargez un document XML dans <xref:System.Xml.Linq.XElement> par le biais de <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, l'objet <xref:System.Xml.Linq.XElement> à la racine de l'arborescence XML contient l'élément racine du document chargé.</span><span class="sxs-lookup"><span data-stu-id="d5517-107">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="d5517-108">Toutefois, lorsque vous chargez le même document XML dans un objet <xref:System.Xml.Linq.XDocument> par le biais de <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, la racine de l'arborescence est un nœud <xref:System.Xml.Linq.XDocument> et l'élément racine du document chargé est le nœud <xref:System.Xml.Linq.XElement> enfant autorisé de l'objet <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="d5517-108">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="d5517-109">Les axes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] opèrent relativement au nœud racine.</span><span class="sxs-lookup"><span data-stu-id="d5517-109">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="d5517-110">Ce premier exemple charge une arborescence XML à l'aide de <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5517-110">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="d5517-111">Il interroge ensuite les éléments enfants de la racine de l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="d5517-111">It then queries for the child elements of the root of the tree.</span></span>  
  
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
  
 <span data-ttu-id="d5517-112">Comme prévu, cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d5517-112">As expected, this example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="d5517-113">L'exemple suivant est identique au précédent, hormis le fait que l'arborescence XML est chargée dans un objet <xref:System.Xml.Linq.XDocument> au lieu d'un objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d5517-113">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
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
  
 <span data-ttu-id="d5517-114">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d5517-114">This example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="d5517-115">Notez que la même requête a retourné le nœud `Root` au lieu des trois nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="d5517-115">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="d5517-116">L'une des solutions à ce problème consiste à utiliser la propriété <xref:System.Xml.Linq.XDocument.Root%2A> avant d'accéder aux méthodes d'axe, comme suit :</span><span class="sxs-lookup"><span data-stu-id="d5517-116">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
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
  
 <span data-ttu-id="d5517-117">Cette requête s'exécute maintenant de la même manière que la requête sur l'arborescence enracinée dans <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d5517-117">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="d5517-118">L'exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d5517-118">The example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  