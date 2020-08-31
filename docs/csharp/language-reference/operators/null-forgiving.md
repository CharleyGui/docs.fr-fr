---
description: '! opérateur (null-indulgent avec)-référence C#'
title: '! opérateur (null-indulgent avec)-référence C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 7ae35f4741e1ef377b73a15066dddd243c94d8fe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118219"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="49564-105">!</span><span class="sxs-lookup"><span data-stu-id="49564-105">!</span></span> <span data-ttu-id="49564-106">(null-indulgent avec), opérateur (référence C#)</span><span class="sxs-lookup"><span data-stu-id="49564-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="49564-107">Disponible en C# 8,0 et versions ultérieures, l’opérateur postfix unaire `!` est l’opérateur null-indulgent avec.</span><span class="sxs-lookup"><span data-stu-id="49564-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="49564-108">Dans un [contexte d’annotation Nullable](../../nullable-references.md#nullable-annotation-context)activé, vous utilisez l’opérateur null-indulgent avec pour déclarer que l’expression `x` d’un type référence n’est pas `null` : `x!` .</span><span class="sxs-lookup"><span data-stu-id="49564-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="49564-109">L’opérateur préfixé unaire `!` est l' [opérateur de négation logique](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="49564-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="49564-110">L’opérateur null-indulgent avec n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="49564-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="49564-111">Elle affecte uniquement l’analyse du déroulement statique du compilateur en modifiant l’État null de l’expression.</span><span class="sxs-lookup"><span data-stu-id="49564-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="49564-112">Au moment de l’exécution, l’expression `x!` prend la valeur du résultat de l’expression sous-jacente `x` .</span><span class="sxs-lookup"><span data-stu-id="49564-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="49564-113">En C# 8, l’opérateur null-indulgent avec met fin à la liste des opérations [conditionnelles null](member-access-operators.md#null-conditional-operators--and-) précédentes.</span><span class="sxs-lookup"><span data-stu-id="49564-113">In C# 8, the null-forgiving operator terminates the list of preceding [null-conditional](member-access-operators.md#null-conditional-operators--and-) operations.</span></span> <span data-ttu-id="49564-114">Par exemple, l’expression `x?.y!.z` est analysée comme `(x?.y)!.z` .</span><span class="sxs-lookup"><span data-stu-id="49564-114">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="49564-115">En raison de cette interprétation, `z` est évalué même si `x` est `null` , ce qui peut entraîner un <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="49564-115">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="49564-116">Pour plus d’informations sur la fonctionnalité des types de référence Nullable, consultez [types de référence Nullable](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="49564-116">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="49564-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="49564-117">Examples</span></span>

<span data-ttu-id="49564-118">L’un des cas d’usage de l’opérateur null-indulgent avec consiste à tester la logique de validation d’argument.</span><span class="sxs-lookup"><span data-stu-id="49564-118">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="49564-119">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="49564-119">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="49564-120">À l’aide de l' [infrastructure de test MSTest](../../../core/testing/unit-testing-with-mstest.md), vous pouvez créer le test suivant pour la logique de validation dans le constructeur :</span><span class="sxs-lookup"><span data-stu-id="49564-120">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="49564-121">Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le code précédent : `Warning CS8625: Cannot convert null literal to non-nullable reference type` .</span><span class="sxs-lookup"><span data-stu-id="49564-121">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="49564-122">En utilisant l’opérateur null-indulgent avec, vous informez le compilateur que le passage `null` est attendu et ne doit pas être averti de.</span><span class="sxs-lookup"><span data-stu-id="49564-122">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="49564-123">Vous pouvez également utiliser l’opérateur null-indulgent avec lorsque vous savez absolument qu’une expression ne peut pas être, `null` mais que le compilateur ne gère pas.</span><span class="sxs-lookup"><span data-stu-id="49564-123">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="49564-124">Dans l’exemple suivant, si la `IsValid` méthode retourne `true` , son argument n’est pas `null` et vous pouvez la déréférencer en toute sécurité :</span><span class="sxs-lookup"><span data-stu-id="49564-124">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="49564-125">Sans l’opérateur null-indulgent avec, le compilateur génère l’avertissement suivant pour le `p.Name` Code : `Warning CS8602: Dereference of a possibly null reference` .</span><span class="sxs-lookup"><span data-stu-id="49564-125">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="49564-126">Si vous pouvez modifier la `IsValid` méthode, vous pouvez utiliser l’attribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) pour informer le compilateur qu’un argument de la `IsValid` méthode ne peut pas être `null` lorsque la méthode retourne `true` :</span><span class="sxs-lookup"><span data-stu-id="49564-126">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="49564-127">Dans l’exemple précédent, vous n’avez pas besoin d’utiliser l’opérateur null-indulgent avec, car le compilateur dispose de suffisamment d’informations pour déterminer qu’il `p` ne peut pas se trouver `null` à l’intérieur de l' `if` instruction.</span><span class="sxs-lookup"><span data-stu-id="49564-127">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="49564-128">Pour plus d’informations sur les attributs qui vous permettent de fournir des informations supplémentaires sur l’État null d’une variable, consultez [mettre à niveau les API avec des attributs pour définir des attentes null](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="49564-128">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="49564-129">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="49564-129">C# language specification</span></span>

<span data-ttu-id="49564-130">Pour plus d’informations, consultez [la section opérateur null-indulgent avec](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) du [brouillon de la spécification des types de référence Nullable](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="49564-130">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="49564-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49564-131">See also</span></span>

- [<span data-ttu-id="49564-132">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="49564-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="49564-133">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="49564-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="49564-134">Didacticiel : concevoir avec des types de référence Nullable</span><span class="sxs-lookup"><span data-stu-id="49564-134">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
