---
title: Récupération d’un seul attribut-LINQ to XML
description: Récupérez un seul attribut d’un élément, en fonction du nom de l’attribut.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: a8a56ec62275f2376d19d7fc9090414b74fc77ad
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553659"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml"></a><span data-ttu-id="4e2f6-103">Comment récupérer un seul attribut (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4e2f6-103">How to retrieve a single attribute (LINQ to XML)</span></span>

<span data-ttu-id="4e2f6-104">Cet article explique comment récupérer un seul attribut d’un élément, étant donné le nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="4e2f6-104">This article explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="4e2f6-105">Ceci est utile pour écrire des expressions de requête où vous souhaitez rechercher un élément qui possède un attribut particulier.</span><span class="sxs-lookup"><span data-stu-id="4e2f6-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>

<span data-ttu-id="4e2f6-106">La méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement> retourne l'objet <xref:System.Xml.Linq.XAttribute> avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="4e2f6-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>

## <a name="example-retrieve-attribute-values-given-the-element-and-attribute-names"></a><span data-ttu-id="4e2f6-107">Exemple : récupérer des valeurs d’attribut, en fonction des noms d’élément et d’attribut</span><span class="sxs-lookup"><span data-stu-id="4e2f6-107">Example: Retrieve attribute values, given the element and attribute names</span></span>

<span data-ttu-id="4e2f6-108">L’exemple suivant utilise la <xref:System.Xml.Linq.XElement> méthode pour créer un élément nommé `PhoneNumbers` .</span><span class="sxs-lookup"><span data-stu-id="4e2f6-108">The following example uses the <xref:System.Xml.Linq.XElement> method to create an element named `PhoneNumbers`.</span></span> <span data-ttu-id="4e2f6-109">Il recherche ensuite tous les éléments descendants nommés `Phone` et, pour chacun d’entre eux, utilise la <xref:System.Xml.Linq.XElement.Attribute%2A> méthode pour obtenir et générer la sortie de la valeur de l’attribut nommé `type` :</span><span class="sxs-lookup"><span data-stu-id="4e2f6-109">It then finds all the descendant elements named `Phone` and, for each, uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method to obtain and output the value of the attribute named `type`:</span></span>

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList = From el In cust...<Phone>
For Each e As XElement In elList
    Console.WriteLine(e.@type)
Next
```

<span data-ttu-id="4e2f6-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4e2f6-110">This example produces the following output:</span></span>

```output
home
work
```

## <a name="example-retrieve-an-attribute-value-with-a-cast"></a><span data-ttu-id="4e2f6-111">Exemple : récupérer une valeur d’attribut avec un cast</span><span class="sxs-lookup"><span data-stu-id="4e2f6-111">Example: Retrieve an attribute value with a cast</span></span>

<span data-ttu-id="4e2f6-112">Vous pouvez récupérer la valeur d’un attribut en la castant, comme vous le feriez avec des <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="4e2f6-112">You can retrieve the value of an attribute by casting it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="4e2f6-113">Cela est illustré par l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4e2f6-113">The following example demonstrates this:</span></span>

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList As IEnumerable(Of XElement) = _
    From el In cust...<Phone> _
    Select el
For Each el As XElement In elList
    Console.WriteLine(el.@type)
Next
```

<span data-ttu-id="4e2f6-114">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4e2f6-114">This example produces the following output:</span></span>

```output
home
work
```

<span data-ttu-id="4e2f6-115">LINQ to XML fournit des opérateurs de cast explicites pour la <xref:System.Xml.Linq.XAttribute> classe à `string` , `bool` , `bool?` , `int` ,,,,,,,, `int?` `uint` `uint?` `long` `long?` `ulong` `ulong?` `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` , `DateTime?` ,,,, `TimeSpan` `TimeSpan?` `GUID` et `GUID?` .</span><span class="sxs-lookup"><span data-stu-id="4e2f6-115">LINQ to XML provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>

## <a name="example-cast-for-an-attribute-in-a-namespace"></a><span data-ttu-id="4e2f6-116">Exemple : cast pour un attribut dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="4e2f6-116">Example: Cast for an attribute in a namespace</span></span>

<span data-ttu-id="4e2f6-117">L’exemple suivant montre le même code pour un attribut qui se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4e2f6-117">The following example shows the same code for an attribute that's in a namespace.</span></span> <span data-ttu-id="4e2f6-118">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4e2f6-118">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement cust = new XElement(aw + "PhoneNumbers",
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "home"),
        "555-555-5555"),
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants(aw + "Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute(aw + "type"));
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim cust As XElement = _
            <aw:PhoneNumbers>
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>
            </aw:PhoneNumbers>
        Dim elList As IEnumerable(Of XElement) = _
            From el In cust...<aw:Phone> _
            Select el
        For Each el As XElement In elList
            Console.WriteLine(el.@aw:type)
        Next
    End Sub
End Module
```

<span data-ttu-id="4e2f6-119">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4e2f6-119">This example produces the following output:</span></span>

```output
home
work
```

## <a name="see-also"></a><span data-ttu-id="4e2f6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e2f6-120">See also</span></span>

- [<span data-ttu-id="4e2f6-121">Vue d’ensemble des axes LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="4e2f6-121">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
