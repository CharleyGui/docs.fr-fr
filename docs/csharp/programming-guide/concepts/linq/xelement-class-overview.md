---
title: Vue d’ensemble de la classe XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 6a93dd4bdaf16fddff800b08b0f3146ecb63f9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167892"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="5f7f8-102">Vue d’ensemble de la classe XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="5f7f8-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="5f7f8-103">La classe <xref:System.Xml.Linq.XElement> est l'une des classes fondamentales dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f7f8-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="5f7f8-104">Elle représente un élément XML.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-104">It represents an XML element.</span></span> <span data-ttu-id="5f7f8-105">Vous pouvez utiliser cette classe pour créer des éléments, modifier le contenu de l'élément, ajouter, modifier ou supprimer des éléments enfants, ajouter des attributs à un élément ou sérialiser le contenu d'un élément sous forme textuelle.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="5f7f8-106">Vous pouvez également interagir avec d'autres classes dans <xref:System.Xml?displayProperty=nameWithType>, telles que <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="5f7f8-107">Cette rubrique décrit la fonctionnalité fournie par la classe <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="5f7f8-108">Construction d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="5f7f8-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="5f7f8-109">Vous pouvez construire des arborescences XML de diverses façons, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5f7f8-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="5f7f8-110">Vous pouvez construire une arborescence XML dans du code.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="5f7f8-111">Pour plus d’informations, consultez [Création d’arborescences XML (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5f7f8-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="5f7f8-112">Vous pouvez analyser du code XML de diverses sources, y compris un objet <xref:System.IO.TextReader>, des fichiers texte ou une adresse Web (URL).</span><span class="sxs-lookup"><span data-stu-id="5f7f8-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="5f7f8-113">Pour plus d’informations, consultez [Analyse de code XML (C#)](./how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="5f7f8-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="5f7f8-114">Vous pouvez utiliser un objet <xref:System.Xml.XmlReader> pour remplir l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="5f7f8-115">Pour plus d’informations, consultez <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="5f7f8-116">Si vous avez un module qui peut écrire du contenu dans un objet <xref:System.Xml.XmlWriter>, vous pouvez utiliser la méthode <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un writer, passer ce dernier au module, puis utiliser le contenu écrit dans l'objet <xref:System.Xml.XmlWriter> pour remplir l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="5f7f8-117">Toutefois, la manière la plus courante de créer une arborescence XML est la suivante :</span><span class="sxs-lookup"><span data-stu-id="5f7f8-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="5f7f8-118">Une autre technique très courante pour créer un arbre XML consiste à utiliser les résultats d’une requête LINQ pour peupler un arbre XML, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5f7f8-118">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="5f7f8-119">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5f7f8-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="5f7f8-120">Sérialisation d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="5f7f8-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="5f7f8-121">Vous pouvez sérialiser l'arborescence XML vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="5f7f8-122">Pour plus d’informations, consultez [Sérialisation d’arborescences XML (C#)](./preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="5f7f8-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="5f7f8-123">Récupération de données XML par le biais de méthodes d'axe</span><span class="sxs-lookup"><span data-stu-id="5f7f8-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="5f7f8-124">Vous pouvez utiliser des méthodes d'axe pour récupérer des attributs, des éléments enfants, des éléments descendants et des éléments ancêtres.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="5f7f8-125">Les requêtes LINQ fonctionnent selon les méthodes de l’axe et offrent plusieurs façons flexibles et puissantes de naviguer à travers et de traiter un arbre XML.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-125">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="5f7f8-126">Pour plus d’informations, consultez [Axes LINQ to XML (C#)](./linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5f7f8-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="5f7f8-127">Interrogation d’arborescences XML</span><span class="sxs-lookup"><span data-stu-id="5f7f8-127">Querying XML Trees</span></span>  
 <span data-ttu-id="5f7f8-128">Vous pouvez écrire des requêtes LINQ qui extraient des données d’un arbre XML.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-128">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="5f7f8-129">Pour plus d’informations, consultez [Interrogation d’arborescences XML (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="5f7f8-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="5f7f8-130">Modification d’arborescences XML</span><span class="sxs-lookup"><span data-stu-id="5f7f8-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="5f7f8-131">Vous pouvez modifier un élément de différentes façons, y compris modifier son contenu ou ses attributs.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="5f7f8-132">Vous pouvez également supprimer un élément de son parent.</span><span class="sxs-lookup"><span data-stu-id="5f7f8-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="5f7f8-133">Pour plus d’informations, consultez [Modification d’arborescences XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5f7f8-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f7f8-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f7f8-134">See also</span></span>

- [<span data-ttu-id="5f7f8-135">Vue d’ensemble de la programmation LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5f7f8-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
