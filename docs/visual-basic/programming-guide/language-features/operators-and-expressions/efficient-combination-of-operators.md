---
title: Association efficace d'opérateurs
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 3088072646278dac13e4d483cb4f99297eaad9ca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403470"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="28d89-102">Association efficace d'opérateurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28d89-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="28d89-103">Les expressions complexes peuvent contenir de nombreux opérateurs différents.</span><span class="sxs-lookup"><span data-stu-id="28d89-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="28d89-104">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="28d89-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="28d89-105">La création d’expressions complexes, telles que celle de l’exemple précédent, requiert une compréhension approfondie des règles de priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="28d89-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="28d89-106">Pour plus d’informations, consultez [priorité des opérateurs dans Visual Basic](../../../language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="28d89-106">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="28d89-107">Expressions entre parenthèses</span><span class="sxs-lookup"><span data-stu-id="28d89-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="28d89-108">Souvent, vous souhaitez que les opérations se déroulent dans un ordre différent de celui déterminé par la priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="28d89-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="28d89-109">Considérez l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="28d89-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="28d89-110">L’exemple précédent multiplie `z` par `y` , puis ajoute le résultat à `4` .</span><span class="sxs-lookup"><span data-stu-id="28d89-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="28d89-111">Toutefois, si vous souhaitez ajouter `y` et `4` avant de multiplier le résultat par `z` , vous pouvez substituer la priorité d’opérateur normale en utilisant des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="28d89-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="28d89-112">En plaçant une expression entre parenthèses, vous forcez l’évaluation de cette expression en premier, quelle que soit la priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="28d89-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="28d89-113">Pour forcer l’exemple précédent à effectuer l’addition en premier, vous pouvez le réécrire comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="28d89-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="28d89-114">L’exemple précédent ajoute `y` et `4` , puis multiplie cette somme par `z` .</span><span class="sxs-lookup"><span data-stu-id="28d89-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="28d89-115">Expressions entre parenthèses imbriquées</span><span class="sxs-lookup"><span data-stu-id="28d89-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="28d89-116">Vous pouvez imbriquer des expressions à plusieurs niveaux de parenthèses pour remplacer la précédence encore plus loin.</span><span class="sxs-lookup"><span data-stu-id="28d89-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="28d89-117">Les expressions les plus profondément imbriquées entre parenthèses sont évaluées en premier, suivies du plus profondément imbriqué, et ainsi de suite jusqu’au moins profondément imbriqué, et enfin des expressions en dehors des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="28d89-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="28d89-118">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="28d89-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="28d89-119">Dans l’exemple précédent, `z + 2` est évalué en premier, puis les autres expressions entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="28d89-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="28d89-120">L’élévation à une puissance, qui a généralement une priorité plus élevée que l’addition ou la multiplication, est évaluée en dernier dans cet exemple car les autres expressions sont placées entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="28d89-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d89-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28d89-121">See also</span></span>

- [<span data-ttu-id="28d89-122">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28d89-122">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="28d89-123">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28d89-123">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="28d89-124">Opérateurs de bits et opérateurs logiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28d89-124">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="28d89-125">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28d89-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="28d89-126">Expressions booléennes</span><span class="sxs-lookup"><span data-stu-id="28d89-126">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="28d89-127">Comparaisons de valeurs</span><span class="sxs-lookup"><span data-stu-id="28d89-127">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="28d89-128">Comment : calculer des valeurs numériques</span><span class="sxs-lookup"><span data-stu-id="28d89-128">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="28d89-129">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28d89-129">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
