---
title: Vue d’ensemble de LINQ to XML
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: afdec54ac05bb4a631de7fdb599123ffe964c443
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368736"
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="a2037-102">Vue d’ensemble de LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2037-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="a2037-103">Le langage XML a été largement adopté comme méthode pour mettre en forme des données dans de nombreux contextes.</span><span class="sxs-lookup"><span data-stu-id="a2037-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="a2037-104">Par exemple, on trouve du code XML sur le Web, dans les fichiers de configuration, dans les fichiers Microsoft Office Word et dans les bases de données.</span><span class="sxs-lookup"><span data-stu-id="a2037-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="a2037-105">est une approche à jour et repensée de la programmation avec XML.</span><span class="sxs-lookup"><span data-stu-id="a2037-105">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="a2037-106">Il fournit les fonctionnalités de modification de document en mémoire du Document Object Model (DOM) et prend en charge les expressions de requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="a2037-106">It provides the in-memory document-modification capabilities of the Document Object Model (DOM) and supports LINQ query expressions.</span></span> <span data-ttu-id="a2037-107">Bien que ces expressions de requête soient syntaxiquement différentes de XPath, elles procurent la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="a2037-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="a2037-108">Développeurs LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="a2037-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="a2037-109">cible un large éventail de développeurs.</span><span class="sxs-lookup"><span data-stu-id="a2037-109">targets a variety of developers.</span></span> <span data-ttu-id="a2037-110">Pour un développeur qui souhaite simplement se faciliter la tâche, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rend le XML plus abordable en fournissant une expérience de requête semblable à SQL.</span><span class="sxs-lookup"><span data-stu-id="a2037-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="a2037-111">Un rapide apprentissage permettra aux programmeurs d'écrire des requêtes succinctes et puissantes dans le langage de programmation de leur choix.</span><span class="sxs-lookup"><span data-stu-id="a2037-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="a2037-112">Les développeurs professionnels peuvent utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour accroître considérablement leur productivité.</span><span class="sxs-lookup"><span data-stu-id="a2037-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="a2037-113">Avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ils peuvent écrire moins de code qui est plus expressif, plus compact et plus puissant.</span><span class="sxs-lookup"><span data-stu-id="a2037-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="a2037-114">Ils peuvent utiliser simultanément des expressions de requête de plusieurs domaines de données.</span><span class="sxs-lookup"><span data-stu-id="a2037-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="a2037-115">Qu'est-ce que LINQ to XML ?</span><span class="sxs-lookup"><span data-stu-id="a2037-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="a2037-116">est une interface de programmation XML prenant en charge LINQ qui vous permet de travailler avec du code XML dans les langages de programmation .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2037-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="a2037-117">s’apparente au modèle DOM en ce sens qu’il place le document XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a2037-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="a2037-118">Vous pouvez interroger et modifier le document, et après l'avoir modifié, vous pouvez l'enregistrer dans un fichier ou le sérialiser et l'envoyer via Internet.</span><span class="sxs-lookup"><span data-stu-id="a2037-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="a2037-119">Toutefois, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] diffère de DOM : il fournit un nouveau modèle objet qui est plus léger et plus facile à utiliser, et qui tire parti des fonctionnalités de langage dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a2037-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="a2037-120">L’avantage le plus important de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est son intégration avec LINQ (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="a2037-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="a2037-121">Cette intégration vous permet d'écrire des requêtes sur le document XML en mémoire afin de récupérer des collections d'éléments et d'attributs.</span><span class="sxs-lookup"><span data-stu-id="a2037-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="a2037-122">La capacité de requête de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est comparable en terme de fonctionnalités (mais pas en termes de syntaxe) à XQuery et XPath.</span><span class="sxs-lookup"><span data-stu-id="a2037-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="a2037-123">L’intégration de LINQ dans Visual Basic fournit un typage plus fort, une vérification au moment de la compilation et une prise en charge améliorée du débogueur.</span><span class="sxs-lookup"><span data-stu-id="a2037-123">The integration of LINQ in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="a2037-124">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] présente également l'avantage de pouvoir utiliser des résultats de requête en tant que paramètres de constructeurs d'objets <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XAttribute>, ce qui constitue une approche puissante pour la création d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="a2037-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="a2037-125">Cette approche, appelée *construction fonctionnelle*, permet aux développeurs de transformer facilement des arborescences XML d’une forme en une autre.</span><span class="sxs-lookup"><span data-stu-id="a2037-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="a2037-126">Par exemple, vous pouvez avoir un bon de commande XML classique comme décrit dans [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a2037-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span> <span data-ttu-id="a2037-127">En utilisant [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pourriez exécuter la requête suivante afin d'obtenir la valeur d'attribut de numéro de référence pour chaque élément de la commande fournisseur :</span><span class="sxs-lookup"><span data-stu-id="a2037-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="a2037-128">Vous pourriez également, si vous le souhaitez, générer une liste des éléments avec une valeur supérieure à $ 100, triés par numéro de référence.</span><span class="sxs-lookup"><span data-stu-id="a2037-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="a2037-129">Pour obtenir ces informations, vous pourriez exécuter la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="a2037-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="a2037-130">Outre ces fonctionnalités LINQ, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fournit une interface de programmation XML améliorée.</span><span class="sxs-lookup"><span data-stu-id="a2037-130">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="a2037-131">Grâce à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="a2037-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
- <span data-ttu-id="a2037-132">charger du code XML à partir de fichiers ou de flux ;</span><span class="sxs-lookup"><span data-stu-id="a2037-132">Load XML from files or streams.</span></span>  
  
- <span data-ttu-id="a2037-133">sérialiser du code XML vers des fichiers ou des flux ;</span><span class="sxs-lookup"><span data-stu-id="a2037-133">Serialize XML to files or streams.</span></span>  
  
- <span data-ttu-id="a2037-134">créer du code XML à partir de zéro à l'aide de la construction fonctionnelle ;</span><span class="sxs-lookup"><span data-stu-id="a2037-134">Create XML from scratch by using functional construction.</span></span>  
  
- <span data-ttu-id="a2037-135">interroger du code XML à l’aide d’axes de type XPath ;</span><span class="sxs-lookup"><span data-stu-id="a2037-135">Query XML using XPath-like axes.</span></span>  
  
- <span data-ttu-id="a2037-136">manipuler l'arborescence XML en mémoire à l'aide de méthodes telles que <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> et <xref:System.Xml.Linq.XElement.SetValue%2A> ;</span><span class="sxs-lookup"><span data-stu-id="a2037-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
- <span data-ttu-id="a2037-137">valider des arborescences XML à l'aide de XSD ;</span><span class="sxs-lookup"><span data-stu-id="a2037-137">Validate XML trees using XSD.</span></span>  
  
- <span data-ttu-id="a2037-138">utiliser une combinaison de ces fonctionnalités pour transformer des arborescences XML d'une forme à une autre.</span><span class="sxs-lookup"><span data-stu-id="a2037-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="a2037-139">Création d'arborescences XML</span><span class="sxs-lookup"><span data-stu-id="a2037-139">Creating XML Trees</span></span>  
 <span data-ttu-id="a2037-140">L'un des principaux avantages liés à la programmation avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tient à la facilité de création d'arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="a2037-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="a2037-141">Par exemple, pour créer une petite arborescence XML, vous pouvez écrire du code comme suit :</span><span class="sxs-lookup"><span data-stu-id="a2037-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 <span data-ttu-id="a2037-142">Le compilateur de Visual Basic traduit les littéraux XML en [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="a2037-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="a2037-143">Pour plus d’informations, consultez [création d’arborescences XML (Visual Basic)](creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="a2037-143">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2037-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2037-144">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="a2037-145">Mise en route (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a2037-145">Getting Started (LINQ to XML)</span></span>](getting-started-linq-to-xml.md)
- [<span data-ttu-id="a2037-146">Vue d’ensemble de LINQ to XML en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2037-146">Overview of LINQ to XML in Visual Basic</span></span>](../../language-features/xml/overview-of-linq-to-xml.md)
- [<span data-ttu-id="a2037-147">XML</span><span class="sxs-lookup"><span data-stu-id="a2037-147">XML</span></span>](../../language-features/xml/index.md)
