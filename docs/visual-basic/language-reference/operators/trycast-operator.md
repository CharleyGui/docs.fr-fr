---
title: TryCast, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: dc4807781f9e1aaf894016952911bd7b32c42948
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875323"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="b1fbd-102">Opérateur TryCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1fbd-102">TryCast Operator (Visual Basic)</span></span>

<span data-ttu-id="b1fbd-103">Introduit une opération de conversion de type qui ne lève pas d’exception.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1fbd-104">Notes</span><span class="sxs-lookup"><span data-stu-id="b1fbd-104">Remarks</span></span>  

 <span data-ttu-id="b1fbd-105">Si une tentative de conversion échoue, `CType` et `DirectCast` les deux génèrent une <xref:System.InvalidCastException> erreur.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="b1fbd-106">Cela peut nuire aux performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="b1fbd-107">`TryCast` retourne [Nothing](../nothing.md), de sorte qu’au lieu de devoir gérer une exception possible, vous devez uniquement tester le résultat retourné par rapport à `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="b1fbd-107">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="b1fbd-108">Vous utilisez le `TryCast` mot clé de la même façon que vous utilisez la [fonction CType](../functions/ctype-function.md) et le mot clé d' [opérateur DirectCast](directcast-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="b1fbd-108">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="b1fbd-109">Vous fournissez une expression comme premier argument et un type à convertir en tant que deuxième argument.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="b1fbd-110">`TryCast` fonctionne uniquement sur les types référence, tels que les classes et les interfaces.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="b1fbd-111">Elle nécessite une relation d’héritage ou d’implémentation entre les deux types.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="b1fbd-112">Cela signifie qu’un type doit hériter de ou implémenter l’autre.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="b1fbd-113">Erreurs et échecs</span><span class="sxs-lookup"><span data-stu-id="b1fbd-113">Errors and Failures</span></span>  

 <span data-ttu-id="b1fbd-114">`TryCast` génère une erreur du compilateur s’il détecte qu’il n’existe aucune relation d’héritage ou d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="b1fbd-115">Toutefois, l’absence d’erreur du compilateur ne garantit pas une conversion réussie.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="b1fbd-116">Si la conversion souhaitée est restrictive, elle peut échouer au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="b1fbd-117">Dans ce cas, `TryCast` [ne retourne rien](../nothing.md).</span><span class="sxs-lookup"><span data-stu-id="b1fbd-117">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="b1fbd-118">Mots clés de conversion</span><span class="sxs-lookup"><span data-stu-id="b1fbd-118">Conversion Keywords</span></span>  

 <span data-ttu-id="b1fbd-119">Une comparaison des mots clés de conversion de type est la suivante.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="b1fbd-120">Mot clé</span><span class="sxs-lookup"><span data-stu-id="b1fbd-120">Keyword</span></span>|<span data-ttu-id="b1fbd-121">Types de données</span><span class="sxs-lookup"><span data-stu-id="b1fbd-121">Data types</span></span>|<span data-ttu-id="b1fbd-122">Relation d’argument</span><span class="sxs-lookup"><span data-stu-id="b1fbd-122">Argument relationship</span></span>|<span data-ttu-id="b1fbd-123">Échec au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="b1fbd-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="b1fbd-124">CType Function</span><span class="sxs-lookup"><span data-stu-id="b1fbd-124">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="b1fbd-125">Tous les types de données</span><span class="sxs-lookup"><span data-stu-id="b1fbd-125">Any data types</span></span>|<span data-ttu-id="b1fbd-126">La conversion étendue ou restrictive doit être définie entre les deux types de données</span><span class="sxs-lookup"><span data-stu-id="b1fbd-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="b1fbd-127">Lève <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="b1fbd-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="b1fbd-128">DirectCast, opérateur</span><span class="sxs-lookup"><span data-stu-id="b1fbd-128">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="b1fbd-129">Tous les types de données</span><span class="sxs-lookup"><span data-stu-id="b1fbd-129">Any data types</span></span>|<span data-ttu-id="b1fbd-130">Un type doit hériter de ou implémenter l’autre type</span><span class="sxs-lookup"><span data-stu-id="b1fbd-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="b1fbd-131">Lève <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="b1fbd-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="b1fbd-132">Types référence uniquement</span><span class="sxs-lookup"><span data-stu-id="b1fbd-132">Reference types only</span></span>|<span data-ttu-id="b1fbd-133">Un type doit hériter de ou implémenter l’autre type</span><span class="sxs-lookup"><span data-stu-id="b1fbd-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="b1fbd-134">Retourne [Nothing](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="b1fbd-134">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b1fbd-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1fbd-135">Example</span></span>  

 <span data-ttu-id="b1fbd-136">L'exemple suivant montre comment utiliser `TryCast`.</span><span class="sxs-lookup"><span data-stu-id="b1fbd-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b1fbd-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1fbd-137">See also</span></span>

- [<span data-ttu-id="b1fbd-138">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="b1fbd-138">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="b1fbd-139">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="b1fbd-139">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
