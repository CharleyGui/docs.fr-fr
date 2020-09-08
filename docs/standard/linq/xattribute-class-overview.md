---
title: Vue d’ensemble de la classe XAttribute
description: La classe XAttribute représente des attributs XML. L’utilisation des attributs dans LINQ to XML est semblable à l’utilisation des éléments.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: deab6e8dd9695a442cd362401aec8b68cdbf218f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552401"
---
# <a name="xattribute-class-overview"></a><span data-ttu-id="b7e48-104">Vue d’ensemble de la classe XAttribute</span><span class="sxs-lookup"><span data-stu-id="b7e48-104">XAttribute class overview</span></span>

<span data-ttu-id="b7e48-105">Les attributs sont des paires nom-valeur associées à un élément.</span><span class="sxs-lookup"><span data-stu-id="b7e48-105">Attributes are name-value pairs that are associated with an element.</span></span> <span data-ttu-id="b7e48-106">La classe <xref:System.Xml.Linq.XAttribute> représente des attributs XML.</span><span class="sxs-lookup"><span data-stu-id="b7e48-106">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>

<span data-ttu-id="b7e48-107">L’utilisation des attributs dans LINQ to XML est semblable à l’utilisation des éléments.</span><span class="sxs-lookup"><span data-stu-id="b7e48-107">Working with attributes in LINQ to XML is similar to working with elements.</span></span> <span data-ttu-id="b7e48-108">Leurs constructeurs sont similaires.</span><span class="sxs-lookup"><span data-stu-id="b7e48-108">Their constructors are similar.</span></span> <span data-ttu-id="b7e48-109">Les méthodes que vous utilisez pour en récupérer des collections sont similaires.</span><span class="sxs-lookup"><span data-stu-id="b7e48-109">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="b7e48-110">Une expression de requête LINQ pour une collection d’attributs ressemble à une expression de requête LINQ pour une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="b7e48-110">A LINQ query expression for a collection of attributes looks similar to a LINQ query expression for a collection of elements.</span></span>

<span data-ttu-id="b7e48-111">L'ordre dans lequel les attributs ont été ajoutés à un élément est conservé.</span><span class="sxs-lookup"><span data-stu-id="b7e48-111">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="b7e48-112">Autrement dit, lorsque vous itérez au sein des attributs, vous les voyez dans l'ordre dans lequel ils ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="b7e48-112">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>

## <a name="the-xattribute-constructor"></a><span data-ttu-id="b7e48-113">Le constructeur XAttribute</span><span class="sxs-lookup"><span data-stu-id="b7e48-113">The XAttribute constructor</span></span>

<span data-ttu-id="b7e48-114">Le constructeur suivant de la <xref:System.Xml.Linq.XAttribute> classe est celui que vous utiliserez le plus souvent :</span><span class="sxs-lookup"><span data-stu-id="b7e48-114">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you'll most commonly use:</span></span>

|<span data-ttu-id="b7e48-115">Constructeur</span><span class="sxs-lookup"><span data-stu-id="b7e48-115">Constructor</span></span>|<span data-ttu-id="b7e48-116">Description</span><span class="sxs-lookup"><span data-stu-id="b7e48-116">Description</span></span>|
|-----------------|-----------------|
|`XAttribute(XName name, object content)`|<span data-ttu-id="b7e48-117">Elle crée un objet <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b7e48-117">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="b7e48-118">L'argument `name` spécifie le nom de l'attribut ; l'argument `content` spécifie le contenu de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="b7e48-118">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|

## <a name="example-create-an-element-with-an-attribute"></a><span data-ttu-id="b7e48-119">Exemple : créer un élément avec un attribut</span><span class="sxs-lookup"><span data-stu-id="b7e48-119">Example: Create an element with an attribute</span></span>

<span data-ttu-id="b7e48-120">L’exemple suivant illustre la tâche courante de création d’un élément qui contient un attribut.</span><span class="sxs-lookup"><span data-stu-id="b7e48-120">The following example shows the common task of creating an element that contains an attribute.</span></span>

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

```vb
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>
Console.WriteLine(phone)
```

<span data-ttu-id="b7e48-121">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b7e48-121">This example produces the following output:</span></span>

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-functional-construction-of-attributes"></a><span data-ttu-id="b7e48-122">Exemple : construction fonctionnelle d’attributs</span><span class="sxs-lookup"><span data-stu-id="b7e48-122">Example: Functional construction of attributes</span></span>

<span data-ttu-id="b7e48-123">Vous pouvez construire des <xref:System.Xml.Linq.XAttribute> objets en ligne avec la construction d' <xref:System.Xml.Linq.XElement> objets, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b7e48-123">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as shown in the following example:</span></span>

```csharp
XElement c = new XElement("Customers",
    new XElement("Customer",
        new XElement("Name", "John Doe"),
        new XElement("PhoneNumbers",
            new XElement("Phone",
                new XAttribute("type", "home"),
                "555-555-5555"),
            new XElement("Phone",
                new XAttribute("type", "work"),
                "666-666-6666")
        )
    )
);
Console.WriteLine(c);
```

```vb
Dim c As XElement = _
    <Customers>
        <Customer>
            <Name>John Doe</Name>
            <PhoneNumbers>
                <Phone type="home">555-555-5555</Phone>
                <Phone type="work">666-666-6666</Phone>
            </PhoneNumbers>
        </Customer>
    </Customers>
Console.WriteLine(c)
```

<span data-ttu-id="b7e48-124">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b7e48-124">This example produces the following output:</span></span>

```xml
<Customers>
  <Customer>
    <Name>John Doe</Name>
    <PhoneNumbers>
      <Phone type="home">555-555-5555</Phone>
      <Phone type="work">666-666-6666</Phone>
    </PhoneNumbers>
  </Customer>
</Customers>
```

## <a name="attributes-arent-nodes"></a><span data-ttu-id="b7e48-125">Les attributs ne sont pas des nœuds</span><span class="sxs-lookup"><span data-stu-id="b7e48-125">Attributes aren't nodes</span></span>

<span data-ttu-id="b7e48-126">Il existe certaines différences entre les attributs et les éléments.</span><span class="sxs-lookup"><span data-stu-id="b7e48-126">There are some differences between attributes and elements.</span></span> <span data-ttu-id="b7e48-127"><xref:System.Xml.Linq.XAttribute> les objets ne sont pas des nœuds dans l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="b7e48-127"><xref:System.Xml.Linq.XAttribute> objects aren't nodes in the XML tree.</span></span> <span data-ttu-id="b7e48-128">Il s’agit de paires nom-valeur associées à un élément XML.</span><span class="sxs-lookup"><span data-stu-id="b7e48-128">They're name-value pairs associated with an XML element.</span></span> <span data-ttu-id="b7e48-129">Par opposition au modèle DOM (Document Objet Model), cela reflète plus étroitement la structure du langage XML.</span><span class="sxs-lookup"><span data-stu-id="b7e48-129">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="b7e48-130">Bien que <xref:System.Xml.Linq.XAttribute> les objets ne soient pas réellement des nœuds dans l’arborescence XML, l’utilisation d' <xref:System.Xml.Linq.XAttribute> objets est semblable à l’utilisation d' <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="b7e48-130">Although <xref:System.Xml.Linq.XAttribute> objects aren't actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="b7e48-131">Cette distinction ne revêt une importance que pour les développeurs qui écrivent du code qui interagit avec des arborescences XML au niveau nœud.</span><span class="sxs-lookup"><span data-stu-id="b7e48-131">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="b7e48-132">De nombreux développeurs ne se soucient pas de cette distinction.</span><span class="sxs-lookup"><span data-stu-id="b7e48-132">Many developers won't be concerned with this distinction.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7e48-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7e48-133">See also</span></span>

- [<span data-ttu-id="b7e48-134">Présentation de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b7e48-134">LINQ to XML overview</span></span>](linq-xml-overview.md)
