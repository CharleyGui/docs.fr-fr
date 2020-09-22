---
title: '&amp;= (Opérateur)'
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
ms.openlocfilehash: 9b77c44aa77afd59e36e1d21451205d3929ef527
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874874"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="24b25-102">&amp;=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24b25-102">&amp;= Operator (Visual Basic)</span></span>

<span data-ttu-id="24b25-103">Concatène une `String` expression à une `String` variable ou une propriété et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="24b25-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24b25-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="24b25-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="24b25-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="24b25-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="24b25-106">Required.</span></span> <span data-ttu-id="24b25-107">Toute `String` variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="24b25-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="24b25-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="24b25-108">Required.</span></span> <span data-ttu-id="24b25-109">Toute expression `String` .</span><span class="sxs-lookup"><span data-stu-id="24b25-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24b25-110">Notes</span><span class="sxs-lookup"><span data-stu-id="24b25-110">Remarks</span></span>  

 <span data-ttu-id="24b25-111">L’élément situé à gauche de l' `&=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="24b25-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="24b25-112">La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="24b25-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="24b25-113">L' `&=` opérateur concatène l' `String` expression à droite à la `String` variable ou à la propriété à sa gauche, et assigne le résultat à la variable ou à la propriété à sa gauche.</span><span class="sxs-lookup"><span data-stu-id="24b25-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="24b25-114">Surcharge</span><span class="sxs-lookup"><span data-stu-id="24b25-114">Overloading</span></span>  

 <span data-ttu-id="24b25-115">L' [ opérateur&](concatenation-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="24b25-115">The [& Operator](concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="24b25-116">La surcharge de l' `&` opérateur affecte le comportement de l' `&=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="24b25-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="24b25-117">Si votre code utilise `&=` sur une classe ou une structure qui surcharge `&` , assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="24b25-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="24b25-118">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="24b25-118">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24b25-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="24b25-119">Example</span></span>  

 <span data-ttu-id="24b25-120">L’exemple suivant utilise l' `&=` opérateur pour concaténer deux `String` variables et assigner le résultat à la première variable.</span><span class="sxs-lookup"><span data-stu-id="24b25-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="24b25-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24b25-121">See also</span></span>

- [<span data-ttu-id="24b25-122"> Opérateur&</span><span class="sxs-lookup"><span data-stu-id="24b25-122">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="24b25-123">Opérateur + =</span><span class="sxs-lookup"><span data-stu-id="24b25-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="24b25-124">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="24b25-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="24b25-125">Opérateurs de concaténation</span><span class="sxs-lookup"><span data-stu-id="24b25-125">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="24b25-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24b25-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="24b25-127">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="24b25-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="24b25-128">Publication</span><span class="sxs-lookup"><span data-stu-id="24b25-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
