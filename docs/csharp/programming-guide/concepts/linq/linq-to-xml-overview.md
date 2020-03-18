---
title: Vue d’ensemble de LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 334788a50832b8fe42ecc9a3272dd71f2f2af4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168413"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="c9dc5-102">Vue d’ensemble de LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c9dc5-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="c9dc5-103">LINQ to XML fournit une interface de programmation XML en mémoire qui exploite le framework LINQ (Language-Integrated Query) de .NET.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="c9dc5-104">LINQ to XML utilise les capacités .NET et s’apparente à une interface de programmation XML DOM (Document Object Model) améliorée et mise à jour.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="c9dc5-105">Le langage XML a été largement adopté comme méthode pour mettre en forme des données dans de nombreux contextes.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="c9dc5-106">Par exemple, on trouve du code XML sur le Web, dans les fichiers de configuration, dans les fichiers Microsoft Office Word et dans les bases de données.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c9dc5-107">est une approche à jour et repensée de la programmation avec XML.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-107">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="c9dc5-108">Il fournit les capacités de modification de documents en mémoire du modèle d’objet de document (DOM), et prend en charge les expressions de requête linQ.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="c9dc5-109">Bien que ces expressions de requête soient syntaxiquement différentes de XPath, elles procurent la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="c9dc5-110">Développeurs LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="c9dc5-110">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c9dc5-111">cible un large éventail de développeurs.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-111">targets a variety of developers.</span></span> <span data-ttu-id="c9dc5-112">Pour un développeur qui souhaite simplement se faciliter la tâche, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rend le XML plus abordable en fournissant une expérience de requête semblable à SQL.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="c9dc5-113">Un rapide apprentissage permettra aux programmeurs d'écrire des requêtes succinctes et puissantes dans le langage de programmation de leur choix.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="c9dc5-114">Les développeurs professionnels peuvent utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour accroître considérablement leur productivité.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="c9dc5-115">Avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ils peuvent écrire moins de code qui est plus expressif, plus compact et plus puissant.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="c9dc5-116">Ils peuvent utiliser simultanément des expressions de requête de plusieurs domaines de données.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="c9dc5-117">Qu'est-ce que LINQ to XML ?</span><span class="sxs-lookup"><span data-stu-id="c9dc5-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c9dc5-118">est une interface de programmation XML prenant en charge LINQ qui vous permet de travailler avec du code XML dans les langages de programmation .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c9dc5-119">s’apparente au modèle DOM en ce sens qu’il place le document XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-119">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="c9dc5-120">Vous pouvez interroger et modifier le document, et après l'avoir modifié, vous pouvez l'enregistrer dans un fichier ou le sérialiser et l'envoyer via Internet.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="c9dc5-121">Cependant, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] diffère du modèle DOM : il procure un nouveau modèle objet qui est plus léger et plus facile à manipuler, et qui tire parti des fonctionnalités du langage dans C#.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="c9dc5-122">L’avantage le [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] plus important est son intégration avec la requête intégrée à la langue (LINQ).</span><span class="sxs-lookup"><span data-stu-id="c9dc5-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="c9dc5-123">Cette intégration vous permet d'écrire des requêtes sur le document XML en mémoire afin de récupérer des collections d'éléments et d'attributs.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="c9dc5-124">La capacité de requête de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est comparable en terme de fonctionnalités (mais pas en termes de syntaxe) à XQuery et XPath.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="c9dc5-125">L’intégration de LINQ dans le CMD fournit une dactylographie plus forte, une vérification du temps de compilation et un meilleur soutien de débbuggeur.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-125">The integration of LINQ in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="c9dc5-126">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] présente également l'avantage de pouvoir utiliser des résultats de requête en tant que paramètres de constructeurs d'objets <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute>, ce qui constitue une approche puissante pour la création d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="c9dc5-127">Cette approche, appelée *construction fonctionnelle*, permet aux développeurs de transformer facilement des arborescences XML d’une forme en une autre.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="c9dc5-128">Par exemple, vous pouvez avoir un bon de commande XML classique comme décrit dans [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="c9dc5-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="c9dc5-129">En utilisant [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pourriez exécuter la requête suivante afin d'obtenir la valeur d'attribut de numéro de référence pour chaque élément de la commande fournisseur :</span><span class="sxs-lookup"><span data-stu-id="c9dc5-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="c9dc5-130">Vous pouvez réécrire ceci sous forme d’une syntaxe de méthode :</span><span class="sxs-lookup"><span data-stu-id="c9dc5-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="c9dc5-131">Vous pourriez également, si vous le souhaitez, générer une liste des éléments avec une valeur supérieure à $ 100, triés par numéro de référence.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="c9dc5-132">Pour obtenir ces informations, vous pourriez exécuter la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="c9dc5-132">To obtain this information, you could run the following query:</span></span>

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

<span data-ttu-id="c9dc5-133">Vous pouvez aussi réécrire ceci sous forme d’une syntaxe de méthode :</span><span class="sxs-lookup"><span data-stu-id="c9dc5-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="c9dc5-134">En plus de ces [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] capacités LINQ, fournit une interface de programmation XML améliorée.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-134">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="c9dc5-135">Grâce à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="c9dc5-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="c9dc5-136">Chargez XML à partir de [fichiers](how-to-load-xml-from-a-file.md) ou [de flux](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="c9dc5-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="c9dc5-137">sérialiser du code XML vers des fichiers ou des flux ;</span><span class="sxs-lookup"><span data-stu-id="c9dc5-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="c9dc5-138">créer du code XML à partir de zéro à l'aide de la construction fonctionnelle ;</span><span class="sxs-lookup"><span data-stu-id="c9dc5-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="c9dc5-139">interroger du code XML à l’aide d’axes de type XPath ;</span><span class="sxs-lookup"><span data-stu-id="c9dc5-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="c9dc5-140">manipuler l'arborescence XML en mémoire à l'aide de méthodes telles que <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> et <xref:System.Xml.Linq.XElement.SetValue%2A> ;</span><span class="sxs-lookup"><span data-stu-id="c9dc5-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="c9dc5-141">valider des arborescences XML à l'aide de XSD ;</span><span class="sxs-lookup"><span data-stu-id="c9dc5-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="c9dc5-142">utiliser une combinaison de ces fonctionnalités pour transformer des arborescences XML d'une forme à une autre.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="c9dc5-143">Création d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="c9dc5-143">Creating XML Trees</span></span>

<span data-ttu-id="c9dc5-144">Un des principaux avantages liés à la programmation avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tient à la facilité de création d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="c9dc5-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="c9dc5-145">Par exemple, pour créer une petite arborescence XML, vous pouvez écrire du code comme suit :</span><span class="sxs-lookup"><span data-stu-id="c9dc5-145">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="c9dc5-146">Pour plus d’informations, consultez [Création d’arborescences XML (C#)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="c9dc5-146">For more information, see [Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9dc5-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9dc5-147">See also</span></span>

- [<span data-ttu-id="c9dc5-148">Référence (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c9dc5-148">Reference (LINQ to XML)</span></span>](./reference-linq-to-xml.md)
- [<span data-ttu-id="c9dc5-149">LINQ à XML vs DOM (C)</span><span class="sxs-lookup"><span data-stu-id="c9dc5-149">LINQ to XML vs. DOM (C#)</span></span>](./linq-to-xml-vs-dom.md)
- [<span data-ttu-id="c9dc5-150">Comparaison de LINQ to XML et des autres technologies XML</span><span class="sxs-lookup"><span data-stu-id="c9dc5-150">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
