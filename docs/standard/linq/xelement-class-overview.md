---
title: Vue d’ensemble de la classe XElement
description: La classe XElement représente des éléments XML. Vous pouvez l’utiliser pour créer et modifier des éléments, ajouter des attributs et des enfants, et pour sérialiser.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 325afd09661532fe44aecf89fe9784520274638e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552524"
---
# <a name="xelement-class-overview"></a><span data-ttu-id="387ec-104">Vue d’ensemble de la classe XElement</span><span class="sxs-lookup"><span data-stu-id="387ec-104">XElement class overview</span></span>

<span data-ttu-id="387ec-105">La <xref:System.Xml.Linq.XElement> classe est l’une des classes fondamentales de LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="387ec-105">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in LINQ to XML.</span></span> <span data-ttu-id="387ec-106">Elle représente un élément XML.</span><span class="sxs-lookup"><span data-stu-id="387ec-106">It represents an XML element.</span></span> <span data-ttu-id="387ec-107">La liste suivante montre ce que vous pouvez utiliser pour :</span><span class="sxs-lookup"><span data-stu-id="387ec-107">The following list shows what you can use this class for:</span></span>

- <span data-ttu-id="387ec-108">Créer des éléments.</span><span class="sxs-lookup"><span data-stu-id="387ec-108">Create elements.</span></span>
- <span data-ttu-id="387ec-109">Modifiez le contenu de l’élément.</span><span class="sxs-lookup"><span data-stu-id="387ec-109">Change the content of the element.</span></span>
- <span data-ttu-id="387ec-110">Ajoutez, modifiez ou supprimez des éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="387ec-110">Add, change, or delete child elements.</span></span>
- <span data-ttu-id="387ec-111">Ajoutez des attributs à un élément.</span><span class="sxs-lookup"><span data-stu-id="387ec-111">Add attributes to an element.</span></span>
- <span data-ttu-id="387ec-112">Sérialiser le contenu d’un élément sous forme de texte.</span><span class="sxs-lookup"><span data-stu-id="387ec-112">Serialize the contents of an element in text form.</span></span>

<span data-ttu-id="387ec-113">Vous pouvez également interagir avec d'autres classes dans <xref:System.Xml?displayProperty=nameWithType>, telles que <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="387ec-113">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="387ec-114">Cet article décrit les fonctionnalités fournies par la <xref:System.Xml.Linq.XElement> classe.</span><span class="sxs-lookup"><span data-stu-id="387ec-114">This article describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>

## <a name="construct-xml-trees"></a><span data-ttu-id="387ec-115">Construire des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="387ec-115">Construct XML trees</span></span>

<span data-ttu-id="387ec-116">Vous pouvez construire des arborescences XML de différentes façons, notamment :</span><span class="sxs-lookup"><span data-stu-id="387ec-116">You can construct XML trees in different ways, including the following:</span></span>

- <span data-ttu-id="387ec-117">Vous pouvez construire une arborescence XML dans du code.</span><span class="sxs-lookup"><span data-stu-id="387ec-117">You can construct an XML tree in code.</span></span> <span data-ttu-id="387ec-118">Pour plus d’informations, consultez [arborescences XML](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="387ec-118">For more information, see [XML trees](functional-construction.md).</span></span>
- <span data-ttu-id="387ec-119">Vous pouvez analyser du code XML de diverses sources, y compris un objet <xref:System.IO.TextReader>, des fichiers texte ou une adresse Web (URL).</span><span class="sxs-lookup"><span data-stu-id="387ec-119">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="387ec-120">Pour plus d’informations, consultez [Parse XML](parse-string.md).</span><span class="sxs-lookup"><span data-stu-id="387ec-120">For more information, see [Parse XML](parse-string.md).</span></span>
- <span data-ttu-id="387ec-121">Vous pouvez utiliser un objet <xref:System.Xml.XmlReader> pour remplir l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="387ec-121">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="387ec-122">Pour plus d'informations, consultez <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="387ec-122">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>
- <span data-ttu-id="387ec-123">Si vous avez un module qui peut écrire du contenu dans un <xref:System.Xml.XmlWriter> , vous pouvez utiliser la <xref:System.Xml.Linq.XContainer.CreateWriter%2A> méthode pour créer un writer, passer l’enregistreur au module, puis utiliser le contenu écrit dans <xref:System.Xml.XmlWriter> pour remplir l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="387ec-123">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that's written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>

<span data-ttu-id="387ec-124">L’exemple suivant crée une arborescence.</span><span class="sxs-lookup"><span data-stu-id="387ec-124">The following example creates a tree.</span></span> <span data-ttu-id="387ec-125">La version C# utilise des créations d’éléments imbriqués.</span><span class="sxs-lookup"><span data-stu-id="387ec-125">The C# version uses nested element creations.</span></span> <span data-ttu-id="387ec-126">Vous pouvez utiliser la même technique dans Visual Basic, mais cet exemple utilise des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="387ec-126">You can use the same technique in Visual Basic, but this example uses XML literals.</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

<span data-ttu-id="387ec-127">Vous pouvez également utiliser une requête LINQ to XML pour remplir une arborescence XML, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="387ec-127">You can also use a LINQ to XML query to populate an XML tree, as shown in the following example:</span></span>

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where el.Value > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="387ec-128">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="387ec-128">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="serialize-xml-trees"></a><span data-ttu-id="387ec-129">Sérialiser des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="387ec-129">Serialize XML trees</span></span>

<span data-ttu-id="387ec-130">Vous pouvez sérialiser l'arborescence XML vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="387ec-130">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="387ec-131">Pour plus d’informations, consultez [sérialiser des arborescences XML](preserve-white-space-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="387ec-131">For more information, see [Serialize XML trees](preserve-white-space-serializing.md).</span></span>

## <a name="retrieve-xml-data-via-axis-methods"></a><span data-ttu-id="387ec-132">Récupérer des données XML à l’aide de méthodes d’axe</span><span class="sxs-lookup"><span data-stu-id="387ec-132">Retrieve XML data via axis methods</span></span>

<span data-ttu-id="387ec-133">Vous pouvez utiliser des méthodes d'axe pour récupérer des attributs, des éléments enfants, des éléments descendants et des éléments ancêtres.</span><span class="sxs-lookup"><span data-stu-id="387ec-133">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="387ec-134">LINQ to XML requêtes opèrent sur des méthodes d’axe et offrent plusieurs moyens flexibles et puissants de parcourir et de traiter une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="387ec-134">LINQ to XML queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>

<span data-ttu-id="387ec-135">Pour plus d’informations, consultez [LINQ to XML vue d’ensemble des axes](linq-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="387ec-135">For more information, see [LINQ to XML axes overview](linq-xml-axes-overview.md).</span></span>

## <a name="query-xml-trees"></a><span data-ttu-id="387ec-136">Interroger des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="387ec-136">Query XML trees</span></span>

<span data-ttu-id="387ec-137">Vous pouvez écrire des LINQ to XML des requêtes qui extraient des données d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="387ec-137">You can write LINQ to XML queries that extract data from an XML tree.</span></span>

<span data-ttu-id="387ec-138">Pour plus d’informations, consultez [vue d’ensemble de la requête d’arborescences XML](query-xml-trees-overview.md).</span><span class="sxs-lookup"><span data-stu-id="387ec-138">For more information, see [Query XML trees overview](query-xml-trees-overview.md).</span></span>

## <a name="modify-xml-trees"></a><span data-ttu-id="387ec-139">Modifier des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="387ec-139">Modify XML trees</span></span>

<span data-ttu-id="387ec-140">Vous pouvez modifier un élément de différentes façons, y compris modifier son contenu ou ses attributs.</span><span class="sxs-lookup"><span data-stu-id="387ec-140">You can modify an element in different ways, including changing its content or attributes.</span></span> <span data-ttu-id="387ec-141">Vous pouvez également supprimer un élément de son parent.</span><span class="sxs-lookup"><span data-stu-id="387ec-141">You can also remove an element from its parent.</span></span>

<span data-ttu-id="387ec-142">Pour plus d’informations, consultez [modifier des arborescences XML](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="387ec-142">For more information, see [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="387ec-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="387ec-143">See also</span></span>

- [<span data-ttu-id="387ec-144">Vue d’ensemble de la programmation LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="387ec-144">LINQ to XML programming overview</span></span>](functional-vs-procedural-programming.md)
