---
title: Vue d’ensemble des arborescences XML de requête-LINQ to XML
description: Découvrez comment interroger une arborescence XML et comment combiner une requête et une construction fonctionnelle pour reformer une arborescence.
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 3529650aa5ee0575331653f5714c841d1fc1dfb5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553706"
---
# <a name="query-xml-trees-overview-linq-to-xml"></a><span data-ttu-id="d8f12-103">Vue d’ensemble de la requête d’arborescences XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d8f12-103">Query XML trees overview (LINQ to XML)</span></span>

<span data-ttu-id="d8f12-104">Une fois que vous avez instancié une arborescence XML, l’écriture de requêtes est le moyen le plus efficace pour extraire des données de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="d8f12-104">After you've instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="d8f12-105">De plus, l'interrogation combinée à la construction fonctionnelle vous permet de générer un nouveau document XML qui possède une forme différente du document d'origine.</span><span class="sxs-lookup"><span data-stu-id="d8f12-105">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>

<span data-ttu-id="d8f12-106">Pour obtenir des informations générales sur les requêtes LINQ, consultez :</span><span class="sxs-lookup"><span data-stu-id="d8f12-106">For background information about LINQ queries, see:</span></span>

- [<span data-ttu-id="d8f12-107">Introduction aux requêtes LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="d8f12-107">Introduction to LINQ Queries (C#)</span></span>](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [<span data-ttu-id="d8f12-108">Écriture de votre première requête LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8f12-108">Writing Your First LINQ Query (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)

## <a name="in-this-section"></a><span data-ttu-id="d8f12-109">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="d8f12-109">In this section</span></span>

<span data-ttu-id="d8f12-110">Cette section d’articles fournit des informations, notamment des exemples, sur les requêtes LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="d8f12-110">This section of articles provides information, including examples, about LINQ to XML queries.</span></span> <span data-ttu-id="d8f12-111">Il comprend les sous-sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8f12-111">It comprises the following subsections:</span></span>

|<span data-ttu-id="d8f12-112">Article</span><span class="sxs-lookup"><span data-stu-id="d8f12-112">Article</span></span>|<span data-ttu-id="d8f12-113">Description</span><span class="sxs-lookup"><span data-stu-id="d8f12-113">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="d8f12-114">Requêtes de base</span><span class="sxs-lookup"><span data-stu-id="d8f12-114">Basic queries</span></span>](find-element-specific-attribute.md)|<span data-ttu-id="d8f12-115">Fournit des exemples courants d’interrogation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="d8f12-115">Provides common examples of querying XML trees.</span></span>|
|[<span data-ttu-id="d8f12-116">Projections et transformations</span><span class="sxs-lookup"><span data-stu-id="d8f12-116">Projections and transformations</span></span>](work-dictionaries-linq-xml.md)|<span data-ttu-id="d8f12-117">Fournit des exemples courants de projection à partir d’arborescences XML et de transformation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="d8f12-117">Provides common examples of projecting from and transforming XML trees.</span></span>|
|[<span data-ttu-id="d8f12-118">Techniques de requêtes avancées</span><span class="sxs-lookup"><span data-stu-id="d8f12-118">Advanced query techniques</span></span>](join-two-collections.md)|<span data-ttu-id="d8f12-119">Fournit des techniques d'interrogation utiles dans les scénarios plus avancés.</span><span class="sxs-lookup"><span data-stu-id="d8f12-119">Provides query techniques that are useful in more advanced scenarios.</span></span>|
|[<span data-ttu-id="d8f12-120">LINQ to XML pour les utilisateurs XPath</span><span class="sxs-lookup"><span data-stu-id="d8f12-120">LINQ to XML for XPath users</span></span>](comparison-xpath-linq-xml.md)|<span data-ttu-id="d8f12-121">Présente un certain nombre d’expressions XPath et leurs équivalents LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="d8f12-121">Presents a number of XPath expressions and their LINQ to XML equivalents.</span></span>|
|[<span data-ttu-id="d8f12-122">Présentation des transformations fonctionnelles pures</span><span class="sxs-lookup"><span data-stu-id="d8f12-122">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)|<span data-ttu-id="d8f12-123">Présente un petit didacticiel sur l'écriture des requêtes dans le style de programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="d8f12-123">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d8f12-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8f12-124">See also</span></span>

- [<span data-ttu-id="d8f12-125">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="d8f12-125">Language-Integrated Query (LINQ) (C#)</span></span>](../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d8f12-126">Introduction aux requêtes LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="d8f12-126">Introduction to LINQ Queries (C#)</span></span>](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [<span data-ttu-id="d8f12-127">LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8f12-127">LINQ in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="d8f12-128">LINQ (Language-Integrated Query) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8f12-128">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d8f12-129">Mise en route de LINQ dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8f12-129">Getting Started with LINQ in Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="d8f12-130">Écriture de votre première requête LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8f12-130">Writing Your First LINQ Query (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)
