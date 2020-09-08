---
title: Préatomisation des objets XName-LINQ to XML
description: Découvrez comment effectuer une préatomisation pour améliorer les performances lorsque vous créez un grand nombre d’éléments portant le même nom.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 97da1e09e246491d8427c7a69953e006c80475a4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552496"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml"></a><span data-ttu-id="00999-103">Préatomisation des objets XName (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="00999-103">Pre-Atomization of XName objects (LINQ to XML)</span></span>

<span data-ttu-id="00999-104">L'un des moyens d'améliorer les performances dans LINQ to XML est de préatomiser les objets <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="00999-104">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="00999-105">La préatomisation signifie que vous attribuez une chaîne à un objet <xref:System.Xml.Linq.XName> avant de créer l'arborescence XML à l'aide des constructeurs des classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="00999-105">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="00999-106">Ensuite, au lieu de passer une chaîne au constructeur, ce qui utiliserait la conversion implicite de la chaîne en <xref:System.Xml.Linq.XName>, vous passez l'objet <xref:System.Xml.Linq.XName> initialisé.</span><span class="sxs-lookup"><span data-stu-id="00999-106">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>

<span data-ttu-id="00999-107">Cela améliore les performances lorsque vous créez une grande arborescence XML dans laquelle les noms sont répétés.</span><span class="sxs-lookup"><span data-stu-id="00999-107">This improves performance when you create a large XML tree in which names are repeated.</span></span> <span data-ttu-id="00999-108">Pour ce faire, vous devez déclarer et initialiser les objets <xref:System.Xml.Linq.XName> avant de construire l'arborescence XML, puis vous devez utiliser les objets <xref:System.Xml.Linq.XName> au lieu de spécifier des chaînes pour les noms d'élément et d'attribut.</span><span class="sxs-lookup"><span data-stu-id="00999-108">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="00999-109">Cette technique permet d’obtenir des gains de performances significatifs si vous créez un grand nombre d’éléments ou d’attributs portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="00999-109">This technique can yield significant performance gains if you're creating a large number of elements or attributes with the same name.</span></span>

<span data-ttu-id="00999-110">Vous devez tester la préatomisation avec votre scénario pour décider si vous devez l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="00999-110">You should test pre-atomization with your scenario to decide if you should use it.</span></span>

## <a name="example-create-elements-in-various-ways-with-and-without-pre-atomization"></a><span data-ttu-id="00999-111">Exemple : créer des éléments de différentes façons, avec et sans atomisation</span><span class="sxs-lookup"><span data-stu-id="00999-111">Example: Create elements in various ways, with and without pre-atomization</span></span>

<span data-ttu-id="00999-112">L’exemple suivant illustre la pré-atomisation.</span><span class="sxs-lookup"><span data-stu-id="00999-112">The following example demonstrates pre-atomization.</span></span>

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

<span data-ttu-id="00999-113">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="00999-113">This example produces the following output:</span></span>

```xml
<Root>
  <Data ID="1">4,100,000</Data>
  <Data ID="2">3,700,000</Data>
  <Data ID="3">1,150,000</Data>
</Root>
```

<span data-ttu-id="00999-114">L’exemple suivant illustre la même technique pour un document XML dans un espace de noms :</span><span class="sxs-lookup"><span data-stu-id="00999-114">The following example shows the same technique for an XML document in a namespace:</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XName Root = aw + "Root";
XName Data = aw + "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XAttribute(XNamespace.Xmlns + "aw", aw),
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

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

<span data-ttu-id="00999-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="00999-115">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Data ID="1">4,100,000</aw:Data>
  <aw:Data ID="2">3,700,000</aw:Data>
  <aw:Data ID="3">1,150,000</aw:Data>
</aw:Root>
```

<span data-ttu-id="00999-116">L'exemple suivant reflète mieux la situation que vous êtes susceptible de rencontrer dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="00999-116">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="00999-117">Dans cet exemple, le contenu de l'élément est fourni par une requête :</span><span class="sxs-lookup"><span data-stu-id="00999-117">In this example, the content of the element is supplied by a query:</span></span>

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

DateTime t1 = DateTime.Now;
XElement root = new XElement(Root,
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement(Data,
        new XAttribute(ID, i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

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

<span data-ttu-id="00999-118">L’exemple précédent est plus performant que l’exemple suivant, dans lequel les noms ne sont pas préatomisés :</span><span class="sxs-lookup"><span data-stu-id="00999-118">The previous example performs better than the following example, in which names aren't pre-atomized:</span></span>

```csharp
DateTime t1 = DateTime.Now;
XElement root = new XElement("Root",
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement("Data",
        new XAttribute("ID", i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a><span data-ttu-id="00999-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00999-119">See also</span></span>

- [<span data-ttu-id="00999-120">Objets XName et XNamespace atomisés</span><span class="sxs-lookup"><span data-stu-id="00999-120">Atomized XName and XNamespace objects</span></span>](atomized-xname-xnamespace-objects.md)
