---
title: Opérateurs de conversion définie par l’utilisateur - Référence C#
description: Découvrez comment définir des conversions de type implicites et explicites personnalisées en C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 8788883a6c60032de2ffab658fcf2721654fc6f7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566676"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="8dde6-103">Opérateurs de conversion définie par l’utilisateur (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="8dde6-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="8dde6-104">Un type défini par l’utilisateur peut définir une conversion implicite ou explicite personnalisée depuis ou vers un autre type.</span><span class="sxs-lookup"><span data-stu-id="8dde6-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="8dde6-105">Les conversions implicites ne nécessitent pas une syntaxe spéciale à appeler et peuvent se produire dans diverses situations, par exemple, dans les appels de méthodes et les affectations.</span><span class="sxs-lookup"><span data-stu-id="8dde6-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="8dde6-106">Les conversions implicites C# prédéfinies réussissent toujours et ne lèvent jamais d’exception ni ne perdent d’informations.</span><span class="sxs-lookup"><span data-stu-id="8dde6-106">Predefined C# implicit conversions always succeed and never throw an exception or lose information.</span></span> <span data-ttu-id="8dde6-107">Les conversions implicites définies par l’utilisateur doivent aussi se comporter de cette façon.</span><span class="sxs-lookup"><span data-stu-id="8dde6-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="8dde6-108">Si une conversion personnalisée peut lever une exception ou perdre des informations, définissez-la comme conversion explicite.</span><span class="sxs-lookup"><span data-stu-id="8dde6-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="8dde6-109">Les conversions définies par l’utilisateur ne sont pas prises en compte par les opérateurs [is](type-testing-and-cast.md#is-operator) et [as](type-testing-and-cast.md#as-operator).</span><span class="sxs-lookup"><span data-stu-id="8dde6-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="8dde6-110">Utilisez l’[opérateur de cast ()](type-testing-and-cast.md#cast-operator-) pour appeler une conversion explicite définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8dde6-110">Use the [cast operator ()](type-testing-and-cast.md#cast-operator-) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="8dde6-111">Utilisez les mots clés `operator` et `implicit` ou `explicit` pour définir une conversion implicite ou explicite, respectivement.</span><span class="sxs-lookup"><span data-stu-id="8dde6-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="8dde6-112">Le type qui définit une conversion doit être un type source ou un type cible de cette conversion.</span><span class="sxs-lookup"><span data-stu-id="8dde6-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="8dde6-113">Une conversion entre deux types définis par l’utilisateur peut être définie dans l’un ou l’autre des deux types.</span><span class="sxs-lookup"><span data-stu-id="8dde6-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="8dde6-114">L'exemple suivant montre comment définir une conversion implicite et explicite :</span><span class="sxs-lookup"><span data-stu-id="8dde6-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

<span data-ttu-id="8dde6-115">Utilisez également le mot clé `operator` pour surcharger un opérateur C# prédéfini.</span><span class="sxs-lookup"><span data-stu-id="8dde6-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="8dde6-116">Pour plus d’informations, consultez [Surcharge d’opérateur](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="8dde6-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8dde6-117">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8dde6-117">C# language specification</span></span>

<span data-ttu-id="8dde6-118">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="8dde6-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8dde6-119">Opérateurs de conversion</span><span class="sxs-lookup"><span data-stu-id="8dde6-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="8dde6-120">Conversions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="8dde6-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="8dde6-121">Conversions implicites</span><span class="sxs-lookup"><span data-stu-id="8dde6-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="8dde6-122">Conversions explicites</span><span class="sxs-lookup"><span data-stu-id="8dde6-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="8dde6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dde6-123">See also</span></span>

- [<span data-ttu-id="8dde6-124">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="8dde6-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8dde6-125">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="8dde6-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="8dde6-126">Surcharge d’opérateur</span><span class="sxs-lookup"><span data-stu-id="8dde6-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="8dde6-127">Opérateurs de test et de cast de type</span><span class="sxs-lookup"><span data-stu-id="8dde6-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="8dde6-128">Cast et conversion de types</span><span class="sxs-lookup"><span data-stu-id="8dde6-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="8dde6-129">Conversions explicites définies par l’utilisateur chaînées en C#</span><span class="sxs-lookup"><span data-stu-id="8dde6-129">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
