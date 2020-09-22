---
title: IsTrue, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 2e67a4adabe58ab12d317ae6318c0a2fac29da7d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866938"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="f4653-102">Opérateur IsTrue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4653-102">IsTrue Operator (Visual Basic)</span></span>

<span data-ttu-id="f4653-103">Détermine si une expression est `True` .</span><span class="sxs-lookup"><span data-stu-id="f4653-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="f4653-104">Vous ne pouvez pas appeler `IsTrue` explicitement dans votre code, mais le compilateur Visual Basic peut l’utiliser pour générer du code à partir de `OrElse` clauses.</span><span class="sxs-lookup"><span data-stu-id="f4653-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="f4653-105">Si vous définissez une classe ou une structure, puis que vous utilisez une variable de ce type dans une `OrElse` clause, vous devez définir `IsTrue` sur cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="f4653-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="f4653-106">Le compilateur considère les `IsTrue` `IsFalse` opérateurs et comme une *paire correspondante*.</span><span class="sxs-lookup"><span data-stu-id="f4653-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="f4653-107">Cela signifie que si vous définissez l’une d’entre elles, vous devez également définir l’autre.</span><span class="sxs-lookup"><span data-stu-id="f4653-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="f4653-108">Utilisation de IsTrue par le compilateur</span><span class="sxs-lookup"><span data-stu-id="f4653-108">Compiler Use of IsTrue</span></span>  

 <span data-ttu-id="f4653-109">Lorsque vous avez défini une classe ou une structure, vous pouvez utiliser une variable de ce type dans `For` une `If` instruction,, `Else If` ou `While` , ou dans une `When` clause.</span><span class="sxs-lookup"><span data-stu-id="f4653-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="f4653-110">Dans ce cas, le compilateur requiert un opérateur qui convertit votre type en `Boolean` valeur afin de pouvoir tester une condition.</span><span class="sxs-lookup"><span data-stu-id="f4653-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="f4653-111">Il recherche un opérateur approprié dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="f4653-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="f4653-112">Opérateur de conversion étendue de votre classe ou structure en `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f4653-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="f4653-113">Opérateur de conversion étendue de votre classe ou structure en `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="f4653-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="f4653-114">`IsTrue`Opérateur sur votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="f4653-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="f4653-115">Conversion restrictive vers `Boolean?` qui n’implique pas de conversion de `Boolean` en `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="f4653-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="f4653-116">Opérateur de conversion restrictive de votre classe ou structure en `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f4653-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="f4653-117">Si vous n’avez défini aucune conversion vers `Boolean` ou un `IsTrue` opérateur, le compilateur signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="f4653-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4653-118">L' `IsTrue` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="f4653-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="f4653-119">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="f4653-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f4653-120">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f4653-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4653-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="f4653-121">Example</span></span>  

 <span data-ttu-id="f4653-122">L’exemple de code suivant définit le plan d’une structure qui comprend des définitions pour les `IsFalse` `IsTrue` opérateurs et.</span><span class="sxs-lookup"><span data-stu-id="f4653-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="f4653-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4653-123">See also</span></span>

- [<span data-ttu-id="f4653-124">IsFalse, opérateur</span><span class="sxs-lookup"><span data-stu-id="f4653-124">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="f4653-125">Comment : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="f4653-125">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="f4653-126">OrElse, opérateur</span><span class="sxs-lookup"><span data-stu-id="f4653-126">OrElse Operator</span></span>](orelse-operator.md)
