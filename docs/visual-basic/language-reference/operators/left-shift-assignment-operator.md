---
title: < < =, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: aae71069bdcb88efa5842526dd7eb47806f248d0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701105"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8a38e-102">\<\<=, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a38e-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="8a38e-103">Effectue un décalage arithmétique vers la gauche sur la valeur d’une variable ou d’une propriété et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="8a38e-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a38e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a38e-104">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="8a38e-105">Composants</span><span class="sxs-lookup"><span data-stu-id="8a38e-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8a38e-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="8a38e-106">Required.</span></span> <span data-ttu-id="8a38e-107">Variable ou propriété d’un type intégral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="8a38e-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="8a38e-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="8a38e-108">Required.</span></span> <span data-ttu-id="8a38e-109">Expression numérique d’un type de données qui s’étend à `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8a38e-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a38e-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="8a38e-110">Remarks</span></span>  
 <span data-ttu-id="8a38e-111">L’élément situé à gauche de l’opérateur `<<=` peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="8a38e-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8a38e-112">La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8a38e-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="8a38e-113">L’opérateur `<<=` effectue d’abord un décalage arithmétique vers la gauche sur la valeur de la variable ou de la propriété.</span><span class="sxs-lookup"><span data-stu-id="8a38e-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="8a38e-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="8a38e-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="8a38e-115">Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="8a38e-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="8a38e-116">Dans un décalage arithmétique vers la gauche, les bits décalés au-delà de la plage du type de données de résultat sont ignorés, et les positions de bits libérées à droite sont définies sur zéro.</span><span class="sxs-lookup"><span data-stu-id="8a38e-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8a38e-117">Surcharge</span><span class="sxs-lookup"><span data-stu-id="8a38e-117">Overloading</span></span>  
 <span data-ttu-id="8a38e-118">L' [opérateur < <](../../../visual-basic/language-reference/operators/left-shift-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="8a38e-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8a38e-119">La surcharge de l’opérateur `<<` affecte le comportement de l’opérateur `<<=`.</span><span class="sxs-lookup"><span data-stu-id="8a38e-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="8a38e-120">Si votre code utilise `<<=` sur une classe ou une structure qui surcharge `<<`, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="8a38e-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8a38e-121">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8a38e-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a38e-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a38e-122">Example</span></span>  
 <span data-ttu-id="8a38e-123">L’exemple suivant utilise l’opérateur `<<=` pour décaler le modèle binaire d’une variable `Integer` vers la gauche selon la valeur spécifiée et assigner le résultat à la variable.</span><span class="sxs-lookup"><span data-stu-id="8a38e-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="8a38e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a38e-124">See also</span></span>

- [<span data-ttu-id="8a38e-125"><<, opérateur</span><span class="sxs-lookup"><span data-stu-id="8a38e-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [<span data-ttu-id="8a38e-126">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="8a38e-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8a38e-127">Opérateurs de décalage de bits</span><span class="sxs-lookup"><span data-stu-id="8a38e-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="8a38e-128">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8a38e-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8a38e-129">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="8a38e-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8a38e-130">Instructions</span><span class="sxs-lookup"><span data-stu-id="8a38e-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
