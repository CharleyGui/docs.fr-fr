---
description: '! opérateur (null-indulgent avec)-référence C#'
title: '! opérateur (null-indulgent avec)-référence C#'
ms.date: 11/13/2020
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 5489c77fa7290bdd1c03e04d8cc777ab772fdce7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699628"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="14f9d-105">!</span><span class="sxs-lookup"><span data-stu-id="14f9d-105">!</span></span> <span data-ttu-id="14f9d-106">(null-indulgent avec), opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="14f9d-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="14f9d-107">Disponible en C# 8,0 et versions ultérieures, l’opérateur postfix unaire `!` est l’opérateur null-indulgent avec.</span><span class="sxs-lookup"><span data-stu-id="14f9d-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="14f9d-108">Dans un [contexte d’annotation Nullable](../../nullable-references.md#nullable-annotation-context)activé, vous utilisez l’opérateur null-indulgent avec pour déclarer que l’expression `x` d’un type référence n’est pas `null` : `x!` .</span><span class="sxs-lookup"><span data-stu-id="14f9d-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="14f9d-109">L’opérateur préfixé unaire `!` est l' [opérateur de négation logique](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="14f9d-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="14f9d-110">L’opérateur null-indulgent avec n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="14f9d-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="14f9d-111">Elle affecte uniquement l’analyse du déroulement statique du compilateur en modifiant l’État null de l’expression.</span><span class="sxs-lookup"><span data-stu-id="14f9d-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="14f9d-112">Au moment de l’exécution, l’expression `x!` prend la valeur du résultat de l’expression sous-jacente `x` .</span><span class="sxs-lookup"><span data-stu-id="14f9d-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="14f9d-113">Pour plus d’informations sur la fonctionnalité des types de référence Nullable, consultez [types de référence Nullable](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="14f9d-113">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="14f9d-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="14f9d-114">Examples</span></span>

<span data-ttu-id="14f9d-115">L’un des cas d’usage de l’opérateur null-indulgent avec consiste à tester la logique de validation d’argument.</span><span class="sxs-lookup"><span data-stu-id="14f9d-115">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="14f9d-116">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="14f9d-116">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="14f9d-117">À l’aide de l' [infrastructure de test MSTest](../../../core/testing/unit-testing-with-mstest.md), vous pouvez créer le test suivant pour la logique de validation dans le constructeur :</span><span class="sxs-lookup"><span data-stu-id="14f9d-117">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="14f9d-118">Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le code précédent : `Warning CS8625: Cannot convert null literal to non-nullable reference type` .</span><span class="sxs-lookup"><span data-stu-id="14f9d-118">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="14f9d-119">En utilisant l’opérateur null-indulgent avec, vous informez le compilateur que le passage `null` est attendu et ne doit pas être averti de.</span><span class="sxs-lookup"><span data-stu-id="14f9d-119">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="14f9d-120">Vous pouvez également utiliser l’opérateur null-indulgent avec lorsque vous savez absolument qu’une expression ne peut pas être, `null` mais que le compilateur ne gère pas.</span><span class="sxs-lookup"><span data-stu-id="14f9d-120">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="14f9d-121">Dans l’exemple suivant, si la `IsValid` méthode retourne `true` , son argument n’est pas `null` et vous pouvez la déréférencer en toute sécurité :</span><span class="sxs-lookup"><span data-stu-id="14f9d-121">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="14f9d-122">Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le `p.Name` Code : `Warning CS8602: Dereference of a possibly null reference` .</span><span class="sxs-lookup"><span data-stu-id="14f9d-122">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="14f9d-123">Si vous pouvez modifier la `IsValid` méthode, vous pouvez utiliser l’attribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) pour informer le compilateur qu’un argument de la `IsValid` méthode ne peut pas être `null` lorsque la méthode retourne `true` :</span><span class="sxs-lookup"><span data-stu-id="14f9d-123">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="14f9d-124">Dans l’exemple précédent, vous n’avez pas besoin d’utiliser l’opérateur null-indulgent avec, car le compilateur dispose de suffisamment d’informations pour déterminer qu’il `p` ne peut pas se trouver `null` à l’intérieur de l' `if` instruction.</span><span class="sxs-lookup"><span data-stu-id="14f9d-124">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="14f9d-125">Pour plus d’informations sur les attributs qui vous permettent de fournir des informations supplémentaires sur l’État null d’une variable, consultez [mettre à niveau les API avec des attributs pour définir des attentes null](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="14f9d-125">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="14f9d-126">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="14f9d-126">C# language specification</span></span>

<span data-ttu-id="14f9d-127">Pour plus d’informations, consultez [la section opérateur null-indulgent avec](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) du [brouillon de la spécification des types de référence Nullable](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="14f9d-127">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14f9d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14f9d-128">See also</span></span>

- [<span data-ttu-id="14f9d-129">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="14f9d-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="14f9d-130">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="14f9d-130">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="14f9d-131">Didacticiel : concevoir avec des types de référence Nullable</span><span class="sxs-lookup"><span data-stu-id="14f9d-131">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
