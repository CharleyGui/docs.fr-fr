---
title: Modification de l’arborescence XML en mémoire par rapport à la construction fonctionnelle-LINQ to XML
description: Consultez des exemples de deux approches différentes pour modifier des arborescences XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 71f76d12024bb07cf90df2299df14646ae271b47
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552420"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml"></a><span data-ttu-id="6c0e6-103">Modification de l’arborescence XML en mémoire par rapport à la construction fonctionnelle (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6c0e6-103">In-memory XML tree modification vs. functional construction (LINQ to XML)</span></span>

<span data-ttu-id="6c0e6-104">La modification d'une arborescence XML sur place est une approche traditionnelle de la modification de la forme d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="6c0e6-105">Une application typique charge un document dans un magasin de données tel que DOM ou LINQ to XML ; utilise une interface de programmation pour insérer ou supprimer des nœuds, ou modifier leur contenu ; puis enregistre le code XML dans un fichier ou le transmet sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-105">A typical application loads a document into a data store such as DOM or LINQ to XML; uses a programming interface to insert or delete nodes, or change their content; and then saves the XML to a file or transmits it over a network.</span></span>

<span data-ttu-id="6c0e6-106">LINQ to XML offre une autre approche utile dans de nombreux scénarios : la *construction fonctionnelle*.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-106">LINQ to XML enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="6c0e6-107">La construction fonctionnelle traite la modification des données comme un problème de transformation plutôt que comme une manipulation détaillée d'un magasin de données.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="6c0e6-108">Si vous pouvez prendre une représentation de données et la transformer de manière efficace d'une forme en une autre, cela équivaut à prendre un magasin de données et à le manipuler d'une certaine manière de sorte qu'il prenne une autre forme.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="6c0e6-109">L’une des clés de l’approche de construction fonctionnelle consiste à passer les résultats des requêtes à des constructeurs <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>

<span data-ttu-id="6c0e6-110">Dans de nombreux cas, vous pouvez écrire le code de transformation dans une fraction du temps qu’il faudrait pour manipuler le magasin de données, et le code obtenu est plus robuste et plus facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and the resulting code is more robust and easier to maintain.</span></span> <span data-ttu-id="6c0e6-111">Dans ce cas, bien que l’approche transformationnelle puisse nécessiter davantage de puissance de traitement, il est plus efficace de modifier les données.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-111">In these cases, even though the transformational approach can take more processing power, it's a more effective way to modify data.</span></span> <span data-ttu-id="6c0e6-112">Si un développeur est familiarisé avec l’approche fonctionnelle, le code résultant dans de nombreux cas est plus facile à comprendre et il est facile de trouver le code qui modifie chaque partie de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand, and it's easy to find the code that modifies each part of the tree.</span></span>

<span data-ttu-id="6c0e6-113">L’approche qui consiste à modifier une arborescence XML sur place est plus familière à de nombreux programmeurs DOM, tandis que le code écrit à l’aide de l’approche fonctionnelle peut sembler peu familier à un développeur qui n’a pas encore compris cette approche.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-113">The approach where you modify an XML tree in place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="6c0e6-114">Si vous ne devez modifier qu'une petite partie d'une grande arborescence XML, la modification de l'arborescence sur place nécessite généralement moins de temps processeur.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>

<span data-ttu-id="6c0e6-115">Cet article fournit des exemples des deux approches.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-115">This article provides examples of both approaches.</span></span> <span data-ttu-id="6c0e6-116">Supposons que vous souhaitiez modifier le document XML simple suivant de sorte que les attributs deviennent des éléments :</span><span class="sxs-lookup"><span data-stu-id="6c0e6-116">Suppose you want to modify the following simple XML document so that the attributes become elements:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root Data1="123" Data2="456">
  <Child1>Content</Child1>
</Root>
```

<span data-ttu-id="6c0e6-117">Le premier des exemples suivants utilise l’approche traditionnelle de modification sur place, tandis que la seconde utilise l’approche de construction fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-117">The first of the following examples uses the traditional in-place modification approach, and the second uses the functional construction approach.</span></span>

## <a name="example-transform-attributes-into-elements-with-the-traditional-in-place-approach"></a><span data-ttu-id="6c0e6-118">Exemple : transformer des attributs en éléments avec l’approche sur place traditionnelle</span><span class="sxs-lookup"><span data-stu-id="6c0e6-118">Example: Transform attributes into elements with the traditional in-place approach</span></span>

<span data-ttu-id="6c0e6-119">Vous pouvez écrire des procédures de code pour créer des éléments à partir des attributs, puis supprimer les attributs comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c0e6-119">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
foreach (XAttribute att in root.Attributes()) {
    root.Add(new XElement(att.Name, (string)att));
}
root.Attributes().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
For Each att As XAttribute In root.Attributes()
    root.Add(New XElement(att.Name, att.Value))
Next
root.Attributes().Remove()
Console.WriteLine(root)
```

<span data-ttu-id="6c0e6-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6c0e6-120">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Content</Child1>
  <Data1>123</Data1>
  <Data2>456</Data2>
</Root>
```

## <a name="example-transform-attributes-into-elements-with-the-functional-construction-approach"></a><span data-ttu-id="6c0e6-121">Exemple : transformer des attributs en éléments avec l’approche de construction fonctionnelle</span><span class="sxs-lookup"><span data-stu-id="6c0e6-121">Example: Transform attributes into elements with the functional construction approach</span></span>

<span data-ttu-id="6c0e6-122">En revanche, une approche fonctionnelle consiste à coder pour former une nouvelle arborescence, à choisir des éléments et des attributs à partir de l’arborescence source et à les transformer en fonction des besoins lorsqu’ils sont ajoutés à la nouvelle arborescence.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-122">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they're added to the new tree.</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
XElement newTree = new XElement("Root",
    root.Element("Child1"),
    from att in root.Attributes()
    select new XElement(att.Name, (string)att)
);
Console.WriteLine(newTree);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim newTree As XElement = _
    <Root>
        <%= root.<Child1> %>
        <%= From att In root.Attributes() _
            Select New XElement(att.Name, att.Value) %>
    </Root>
Console.WriteLine(newTree)
```

<span data-ttu-id="6c0e6-123">Cet exemple renvoie le même code XML que le premier exemple.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-123">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="6c0e6-124">Toutefois, remarquez que vous pouvez observer la structure résultante du nouveau code XML avec l'approche fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-124">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="6c0e6-125">Vous pouvez voir la création de l'élément `Root`, le code qui extrait l'élément `Child1` de l'arborescence source et le code qui transforme les attributs de l'arborescence source en éléments dans la nouvelle arborescence.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-125">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>

<span data-ttu-id="6c0e6-126">Dans ce cas, l’exemple fonctionnel n’est ni plus rapide ni plus simple que le premier exemple.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-126">The functional example in this case is neither shorter nor simpler than the first example.</span></span> <span data-ttu-id="6c0e6-127">Toutefois, si vous avez de nombreuses modifications à apporter à une arborescence XML, l’approche procédurale devient assez complexe et quelque peu abstruse.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-127">However, if you have many changes to make to an XML tree, the procedural approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="6c0e6-128">En revanche, avec l'approche fonctionnelle, il suffit toujours de former le code XML souhaité, d'incorporer les requêtes et les expressions, puis d'extraire le contenu souhaité.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-128">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="6c0e6-129">L'approche fonctionnelle génère du code qui est plus facile à maintenir.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-129">The functional approach yields code that is easier to maintain.</span></span>

<span data-ttu-id="6c0e6-130">Notez que dans ce cas les performances obtenues par le biais de l'approche fonctionnelle seraient inférieures à celles de l'approche par manipulation.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-130">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="6c0e6-131">Le principal problème est que l’approche fonctionnelle crée davantage d’objets éphémères.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-131">The main issue is that the functional approach creates more short-lived objects.</span></span> <span data-ttu-id="6c0e6-132">Toutefois, le compromis est que cette approche autorise une meilleure productivité du programmeur.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-132">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>

<span data-ttu-id="6c0e6-133">Il s'agit d'un exemple très simple, mais qui permet d'illustrer les différences de philosophie de ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-133">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="6c0e6-134">L'approche fonctionnelle génère des gains de productivité supérieurs pour la transformation des grands documents XML.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-134">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>
