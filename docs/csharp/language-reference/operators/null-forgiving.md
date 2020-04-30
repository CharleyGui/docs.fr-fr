---
title: '! opérateur (null-indulgent avec)-référence C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 772f37f1fc7446eae66f0cd0f12adb5e2e41997d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595947"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="675d3-103">!</span><span class="sxs-lookup"><span data-stu-id="675d3-103">!</span></span> <span data-ttu-id="675d3-104">(null-indulgent avec), opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="675d3-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="675d3-105">Disponible en C# 8,0 et versions ultérieures, l' `!` opérateur postfix unaire est l’opérateur null-indulgent avec.</span><span class="sxs-lookup"><span data-stu-id="675d3-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="675d3-106">Dans un [contexte d’annotation Nullable](../../nullable-references.md#nullable-annotation-context)activé, vous utilisez l’opérateur null-indulgent avec pour déclarer que `x` l’expression d’un type `null`référence `x!`n’est pas :.</span><span class="sxs-lookup"><span data-stu-id="675d3-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="675d3-107">L’opérateur préfixé `!` unaire est l' [opérateur de négation logique](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="675d3-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="675d3-108">L’opérateur null-indulgent avec n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="675d3-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="675d3-109">Elle affecte uniquement l’analyse du déroulement statique du compilateur en modifiant l’État null de l’expression.</span><span class="sxs-lookup"><span data-stu-id="675d3-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="675d3-110">Au moment de l’exécution `x!` , l’expression prend la valeur du résultat de `x`l’expression sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="675d3-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="675d3-111">En C# 8, l’opérateur null-indulgent avec interagit avec les [opérateurs conditionnels null](member-access-operators.md#null-conditional-operators--and-) d’une manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="675d3-111">In C# 8 the null-forgiving operator interacts with the [null-conditional operators](member-access-operators.md#null-conditional-operators--and-) in an unexpected way.</span></span> <span data-ttu-id="675d3-112">L’expression `x?.y!.z` est analysée en `(x?.y)!.z`tant que.</span><span class="sxs-lookup"><span data-stu-id="675d3-112">The expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="675d3-113">En raison de cette `z` interprétation, elle est `x` évaluée même si a `null`la valeur <xref:System.NullReferenceException>, ce qui peut entraîner un.</span><span class="sxs-lookup"><span data-stu-id="675d3-113">Due to this interpretation `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="675d3-114">Pour plus d’informations sur la fonctionnalité des types de référence Nullable, consultez [types de référence Nullable](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="675d3-114">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="675d3-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="675d3-115">Examples</span></span>

<span data-ttu-id="675d3-116">L’un des cas d’usage de l’opérateur null-indulgent avec consiste à tester la logique de validation d’argument.</span><span class="sxs-lookup"><span data-stu-id="675d3-116">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="675d3-117">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="675d3-117">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="675d3-118">À l’aide de l' [infrastructure de test MSTest](../../../core/testing/unit-testing-with-mstest.md), vous pouvez créer le test suivant pour la logique de validation dans le constructeur :</span><span class="sxs-lookup"><span data-stu-id="675d3-118">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="675d3-119">Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le code précédent : `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="675d3-119">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="675d3-120">En utilisant l’opérateur null-indulgent avec, vous informez le compilateur `null` que le passage est attendu et ne doit pas être averti de.</span><span class="sxs-lookup"><span data-stu-id="675d3-120">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="675d3-121">Vous pouvez également utiliser l’opérateur null-indulgent avec lorsque vous savez absolument qu’une expression ne peut `null` pas être, mais que le compilateur ne gère pas.</span><span class="sxs-lookup"><span data-stu-id="675d3-121">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="675d3-122">Dans l’exemple suivant, si la `IsValid` méthode retourne `true`, son argument n’est `null` pas et vous pouvez la déréférencer en toute sécurité :</span><span class="sxs-lookup"><span data-stu-id="675d3-122">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="675d3-123">Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le `p.Name` code : `Warning CS8602: Dereference of a possibly null reference`.</span><span class="sxs-lookup"><span data-stu-id="675d3-123">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="675d3-124">Si vous pouvez modifier la `IsValid` méthode, vous pouvez utiliser l’attribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) pour informer le compilateur qu’un argument de la `IsValid` méthode ne peut `null` pas être lorsque la `true`méthode retourne :</span><span class="sxs-lookup"><span data-stu-id="675d3-124">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="675d3-125">Dans l’exemple précédent, vous n’avez pas besoin d’utiliser l’opérateur null-indulgent avec, car le compilateur dispose de suffisamment d' `p` informations pour `null` déterminer qu' `if` il ne peut pas se trouver à l’intérieur de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="675d3-125">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="675d3-126">Pour plus d’informations sur les attributs qui vous permettent de fournir des informations supplémentaires sur l’État null d’une variable, consultez [mettre à niveau les API avec des attributs pour définir des attentes null](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="675d3-126">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="675d3-127">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="675d3-127">C# language specification</span></span>

<span data-ttu-id="675d3-128">Pour plus d’informations, consultez [la section opérateur null-indulgent avec](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) du [brouillon de la spécification des types de référence Nullable](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="675d3-128">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="675d3-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="675d3-129">See also</span></span>

- [<span data-ttu-id="675d3-130">Référence C#</span><span class="sxs-lookup"><span data-stu-id="675d3-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="675d3-131">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="675d3-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="675d3-132">Didacticiel : concevoir avec des types de référence Nullable</span><span class="sxs-lookup"><span data-stu-id="675d3-132">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
