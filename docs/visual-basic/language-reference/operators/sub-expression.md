---
title: Sous-expression
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: f862730220d0595faecaa915b1eaad2a3cdc0053
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406312"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="5249d-102">Sous-expression (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5249d-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="5249d-103">Déclare les paramètres et le code qui définissent une expression lambda de sous-routine.</span><span class="sxs-lookup"><span data-stu-id="5249d-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5249d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5249d-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="5249d-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="5249d-105">Parts</span></span>  
  
|<span data-ttu-id="5249d-106">Terme</span><span class="sxs-lookup"><span data-stu-id="5249d-106">Term</span></span>|<span data-ttu-id="5249d-107">Définition</span><span class="sxs-lookup"><span data-stu-id="5249d-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="5249d-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="5249d-108">Optional.</span></span> <span data-ttu-id="5249d-109">Liste des noms de variables locales qui représentent les paramètres de la procédure.</span><span class="sxs-lookup"><span data-stu-id="5249d-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="5249d-110">Les parenthèses doivent être présentes même lorsque la liste est vide.</span><span class="sxs-lookup"><span data-stu-id="5249d-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="5249d-111">Pour plus d'informations, consultez [Parameter List](../statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="5249d-111">For more information, see [Parameter List](../statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="5249d-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5249d-112">Required.</span></span> <span data-ttu-id="5249d-113">Instruction unique.</span><span class="sxs-lookup"><span data-stu-id="5249d-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="5249d-114">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="5249d-114">Required.</span></span> <span data-ttu-id="5249d-115">Liste d’instructions.</span><span class="sxs-lookup"><span data-stu-id="5249d-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5249d-116">Notes</span><span class="sxs-lookup"><span data-stu-id="5249d-116">Remarks</span></span>  
 <span data-ttu-id="5249d-117">Une *expression lambda* est une sous-routine qui n’a pas de nom et qui exécute une ou plusieurs instructions.</span><span class="sxs-lookup"><span data-stu-id="5249d-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="5249d-118">Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu’argument de `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="5249d-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="5249d-119">Pour plus d’informations sur les délégués et l’utilisation d’expressions lambda avec des délégués, consultez [instruction de délégué](../statements/delegate-statement.md) et [conversion simplifiée](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)des délégués.</span><span class="sxs-lookup"><span data-stu-id="5249d-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="5249d-120">Syntaxe d’expression lambda</span><span class="sxs-lookup"><span data-stu-id="5249d-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="5249d-121">La syntaxe d’une expression lambda ressemble à celle d’une sous-routine standard.</span><span class="sxs-lookup"><span data-stu-id="5249d-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="5249d-122">Les différences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5249d-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="5249d-123">Une expression lambda n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="5249d-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="5249d-124">Une expression lambda ne peut pas avoir de modificateur, tel que `Overloads` ou `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="5249d-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="5249d-125">Le corps d’une expression lambda sur une seule ligne doit être une instruction, et non une expression.</span><span class="sxs-lookup"><span data-stu-id="5249d-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="5249d-126">Le corps peut se composer d’un appel à une procédure Sub, mais pas d’un appel à une procédure Function.</span><span class="sxs-lookup"><span data-stu-id="5249d-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="5249d-127">Dans une expression lambda, tous les paramètres doivent avoir des types de données spécifiés ou tous les paramètres doivent être déduits.</span><span class="sxs-lookup"><span data-stu-id="5249d-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="5249d-128">Les paramètres facultatifs et ne `ParamArray` sont pas autorisés dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="5249d-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="5249d-129">Les paramètres génériques ne sont pas autorisés dans les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="5249d-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5249d-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="5249d-130">Example</span></span>  
 <span data-ttu-id="5249d-131">Voici un exemple d’expression lambda qui écrit une valeur dans la console.</span><span class="sxs-lookup"><span data-stu-id="5249d-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="5249d-132">L’exemple montre la syntaxe d’expression lambda à ligne unique et multiligne pour une sous-routine.</span><span class="sxs-lookup"><span data-stu-id="5249d-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="5249d-133">Pour obtenir plus d’exemples, consultez [expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5249d-133">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="5249d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5249d-134">See also</span></span>

- [<span data-ttu-id="5249d-135">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="5249d-135">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="5249d-136">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="5249d-136">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="5249d-137">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="5249d-137">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="5249d-138">Instructions</span><span class="sxs-lookup"><span data-stu-id="5249d-138">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="5249d-139">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="5249d-139">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
