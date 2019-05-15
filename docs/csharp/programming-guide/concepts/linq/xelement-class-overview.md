---
title: Vue d’ensemble de la classe XElement (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: cddb36ac6401c20478a1254fe3d63afe5bd13099
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595763"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="6c257-102">Vue d’ensemble de la classe XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="6c257-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="6c257-103">La classe <xref:System.Xml.Linq.XElement> est l'une des classes fondamentales dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c257-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="6c257-104">Elle représente un élément XML.</span><span class="sxs-lookup"><span data-stu-id="6c257-104">It represents an XML element.</span></span> <span data-ttu-id="6c257-105">Vous pouvez utiliser cette classe pour créer des éléments, modifier le contenu de l'élément, ajouter, modifier ou supprimer des éléments enfants, ajouter des attributs à un élément ou sérialiser le contenu d'un élément sous forme textuelle.</span><span class="sxs-lookup"><span data-stu-id="6c257-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="6c257-106">Vous pouvez également interagir avec d'autres classes dans <xref:System.Xml?displayProperty=nameWithType>, telles que <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> et <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="6c257-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="6c257-107">Fonctionnalité de XElement</span><span class="sxs-lookup"><span data-stu-id="6c257-107">XElement Functionality</span></span>  
 <span data-ttu-id="6c257-108">Cette rubrique décrit la fonctionnalité fournie par la classe <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6c257-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="6c257-109">Construction d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="6c257-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="6c257-110">Vous pouvez construire des arborescences XML de diverses façons, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c257-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="6c257-111">Vous pouvez construire une arborescence XML dans du code.</span><span class="sxs-lookup"><span data-stu-id="6c257-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="6c257-112">Pour plus d’informations, consultez [Création d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="6c257-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
- <span data-ttu-id="6c257-113">Vous pouvez analyser du code XML de diverses sources, y compris un objet <xref:System.IO.TextReader>, des fichiers texte ou une adresse Web (URL).</span><span class="sxs-lookup"><span data-stu-id="6c257-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="6c257-114">Pour plus d’informations, consultez [Analyse de code XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6c257-114">For more information, see [Parsing XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
- <span data-ttu-id="6c257-115">Vous pouvez utiliser un objet <xref:System.Xml.XmlReader> pour remplir l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="6c257-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="6c257-116">Pour plus d'informations, consultez <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c257-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="6c257-117">Si vous avez un module qui peut écrire du contenu dans un objet <xref:System.Xml.XmlWriter>, vous pouvez utiliser la méthode <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un writer, passer ce dernier au module, puis utiliser le contenu écrit dans l'objet <xref:System.Xml.XmlWriter> pour remplir l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="6c257-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="6c257-118">Toutefois, la manière la plus courante de créer une arborescence XML est la suivante :</span><span class="sxs-lookup"><span data-stu-id="6c257-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="6c257-119">Une autre technique de création d’arborescence XML très courante consiste à utiliser les résultats d’une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pour remplir une arborescence XML, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6c257-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="6c257-120">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6c257-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="6c257-121">Sérialisation d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="6c257-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="6c257-122">Vous pouvez sérialiser l'arborescence XML vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6c257-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="6c257-123">Pour plus d’informations, consultez [Sérialisation d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="6c257-123">For more information, see [Serializing XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="6c257-124">Récupération de données XML par le biais de méthodes d'axe</span><span class="sxs-lookup"><span data-stu-id="6c257-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="6c257-125">Vous pouvez utiliser des méthodes d'axe pour récupérer des attributs, des éléments enfants, des éléments descendants et des éléments ancêtres.</span><span class="sxs-lookup"><span data-stu-id="6c257-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="6c257-126">Les requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] opèrent sur les méthodes d'axe et offrent plusieurs moyens flexibles et puissants de parcourir et de traiter une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="6c257-126">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="6c257-127">Pour plus d’informations, consultez [Axes LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="6c257-127">For more information, see [LINQ to XML Axes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="6c257-128">Interrogation d’arborescences XML</span><span class="sxs-lookup"><span data-stu-id="6c257-128">Querying XML Trees</span></span>  
 <span data-ttu-id="6c257-129">Vous pouvez écrire des requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] qui extraient des données d’une arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="6c257-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="6c257-130">Pour plus d’informations, consultez [Interrogation d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="6c257-130">For more information, see [Querying XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="6c257-131">Modification d’arborescences XML</span><span class="sxs-lookup"><span data-stu-id="6c257-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="6c257-132">Vous pouvez modifier un élément de différentes façons, y compris modifier son contenu ou ses attributs.</span><span class="sxs-lookup"><span data-stu-id="6c257-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="6c257-133">Vous pouvez également supprimer un élément de son parent.</span><span class="sxs-lookup"><span data-stu-id="6c257-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="6c257-134">Pour plus d’informations, consultez [Modification d’arborescences XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6c257-134">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c257-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c257-135">See also</span></span>

- [<span data-ttu-id="6c257-136">Vue d’ensemble de la programmation LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6c257-136">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
