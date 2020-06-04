---
title: <<=, opérateur
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
ms.openlocfilehash: ff7cbb02a9a10dbe11450491e93fd85fd77b44ba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370659"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="01a70-102">\<\<=, Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01a70-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="01a70-103">Effectue un décalage arithmétique vers la gauche sur la valeur d’une variable ou d’une propriété et assigne le résultat à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="01a70-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01a70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01a70-104">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="01a70-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="01a70-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="01a70-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="01a70-106">Required.</span></span> <span data-ttu-id="01a70-107">Variable ou propriété d’un type intégral ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` ou `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="01a70-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="01a70-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="01a70-108">Required.</span></span> <span data-ttu-id="01a70-109">Expression numérique d’un type de données qui s’étend à `Integer` .</span><span class="sxs-lookup"><span data-stu-id="01a70-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01a70-110">Notes</span><span class="sxs-lookup"><span data-stu-id="01a70-110">Remarks</span></span>  
 <span data-ttu-id="01a70-111">L’élément situé à gauche de l' `<<=` opérateur peut être une variable scalaire simple, une propriété ou un élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="01a70-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="01a70-112">La variable ou la propriété ne peut pas être [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="01a70-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="01a70-113">L' `<<=` opérateur effectue d’abord un décalage arithmétique vers la gauche sur la valeur de la variable ou de la propriété.</span><span class="sxs-lookup"><span data-stu-id="01a70-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="01a70-114">L’opérateur assigne ensuite le résultat de cette opération à la variable ou à la propriété.</span><span class="sxs-lookup"><span data-stu-id="01a70-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="01a70-115">Les décalages arithmétiques ne sont pas circulaires, ce qui signifie que les bits décalés d’une extrémité du résultat ne sont pas réintroduits à l’autre extrémité.</span><span class="sxs-lookup"><span data-stu-id="01a70-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="01a70-116">Dans un décalage arithmétique vers la gauche, les bits décalés au-delà de la plage du type de données de résultat sont ignorés, et les positions de bits libérées à droite sont définies sur zéro.</span><span class="sxs-lookup"><span data-stu-id="01a70-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="01a70-117">Surcharge</span><span class="sxs-lookup"><span data-stu-id="01a70-117">Overloading</span></span>  
 <span data-ttu-id="01a70-118">L' [opérateur<< ](left-shift-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="01a70-118">The [<< Operator](left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="01a70-119">La surcharge de l' `<<` opérateur affecte le comportement de l' `<<=` opérateur.</span><span class="sxs-lookup"><span data-stu-id="01a70-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="01a70-120">Si votre code utilise `<<=` sur une classe ou une structure qui surcharge `<<` , assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="01a70-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="01a70-121">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="01a70-121">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01a70-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="01a70-122">Example</span></span>  
 <span data-ttu-id="01a70-123">L’exemple suivant utilise l' `<<=` opérateur pour décaler le modèle binaire d’une variable vers la `Integer` gauche selon la valeur spécifiée et assigner le résultat à la variable.</span><span class="sxs-lookup"><span data-stu-id="01a70-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="01a70-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01a70-124">See also</span></span>

- [<span data-ttu-id="01a70-125">Opérateur<< </span><span class="sxs-lookup"><span data-stu-id="01a70-125"><< Operator</span></span>](left-shift-operator.md)
- [<span data-ttu-id="01a70-126">Opérateurs d’assignation</span><span class="sxs-lookup"><span data-stu-id="01a70-126">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="01a70-127">Opérateurs de décalage de bits</span><span class="sxs-lookup"><span data-stu-id="01a70-127">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="01a70-128">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01a70-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="01a70-129">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="01a70-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="01a70-130">Instructions</span><span class="sxs-lookup"><span data-stu-id="01a70-130">Statements</span></span>](../../programming-guide/language-features/statements.md)
