---
title: Programmation fonctionnelle et programmation de procédures
description: LINQ to XML prend en charge la construction fonctionnelle et les techniques procédurales pour la création d’applications XML. La construction fonctionnelle est une approche déclarative. Les techniques procédurales prennent en charge la modification en mémoire des arborescences XML.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: a2753a31e88fd338dad61063f559431869b9e17f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552436"
---
# <a name="functional-vs-procedural-programming-linq-to-xml"></a><span data-ttu-id="e9850-105">Comparaison entre la programmation fonctionnelle et la programmation procédurale (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e9850-105">Functional vs. procedural programming (LINQ to XML)</span></span>

<span data-ttu-id="e9850-106">Il existe différents types d'applications XML :</span><span class="sxs-lookup"><span data-stu-id="e9850-106">There are various types of XML applications:</span></span>

- <span data-ttu-id="e9850-107">Certaines applications prennent des documents XML sources et produisent de nouveaux documents XML d'une forme différente des documents sources.</span><span class="sxs-lookup"><span data-stu-id="e9850-107">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>
- <span data-ttu-id="e9850-108">Certaines applications prennent des documents XML sources et produisent des documents d'une forme totalement différente, tels que des fichiers texte CSV ou HTML.</span><span class="sxs-lookup"><span data-stu-id="e9850-108">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>
- <span data-ttu-id="e9850-109">Certaines applications prennent des documents XML sources et insèrent des enregistrements dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="e9850-109">Some applications take source XML documents, and insert records into a database.</span></span>
- <span data-ttu-id="e9850-110">Certaines applications prennent des données à partir d'une autre source, telle qu'une base de données, et créent des documents XML à partir de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="e9850-110">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>

<span data-ttu-id="e9850-111">Il ne s’agit pas de tous les types d’applications XML, mais il s’agit d’un ensemble représentatif des types de fonctionnalités qu’un programmeur XML doit implémenter.</span><span class="sxs-lookup"><span data-stu-id="e9850-111">These aren't all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>

<span data-ttu-id="e9850-112">Avec tous ces types d'applications, un développeur peut suivre deux approches contrastées :</span><span class="sxs-lookup"><span data-stu-id="e9850-112">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>

- <span data-ttu-id="e9850-113">Construction fonctionnelle à l'aide d'une approche déclarative.</span><span class="sxs-lookup"><span data-stu-id="e9850-113">Functional construction using a declarative approach.</span></span>
- <span data-ttu-id="e9850-114">Modification d'arborescence XML en mémoire à l'aide de procédures de code.</span><span class="sxs-lookup"><span data-stu-id="e9850-114">In-memory XML tree modification using procedural code.</span></span>

<span data-ttu-id="e9850-115">LINQ to XML prend en charge les deux approches.</span><span class="sxs-lookup"><span data-stu-id="e9850-115">LINQ to XML supports both approaches.</span></span>

<span data-ttu-id="e9850-116">Lors de l'utilisation de l'approche fonctionnelle, vous écrivez des transformations qui prennent les documents sources et génèrent des documents de résultats complètement nouveaux de la forme souhaitée.</span><span class="sxs-lookup"><span data-stu-id="e9850-116">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>

<span data-ttu-id="e9850-117">Lors de la modification d'une arborescence XML en place, vous écrivez du code qui traverse et parcourt les nœuds d'une arborescence XML en mémoire, en insérant, supprimant et modifiant des nœuds si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e9850-117">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>

<span data-ttu-id="e9850-118">Vous pouvez utiliser LINQ to XML avec l'une ou l'autre de ces approches.</span><span class="sxs-lookup"><span data-stu-id="e9850-118">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="e9850-119">Vous utilisez les mêmes classes et, dans certains cas, les mêmes méthodes.</span><span class="sxs-lookup"><span data-stu-id="e9850-119">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="e9850-120">Toutefois, la structure et les objectifs des deux approches sont différents.</span><span class="sxs-lookup"><span data-stu-id="e9850-120">However, the structure and goals of the two approaches are different.</span></span> <span data-ttu-id="e9850-121">Par exemple, dans différentes situations, l'une ou l'autre approche fournira souvent de meilleures performances et utilisera plus ou moins de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e9850-121">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="e9850-122">En outre, l'une ou l'autre approche sera plus facile à écrire et génèrera du code plus facile à maintenir.</span><span class="sxs-lookup"><span data-stu-id="e9850-122">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>

<span data-ttu-id="e9850-123">Pour voir les deux approches contrastées, consultez [modification de l’arborescence XML en mémoire par rapport à la construction fonctionnelle](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="e9850-123">To see the two approaches contrasted, see [In-memory XML tree modification vs. functional construction](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

<span data-ttu-id="e9850-124">Pour obtenir un didacticiel sur l’écriture des transformations fonctionnelles, consultez [Introduction aux transformations fonctionnelles pures](introduction-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="e9850-124">For a tutorial on writing functional transformations, see [Introduction to pure functional transformations](introduction-pure-functional-transformations.md).</span></span>
