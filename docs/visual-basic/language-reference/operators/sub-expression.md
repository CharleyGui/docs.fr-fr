---
title: Sous-expression (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 2330b410f54b54d8f6cb7d8ad6f9b39a3f4d31bc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701335"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="6e419-102">Sous-expression (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e419-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="6e419-103">Déclare les paramètres et le code qui définissent une expression lambda de sous-routine.</span><span class="sxs-lookup"><span data-stu-id="6e419-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e419-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e419-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="6e419-105">Composants</span><span class="sxs-lookup"><span data-stu-id="6e419-105">Parts</span></span>  
  
|<span data-ttu-id="6e419-106">Terme</span><span class="sxs-lookup"><span data-stu-id="6e419-106">Term</span></span>|<span data-ttu-id="6e419-107">Définition</span><span class="sxs-lookup"><span data-stu-id="6e419-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="6e419-108">facultatif.</span><span class="sxs-lookup"><span data-stu-id="6e419-108">Optional.</span></span> <span data-ttu-id="6e419-109">Liste des noms de variables locales qui représentent les paramètres de la procédure.</span><span class="sxs-lookup"><span data-stu-id="6e419-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="6e419-110">Les parenthèses doivent être présentes même lorsque la liste est vide.</span><span class="sxs-lookup"><span data-stu-id="6e419-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="6e419-111">Pour plus d'informations, consultez [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="6e419-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="6e419-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6e419-112">Required.</span></span> <span data-ttu-id="6e419-113">Instruction unique.</span><span class="sxs-lookup"><span data-stu-id="6e419-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="6e419-114">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="6e419-114">Required.</span></span> <span data-ttu-id="6e419-115">Liste d’instructions.</span><span class="sxs-lookup"><span data-stu-id="6e419-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e419-116">Notes</span><span class="sxs-lookup"><span data-stu-id="6e419-116">Remarks</span></span>  
 <span data-ttu-id="6e419-117">Une *expression lambda* est une sous-routine qui n’a pas de nom et qui exécute une ou plusieurs instructions.</span><span class="sxs-lookup"><span data-stu-id="6e419-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="6e419-118">Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu’argument pour `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="6e419-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="6e419-119">Pour plus d’informations sur les délégués et l’utilisation d’expressions lambda avec des délégués, consultez [instruction de délégué](../../../visual-basic/language-reference/statements/delegate-statement.md) et [conversion simplifiée](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)des délégués.</span><span class="sxs-lookup"><span data-stu-id="6e419-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="6e419-120">Syntaxe d’expression lambda</span><span class="sxs-lookup"><span data-stu-id="6e419-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="6e419-121">La syntaxe d’une expression lambda ressemble à celle d’une sous-routine standard.</span><span class="sxs-lookup"><span data-stu-id="6e419-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="6e419-122">Les différences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6e419-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="6e419-123">Une expression lambda n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="6e419-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="6e419-124">Une expression lambda ne peut pas avoir de modificateur, tel que `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="6e419-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="6e419-125">Le corps d’une expression lambda sur une seule ligne doit être une instruction, et non une expression.</span><span class="sxs-lookup"><span data-stu-id="6e419-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="6e419-126">Le corps peut se composer d’un appel à une procédure Sub, mais pas d’un appel à une procédure Function.</span><span class="sxs-lookup"><span data-stu-id="6e419-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="6e419-127">Dans une expression lambda, tous les paramètres doivent avoir des types de données spécifiés ou tous les paramètres doivent être déduits.</span><span class="sxs-lookup"><span data-stu-id="6e419-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="6e419-128">Les paramètres facultatifs et `ParamArray` ne sont pas autorisés dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="6e419-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="6e419-129">Les paramètres génériques ne sont pas autorisés dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="6e419-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e419-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e419-130">Example</span></span>  
 <span data-ttu-id="6e419-131">Voici un exemple d’expression lambda qui écrit une valeur dans la console.</span><span class="sxs-lookup"><span data-stu-id="6e419-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="6e419-132">L’exemple montre la syntaxe d’expression lambda à ligne unique et multiligne pour une sous-routine.</span><span class="sxs-lookup"><span data-stu-id="6e419-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="6e419-133">Pour obtenir plus d’exemples, consultez [expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6e419-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="6e419-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e419-134">See also</span></span>

- [<span data-ttu-id="6e419-135">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="6e419-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="6e419-136">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="6e419-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="6e419-137">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="6e419-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="6e419-138">Instructions</span><span class="sxs-lookup"><span data-stu-id="6e419-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="6e419-139">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="6e419-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
