---
title: '>>=, opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: cad021c7730782d6233c60841483df7173308dc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351992"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="55d87-102">> > =, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55d87-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="55d87-103">Effectue un décalage arithmétique vers la droite sur la valeur d’une variable ou d’une propriété et réassigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="55d87-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55d87-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="55d87-105">Composants</span><span class="sxs-lookup"><span data-stu-id="55d87-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="55d87-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="55d87-106">Required.</span></span> <span data-ttu-id="55d87-107">Variable ou propriété d’un type intégral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="55d87-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="55d87-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="55d87-108">Required.</span></span> <span data-ttu-id="55d87-109">Expression numérique d’un type de données qui s’étend à `Integer`.</span><span class="sxs-lookup"><span data-stu-id="55d87-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55d87-110">Notes</span><span class="sxs-lookup"><span data-stu-id="55d87-110">Remarks</span></span>  
 <span data-ttu-id="55d87-111">L’élément situé à gauche de l’opérateur `>>=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="55d87-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="55d87-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="55d87-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="55d87-113">L’opérateur `>>=` effectue d’abord un décalage arithmétique à droite sur la valeur de la variable ou de la propriété.</span><span class="sxs-lookup"><span data-stu-id="55d87-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="55d87-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="55d87-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="55d87-115">Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="55d87-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="55d87-116">Dans un décalage arithmétique vers la droite, les bits décalés au-delà de la position du bit le plus à droite sont ignorés, et le bit le plus à gauche est propagé dans les positions de bits libérées à gauche.</span><span class="sxs-lookup"><span data-stu-id="55d87-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="55d87-117">Cela signifie que si `variableorproperty` a une valeur négative, les positions libérées sont définies sur un.</span><span class="sxs-lookup"><span data-stu-id="55d87-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="55d87-118">Si `variableorproperty` est positif, ou si son type de données est un type non signé, les positions libérées sont définies à zéro.</span><span class="sxs-lookup"><span data-stu-id="55d87-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="55d87-119">Surcharge</span><span class="sxs-lookup"><span data-stu-id="55d87-119">Overloading</span></span>  
 <span data-ttu-id="55d87-120">L' [opérateur > >](../../../visual-basic/language-reference/operators/right-shift-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="55d87-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="55d87-121">La surcharge de l’opérateur `>>` affecte le comportement de l’opérateur `>>=`.</span><span class="sxs-lookup"><span data-stu-id="55d87-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="55d87-122">Si votre code utilise `>>=` sur une classe ou une structure qui surcharge `>>`, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="55d87-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="55d87-123">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="55d87-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55d87-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="55d87-124">Example</span></span>  
 <span data-ttu-id="55d87-125">L’exemple suivant utilise l’opérateur `>>=` pour décaler le modèle binaire d’une variable `Integer` à droite de la valeur spécifiée et assigner le résultat à la variable.</span><span class="sxs-lookup"><span data-stu-id="55d87-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="55d87-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55d87-126">See also</span></span>

- [<span data-ttu-id="55d87-127">>>, opérateur</span><span class="sxs-lookup"><span data-stu-id="55d87-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="55d87-128">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="55d87-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="55d87-129">Opérateurs de décalage de bits</span><span class="sxs-lookup"><span data-stu-id="55d87-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="55d87-130">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55d87-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="55d87-131">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="55d87-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="55d87-132">Instructions</span><span class="sxs-lookup"><span data-stu-id="55d87-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
