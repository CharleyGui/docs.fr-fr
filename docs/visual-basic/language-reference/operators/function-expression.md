---
title: Expression de fonction
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: d14d7c9bc701b5e06c51202c07c3b79832aba7cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331084"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="b0f33-102">Expression de fonction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0f33-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="b0f33-103">Déclare les paramètres et le code qui définissent une expression lambda de fonction.</span><span class="sxs-lookup"><span data-stu-id="b0f33-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0f33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0f33-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="b0f33-105">Composants</span><span class="sxs-lookup"><span data-stu-id="b0f33-105">Parts</span></span>  
  
|<span data-ttu-id="b0f33-106">Terme</span><span class="sxs-lookup"><span data-stu-id="b0f33-106">Term</span></span>|<span data-ttu-id="b0f33-107">Définition</span><span class="sxs-lookup"><span data-stu-id="b0f33-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="b0f33-108">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b0f33-108">Optional.</span></span> <span data-ttu-id="b0f33-109">Liste des noms de variables locales qui représentent les paramètres de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="b0f33-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="b0f33-110">Les parenthèses doivent être présentes même lorsque la liste est vide.</span><span class="sxs-lookup"><span data-stu-id="b0f33-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="b0f33-111">Consultez la [liste des paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="b0f33-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="b0f33-112">Requis.</span><span class="sxs-lookup"><span data-stu-id="b0f33-112">Required.</span></span> <span data-ttu-id="b0f33-113">Expression unique.</span><span class="sxs-lookup"><span data-stu-id="b0f33-113">A single expression.</span></span> <span data-ttu-id="b0f33-114">Le type de l’expression est le type de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b0f33-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="b0f33-115">Requis.</span><span class="sxs-lookup"><span data-stu-id="b0f33-115">Required.</span></span> <span data-ttu-id="b0f33-116">Liste d’instructions qui retourne une valeur à l’aide de l’instruction `Return`.</span><span class="sxs-lookup"><span data-stu-id="b0f33-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="b0f33-117">(Consultez [instruction return](../../../visual-basic/language-reference/statements/return-statement.md).) Le type de la valeur retournée est le type de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b0f33-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0f33-118">Notes</span><span class="sxs-lookup"><span data-stu-id="b0f33-118">Remarks</span></span>  
 <span data-ttu-id="b0f33-119">Une *expression lambda* est une fonction sans nom qui calcule et retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="b0f33-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="b0f33-120">Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu’argument pour `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="b0f33-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="b0f33-121">Pour plus d’informations sur les délégués et l’utilisation d’expressions lambda avec des délégués, consultez [instruction de délégué](../../../visual-basic/language-reference/statements/delegate-statement.md) et [conversion simplifiée](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)des délégués.</span><span class="sxs-lookup"><span data-stu-id="b0f33-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="b0f33-122">Syntaxe d’expression lambda</span><span class="sxs-lookup"><span data-stu-id="b0f33-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="b0f33-123">La syntaxe d’une expression lambda ressemble à celle d’une fonction standard.</span><span class="sxs-lookup"><span data-stu-id="b0f33-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="b0f33-124">Les différences sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b0f33-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="b0f33-125">Une expression lambda n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="b0f33-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="b0f33-126">Les expressions lambda ne peuvent pas avoir de modificateurs, tels que `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="b0f33-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="b0f33-127">Les expressions lambda n’utilisent pas de clause `As` pour désigner le type de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="b0f33-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="b0f33-128">Au lieu de cela, le type est déduit de la valeur à laquelle le corps d’une expression lambda sur une seule ligne prend la valeur, ou la valeur de retour d’une expression lambda multiligne.</span><span class="sxs-lookup"><span data-stu-id="b0f33-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="b0f33-129">Par exemple, si le corps d’une expression lambda sur une seule ligne est `Where cust.City = "London"`, son type de retour est `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b0f33-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="b0f33-130">Le corps d’une expression lambda sur une seule ligne doit être une expression, et non une instruction.</span><span class="sxs-lookup"><span data-stu-id="b0f33-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="b0f33-131">Le corps peut se composer d’un appel à une procédure de fonction, mais pas d’un appel à une procédure Sub.</span><span class="sxs-lookup"><span data-stu-id="b0f33-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="b0f33-132">Tous les paramètres doivent avoir des types de données spécifiés ou tous doivent être déduits.</span><span class="sxs-lookup"><span data-stu-id="b0f33-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="b0f33-133">Les paramètres facultatifs et ParamArray ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="b0f33-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="b0f33-134">Les paramètres génériques ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="b0f33-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0f33-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="b0f33-135">Example</span></span>  
 <span data-ttu-id="b0f33-136">Les exemples suivants illustrent deux façons de créer des expressions lambda simples.</span><span class="sxs-lookup"><span data-stu-id="b0f33-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="b0f33-137">La première utilise un `Dim` pour fournir un nom pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="b0f33-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="b0f33-138">Pour appeler la fonction, vous devez envoyer une valeur pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="b0f33-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="b0f33-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="b0f33-139">Example</span></span>  
 <span data-ttu-id="b0f33-140">Vous pouvez également déclarer et exécuter la fonction en même temps.</span><span class="sxs-lookup"><span data-stu-id="b0f33-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b0f33-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="b0f33-141">Example</span></span>  
 <span data-ttu-id="b0f33-142">Voici un exemple d’expression lambda qui incrémente son argument et retourne la valeur.</span><span class="sxs-lookup"><span data-stu-id="b0f33-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="b0f33-143">L’exemple montre la syntaxe d’expression lambda à ligne unique et multiligne pour une fonction.</span><span class="sxs-lookup"><span data-stu-id="b0f33-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="b0f33-144">Pour obtenir plus d’exemples, consultez [expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b0f33-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="b0f33-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="b0f33-145">Example</span></span>  
 <span data-ttu-id="b0f33-146">Les expressions lambda sont sous-jacentes de nombreux opérateurs de requête dans [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]et peuvent être utilisées explicitement dans les requêtes basées sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="b0f33-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="b0f33-147">L’exemple suivant montre une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] classique, suivie de la traduction de la requête en format de méthode.</span><span class="sxs-lookup"><span data-stu-id="b0f33-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="b0f33-148">Pour plus d’informations sur les méthodes de requête, consultez [requêtes](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="b0f33-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="b0f33-149">Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble des opérateurs de requête standard](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b0f33-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f33-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0f33-150">See also</span></span>

- [<span data-ttu-id="b0f33-151">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="b0f33-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="b0f33-152">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="b0f33-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="b0f33-153">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="b0f33-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="b0f33-154">Instructions</span><span class="sxs-lookup"><span data-stu-id="b0f33-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="b0f33-155">Comparaisons de valeurs</span><span class="sxs-lookup"><span data-stu-id="b0f33-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="b0f33-156">Expressions booléennes</span><span class="sxs-lookup"><span data-stu-id="b0f33-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="b0f33-157">If (opérateur)</span><span class="sxs-lookup"><span data-stu-id="b0f33-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="b0f33-158">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="b0f33-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
