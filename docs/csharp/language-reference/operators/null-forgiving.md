---
title: '! (null-indulgent avec)- C# référence d’opérateur'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 865e55a28e2f3db85d50a81f6ab29c354ee3c62a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319093"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="6a04f-103">!</span><span class="sxs-lookup"><span data-stu-id="6a04f-103">!</span></span> <span data-ttu-id="6a04f-104">(null-indulgent avec), opérateurC# (référence)</span><span class="sxs-lookup"><span data-stu-id="6a04f-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="6a04f-105">Disponible dans C# 8,0 et versions ultérieures, l’opérateur postfix unaire `!` est l’opérateur null-indulgent avec.</span><span class="sxs-lookup"><span data-stu-id="6a04f-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="6a04f-106">Dans un [contexte d’annotation Nullable](../../nullable-references.md#nullable-annotation-context)activé, vous utilisez l’opérateur null-indulgent avec pour déclarer que l’expression `x` d’un type référence n’est pas null : `x!`.</span><span class="sxs-lookup"><span data-stu-id="6a04f-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't null: `x!`.</span></span> <span data-ttu-id="6a04f-107">Le préfixe unaire @no__t opérateur-0 est l' [opérateur de négation logique](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="6a04f-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="6a04f-108">L’opérateur null-indulgent avec n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6a04f-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="6a04f-109">Elle affecte uniquement l’analyse du déroulement statique du compilateur en modifiant l’État null de l’expression.</span><span class="sxs-lookup"><span data-stu-id="6a04f-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="6a04f-110">Au moment de l’exécution, l’expression `x!` correspond au résultat de l’expression sous-jacente `x`.</span><span class="sxs-lookup"><span data-stu-id="6a04f-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="6a04f-111">Pour plus d’informations sur la fonctionnalité des types de référence Nullable, consultez [types de référence Nullable](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="6a04f-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="6a04f-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="6a04f-112">Examples</span></span>

<span data-ttu-id="6a04f-113">L’un des cas d’usage de l’opérateur null-indulgent avec consiste à tester la logique de validation d’argument.</span><span class="sxs-lookup"><span data-stu-id="6a04f-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="6a04f-114">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="6a04f-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="6a04f-115">À l’aide de l' [infrastructure de test MSTest](../../../core/testing/unit-testing-with-mstest.md), vous pouvez créer le test suivant pour la logique de validation dans le constructeur :</span><span class="sxs-lookup"><span data-stu-id="6a04f-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="6a04f-116">Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le code précédent : `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="6a04f-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="6a04f-117">Avec l’utilisation de l’opérateur null-indulgent avec, vous laissez le compilateur savoir que le passage de `null` est attendu et ne doit pas être averti de.</span><span class="sxs-lookup"><span data-stu-id="6a04f-117">With the use of the null-forgiving operator, you let the compiler know that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="6a04f-118">Vous pouvez également utiliser l’opérateur null-indulgent avec lorsque vous savez absolument qu’une expression ne peut pas être `null`, mais que le compilateur ne gère pas.</span><span class="sxs-lookup"><span data-stu-id="6a04f-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="6a04f-119">Dans l’exemple suivant, si la méthode `IsValid` retourne `true`, son argument n’est pas `null` et vous pouvez le déréférencer en toute sécurité :</span><span class="sxs-lookup"><span data-stu-id="6a04f-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="6a04f-120">Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le code `p.Name` : `Warning CS8602: Dereference of a possibly null reference`.</span><span class="sxs-lookup"><span data-stu-id="6a04f-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="6a04f-121">Si vous pouvez modifier la méthode `IsValid`, vous pouvez utiliser l’attribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) pour informer le compilateur qu’un argument de la méthode `IsValid` ne peut pas être `null` lorsque la méthode retourne `true` :</span><span class="sxs-lookup"><span data-stu-id="6a04f-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to let the compiler know that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="6a04f-122">Dans l’exemple précédent, vous n’avez pas besoin d’utiliser l’opérateur null-indulgent avec, car le compilateur dispose de suffisamment d’informations pour déterminer que `p` ne peut pas être `null` à l’intérieur de l’instruction `if`.</span><span class="sxs-lookup"><span data-stu-id="6a04f-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="6a04f-123">Pour plus d’informations sur les attributs qui vous permettent de spécifier des informations supplémentaires sur l’État null d’une variable, consultez [mettre à niveau les API avec des attributs pour définir des attentes null](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6a04f-123">For more information about the attributes that allow you to specify additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6a04f-124">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6a04f-124">C# language specification</span></span>

<span data-ttu-id="6a04f-125">Pour plus d’informations, consultez [la section opérateur null-indulgent avec](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) du [brouillon de la spécification des types de référence Nullable](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="6a04f-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a04f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a04f-126">See also</span></span>

- [<span data-ttu-id="6a04f-127">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="6a04f-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6a04f-128">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="6a04f-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="6a04f-129">Didacticiel : concevoir avec des types de référence Nullable</span><span class="sxs-lookup"><span data-stu-id="6a04f-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
