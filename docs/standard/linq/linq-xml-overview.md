---
title: Vue d’ensemble-LINQ to XML
description: LINQ to XML fournit une interface de programmation XML en mémoire qui est basée sur les fonctionnalités de .NET et comparable à une API DOM mise à jour.
ms.date: 10/30/2018
dev_langs:
- csharp
- vb
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: f805d757c9059a07988c6cb16e41ffed017fe853
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553356"
---
# <a name="linq-to-xml-overview"></a><span data-ttu-id="2a7d0-103">Présentation de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="2a7d0-103">LINQ to XML overview</span></span>

<span data-ttu-id="2a7d0-104">LINQ to XML fournit une interface de programmation XML en mémoire qui exploite le framework LINQ (Language-Integrated Query) de .NET.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-104">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="2a7d0-105">LINQ to XML utilise les capacités .NET et s’apparente à une interface de programmation XML DOM (Document Object Model) améliorée et mise à jour.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-105">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="2a7d0-106">Le langage XML a été largement adopté comme méthode pour mettre en forme des données dans de nombreux contextes.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-106">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="2a7d0-107">Par exemple, on trouve du code XML sur le Web, dans les fichiers de configuration, dans les fichiers Microsoft Office Word et dans les bases de données.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-107">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

<span data-ttu-id="2a7d0-108">LINQ to XML est une approche à jour et repensée de la programmation avec XML.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-108">LINQ to XML is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="2a7d0-109">Il fournit les fonctionnalités de modification de document en mémoire du Document Object Model (DOM) et prend en charge les expressions de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-109">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="2a7d0-110">Bien que ces expressions de requête soient syntaxiquement différentes de XPath, elles procurent la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-110">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="2a7d0-111">LINQ to XML les développeurs</span><span class="sxs-lookup"><span data-stu-id="2a7d0-111">LINQ to XML developers</span></span>

<span data-ttu-id="2a7d0-112">LINQ to XML cible un large éventail de développeurs.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-112">LINQ to XML targets a variety of developers.</span></span> <span data-ttu-id="2a7d0-113">Pour un développeur en moyenne qui souhaite simplement faire un travail, LINQ to XML facilite le XML en fournissant une expérience de requête similaire à SQL.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-113">For an average developer who just wants to get something done, LINQ to XML makes XML easier by providing a query experience that's similar to SQL.</span></span> <span data-ttu-id="2a7d0-114">Un rapide apprentissage permettra aux programmeurs d'écrire des requêtes succinctes et puissantes dans le langage de programmation de leur choix.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-114">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="2a7d0-115">Les développeurs professionnels peuvent utiliser LINQ to XML pour augmenter leur productivité de façon considérable.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-115">Professional developers can use LINQ to XML to greatly increase their productivity.</span></span> <span data-ttu-id="2a7d0-116">Avec LINQ to XML, ils peuvent écrire moins de code qui est plus expressif, plus compact et plus puissant.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-116">With LINQ to XML, they can write less code that's more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="2a7d0-117">Ils peuvent utiliser simultanément des expressions de requête de plusieurs domaines de données.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-117">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="linq-to-xml-is-an-xml-programming-interface"></a><span data-ttu-id="2a7d0-118">LINQ to XML est une interface de programmation XML</span><span class="sxs-lookup"><span data-stu-id="2a7d0-118">LINQ to XML is an XML programming interface</span></span>

<span data-ttu-id="2a7d0-119">LINQ to XML est une interface de programmation XML en mémoire compatible avec LINQ qui vous permet d’utiliser XML à partir des langages de programmation .NET.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-119">LINQ to XML is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

<span data-ttu-id="2a7d0-120">LINQ to XML est semblable au Document Object Model (DOM) dans le fait qu’il remet le document XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-120">LINQ to XML is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="2a7d0-121">Vous pouvez interroger et modifier le document, et après l'avoir modifié, vous pouvez l'enregistrer dans un fichier ou le sérialiser et l'envoyer via Internet.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-121">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="2a7d0-122">Toutefois, LINQ to XML diffère de DOM :</span><span class="sxs-lookup"><span data-stu-id="2a7d0-122">However, LINQ to XML differs from DOM:</span></span>

- <span data-ttu-id="2a7d0-123">Il fournit un nouveau modèle objet qui est plus léger et plus facile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-123">It provides a new object model that's lighter weight and easier to work with.</span></span>
- <span data-ttu-id="2a7d0-124">Elle tire parti des fonctionnalités de langage en C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-124">It takes advantage of language features in C# and Visual Basic.</span></span>

<span data-ttu-id="2a7d0-125">L’avantage le plus important de LINQ to XML est son intégration à LINQ (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="2a7d0-125">The most important advantage of LINQ to XML is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="2a7d0-126">Cette intégration vous permet d'écrire des requêtes sur le document XML en mémoire afin de récupérer des collections d'éléments et d'attributs.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-126">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="2a7d0-127">La fonctionnalité de requête de LINQ to XML est comparable dans les fonctionnalités (mais pas dans la syntaxe) à XPath et XQuery.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-127">The query capability of LINQ to XML is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="2a7d0-128">L’intégration de LINQ en C# et Visual Basic fournit un typage plus fort, une vérification au moment de la compilation et une prise en charge améliorée du débogueur.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-128">The integration of LINQ in C# and Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="2a7d0-129">Un autre avantage de LINQ to XML est la possibilité d’utiliser les résultats de requête en tant que paramètres pour <xref:System.Xml.Linq.XElement> et les <xref:System.Xml.Linq.XAttribute> constructeurs d’objets permet une approche puissante de la création d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-129">Another advantage of LINQ to XML is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="2a7d0-130">Cette approche, appelée *construction fonctionnelle*, permet aux développeurs de transformer facilement des arborescences XML d’une forme en une autre.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-130">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="2a7d0-131">Par exemple, vous pouvez avoir un bon de commande XML standard, comme décrit dans [exemple de fichier XML : bon de commande standard](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="2a7d0-131">For example, you might have a typical XML purchase order as described in [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span> <span data-ttu-id="2a7d0-132">À l’aide de LINQ to XML, vous pouvez exécuter la requête suivante pour obtenir la valeur de l’attribut de numéro de référence pour chaque élément item dans le bon de commande :</span><span class="sxs-lookup"><span data-stu-id="2a7d0-132">By using LINQ to XML, you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
    From item In purchaseOrder...<Item> _
    Select item.@PartNumber
```

<span data-ttu-id="2a7d0-133">En C#, cela peut être réécrit dans la syntaxe de la méthode :</span><span class="sxs-lookup"><span data-stu-id="2a7d0-133">In C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="2a7d0-134">Vous pourriez également, si vous le souhaitez, générer une liste des éléments avec une valeur supérieure à $ 100, triés par numéro de référence.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-134">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="2a7d0-135">Pour obtenir ces informations, vous pourriez exécuter la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="2a7d0-135">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
From item In purchaseOrder...<Item> _
Where (item.<Quantity>.Value * _
       item.<USPrice>.Value) > 100 _
Order By item.<PartNumber>.Value _
Select item
```

<span data-ttu-id="2a7d0-136">Là encore, en C#, cela peut être réécrit dans la syntaxe de la méthode :</span><span class="sxs-lookup"><span data-stu-id="2a7d0-136">Again, in C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="2a7d0-137">Outre ces fonctionnalités LINQ, LINQ to XML fournit une interface de programmation XML améliorée.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-137">In addition to these LINQ capabilities, LINQ to XML provides an improved XML programming interface.</span></span> <span data-ttu-id="2a7d0-138">À l’aide de LINQ to XML, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="2a7d0-138">Using LINQ to XML, you can:</span></span>

- <span data-ttu-id="2a7d0-139">Charger du code XML à partir de [fichiers](load-xml-file.md) ou de [flux](stream-xml-fragments-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="2a7d0-139">Load XML from [files](load-xml-file.md) or [streams](stream-xml-fragments-xmlreader.md).</span></span>
- <span data-ttu-id="2a7d0-140">sérialiser du code XML vers des fichiers ou des flux ;</span><span class="sxs-lookup"><span data-stu-id="2a7d0-140">Serialize XML to files or streams.</span></span>
- <span data-ttu-id="2a7d0-141">créer du code XML à partir de zéro à l'aide de la construction fonctionnelle ;</span><span class="sxs-lookup"><span data-stu-id="2a7d0-141">Create XML from scratch by using functional construction.</span></span>
- <span data-ttu-id="2a7d0-142">interroger du code XML à l’aide d’axes de type XPath ;</span><span class="sxs-lookup"><span data-stu-id="2a7d0-142">Query XML using XPath-like axes.</span></span>
- <span data-ttu-id="2a7d0-143">manipuler l'arborescence XML en mémoire à l'aide de méthodes telles que <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> et <xref:System.Xml.Linq.XElement.SetValue%2A> ;</span><span class="sxs-lookup"><span data-stu-id="2a7d0-143">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>
- <span data-ttu-id="2a7d0-144">valider des arborescences XML à l'aide de XSD ;</span><span class="sxs-lookup"><span data-stu-id="2a7d0-144">Validate XML trees using XSD.</span></span>
- <span data-ttu-id="2a7d0-145">utiliser une combinaison de ces fonctionnalités pour transformer des arborescences XML d'une forme à une autre.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-145">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="create-xml-trees"></a><span data-ttu-id="2a7d0-146">Créer des arborescences XML</span><span class="sxs-lookup"><span data-stu-id="2a7d0-146">Create XML trees</span></span>

<span data-ttu-id="2a7d0-147">L’un des avantages les plus significatifs de la programmation avec LINQ to XML est qu’il est facile de créer des arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-147">One of the most significant advantages of programming with LINQ to XML is that it's easy to create XML trees.</span></span> <span data-ttu-id="2a7d0-148">Par exemple, pour créer une petite arborescence XML, vous pouvez écrire du code comme suit :</span><span class="sxs-lookup"><span data-stu-id="2a7d0-148">For example, to create a small XML tree, you can write code as follows:</span></span>

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
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

> [!NOTE]
> <span data-ttu-id="2a7d0-149">La version Visual Basic de l’exemple utilise des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-149">The Visual Basic version of the example uses XML literals.</span></span> <span data-ttu-id="2a7d0-150">Vous pouvez également utiliser <xref:System.Xml.Linq.XElement> dans Visual Basic, comme dans la version C#.</span><span class="sxs-lookup"><span data-stu-id="2a7d0-150">You can also use <xref:System.Xml.Linq.XElement> in Visual Basic, as in the C# version.</span></span>

<span data-ttu-id="2a7d0-151">Pour plus d’informations, consultez [arborescences XML](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="2a7d0-151">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a7d0-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a7d0-152">See also</span></span>

- [<span data-ttu-id="2a7d0-153">Référence</span><span class="sxs-lookup"><span data-stu-id="2a7d0-153">Reference</span></span>](reference.md)
- [<span data-ttu-id="2a7d0-154">LINQ to XML, différences par rapport à DOM</span><span class="sxs-lookup"><span data-stu-id="2a7d0-154">LINQ to XML vs. DOM</span></span>](linq-xml-vs-dom.md)
- [<span data-ttu-id="2a7d0-155">LINQ to XML différences par rapport à d’autres technologies XML</span><span class="sxs-lookup"><span data-stu-id="2a7d0-155">LINQ to XML vs. other XML technologies</span></span>](linq-xml-vs-xml-technologies.md)
- <xref:System.Xml.Linq>
