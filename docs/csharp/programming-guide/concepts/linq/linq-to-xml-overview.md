---
title: Vue d’ensemble de LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 2394151d855d75b418616d9fa1a6f69b08cdef86
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585738"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="2dc84-102">Vue d’ensemble de LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2dc84-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="2dc84-103">Le langage XML a été largement adopté comme méthode pour mettre en forme des données dans de nombreux contextes.</span><span class="sxs-lookup"><span data-stu-id="2dc84-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="2dc84-104">Par exemple, on trouve du code XML sur le Web, dans les fichiers de configuration, dans les fichiers Microsoft Office Word et dans les bases de données.</span><span class="sxs-lookup"><span data-stu-id="2dc84-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="2dc84-105">est une approche à jour et repensée de la programmation avec XML.</span><span class="sxs-lookup"><span data-stu-id="2dc84-105">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="2dc84-106">Elle propose les fonctionnalités de modification des documents en mémoire du modèle DOM (Document Objet Model) et prend en charge les expressions de requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2dc84-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="2dc84-107">Bien que ces expressions de requête soient syntaxiquement différentes de XPath, elles procurent la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="2dc84-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="2dc84-108">Développeurs LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="2dc84-108">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="2dc84-109">cible un large éventail de développeurs.</span><span class="sxs-lookup"><span data-stu-id="2dc84-109">targets a variety of developers.</span></span> <span data-ttu-id="2dc84-110">Pour un développeur qui souhaite simplement se faciliter la tâche, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rend le XML plus abordable en fournissant une expérience de requête semblable à SQL.</span><span class="sxs-lookup"><span data-stu-id="2dc84-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="2dc84-111">Un rapide apprentissage permettra aux programmeurs d'écrire des requêtes succinctes et puissantes dans le langage de programmation de leur choix.</span><span class="sxs-lookup"><span data-stu-id="2dc84-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="2dc84-112">Les développeurs professionnels peuvent utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour accroître considérablement leur productivité.</span><span class="sxs-lookup"><span data-stu-id="2dc84-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="2dc84-113">Avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ils peuvent écrire moins de code qui est plus expressif, plus compact et plus puissant.</span><span class="sxs-lookup"><span data-stu-id="2dc84-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="2dc84-114">Ils peuvent utiliser simultanément des expressions de requête de plusieurs domaines de données.</span><span class="sxs-lookup"><span data-stu-id="2dc84-114">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="2dc84-115">Qu'est-ce que LINQ to XML ?</span><span class="sxs-lookup"><span data-stu-id="2dc84-115">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="2dc84-116">est une interface de programmation XML prenant en charge LINQ qui vous permet de travailler avec du code XML dans les langages de programmation .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2dc84-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="2dc84-117">s’apparente au modèle DOM en ce sens qu’il place le document XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="2dc84-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="2dc84-118">Vous pouvez interroger et modifier le document, et après l'avoir modifié, vous pouvez l'enregistrer dans un fichier ou le sérialiser et l'envoyer via Internet.</span><span class="sxs-lookup"><span data-stu-id="2dc84-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="2dc84-119">Cependant, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] diffère du modèle DOM : il fournit un nouveau modèle objet qui est plus léger et plus facile à manipuler, et qui tire parti des fonctionnalités du langage C#.</span><span class="sxs-lookup"><span data-stu-id="2dc84-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="2dc84-120">Le principal avantage de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est son intégration avec [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2dc84-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="2dc84-121">Cette intégration vous permet d'écrire des requêtes sur le document XML en mémoire afin de récupérer des collections d'éléments et d'attributs.</span><span class="sxs-lookup"><span data-stu-id="2dc84-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="2dc84-122">La capacité de requête de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est comparable en terme de fonctionnalités (mais pas en termes de syntaxe) à XQuery et XPath.</span><span class="sxs-lookup"><span data-stu-id="2dc84-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="2dc84-123">L’intégration de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dans C# fournit un typage plus fort, la vérification au moment de la compilation et une prise en charge améliorée du débogueur.</span><span class="sxs-lookup"><span data-stu-id="2dc84-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="2dc84-124">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] présente également l'avantage de pouvoir utiliser des résultats de requête en tant que paramètres de constructeurs d'objets <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute>, ce qui constitue une approche puissante pour la création d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="2dc84-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="2dc84-125">Cette approche, appelée *construction fonctionnelle*, permet aux développeurs de transformer facilement des arborescences XML d’une forme en une autre.</span><span class="sxs-lookup"><span data-stu-id="2dc84-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="2dc84-126">Par exemple, vous pouvez avoir un bon de commande XML standard comme décrit dans [Exemple de fichier XML : Commande fournisseur standard (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="2dc84-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="2dc84-127">En utilisant [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pourriez exécuter la requête suivante afin d'obtenir la valeur d'attribut de numéro de référence pour chaque élément de la commande fournisseur :</span><span class="sxs-lookup"><span data-stu-id="2dc84-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="2dc84-128">Vous pouvez réécrire ceci sous forme d’une syntaxe de méthode :</span><span class="sxs-lookup"><span data-stu-id="2dc84-128">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="2dc84-129">Vous pourriez également, si vous le souhaitez, générer une liste des éléments avec une valeur supérieure à $ 100, triés par numéro de référence.</span><span class="sxs-lookup"><span data-stu-id="2dc84-129">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="2dc84-130">Pour obtenir ces informations, vous pourriez exécuter la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="2dc84-130">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

<span data-ttu-id="2dc84-131">Vous pouvez aussi réécrire ceci sous forme d’une syntaxe de méthode :</span><span class="sxs-lookup"><span data-stu-id="2dc84-131">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="2dc84-132">Outre ces fonctionnalités [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit une interface de programmation XML améliorée.</span><span class="sxs-lookup"><span data-stu-id="2dc84-132">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="2dc84-133">Grâce à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="2dc84-133">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="2dc84-134">charger du code XML à partir de [fichiers](how-to-load-xml-from-a-file.md) ou de [flux](how-to-stream-xml-fragments-from-an-xmlreader.md) ;</span><span class="sxs-lookup"><span data-stu-id="2dc84-134">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="2dc84-135">sérialiser du code XML vers des fichiers ou des flux ;</span><span class="sxs-lookup"><span data-stu-id="2dc84-135">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="2dc84-136">créer du code XML à partir de zéro à l'aide de la construction fonctionnelle ;</span><span class="sxs-lookup"><span data-stu-id="2dc84-136">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="2dc84-137">interroger du code XML à l'aide d'axes de type XPath ;</span><span class="sxs-lookup"><span data-stu-id="2dc84-137">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="2dc84-138">manipuler l'arborescence XML en mémoire à l'aide de méthodes telles que <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> et <xref:System.Xml.Linq.XElement.SetValue%2A> ;</span><span class="sxs-lookup"><span data-stu-id="2dc84-138">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="2dc84-139">valider des arborescences XML à l'aide de XSD ;</span><span class="sxs-lookup"><span data-stu-id="2dc84-139">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="2dc84-140">utiliser une combinaison de ces fonctionnalités pour transformer des arborescences XML d'une forme à une autre.</span><span class="sxs-lookup"><span data-stu-id="2dc84-140">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="2dc84-141">Création d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="2dc84-141">Creating XML Trees</span></span>

<span data-ttu-id="2dc84-142">Un des principaux avantages liés à la programmation avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tient à la facilité de création d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="2dc84-142">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="2dc84-143">Par exemple, pour créer une petite arborescence XML, vous pouvez écrire du code comme suit :</span><span class="sxs-lookup"><span data-stu-id="2dc84-143">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="2dc84-144">Pour plus d’informations, consultez [Création d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="2dc84-144">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2dc84-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dc84-145">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="2dc84-146">Bien démarrer (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2dc84-146">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
