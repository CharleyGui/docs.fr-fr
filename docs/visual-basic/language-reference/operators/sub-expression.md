---
title: Sous-expression (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 6cdb75f150831ae3857a510d87b58773bdcf13c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609595"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="4da9b-102">Sous-expression (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4da9b-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="4da9b-103">Déclare les paramètres et le code qui définissent une expression lambda de sous-routine.</span><span class="sxs-lookup"><span data-stu-id="4da9b-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4da9b-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="4da9b-105">Composants</span><span class="sxs-lookup"><span data-stu-id="4da9b-105">Parts</span></span>  
  
|<span data-ttu-id="4da9b-106">Terme</span><span class="sxs-lookup"><span data-stu-id="4da9b-106">Term</span></span>|<span data-ttu-id="4da9b-107">Définition</span><span class="sxs-lookup"><span data-stu-id="4da9b-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="4da9b-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4da9b-108">Optional.</span></span> <span data-ttu-id="4da9b-109">Liste des noms de variables locales qui représentent les paramètres de la procédure.</span><span class="sxs-lookup"><span data-stu-id="4da9b-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="4da9b-110">Les parenthèses doivent être présents même lorsque la liste est vide.</span><span class="sxs-lookup"><span data-stu-id="4da9b-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="4da9b-111">Pour plus d'informations, consultez [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="4da9b-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="4da9b-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4da9b-112">Required.</span></span> <span data-ttu-id="4da9b-113">Une instruction unique.</span><span class="sxs-lookup"><span data-stu-id="4da9b-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="4da9b-114">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4da9b-114">Required.</span></span> <span data-ttu-id="4da9b-115">Une liste d’instructions.</span><span class="sxs-lookup"><span data-stu-id="4da9b-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4da9b-116">Notes</span><span class="sxs-lookup"><span data-stu-id="4da9b-116">Remarks</span></span>  
 <span data-ttu-id="4da9b-117">Un *expression lambda* est une sous-routine qui n’a pas un nom et qui s’exécute une ou plusieurs instructions.</span><span class="sxs-lookup"><span data-stu-id="4da9b-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="4da9b-118">Vous pouvez utiliser une expression lambda n’importe où que vous pouvez utiliser un type délégué, sauf en tant qu’argument à `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="4da9b-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="4da9b-119">Pour plus d’informations sur les délégués et l’utilisation d’expressions lambda avec les délégués, consultez [instruction Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) et [Conversion souple des délégués](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="4da9b-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="4da9b-120">Syntaxe d’expression lambda</span><span class="sxs-lookup"><span data-stu-id="4da9b-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="4da9b-121">La syntaxe d’une expression lambda ressemble à celle d’une sous-routine standard.</span><span class="sxs-lookup"><span data-stu-id="4da9b-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="4da9b-122">Les différences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4da9b-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="4da9b-123">Une expression lambda n’a pas un nom.</span><span class="sxs-lookup"><span data-stu-id="4da9b-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="4da9b-124">Une expression lambda ne peut pas avoir un modificateur, tel que `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="4da9b-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="4da9b-125">Le corps d’une expression lambda sur une ligne doit être une instruction, pas une expression.</span><span class="sxs-lookup"><span data-stu-id="4da9b-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="4da9b-126">Le corps peut se composer d’un appel à une procédure sub, mais pas un appel à une procédure de fonction.</span><span class="sxs-lookup"><span data-stu-id="4da9b-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="4da9b-127">Dans une expression lambda, soit tous les paramètres doivent avoir spécifié tous les paramètres ou types de données doivent être déduits.</span><span class="sxs-lookup"><span data-stu-id="4da9b-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="4da9b-128">Facultatif et `ParamArray` paramètres ne sont pas autorisés dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="4da9b-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="4da9b-129">Paramètres génériques ne sont pas autorisées dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="4da9b-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4da9b-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="4da9b-130">Example</span></span>  
 <span data-ttu-id="4da9b-131">Voici un exemple d’une expression lambda qui écrit une valeur dans la console.</span><span class="sxs-lookup"><span data-stu-id="4da9b-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="4da9b-132">L’exemple montre les deux la syntaxe d’expression lambda multiligne ou plusieurs lignes d’une sous-routine.</span><span class="sxs-lookup"><span data-stu-id="4da9b-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="4da9b-133">Pour plus d’exemples, consultez [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4da9b-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4da9b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4da9b-134">See also</span></span>

- [<span data-ttu-id="4da9b-135">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="4da9b-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4da9b-136">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="4da9b-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="4da9b-137">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="4da9b-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="4da9b-138">Instructions</span><span class="sxs-lookup"><span data-stu-id="4da9b-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="4da9b-139">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="4da9b-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
