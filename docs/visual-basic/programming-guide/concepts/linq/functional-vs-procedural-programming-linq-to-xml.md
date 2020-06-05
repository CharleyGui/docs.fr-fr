---
title: Comparaison entre la programmation fonctionnelle et la programmation procédurale (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 0b525f13298e7402369b890516434cec47e01542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398433"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="5edb5-102">Comparaison entre la programmation fonctionnelle et la programmation procédurale (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5edb5-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="5edb5-103">Il existe différents types d'applications XML :</span><span class="sxs-lookup"><span data-stu-id="5edb5-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="5edb5-104">Certaines applications prennent des documents XML sources et produisent de nouveaux documents XML d'une forme différente des documents sources.</span><span class="sxs-lookup"><span data-stu-id="5edb5-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="5edb5-105">Certaines applications prennent des documents XML sources et produisent des documents d'une forme totalement différente, tels que des fichiers texte CSV ou HTML.</span><span class="sxs-lookup"><span data-stu-id="5edb5-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="5edb5-106">Certaines applications prennent des documents XML sources et insèrent des enregistrements dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="5edb5-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="5edb5-107">Certaines applications prennent des données à partir d'une autre source, telle qu'une base de données, et créent des documents XML à partir de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="5edb5-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="5edb5-108">Il existe d'autres types d'applications XML, mais ceux-ci sont représentatifs des types de fonctionnalités qu'un programmateur XML doit implémenter.</span><span class="sxs-lookup"><span data-stu-id="5edb5-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="5edb5-109">Avec tous ces types d'applications, un développeur peut suivre deux approches contrastées :</span><span class="sxs-lookup"><span data-stu-id="5edb5-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="5edb5-110">Construction fonctionnelle à l'aide d'une approche déclarative.</span><span class="sxs-lookup"><span data-stu-id="5edb5-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="5edb5-111">Modification d'arborescence XML en mémoire à l'aide de procédures de code.</span><span class="sxs-lookup"><span data-stu-id="5edb5-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="5edb5-112">LINQ to XML prend en charge les deux approches.</span><span class="sxs-lookup"><span data-stu-id="5edb5-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="5edb5-113">Lors de l'utilisation de l'approche fonctionnelle, vous écrivez des transformations qui prennent les documents sources et génèrent des documents de résultats complètement nouveaux de la forme souhaitée.</span><span class="sxs-lookup"><span data-stu-id="5edb5-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="5edb5-114">Lors de la modification d'une arborescence XML en place, vous écrivez du code qui traverse et parcourt les nœuds d'une arborescence XML en mémoire, en insérant, supprimant et modifiant des nœuds si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5edb5-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="5edb5-115">Vous pouvez utiliser LINQ to XML avec l'une ou l'autre de ces approches.</span><span class="sxs-lookup"><span data-stu-id="5edb5-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="5edb5-116">Vous utilisez les mêmes classes et, dans certains cas, les mêmes méthodes.</span><span class="sxs-lookup"><span data-stu-id="5edb5-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="5edb5-117">Toutefois, la structure et les objectifs des deux approches sont très différents.</span><span class="sxs-lookup"><span data-stu-id="5edb5-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="5edb5-118">Par exemple, dans différentes situations, l'une ou l'autre approche fournira souvent de meilleures performances et utilisera plus ou moins de mémoire.</span><span class="sxs-lookup"><span data-stu-id="5edb5-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="5edb5-119">En outre, l'une ou l'autre approche sera plus facile à écrire et génèrera du code plus facile à maintenir.</span><span class="sxs-lookup"><span data-stu-id="5edb5-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="5edb5-120">Pour voir les deux approches contrastées, consultez [modification de l’arborescence XML en mémoire par rapport à la construction fonctionnelle (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="5edb5-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="5edb5-121">Pour obtenir un didacticiel sur l’écriture des transformations fonctionnelles, consultez [transformations fonctionnelles pures de XML (Visual Basic)](pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5edb5-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5edb5-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5edb5-122">See also</span></span>

- [<span data-ttu-id="5edb5-123">Vue d’ensemble de la programmation de LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5edb5-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
