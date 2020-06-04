---
title: 'Comment : calculer des valeurs numériques'
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: 94b02693f308dcfcfa6983f2750a26d9d419f7be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403457"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="768ce-102">Comment : calculer des valeurs numériques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="768ce-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="768ce-103">Vous pouvez calculer des valeurs numériques à l’aide d’expressions numériques.</span><span class="sxs-lookup"><span data-stu-id="768ce-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="768ce-104">Une *expression numérique* est une expression qui contient des littéraux, des constantes et des variables représentant des valeurs numériques, ainsi que des opérateurs qui agissent sur ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="768ce-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="768ce-105">Calcul de valeurs numériques</span><span class="sxs-lookup"><span data-stu-id="768ce-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="768ce-106">Pour calculer une valeur numérique</span><span class="sxs-lookup"><span data-stu-id="768ce-106">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="768ce-107">Combiner un ou plusieurs littéraux numériques, constantes et variables dans une expression numérique.</span><span class="sxs-lookup"><span data-stu-id="768ce-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="768ce-108">L’exemple suivant montre des expressions numériques valides.</span><span class="sxs-lookup"><span data-stu-id="768ce-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="768ce-109">Les trois premières lignes affichent un littéral, une constante et une variable.</span><span class="sxs-lookup"><span data-stu-id="768ce-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="768ce-110">Chacun d’eux forme une expression numérique valide par lui-même.</span><span class="sxs-lookup"><span data-stu-id="768ce-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="768ce-111">La dernière ligne affiche une combinaison d’une variable avec deux littéraux.</span><span class="sxs-lookup"><span data-stu-id="768ce-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="768ce-112">Notez qu’une expression numérique ne constitue pas une instruction Visual Basic complète par elle-même.</span><span class="sxs-lookup"><span data-stu-id="768ce-112">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="768ce-113">Vous devez utiliser l’expression dans le cadre d’une instruction complète.</span><span class="sxs-lookup"><span data-stu-id="768ce-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="768ce-114">Pour stocker une valeur numérique</span><span class="sxs-lookup"><span data-stu-id="768ce-114">To store a numeric value</span></span>  
  
- <span data-ttu-id="768ce-115">Vous pouvez utiliser une instruction d’assignation pour assigner la valeur représentée par une expression numérique à une variable, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="768ce-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="768ce-116">Dans l’exemple précédent, la valeur de l’expression située à droite de l’opérateur égal ( `=` ) est assignée à la variable du `j` côté gauche de l’opérateur, donc la valeur `j` 276.</span><span class="sxs-lookup"><span data-stu-id="768ce-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="768ce-117">Pour plus d’informations, consultez [Instructions](../../../language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="768ce-117">For more information, see [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="768ce-118">Opérateurs multiples</span><span class="sxs-lookup"><span data-stu-id="768ce-118">Multiple Operators</span></span>  
 <span data-ttu-id="768ce-119">Si l’expression numérique contient plusieurs opérateurs, l’ordre dans lequel ils sont évalués est déterminé par les règles de priorité des opérateurs.</span><span class="sxs-lookup"><span data-stu-id="768ce-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="768ce-120">Pour remplacer les règles de priorité des opérateurs, vous devez placer les expressions entre parenthèses, comme dans l’exemple ci-dessus. les expressions entre parenthèses sont évaluées en premier.</span><span class="sxs-lookup"><span data-stu-id="768ce-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="768ce-121">Pour remplacer la priorité d’un opérateur normal</span><span class="sxs-lookup"><span data-stu-id="768ce-121">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="768ce-122">Utilisez des parenthèses pour encadrer les opérations que vous souhaitez effectuer en premier.</span><span class="sxs-lookup"><span data-stu-id="768ce-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="768ce-123">L’exemple suivant montre deux résultats différents avec les mêmes opérandes et opérateurs.</span><span class="sxs-lookup"><span data-stu-id="768ce-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="768ce-124">Dans l’exemple précédent, le calcul pour `j` exécute d’abord l’opérateur d’addition ( `+` ), car les parenthèses autour `(67 + i)` de remplacent la priorité normale et la valeur assignée à `j` est 276 (4 fois 69).</span><span class="sxs-lookup"><span data-stu-id="768ce-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="768ce-125">Le calcul pour `k` exécute les opérateurs dans leur priorité normale ( `*` avant `+` ) et la valeur assignée à `k` est 270 (268 plus 2).</span><span class="sxs-lookup"><span data-stu-id="768ce-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="768ce-126">Pour plus d’informations, consultez [priorité des opérateurs dans Visual Basic](../../../language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="768ce-126">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768ce-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="768ce-127">See also</span></span>

- [<span data-ttu-id="768ce-128">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="768ce-128">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="768ce-129">Comparaisons de valeurs</span><span class="sxs-lookup"><span data-stu-id="768ce-129">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="768ce-130">Instructions</span><span class="sxs-lookup"><span data-stu-id="768ce-130">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="768ce-131">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="768ce-131">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="768ce-132">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="768ce-132">Arithmetic Operators</span></span>](../../../language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="768ce-133">Association efficace d’opérateurs</span><span class="sxs-lookup"><span data-stu-id="768ce-133">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
