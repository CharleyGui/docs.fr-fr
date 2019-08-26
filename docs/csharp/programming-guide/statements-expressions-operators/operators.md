---
title: Opérateurs - Guide de programmation C#
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 4870c744383205c2b7e3832c01fb838a545f085f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588609"
---
# <a name="operators-c-programming-guide"></a><span data-ttu-id="b81c0-102">Opérateurs (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b81c0-102">Operators (C# Programming Guide)</span></span>

<span data-ttu-id="b81c0-103">En C#, un *opérateur* est un élément de programme qui s'applique à un ou plusieurs *opérandes* dans une expression ou une instruction.</span><span class="sxs-lookup"><span data-stu-id="b81c0-103">In C#, an *operator* is a program element that is applied to one or more *operands* in an expression or statement.</span></span> <span data-ttu-id="b81c0-104">Les opérateurs qui prennent un opérande, comme l'opérateur d'incrément (`++`) ou `new`, portent le nom d'opérateurs *unaires* .</span><span class="sxs-lookup"><span data-stu-id="b81c0-104">Operators that take one operand, such as the increment operator (`++`) or `new`, are referred to as *unary* operators.</span></span> <span data-ttu-id="b81c0-105">Les opérateurs qui prennent deux opérandes, comme les opérateurs arithmétiques (`+`,`-`,`*`,`/`) portent le nom d'opérateur *binaires* .</span><span class="sxs-lookup"><span data-stu-id="b81c0-105">Operators that take two operands, such as arithmetic operators (`+`,`-`,`*`,`/`), are referred to as *binary* operators.</span></span> <span data-ttu-id="b81c0-106">Un opérateur, l'opérateur conditionnel (`?:`), prend trois opérandes et est le seul opérateur ternaire en C#.</span><span class="sxs-lookup"><span data-stu-id="b81c0-106">One operator, the conditional operator (`?:`), takes three operands and is the sole ternary operator in C#.</span></span>  
  
 <span data-ttu-id="b81c0-107">L'instruction C# suivante contient un seul opérateur unaire et un seul opérande.</span><span class="sxs-lookup"><span data-stu-id="b81c0-107">The following C# statement contains a single unary operator and a single operand.</span></span> <span data-ttu-id="b81c0-108">L'opérateur d'incrément, `++`, modifie la valeur de l'opérande `y`.</span><span class="sxs-lookup"><span data-stu-id="b81c0-108">The increment operator, `++`, modifies the value of the operand `y`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 <span data-ttu-id="b81c0-109">L'instruction C# suivante contient deux opérateurs binaires, chacun avec deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="b81c0-109">The following C# statement contains two binary operators, each with two operands.</span></span> <span data-ttu-id="b81c0-110">L'opérateur d'assignation, `=`, a la variable de type entier `y` et l'expression `2 + 3` comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="b81c0-110">The assignment operator, `=`, has the integer variable `y` and the expression `2 + 3` as operands.</span></span> <span data-ttu-id="b81c0-111">L'expression `2 + 3` elle-même se compose de l'opérateur Addition et de deux opérandes, `2` et `3`.</span><span class="sxs-lookup"><span data-stu-id="b81c0-111">The expression `2 + 3` itself consists of the addition operator and two operands, `2` and `3`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
<span data-ttu-id="b81c0-112">Un opérande peut être une expression valide qui est composée d'une longueur quelconque de code, et qui peut comporter plusieurs sous-expressions.</span><span class="sxs-lookup"><span data-stu-id="b81c0-112">An operand can be a valid expression that is composed of any length of code, and it can comprise any number of sub expressions.</span></span> <span data-ttu-id="b81c0-113">Dans une expression qui contient plusieurs opérateurs, l'ordre dans lequel les opérateurs sont appliqués est déterminé par la *priorité des opérateurs*, *l'associativité*et les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="b81c0-113">In an expression that contains multiple operators, the order in which the operators are applied is determined by *operator precedence*, *associativity*, and parentheses.</span></span>  

## <a name="operator-precedence"></a><span data-ttu-id="b81c0-114">Précédence des opérateurs</span><span class="sxs-lookup"><span data-stu-id="b81c0-114">Operator precedence</span></span>
  
<span data-ttu-id="b81c0-115">Chaque opérateur a une priorité définie.</span><span class="sxs-lookup"><span data-stu-id="b81c0-115">Each operator has a defined precedence.</span></span> <span data-ttu-id="b81c0-116">Dans une expression qui contient plusieurs opérateurs ayant différents niveaux de priorité, la priorité des opérateurs détermine l'ordre dans lequel les opérateurs sont évalués.</span><span class="sxs-lookup"><span data-stu-id="b81c0-116">In an expression that contains multiple operators that have different precedence levels, the precedence of the operators determines the order in which the operators are evaluated.</span></span> <span data-ttu-id="b81c0-117">Par exemple, l’instruction suivante assigne la valeur 3 à `n1` :</span><span class="sxs-lookup"><span data-stu-id="b81c0-117">For example, the following statement assigns 3 to `n1`:</span></span>

```csharp
n1 = 11 - 2 * 4;
```

<span data-ttu-id="b81c0-118">La multiplication est effectuée en premier lieu parce que la multiplication est prioritaire sur la soustraction.</span><span class="sxs-lookup"><span data-stu-id="b81c0-118">The multiplication is executed first because multiplication takes precedence over subtraction.</span></span>

<span data-ttu-id="b81c0-119">Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](../../language-reference/operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="b81c0-119">For the complete list of C# operators ordered by precedence level, see [C# operators](../../language-reference/operators/index.md).</span></span>
  
## <a name="associativity"></a><span data-ttu-id="b81c0-120">l'associativité</span><span class="sxs-lookup"><span data-stu-id="b81c0-120">Associativity</span></span>

 <span data-ttu-id="b81c0-121">Lorsque deux opérateurs ou plus, de même niveau de priorité figurent dans une expression, ils sont évalués sur la base de l'associativité.</span><span class="sxs-lookup"><span data-stu-id="b81c0-121">When two or more operators that have the same precedence are present in an expression, they are evaluated based on associativity.</span></span> <span data-ttu-id="b81c0-122">Les opérateurs associatifs sur leur gauche sont évalués dans l'ordre, de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="b81c0-122">Left-associative operators are evaluated in order from left to right.</span></span> <span data-ttu-id="b81c0-123">Par exemple, `x * y / z` est évalué comme étant `(x * y) / z`.</span><span class="sxs-lookup"><span data-stu-id="b81c0-123">For example, `x * y / z` is evaluated as `(x * y) / z`.</span></span> <span data-ttu-id="b81c0-124">Les opérateurs associatifs sur leur droite sont évalués dans l'ordre, de droite à gauche.</span><span class="sxs-lookup"><span data-stu-id="b81c0-124">Right-associative operators are evaluated in order from right to left.</span></span> <span data-ttu-id="b81c0-125">Par exemple, l'opérateur d'assignation est associatif sur sa droite.</span><span class="sxs-lookup"><span data-stu-id="b81c0-125">For example, the assignment operator is right associative.</span></span> <span data-ttu-id="b81c0-126">Dans le cas contraire, le code suivant génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="b81c0-126">If it were not, the following code would result in an error.</span></span>  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 <span data-ttu-id="b81c0-127">Autre exemple, l’opérateur ternaire ([?:](../../language-reference/operators/conditional-operator.md)) est associatif sur sa droite.</span><span class="sxs-lookup"><span data-stu-id="b81c0-127">As another example the ternary operator ([?:](../../language-reference/operators/conditional-operator.md)) is right associative.</span></span> <span data-ttu-id="b81c0-128">La plupart des opérateurs binaires sont associatifs sur leur gauche.</span><span class="sxs-lookup"><span data-stu-id="b81c0-128">Most binary operators are left associative.</span></span>  
  
 <span data-ttu-id="b81c0-129">Si les opérateurs présents dans une expression sont associatifs sur leur gauche ou associatifs sur leur droite, les opérandes de chaque expression sont évalués en premier, de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="b81c0-129">Whether the operators in an expression are left associative or right associative, the operands of each expression are evaluated first, from left to right.</span></span> <span data-ttu-id="b81c0-130">Les exemples suivants illustrent l'ordre d'évaluation des opérateurs et des opérandes.</span><span class="sxs-lookup"><span data-stu-id="b81c0-130">The following examples illustrate the order of evaluation of operators and operands.</span></span>  
  
|<span data-ttu-id="b81c0-131">Instruction</span><span class="sxs-lookup"><span data-stu-id="b81c0-131">Statement</span></span>|<span data-ttu-id="b81c0-132">Ordre d'évaluation</span><span class="sxs-lookup"><span data-stu-id="b81c0-132">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = b`|<span data-ttu-id="b81c0-133">a, b, =</span><span class="sxs-lookup"><span data-stu-id="b81c0-133">a, b, =</span></span>|  
|`a = b + c`|<span data-ttu-id="b81c0-134">a, b, c, +, =</span><span class="sxs-lookup"><span data-stu-id="b81c0-134">a, b, c, +, =</span></span>|  
|`a = b + c * d`|<span data-ttu-id="b81c0-135">a, b, c, d, \*, +, =</span><span class="sxs-lookup"><span data-stu-id="b81c0-135">a, b, c, d, \*, +, =</span></span>|  
|`a = b * c + d`|<span data-ttu-id="b81c0-136">a, b, c, \*, d, +, =</span><span class="sxs-lookup"><span data-stu-id="b81c0-136">a, b, c, \*, d, +, =</span></span>|  
|`a = b - c + d`|<span data-ttu-id="b81c0-137">a, b, c, -, d, +, =</span><span class="sxs-lookup"><span data-stu-id="b81c0-137">a, b, c, -, d, +, =</span></span>|  
|`a += b -= c`|<span data-ttu-id="b81c0-138">a, b, c, -=, +=</span><span class="sxs-lookup"><span data-stu-id="b81c0-138">a, b, c, -=, +=</span></span>|  
  
## <a name="adding-parentheses"></a><span data-ttu-id="b81c0-139">Ajout de parenthèses</span><span class="sxs-lookup"><span data-stu-id="b81c0-139">Adding parentheses</span></span>

 <span data-ttu-id="b81c0-140">Vous pouvez modifier l'ordre imposé par la priorité d'opérateur et l'associativité en utilisant des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="b81c0-140">You can change the order imposed by operator precedence and associativity by using parentheses.</span></span> <span data-ttu-id="b81c0-141">Par exemple, `2 + 3 * 2` correspond généralement à 8, car les opérateurs de multiplication ont la priorité sur les opérateurs additifs.</span><span class="sxs-lookup"><span data-stu-id="b81c0-141">For example, `2 + 3 * 2` ordinarily evaluates to 8, because multiplicative operators take precedence over additive operators.</span></span> <span data-ttu-id="b81c0-142">Toutefois, si vous entrez une expression comme `(2 + 3) * 2`, l'addition est évaluée avant la multiplication, et le résultat est 10.</span><span class="sxs-lookup"><span data-stu-id="b81c0-142">However, if you write the expression as `(2 + 3) * 2`, the addition is evaluated before the multiplication, and the result is 10.</span></span> <span data-ttu-id="b81c0-143">Les exemples suivants illustrent l'ordre d'évaluation dans les expressions entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="b81c0-143">The following examples illustrate the order of evaluation in parenthesized expressions.</span></span> <span data-ttu-id="b81c0-144">Comme dans les exemples précédents, l'évaluation des opérandes a lieu avant l'application de l'opérateur.</span><span class="sxs-lookup"><span data-stu-id="b81c0-144">As in previous examples, the operands are evaluated before the operator is applied.</span></span>  
  
|<span data-ttu-id="b81c0-145">Instruction</span><span class="sxs-lookup"><span data-stu-id="b81c0-145">Statement</span></span>|<span data-ttu-id="b81c0-146">Ordre d'évaluation</span><span class="sxs-lookup"><span data-stu-id="b81c0-146">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = (b + c) * d`|<span data-ttu-id="b81c0-147">a, b, c, +, d, \*, =</span><span class="sxs-lookup"><span data-stu-id="b81c0-147">a, b, c, +, d, \*, =</span></span>|  
|`a = b - (c + d)`|<span data-ttu-id="b81c0-148">a, b, c, d, +, -, =</span><span class="sxs-lookup"><span data-stu-id="b81c0-148">a, b, c, d, +, -, =</span></span>|  
|`a = (b + c) * (d - e)`|<span data-ttu-id="b81c0-149">a, b, c, +, d, e, -, \*, =</span><span class="sxs-lookup"><span data-stu-id="b81c0-149">a, b, c, +, d, e, -, \*, =</span></span>|  
  
## <a name="operator-overloading"></a><span data-ttu-id="b81c0-150">Surcharge d’opérateur</span><span class="sxs-lookup"><span data-stu-id="b81c0-150">Operator overloading</span></span>

<span data-ttu-id="b81c0-151">Vous pouvez définir le comportement de certains opérateurs pour les classes et les structs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="b81c0-151">You can define the behavior of certain operators for custom classes and structs.</span></span> <span data-ttu-id="b81c0-152">Ce processus est connu sous le nom de *surcharge d'opérateur*.</span><span class="sxs-lookup"><span data-stu-id="b81c0-152">This process is referred to as *operator overloading*.</span></span> <span data-ttu-id="b81c0-153">Pour plus d’informations, consultez [Surcharge d’opérateur](../../language-reference/operators/operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="b81c0-153">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b81c0-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b81c0-154">See also</span></span>

- [<span data-ttu-id="b81c0-155">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b81c0-155">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b81c0-156">Instructions, expressions et opérateurs</span><span class="sxs-lookup"><span data-stu-id="b81c0-156">Statements, Expressions, and Operators</span></span>](index.md)
- [<span data-ttu-id="b81c0-157">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="b81c0-157">C# Operators</span></span>](../../language-reference/operators/index.md)
