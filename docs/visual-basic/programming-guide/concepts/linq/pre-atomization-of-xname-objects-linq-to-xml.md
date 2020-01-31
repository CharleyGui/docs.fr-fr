---
title: Préatomisation des objets XName (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: c0e75afa797d2b20f32fc55e6c19d0c1593d174c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740791"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="89835-102">Préatomisation des objets XName (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89835-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="89835-103">L'un des moyens d'améliorer les performances dans LINQ to XML est de préatomiser les objets <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="89835-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="89835-104">La préatomisation signifie que vous attribuez une chaîne à un objet <xref:System.Xml.Linq.XName> avant de créer l’arborescence XML à l’aide des constructeurs des classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="89835-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="89835-105">Ensuite, au lieu de passer une chaîne au constructeur, ce qui utiliserait la conversion implicite de la chaîne en <xref:System.Xml.Linq.XName>, vous passez l'objet <xref:System.Xml.Linq.XName> initialisé.</span><span class="sxs-lookup"><span data-stu-id="89835-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>

<span data-ttu-id="89835-106">Ceci améliore la performance lorsque vous créez une grande arborescence XML dans laquelle des noms spécifiques sont répétés.</span><span class="sxs-lookup"><span data-stu-id="89835-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="89835-107">Pour ce faire, vous devez déclarer et initialiser les objets <xref:System.Xml.Linq.XName> avant de construire l'arborescence XML, puis vous devez utiliser les objets <xref:System.Xml.Linq.XName> au lieu de spécifier des chaînes pour les noms d'élément et d'attribut.</span><span class="sxs-lookup"><span data-stu-id="89835-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="89835-108">Cette technique peut apporter une amélioration significative de la performance si vous créez un grand nombre d'éléments (ou d'attributs) avec le même nom.</span><span class="sxs-lookup"><span data-stu-id="89835-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>

<span data-ttu-id="89835-109">Vous devez tester la préatomisation avec votre scénario pour décider si vous devez l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="89835-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>

## <a name="example"></a><span data-ttu-id="89835-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="89835-110">Example</span></span>

<span data-ttu-id="89835-111">Cela est illustré par l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="89835-111">The following example demonstrates this:</span></span>

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

<span data-ttu-id="89835-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="89835-112">This example produces the following output:</span></span>

```xml
<Root>
  <Data ID="1">4,100,000</Data>
  <Data ID="2">3,700,000</Data>
  <Data ID="3">1,150,000</Data>
</Root>
```

<span data-ttu-id="89835-113">L'exemple suivant illustre la même technique dans laquelle le document XML est dans un espace de noms :</span><span class="sxs-lookup"><span data-stu-id="89835-113">The following example shows the same technique where the XML document is in a namespace:</span></span>

```vb
Dim aw As XNamespace = "http://www.adventure-works.com"
Dim root1 As XName = aw + "Root"
Dim data As XName = aw + "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XAttribute(XNamespace.Xmlns + "aw", aw),
                          New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

<span data-ttu-id="89835-114">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="89835-114">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Data ID="1">4,100,000</aw:Data>
  <aw:Data ID="2">3,700,000</aw:Data>
  <aw:Data ID="3">1,150,000</aw:Data>
</aw:Root>
```

<span data-ttu-id="89835-115">L'exemple suivant reflète mieux la situation que vous êtes susceptible de rencontrer dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="89835-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="89835-116">Dans cet exemple, le contenu de l'élément est fourni par une requête :</span><span class="sxs-lookup"><span data-stu-id="89835-116">In this example, the content of the element is supplied by a query:</span></span>

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"
  
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root2 As New XElement(root1, From i In Enumerable.Range(1, 100000)
                                 Select New XElement(data, New XAttribute(ID, i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```  

<span data-ttu-id="89835-117">L'exemple suivant produit une meilleure performance que l'exemple précédent, dans lequel les noms ne sont pas préatomisés :</span><span class="sxs-lookup"><span data-stu-id="89835-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a><span data-ttu-id="89835-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89835-118">See also</span></span>

- [<span data-ttu-id="89835-119">Performances (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89835-119">Performance (LINQ to XML) (Visual Basic)</span></span>](performance-linq-to-xml.md)
- [<span data-ttu-id="89835-120">Objets XName et XNamespace atomisés (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89835-120">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>](atomized-xname-and-xnamespace-objects-linq-to-xml.md)
