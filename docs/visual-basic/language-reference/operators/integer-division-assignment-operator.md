---
title: '\=, opérateur'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 6e749e13c0427354db9e361538d4bef10b6c6b04
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873411"
---
# <a name="-operator"></a><span data-ttu-id="15577-102">\\= (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="15577-102">\\= Operator</span></span>

<span data-ttu-id="15577-103">Divise la valeur d’une variable ou d’une propriété par la valeur d’une expression et assigne le résultat entier à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="15577-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15577-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15577-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="15577-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="15577-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="15577-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="15577-106">Required.</span></span> <span data-ttu-id="15577-107">Toute variable ou propriété numérique.</span><span class="sxs-lookup"><span data-stu-id="15577-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="15577-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="15577-108">Required.</span></span> <span data-ttu-id="15577-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="15577-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15577-110">Notes</span><span class="sxs-lookup"><span data-stu-id="15577-110">Remarks</span></span>  

 <span data-ttu-id="15577-111">L’élément situé à gauche de l' `\=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="15577-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="15577-112">La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="15577-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="15577-113">L' `\=` opérateur divise la valeur d’une variable ou d’une propriété à sa gauche par la valeur de sa droite, et assigne le résultat entier à la variable ou à la propriété à sa gauche</span><span class="sxs-lookup"><span data-stu-id="15577-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="15577-114">Pour plus d’informations sur la Division d’entiers, consultez [\ Operator (Visual Basic)](integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="15577-114">For further information on integer division, see [\ Operator (Visual Basic)](integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="15577-115">Surcharge</span><span class="sxs-lookup"><span data-stu-id="15577-115">Overloading</span></span>  

 <span data-ttu-id="15577-116">L' `\` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="15577-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="15577-117">La surcharge de l' `\` opérateur affecte le comportement de l' `\=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="15577-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="15577-118">Si votre code utilise `\=` sur une classe ou une structure qui surcharge `\` , assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="15577-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="15577-119">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="15577-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15577-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="15577-120">Example</span></span>  

 <span data-ttu-id="15577-121">L’exemple suivant utilise l' `\=` opérateur pour diviser une `Integer` variable par une seconde et assigner le résultat de l’entier à la première variable.</span><span class="sxs-lookup"><span data-stu-id="15577-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="15577-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15577-122">See also</span></span>

- [<span data-ttu-id="15577-123">\, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15577-123">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="15577-124">/=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15577-124">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="15577-125">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="15577-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="15577-126">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="15577-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="15577-127">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15577-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="15577-128">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="15577-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="15577-129">Publication</span><span class="sxs-lookup"><span data-stu-id="15577-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
