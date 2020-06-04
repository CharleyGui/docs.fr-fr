---
title: Where (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359539"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="e680c-102">Where, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e680c-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="e680c-103">Spécifie la condition de filtrage pour une requête.</span><span class="sxs-lookup"><span data-stu-id="e680c-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e680c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e680c-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="e680c-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="e680c-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="e680c-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e680c-106">Required.</span></span> <span data-ttu-id="e680c-107">Expression qui détermine si les valeurs de l’élément actuel dans la collection sont incluses dans la collection de sortie.</span><span class="sxs-lookup"><span data-stu-id="e680c-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="e680c-108">L’expression doit correspondre à une `Boolean` valeur ou à l’équivalent d’une `Boolean` valeur.</span><span class="sxs-lookup"><span data-stu-id="e680c-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="e680c-109">Si la condition a la valeur `True` , l’élément est inclus dans le résultat de la requête ; sinon, l’élément est exclu du résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="e680c-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e680c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e680c-110">Remarks</span></span>  
 <span data-ttu-id="e680c-111">La `Where` clause vous permet de filtrer les données de requête en sélectionnant uniquement les éléments qui répondent à certains critères.</span><span class="sxs-lookup"><span data-stu-id="e680c-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="e680c-112">Les éléments dont les valeurs provoquent l’évaluation de la `Where` clause `True` sont inclus dans le résultat de la requête ; d’autres éléments sont exclus.</span><span class="sxs-lookup"><span data-stu-id="e680c-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="e680c-113">L’expression utilisée dans une `Where` clause doit avoir la `Boolean` valeur ou l’équivalent d’un `Boolean` , tel qu’un entier qui prend la `False` valeur lorsque sa valeur est égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="e680c-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="e680c-114">Vous pouvez combiner plusieurs expressions dans une `Where` clause à l’aide d’opérateurs logiques tels que,,,, `And` `Or` `AndAlso` `OrElse` `Is` et `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="e680c-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="e680c-115">Par défaut, les expressions de requête ne sont pas évaluées tant qu’elles ne sont pas accessibles, par exemple lorsqu’elles sont liées aux données ou itérées dans une `For` boucle.</span><span class="sxs-lookup"><span data-stu-id="e680c-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="e680c-116">Par conséquent, la `Where` clause n’est pas évaluée tant que la requête n’est pas accédée.</span><span class="sxs-lookup"><span data-stu-id="e680c-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="e680c-117">Si vous avez des valeurs externes à la requête utilisées dans la `Where` clause, assurez-vous que la valeur appropriée est utilisée dans la `Where` clause au moment de l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="e680c-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="e680c-118">Pour plus d’informations sur l’exécution des requêtes, consultez [écriture de votre première requête LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="e680c-118">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="e680c-119">Vous pouvez appeler des fonctions dans une `Where` clause pour effectuer un calcul ou une opération sur une valeur de l’élément actuel dans la collection.</span><span class="sxs-lookup"><span data-stu-id="e680c-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="e680c-120">L’appel d’une fonction dans une `Where` clause peut entraîner l’exécution immédiate de la requête lorsqu’elle est définie au lieu de l’accès.</span><span class="sxs-lookup"><span data-stu-id="e680c-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="e680c-121">Pour plus d’informations sur l’exécution des requêtes, consultez [écriture de votre première requête LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="e680c-121">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e680c-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="e680c-122">Example</span></span>  
 <span data-ttu-id="e680c-123">L’expression de requête suivante utilise une `From` clause pour déclarer une variable `cust` de portée pour chaque `Customer` objet de la `customers` collection.</span><span class="sxs-lookup"><span data-stu-id="e680c-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="e680c-124">La `Where` clause utilise la variable de portée pour limiter la sortie aux clients de la région spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e680c-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="e680c-125">La `For Each` boucle affiche le nom de la société pour chaque client dans le résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="e680c-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="e680c-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="e680c-126">Example</span></span>  
 <span data-ttu-id="e680c-127">L’exemple suivant utilise `And` les `Or` opérateurs logiques et dans la `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="e680c-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="e680c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e680c-128">See also</span></span>

- [<span data-ttu-id="e680c-129">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e680c-129">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="e680c-130">Requêtes</span><span class="sxs-lookup"><span data-stu-id="e680c-130">Queries</span></span>](index.md)
- [<span data-ttu-id="e680c-131">From, clause</span><span class="sxs-lookup"><span data-stu-id="e680c-131">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="e680c-132">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="e680c-132">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="e680c-133">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="e680c-133">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
