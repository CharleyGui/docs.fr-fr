---
title: Order By, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: a7104e3dd82ff2dde2911861ce98a7367faf3b25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350417"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="821be-102">Order By, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="821be-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="821be-103">Spécifie l’ordre de tri des résultats d’une requête.</span><span class="sxs-lookup"><span data-stu-id="821be-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="821be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="821be-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="821be-105">Composants</span><span class="sxs-lookup"><span data-stu-id="821be-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="821be-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="821be-106">Required.</span></span> <span data-ttu-id="821be-107">Un ou plusieurs champs du résultat de la requête actuelle qui identifient la façon dont les valeurs retournées doivent être triées.</span><span class="sxs-lookup"><span data-stu-id="821be-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="821be-108">Les noms de champs doivent être séparés par des virgules (,).</span><span class="sxs-lookup"><span data-stu-id="821be-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="821be-109">Vous pouvez identifier chaque champ comme trié dans l’ordre croissant ou décroissant à l’aide des mots clés `Ascending` ou `Descending`.</span><span class="sxs-lookup"><span data-stu-id="821be-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="821be-110">Si aucun `Ascending` ou `Descending` mot clé n’est spécifié, l’ordre de tri par défaut est croissant.</span><span class="sxs-lookup"><span data-stu-id="821be-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="821be-111">Les champs d’ordre de tri sont prioritaires de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="821be-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="821be-112">Notes</span><span class="sxs-lookup"><span data-stu-id="821be-112">Remarks</span></span>  
 <span data-ttu-id="821be-113">Vous pouvez utiliser la clause `Order By` pour trier les résultats d’une requête.</span><span class="sxs-lookup"><span data-stu-id="821be-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="821be-114">La clause `Order By` peut uniquement trier un résultat en fonction de la variable de portée de l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="821be-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="821be-115">Par exemple, la clause `Select` introduit une nouvelle étendue dans une expression de requête avec de nouvelles variables d’itération pour cette étendue.</span><span class="sxs-lookup"><span data-stu-id="821be-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="821be-116">Les variables de plage définies avant une clause `Select` dans une requête ne sont pas disponibles après la clause `Select`.</span><span class="sxs-lookup"><span data-stu-id="821be-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="821be-117">Par conséquent, si vous souhaitez classer vos résultats par un champ qui n’est pas disponible dans la clause `Select`, vous devez placer la clause `Order By` avant la clause `Select`.</span><span class="sxs-lookup"><span data-stu-id="821be-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="821be-118">C’est le cas, par exemple, lorsque vous souhaitez trier votre requête par champs qui ne sont pas retournés dans le cadre du résultat.</span><span class="sxs-lookup"><span data-stu-id="821be-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="821be-119">L’ordre croissant et décroissant pour un champ est déterminé par l’implémentation de l’interface <xref:System.IComparable> pour le type de données du champ.</span><span class="sxs-lookup"><span data-stu-id="821be-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="821be-120">Si le type de données n’implémente pas l’interface <xref:System.IComparable>, l’ordre de tri est ignoré.</span><span class="sxs-lookup"><span data-stu-id="821be-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="821be-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="821be-121">Example</span></span>  
 <span data-ttu-id="821be-122">L’expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `book` pour la collection de `books`.</span><span class="sxs-lookup"><span data-stu-id="821be-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="821be-123">La clause `Order By` trie le résultat de la requête par prix dans l’ordre croissant (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="821be-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="821be-124">Les livres avec le même prix sont triés par titre dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="821be-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="821be-125">La clause `Select` sélectionne les propriétés `Title` et `Price` comme valeurs retournées par la requête.</span><span class="sxs-lookup"><span data-stu-id="821be-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="821be-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="821be-126">Example</span></span>  
 <span data-ttu-id="821be-127">L’expression de requête suivante utilise la clause `Order By` pour trier le résultat de la requête par prix dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="821be-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="821be-128">Les livres avec le même prix sont triés par titre dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="821be-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="821be-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="821be-129">Example</span></span>  
 <span data-ttu-id="821be-130">L’expression de requête suivante utilise une clause `Select` pour sélectionner le titre, le prix, la date de publication et l’auteur du livre.</span><span class="sxs-lookup"><span data-stu-id="821be-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="821be-131">Il remplit ensuite les champs `Title`, `Price`, `PublishDate`et `Author` de la variable de portée pour la nouvelle portée.</span><span class="sxs-lookup"><span data-stu-id="821be-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="821be-132">La clause `Order By` trie la nouvelle variable de portée par nom d’auteur, titre de livre, puis prix.</span><span class="sxs-lookup"><span data-stu-id="821be-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="821be-133">Chaque colonne est triée dans l’ordre par défaut (croissant).</span><span class="sxs-lookup"><span data-stu-id="821be-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="821be-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="821be-134">See also</span></span>

- [<span data-ttu-id="821be-135">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="821be-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="821be-136">Requêtes</span><span class="sxs-lookup"><span data-stu-id="821be-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="821be-137">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="821be-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="821be-138">From (clause)</span><span class="sxs-lookup"><span data-stu-id="821be-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
