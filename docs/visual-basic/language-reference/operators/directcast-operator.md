---
title: DirectCast, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 7b070b8eba240440821f7984a9336c2ecaf61706
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867084"
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="5b518-102">Opérateur DirectCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b518-102">DirectCast Operator (Visual Basic)</span></span>

<span data-ttu-id="5b518-103">Introduit une opération de conversion de type en fonction de l’héritage ou de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="5b518-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b518-104">Notes</span><span class="sxs-lookup"><span data-stu-id="5b518-104">Remarks</span></span>  

 <span data-ttu-id="5b518-105">`DirectCast` n’utilise pas les routines d’assistance au moment de l’exécution Visual Basic pour la conversion, afin d’offrir des performances supérieures à celles de la `CType` conversion vers et à partir du type de données `Object` .</span><span class="sxs-lookup"><span data-stu-id="5b518-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="5b518-106">Vous utilisez le `DirectCast` mot clé de la même façon que vous utilisez la [fonction CType](../functions/ctype-function.md) et le mot clé [opérateur TryCast](trycast-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="5b518-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../functions/ctype-function.md) and the [TryCast Operator](trycast-operator.md) keyword.</span></span> <span data-ttu-id="5b518-107">Vous fournissez une expression comme premier argument et un type à convertir en tant que deuxième argument.</span><span class="sxs-lookup"><span data-stu-id="5b518-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="5b518-108">`DirectCast` requiert une relation d’héritage ou d’implémentation entre les types de données des deux arguments.</span><span class="sxs-lookup"><span data-stu-id="5b518-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="5b518-109">Cela signifie qu’un type doit hériter de ou implémenter l’autre.</span><span class="sxs-lookup"><span data-stu-id="5b518-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="5b518-110">Erreurs et échecs</span><span class="sxs-lookup"><span data-stu-id="5b518-110">Errors and Failures</span></span>  

 <span data-ttu-id="5b518-111">`DirectCast` génère une erreur du compilateur s’il détecte qu’il n’existe aucune relation d’héritage ou d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="5b518-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="5b518-112">Toutefois, l’absence d’erreur du compilateur ne garantit pas une conversion réussie.</span><span class="sxs-lookup"><span data-stu-id="5b518-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="5b518-113">Si la conversion souhaitée est restrictive, elle peut échouer au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5b518-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="5b518-114">Dans ce cas, le runtime génère une <xref:System.InvalidCastException> erreur.</span><span class="sxs-lookup"><span data-stu-id="5b518-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="5b518-115">Mots clés de conversion</span><span class="sxs-lookup"><span data-stu-id="5b518-115">Conversion Keywords</span></span>  

 <span data-ttu-id="5b518-116">Une comparaison des mots clés de conversion de type est la suivante.</span><span class="sxs-lookup"><span data-stu-id="5b518-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="5b518-117">Mot clé</span><span class="sxs-lookup"><span data-stu-id="5b518-117">Keyword</span></span>|<span data-ttu-id="5b518-118">Types de données</span><span class="sxs-lookup"><span data-stu-id="5b518-118">Data types</span></span>|<span data-ttu-id="5b518-119">Relation d’argument</span><span class="sxs-lookup"><span data-stu-id="5b518-119">Argument relationship</span></span>|<span data-ttu-id="5b518-120">Échec au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="5b518-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="5b518-121">CType Function</span><span class="sxs-lookup"><span data-stu-id="5b518-121">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="5b518-122">Tous les types de données</span><span class="sxs-lookup"><span data-stu-id="5b518-122">Any data types</span></span>|<span data-ttu-id="5b518-123">La conversion étendue ou restrictive doit être définie entre les deux types de données</span><span class="sxs-lookup"><span data-stu-id="5b518-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="5b518-124">Lève <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="5b518-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="5b518-125">Tous les types de données</span><span class="sxs-lookup"><span data-stu-id="5b518-125">Any data types</span></span>|<span data-ttu-id="5b518-126">Un type doit hériter de ou implémenter l’autre type</span><span class="sxs-lookup"><span data-stu-id="5b518-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="5b518-127">Lève <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="5b518-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="5b518-128">TryCast, opérateur</span><span class="sxs-lookup"><span data-stu-id="5b518-128">TryCast Operator</span></span>](trycast-operator.md)|<span data-ttu-id="5b518-129">Types référence uniquement</span><span class="sxs-lookup"><span data-stu-id="5b518-129">Reference types only</span></span>|<span data-ttu-id="5b518-130">Un type doit hériter de ou implémenter l’autre type</span><span class="sxs-lookup"><span data-stu-id="5b518-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="5b518-131">Retourne [Nothing](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="5b518-131">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b518-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b518-132">Example</span></span>  

 <span data-ttu-id="5b518-133">L’exemple suivant illustre deux utilisations de `DirectCast` , une qui échoue au moment de l’exécution et une qui réussit.</span><span class="sxs-lookup"><span data-stu-id="5b518-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 <span data-ttu-id="5b518-134">Dans l’exemple précédent, le type au moment de l’exécution `q` est `Double` .</span><span class="sxs-lookup"><span data-stu-id="5b518-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="5b518-135">`CType` réussit, car `Double` peut être converti en `Integer` .</span><span class="sxs-lookup"><span data-stu-id="5b518-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="5b518-136">Toutefois, le premier `DirectCast` échoue au moment de l’exécution, car le type d’exécution de `Double` n’a pas de relation d’héritage avec `Integer` , même s’il existe une conversion.</span><span class="sxs-lookup"><span data-stu-id="5b518-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="5b518-137">La deuxième `DirectCast` opération est effectuée, car elle convertit le type <xref:System.Windows.Forms.Form> en type <xref:System.Windows.Forms.Control> , duquel <xref:System.Windows.Forms.Form> hérite.</span><span class="sxs-lookup"><span data-stu-id="5b518-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b518-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b518-138">See also</span></span>

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5b518-139">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="5b518-139">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="5b518-140">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="5b518-140">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
