---
title: Interrogation d’arborescences XML
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 643b19a0cfcd2a81c6f685de65979f83ca32d918
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636898"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="5247d-102">Interrogation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5247d-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="5247d-103">Cette section fournit des exemples de requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5247d-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="5247d-104">Pour plus d’informations sur l’écriture de requêtes LINQ, consultez [prise en main avec LINQ dans Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="5247d-104">For more information about writing LINQ queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="5247d-105">Une fois que vous avez instancié une arborescence XML, l’écriture de requêtes est le moyen le plus efficace pour extraire des données de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="5247d-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="5247d-106">De plus, l'interrogation combinée à la construction fonctionnelle vous permet de générer un nouveau document XML qui possède une forme différente du document d'origine.</span><span class="sxs-lookup"><span data-stu-id="5247d-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5247d-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5247d-107">In This Section</span></span>  
  
|<span data-ttu-id="5247d-108">Rubrique</span><span class="sxs-lookup"><span data-stu-id="5247d-108">Topic</span></span>|<span data-ttu-id="5247d-109">Description</span><span class="sxs-lookup"><span data-stu-id="5247d-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5247d-110">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5247d-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="5247d-111">Fournit des exemples courants d’interrogation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="5247d-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="5247d-112">Projections et transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5247d-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="5247d-113">Fournit des exemples courants de projection à partir d’arborescences XML et de transformation d’arborescences XML.</span><span class="sxs-lookup"><span data-stu-id="5247d-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="5247d-114">Techniques de requêtes avancées (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5247d-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="5247d-115">Fournit des techniques d'interrogation utiles dans les scénarios plus avancés.</span><span class="sxs-lookup"><span data-stu-id="5247d-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="5247d-116">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5247d-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="5247d-117">Présente un certain nombre d’expressions XPath et leurs équivalents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5247d-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="5247d-118">Transformations fonctionnelles pures de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5247d-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="5247d-119">Présente un petit didacticiel sur l'écriture des requêtes dans le style de programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="5247d-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5247d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5247d-120">See also</span></span>

- [<span data-ttu-id="5247d-121">Guide de programmation (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5247d-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
- [<span data-ttu-id="5247d-122">Bien démarrer avec LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5247d-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
