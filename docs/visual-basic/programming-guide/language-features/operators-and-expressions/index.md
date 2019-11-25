---
title: Opérateurs et expressions
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: fa410a739be2da8802e76a35068448263ddec1fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343609"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="d860b-102">Opérateurs et expressions en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d860b-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="d860b-103">Un *opérateur* est un élément de code qui exécute une opération sur un ou plusieurs éléments de code qui contiennent des valeurs.</span><span class="sxs-lookup"><span data-stu-id="d860b-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="d860b-104">Les éléments de valeur comprennent des variables, des constantes, des littéraux, des propriétés, des expressions et des retours provenant des procédures `Function` et `Operator`.</span><span class="sxs-lookup"><span data-stu-id="d860b-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="d860b-105">Une *expression* est une série d’éléments de valeur combinés à des opérateurs, ce qui retourne une nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="d860b-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="d860b-106">Les opérateurs agissent sur les éléments de valeur en effectuant des calculs, des comparaisons et d’autres opérations.</span><span class="sxs-lookup"><span data-stu-id="d860b-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="d860b-107">Types d’opérateurs</span><span class="sxs-lookup"><span data-stu-id="d860b-107">Types of Operators</span></span>  
 <span data-ttu-id="d860b-108">Visual Basic provides the following types of operators:</span><span class="sxs-lookup"><span data-stu-id="d860b-108">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="d860b-109">Les [opérateurs arithmétiques](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) exécutent des calculs familiers sur les valeurs numériques, dont le décalage de leurs modèles binaires.</span><span class="sxs-lookup"><span data-stu-id="d860b-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="d860b-110">Les [opérateurs de comparaison](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) comparent deux expressions et retournent une valeur `Boolean` représentant le résultat de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="d860b-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="d860b-111">Les [opérateurs de concaténation](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) joignent plusieurs chaînes dans une seule.</span><span class="sxs-lookup"><span data-stu-id="d860b-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="d860b-112">Les [opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combinent des valeurs `Boolean` ou numériques, et retournent un résultat du même type de données que les valeurs.</span><span class="sxs-lookup"><span data-stu-id="d860b-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="d860b-113">Les éléments de valeur associés à un opérateur sont appelés *opérandes* de cet opérateur.</span><span class="sxs-lookup"><span data-stu-id="d860b-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="d860b-114">Les opérateurs associés aux éléments de valeur forment des expressions, à l’exception de l’opérateur d’assignation qui forme une *instruction*.</span><span class="sxs-lookup"><span data-stu-id="d860b-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="d860b-115">Pour plus d’informations, consultez [Instructions](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="d860b-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="d860b-116">Évaluation d’expressions</span><span class="sxs-lookup"><span data-stu-id="d860b-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="d860b-117">Le résultat final d’une expression représente une valeur qui correspond généralement à un type de données familier tel que `Boolean`, `String` ou à un type numérique.</span><span class="sxs-lookup"><span data-stu-id="d860b-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="d860b-118">Voici des exemples d’expressions.</span><span class="sxs-lookup"><span data-stu-id="d860b-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="d860b-119">Plusieurs opérateurs peuvent effectuer des actions dans une expression ou instruction unique, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d860b-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="d860b-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span><span class="sxs-lookup"><span data-stu-id="d860b-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="d860b-121">Dans la pratique, le nombre d’opérateurs pouvant être combinés dans une expression est illimité, mais il est nécessaire de comprendre la [Priorité des opérateurs en Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) pour garantir l’obtention des résultats attendus.</span><span class="sxs-lookup"><span data-stu-id="d860b-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d860b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d860b-122">See also</span></span>

- [<span data-ttu-id="d860b-123">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="d860b-123">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="d860b-124">Association efficace d’opérateurs</span><span class="sxs-lookup"><span data-stu-id="d860b-124">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="d860b-125">Instructions</span><span class="sxs-lookup"><span data-stu-id="d860b-125">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
