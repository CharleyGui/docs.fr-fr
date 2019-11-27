---
title: IsFalse, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 51b7bfb2cf5301a39818e6566b408ee0677689f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349527"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="e043f-102">Opérateur IsFalse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e043f-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="e043f-103">Détermine si une expression est `False`.</span><span class="sxs-lookup"><span data-stu-id="e043f-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="e043f-104">Vous ne pouvez pas appeler `IsFalse` explicitement dans votre code, mais le compilateur Visual Basic peut l’utiliser pour générer du code à partir de clauses `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="e043f-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="e043f-105">Si vous définissez une classe ou une structure, puis que vous utilisez une variable de ce type dans une clause `AndAlso`, vous devez définir `IsFalse` sur cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="e043f-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="e043f-106">Le compilateur considère les opérateurs `IsFalse` et `IsTrue` comme une *paire correspondante*.</span><span class="sxs-lookup"><span data-stu-id="e043f-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="e043f-107">Cela signifie que si vous définissez l’une d’entre elles, vous devez également définir l’autre.</span><span class="sxs-lookup"><span data-stu-id="e043f-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e043f-108">L’opérateur `IsFalse` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="e043f-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="e043f-109">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="e043f-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e043f-110">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e043f-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e043f-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="e043f-111">Example</span></span>  
 <span data-ttu-id="e043f-112">L’exemple de code suivant définit le plan d’une structure qui comprend des définitions pour les opérateurs `IsFalse` et `IsTrue`.</span><span class="sxs-lookup"><span data-stu-id="e043f-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="e043f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e043f-113">See also</span></span>

- [<span data-ttu-id="e043f-114">IsTrue (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e043f-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="e043f-115">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="e043f-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="e043f-116">AndAlso (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e043f-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
