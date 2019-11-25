---
title: IsTrue, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 4b863eed8406a10b9a44d7139f8659ac5cb758ad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349511"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="54c33-102">Opérateur IsTrue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54c33-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="54c33-103">Determines whether an expression is `True`.</span><span class="sxs-lookup"><span data-stu-id="54c33-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="54c33-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span><span class="sxs-lookup"><span data-stu-id="54c33-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="54c33-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span><span class="sxs-lookup"><span data-stu-id="54c33-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="54c33-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span><span class="sxs-lookup"><span data-stu-id="54c33-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="54c33-107">This means that if you define one of them, you must also define the other one.</span><span class="sxs-lookup"><span data-stu-id="54c33-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="54c33-108">Compiler Use of IsTrue</span><span class="sxs-lookup"><span data-stu-id="54c33-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="54c33-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span><span class="sxs-lookup"><span data-stu-id="54c33-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="54c33-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span><span class="sxs-lookup"><span data-stu-id="54c33-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="54c33-111">It searches for a suitable operator in the following order:</span><span class="sxs-lookup"><span data-stu-id="54c33-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="54c33-112">A widening conversion operator from your class or structure to `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="54c33-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="54c33-113">A widening conversion operator from your class or structure to `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="54c33-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="54c33-114">The `IsTrue` operator on your class or structure.</span><span class="sxs-lookup"><span data-stu-id="54c33-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="54c33-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="54c33-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="54c33-116">A narrowing conversion operator from your class or structure to `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="54c33-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="54c33-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span><span class="sxs-lookup"><span data-stu-id="54c33-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54c33-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="54c33-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="54c33-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="54c33-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="54c33-120">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="54c33-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54c33-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="54c33-121">Example</span></span>  
 <span data-ttu-id="54c33-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span><span class="sxs-lookup"><span data-stu-id="54c33-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="54c33-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54c33-123">See also</span></span>

- [<span data-ttu-id="54c33-124">IsFalse (opérateur)</span><span class="sxs-lookup"><span data-stu-id="54c33-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="54c33-125">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="54c33-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="54c33-126">OrElse (opérateur)</span><span class="sxs-lookup"><span data-stu-id="54c33-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
