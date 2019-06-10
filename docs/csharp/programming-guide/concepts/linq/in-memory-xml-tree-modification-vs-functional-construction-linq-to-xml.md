---
title: Comparaison de la modification d’arborescence XML en mémoire et de la construction fonctionnelle (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 55eb95585bdd5d2c52175cacae2e6d049bd06f69
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484557"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="0f3c2-102">Comparaison de la modification d’arborescence XML en mémoire et de la construction fonctionnelle (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0f3c2-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0f3c2-103">La modification d'une arborescence XML sur place est une approche traditionnelle de la modification de la forme d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="0f3c2-104">Une application ordinaire charge un document dans un magasin de données tel que DOM ou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], utilise une interface de programmation pour insérer des nœuds, supprimer des nœuds ou modifier le contenu de nœuds, puis enregistre le code XML dans un fichier ou le transmet sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="0f3c2-105">permet d’adopter une autre approche utile dans de nombreux scénarios : la *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-105">enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="0f3c2-106">La construction fonctionnelle traite la modification des données comme un problème de transformation plutôt que comme une manipulation détaillée d'un magasin de données.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="0f3c2-107">Si vous pouvez prendre une représentation de données et la transformer de manière efficace d'une forme en une autre, cela équivaut à prendre un magasin de données et à le manipuler d'une certaine manière de sorte qu'il prenne une autre forme.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="0f3c2-108">L’une des clés de l’approche de construction fonctionnelle consiste à passer les résultats des requêtes à des constructeurs <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="0f3c2-109">Dans de nombreux cas, vous pouvez écrire du code transformationnel en beaucoup moins de temps qu'il ne faudrait pour manipuler le magasin de données, et ce code est plus robuste et plus facile à maintenir.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="0f3c2-110">Dans ces cas-là, bien que l'approche transformationnelle puisse nécessiter davantage de puissance de traitement, elle est plus efficace pour la modification des données.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="0f3c2-111">Si le développeur a une bonne connaissance de l'approche fonctionnelle, le code résultant est bien souvent plus facile à comprendre.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="0f3c2-112">Il est facile de trouver le code qui modifie chaque partie de l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="0f3c2-113">L'approche qui consiste à modifier une arborescence XML sur place est plus connue des programmeurs DOM, tandis que le code écrit à l'aide de l'approche fonctionnelle peut sembler plus obscur aux yeux d'un développeur qui ne s'est pas encore familiarisé avec cette approche.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="0f3c2-114">Si vous ne devez modifier qu'une petite partie d'une grande arborescence XML, la modification de l'arborescence sur place nécessite généralement moins de temps processeur.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="0f3c2-115">Cette rubrique fournit un exemple qui est implémenté avec les deux approches.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="0f3c2-116">Transformation d'attributs en éléments</span><span class="sxs-lookup"><span data-stu-id="0f3c2-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="0f3c2-117">Pour cet exemple, supposez que vous souhaitez modifier le document XML simple suivant de sorte que les attributs deviennent des éléments.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="0f3c2-118">Cette section présente tout d'abord l'approche classique de modification sur place.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="0f3c2-119">Elle illustre ensuite l'approche de construction fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="0f3c2-120">Modification de l'arborescence XML</span><span class="sxs-lookup"><span data-stu-id="0f3c2-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="0f3c2-121">Vous pouvez écrire des procédures de code pour créer des éléments à partir des attributs, puis supprimer les attributs comme suit :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="0f3c2-122">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="0f3c2-123">Approche de construction fonctionnelle</span><span class="sxs-lookup"><span data-stu-id="0f3c2-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="0f3c2-124">Par contraste, une approche fonctionnelle consiste à écrire du code pour former une nouvelle arborescence, à choisir des éléments et des attributs dans l'arborescence source et à les transformer en conséquence à mesure qu'ils sont ajoutés à la nouvelle arborescence.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="0f3c2-125">L'approche fonctionnelle ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="0f3c2-125">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="0f3c2-126">Cet exemple renvoie le même code XML que le premier exemple.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="0f3c2-127">Toutefois, remarquez que vous pouvez observer la structure résultante du nouveau code XML avec l'approche fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="0f3c2-128">Vous pouvez voir la création de l'élément `Root`, le code qui extrait l'élément `Child1` de l'arborescence source et le code qui transforme les attributs de l'arborescence source en éléments dans la nouvelle arborescence.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="0f3c2-129">Dans ce cas, l'exemple fonctionnel n'est pas plus court que le premier exemple et n'est pas vraiment plus simple non plus.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="0f3c2-130">Toutefois, si vous devez apporter de nombreuses modifications à une arborescence XML, l'approche non fonctionnelle devient assez complexe et quelque peu abstruse.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="0f3c2-131">En revanche, avec l'approche fonctionnelle, il suffit toujours de former le code XML souhaité, d'incorporer les requêtes et les expressions, puis d'extraire le contenu souhaité.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="0f3c2-132">L'approche fonctionnelle génère du code qui est plus facile à maintenir.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="0f3c2-133">Notez que dans ce cas les performances obtenues par le biais de l'approche fonctionnelle seraient inférieures à celles de l'approche par manipulation.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="0f3c2-134">Le principal problème est que l'approche fonctionnelle crée davantage d'objets à courte durée de vie.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="0f3c2-135">Toutefois, le compromis est que cette approche autorise une meilleure productivité du programmeur.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="0f3c2-136">Il s'agit d'un exemple très simple, mais qui permet d'illustrer les différences de philosophie de ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="0f3c2-137">L'approche fonctionnelle génère des gains de productivité supérieurs pour la transformation des grands documents XML.</span><span class="sxs-lookup"><span data-stu-id="0f3c2-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  