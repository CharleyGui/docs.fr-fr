---
title: '&amp;=, opérateur'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 8668bfcbf32bb34b422efe8116bbd12a2d80b1d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350264"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="8c495-102">&amp;=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c495-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="8c495-103">Concatène une expression `String` à une variable ou une propriété `String` et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="8c495-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c495-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c495-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="8c495-105">Composants</span><span class="sxs-lookup"><span data-stu-id="8c495-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8c495-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="8c495-106">Required.</span></span> <span data-ttu-id="8c495-107">Toute variable ou propriété de `String`.</span><span class="sxs-lookup"><span data-stu-id="8c495-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="8c495-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="8c495-108">Required.</span></span> <span data-ttu-id="8c495-109">Toute expression `String` .</span><span class="sxs-lookup"><span data-stu-id="8c495-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c495-110">Notes</span><span class="sxs-lookup"><span data-stu-id="8c495-110">Remarks</span></span>  
 <span data-ttu-id="8c495-111">L’élément situé à gauche de l’opérateur `&=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="8c495-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8c495-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8c495-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="8c495-113">L’opérateur `&=` concatène l’expression `String` à droite à la variable ou à la propriété `String` à gauche, et assigne le résultat à la variable ou à la propriété située à gauche.</span><span class="sxs-lookup"><span data-stu-id="8c495-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8c495-114">Surcharge</span><span class="sxs-lookup"><span data-stu-id="8c495-114">Overloading</span></span>  
 <span data-ttu-id="8c495-115">L' [opérateur &](../../../visual-basic/language-reference/operators/concatenation-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="8c495-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8c495-116">La surcharge de l’opérateur `&` affecte le comportement de l’opérateur `&=`.</span><span class="sxs-lookup"><span data-stu-id="8c495-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="8c495-117">Si votre code utilise `&=` sur une classe ou une structure qui surcharge `&`, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="8c495-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8c495-118">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8c495-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c495-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="8c495-119">Example</span></span>  
 <span data-ttu-id="8c495-120">L’exemple suivant utilise l’opérateur `&=` pour concaténer deux variables `String` et assigner le résultat à la première variable.</span><span class="sxs-lookup"><span data-stu-id="8c495-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8c495-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c495-121">See also</span></span>

- [<span data-ttu-id="8c495-122">&, opérateur</span><span class="sxs-lookup"><span data-stu-id="8c495-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="8c495-123">+=, opérateur</span><span class="sxs-lookup"><span data-stu-id="8c495-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="8c495-124">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="8c495-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8c495-125">Opérateurs de concaténation</span><span class="sxs-lookup"><span data-stu-id="8c495-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="8c495-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c495-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8c495-127">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="8c495-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8c495-128">Instructions</span><span class="sxs-lookup"><span data-stu-id="8c495-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
