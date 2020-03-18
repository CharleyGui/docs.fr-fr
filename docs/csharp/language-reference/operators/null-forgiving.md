---
title: '! opérateur (null-forgiving) - Référence C'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 36bfa46cebd2b35c4985dfc23dbe84f8f5dc9201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846299"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="75184-103">!</span><span class="sxs-lookup"><span data-stu-id="75184-103">!</span></span> <span data-ttu-id="75184-104">opérateur (null-forgiving) (référence C)</span><span class="sxs-lookup"><span data-stu-id="75184-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="75184-105">Disponible en C 8.0 et plus tard, l’opérateur de poteaufix `!` nonary est l’opérateur nul-indulgent.</span><span class="sxs-lookup"><span data-stu-id="75184-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="75184-106">Dans un [contexte d’annotation annulée](../../nullable-references.md#nullable-annotation-context)activé, vous utilisez l’opérateur nul pour déclarer que l’expression `x` d’un type de référence n’est pas `null`: `x!`.</span><span class="sxs-lookup"><span data-stu-id="75184-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="75184-107">L’opérateur de `!` préfixe nonaire est l’opérateur [de négation logique](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="75184-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="75184-108">L’opérateur qui pardonne les nullités n’a aucun effet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="75184-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="75184-109">Il n’affecte que l’analyse statique du flux du compilateur en modifiant l’état nul de l’expression.</span><span class="sxs-lookup"><span data-stu-id="75184-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="75184-110">Au moment de `x!` l’exécution, l’expression `x`évalue au résultat de l’expression sous-jacente .</span><span class="sxs-lookup"><span data-stu-id="75184-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="75184-111">Pour plus d’informations sur la fonction de type de référence annulée, voir [les types de référence Nullable](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="75184-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="75184-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="75184-112">Examples</span></span>

<span data-ttu-id="75184-113">L’un des cas d’utilisation de l’opérateur null-indulgent est de tester la logique de validation de l’argument.</span><span class="sxs-lookup"><span data-stu-id="75184-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="75184-114">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="75184-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="75184-115">En utilisant le [cadre de test MSTest](../../../core/testing/unit-testing-with-mstest.md), vous pouvez créer le test suivant pour la logique de validation dans le constructeur :</span><span class="sxs-lookup"><span data-stu-id="75184-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="75184-116">Sans l’opérateur null-indulgent, le compilateur génère l’avertissement `Warning CS8625: Cannot convert null literal to non-nullable reference type`suivant pour le code précédent: .</span><span class="sxs-lookup"><span data-stu-id="75184-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="75184-117">En utilisant l’opérateur null-indulgent, vous informez `null` le compilateur que le passage est prévu et ne devrait pas être averti.</span><span class="sxs-lookup"><span data-stu-id="75184-117">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="75184-118">Vous pouvez également utiliser l’opérateur null-indulgent quand vous `null` savez certainement qu’une expression ne peut pas être, mais le compilateur ne parvient pas à le reconnaître.</span><span class="sxs-lookup"><span data-stu-id="75184-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="75184-119">Dans l’exemple suivant, si la `IsValid` méthode revient, `true`son argument n’est pas `null` et vous pouvez en toute sécurité le déreférencer:</span><span class="sxs-lookup"><span data-stu-id="75184-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="75184-120">Sans l’opérateur null-indulgent, le compilateur génère l’avertissement suivant pour le `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span><span class="sxs-lookup"><span data-stu-id="75184-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="75184-121">Si vous pouvez `IsValid` modifier la méthode, vous pouvez utiliser l’attribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) pour informer le compilateur qu’un argument de la `IsValid` méthode ne peut pas être `null` lorsque la méthode revient `true`:</span><span class="sxs-lookup"><span data-stu-id="75184-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="75184-122">Dans l’exemple précédent, vous n’avez pas besoin d’utiliser l’opérateur null-indulgent `p` parce `null` que `if` le compilateur a suffisamment d’informations pour savoir qui ne peut pas être à l’intérieur de la déclaration.</span><span class="sxs-lookup"><span data-stu-id="75184-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="75184-123">Pour plus d’informations sur les attributs qui vous permettent de fournir des informations supplémentaires sur l’état nul d’une variable, voir [Upgrade API avec des attributs pour définir les attentes nulles](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="75184-123">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="75184-124">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="75184-124">C# language specification</span></span>

<span data-ttu-id="75184-125">Pour plus d’informations, voir La section [de l’opérateur nul-indulgent](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) de [l’ébauche de la spécification des types de référence nuls](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="75184-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75184-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75184-126">See also</span></span>

- [<span data-ttu-id="75184-127">Référence C#</span><span class="sxs-lookup"><span data-stu-id="75184-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="75184-128">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="75184-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="75184-129">Tutorial: Conception avec des types de référence nuls</span><span class="sxs-lookup"><span data-stu-id="75184-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
