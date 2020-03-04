---
title: Opérateur >= - Référence C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 5df1ae60ddc298f75d70db7769ec1bf1d21b8ef2
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239285"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c41c9-102">Opérateur >= (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c41c9-102">=> operator (C# reference)</span></span>

<span data-ttu-id="c41c9-103">Le jeton `=>` est pris en charge sous deux formes : comme [opérateur lambda](#lambda-operator) et comme séparateur d’un nom de membre et l’implémentation de membre dans une [définition de corps d’expression](#expression-body-definition).</span><span class="sxs-lookup"><span data-stu-id="c41c9-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="c41c9-104">Opérateur lamdba</span><span class="sxs-lookup"><span data-stu-id="c41c9-104">Lambda operator</span></span>

<span data-ttu-id="c41c9-105">Dans les [expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), l’opérateur lambda `=>` sépare les paramètres d’entrée du côté gauche du corps lambda situé à droite.</span><span class="sxs-lookup"><span data-stu-id="c41c9-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="c41c9-106">L’exemple suivant utilise la fonctionnalité [LINQ](../../programming-guide/concepts/linq/index.md) avec la syntaxe de méthode pour illustrer l’utilisation d’expressions lambda :</span><span class="sxs-lookup"><span data-stu-id="c41c9-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="c41c9-107">Les paramètres d’entrée d’une expression lambda sont fortement typés au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="c41c9-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="c41c9-108">Lorsque le compilateur peut déduire les types de paramètres d’entrée, comme dans l’exemple précédent, vous pouvez omettre des déclarations de type.</span><span class="sxs-lookup"><span data-stu-id="c41c9-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="c41c9-109">Si vous devez spécifier le type des paramètres d’entrée, vous devez le faire pour chaque paramètre, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c41c9-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="c41c9-110">L’exemple suivant montre comment définir une expression lambda sans paramètres d’entrée :</span><span class="sxs-lookup"><span data-stu-id="c41c9-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="c41c9-111">Pour plus d’informations, consultez [Expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c41c9-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="c41c9-112">Définition de corps d’expression</span><span class="sxs-lookup"><span data-stu-id="c41c9-112">Expression body definition</span></span>

<span data-ttu-id="c41c9-113">La syntaxe générale d’une définition de corps d’expression est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c41c9-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="c41c9-114">où `expression` est une expression valide.</span><span class="sxs-lookup"><span data-stu-id="c41c9-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="c41c9-115">Le type de retour de `expression` doit être implicitement convertible en type de retour du membre.</span><span class="sxs-lookup"><span data-stu-id="c41c9-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="c41c9-116">Si le type de retour du membre est `void` ou si le membre est un constructeur, un finaliseur ou un accesseur de propriété `set`, `expression` doit être une [*expression d’instruction*](~/_csharplang/spec/statements.md#expression-statements), qui peut être de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="c41c9-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements), which can be of any type.</span></span>

<span data-ttu-id="c41c9-117">L’exemple suivant montre une définition de corps d’expression pour une méthode `Person.ToString` :</span><span class="sxs-lookup"><span data-stu-id="c41c9-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="c41c9-118">Il s’agit d’une version raccourcie de la définition de méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="c41c9-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="c41c9-119">Les définitions de corps d’expression pour les méthodes, les opérateurs et les propriétés en lecture C# seule sont prises en charge à partir de 6.</span><span class="sxs-lookup"><span data-stu-id="c41c9-119">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="c41c9-120">Les définitions de corps d’expression pour les constructeurs, les finaliseurs et les accesseurs de propriété et d' C# indexeur sont pris en charge à partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="c41c9-120">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="c41c9-121">Pour plus d’informations, consultez [Membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="c41c9-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c41c9-122">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="c41c9-122">Operator overloadability</span></span>

<span data-ttu-id="c41c9-123">L’opérateur `=>` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="c41c9-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c41c9-124">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="c41c9-124">C# language specification</span></span>

<span data-ttu-id="c41c9-125">Pour plus d’informations sur l’opérateur lambda, consultez la section [expressions de fonction anonymes](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c41c9-125">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c41c9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c41c9-126">See also</span></span>

- [<span data-ttu-id="c41c9-127">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="c41c9-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c41c9-128">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="c41c9-128">C# operators</span></span>](index.md)
