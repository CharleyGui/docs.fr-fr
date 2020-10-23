---
title: Types énumération-référence C#
description: En savoir plus sur les types énumération C# qui représentent un choix ou une combinaison de choix
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 930efdbdc6a20ea301331c1ce6fc664da43bfc5f
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471848"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="5dff2-103">Types énumération (référence C#)</span><span class="sxs-lookup"><span data-stu-id="5dff2-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="5dff2-104">Un type d' *énumération* (ou un *type enum*) est un [type valeur](value-types.md) défini par un ensemble de constantes nommées du type [numérique intégral](integral-numeric-types.md) sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="5dff2-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="5dff2-105">Pour définir un type d’énumération, utilisez le `enum` mot clé et spécifiez les noms des *membres enum*:</span><span class="sxs-lookup"><span data-stu-id="5dff2-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="5dff2-106">Par défaut, les valeurs constantes associées des membres enum sont de type `int` ; elles commencent par zéro et augmentent d’une unité après l’ordre du texte de définition.</span><span class="sxs-lookup"><span data-stu-id="5dff2-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="5dff2-107">Vous pouvez spécifier explicitement n’importe quel autre type [numérique intégral](integral-numeric-types.md) en tant que type sous-jacent d’un type énumération.</span><span class="sxs-lookup"><span data-stu-id="5dff2-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="5dff2-108">Vous pouvez également spécifier explicitement les valeurs de constante associées, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5dff2-108">You can also explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="5dff2-109">Vous ne pouvez pas définir une méthode à l’intérieur de la définition d’un type d’énumération.</span><span class="sxs-lookup"><span data-stu-id="5dff2-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="5dff2-110">Pour ajouter des fonctionnalités à un type énumération, créez une [méthode d’extension](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="5dff2-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="5dff2-111">La valeur par défaut d’un type énumération `E` est la valeur produite par expression `(E)0` , même si zéro n’a pas le membre enum correspondant.</span><span class="sxs-lookup"><span data-stu-id="5dff2-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="5dff2-112">Vous utilisez un type d’énumération pour représenter un choix à partir d’un ensemble de valeurs s’excluant mutuellement ou d’une combinaison de choix.</span><span class="sxs-lookup"><span data-stu-id="5dff2-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="5dff2-113">Pour représenter une combinaison de choix, définissez un type d’énumération en tant qu’indicateurs binaires.</span><span class="sxs-lookup"><span data-stu-id="5dff2-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="5dff2-114">Types énumération comme indicateurs binaires</span><span class="sxs-lookup"><span data-stu-id="5dff2-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="5dff2-115">Si vous souhaitez qu’un type énumération représente une combinaison de choix, définissez des membres enum pour ces choix de manière à ce qu’un choix individuel soit un champ de bits.</span><span class="sxs-lookup"><span data-stu-id="5dff2-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="5dff2-116">Autrement dit, les valeurs associées à ces membres enum doivent être les puissances de deux.</span><span class="sxs-lookup"><span data-stu-id="5dff2-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="5dff2-117">Ensuite, vous pouvez utiliser les [opérateurs logiques au niveau du bit `|` `&` ou](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) combiner des choix ou croiser des combinaisons de choix, respectivement.</span><span class="sxs-lookup"><span data-stu-id="5dff2-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="5dff2-118">Pour indiquer qu’un type énumération déclare des champs de bits, appliquez l’attribut [Flags](xref:System.FlagsAttribute) à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="5dff2-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="5dff2-119">Comme le montre l’exemple suivant, vous pouvez également inclure des combinaisons typiques dans la définition d’un type énumération.</span><span class="sxs-lookup"><span data-stu-id="5dff2-119">As the following example shows, you can also include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](snippets/shared/EnumType.cs#Flags)]

<span data-ttu-id="5dff2-120">Pour obtenir plus d’informations et des exemples, consultez la <xref:System.FlagsAttribute?displayProperty=nameWithType> page de référence de l’API et la section [membres non exclusifs et l’attribut flags](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) de la <xref:System.Enum?displayProperty=nameWithType> page de référence des API.</span><span class="sxs-lookup"><span data-stu-id="5dff2-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="5dff2-121">Le type System. Enum et la contrainte enum</span><span class="sxs-lookup"><span data-stu-id="5dff2-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="5dff2-122">Le <xref:System.Enum?displayProperty=nameWithType> type est la classe de base abstraite de tous les types énumération.</span><span class="sxs-lookup"><span data-stu-id="5dff2-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="5dff2-123">Il fournit un certain nombre de méthodes pour obtenir des informations sur un type d’énumération et ses valeurs.</span><span class="sxs-lookup"><span data-stu-id="5dff2-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="5dff2-124">Pour plus d’informations et d’exemples, consultez la <xref:System.Enum?displayProperty=nameWithType> page de référence des API.</span><span class="sxs-lookup"><span data-stu-id="5dff2-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="5dff2-125">À compter de C# 7,3, vous pouvez utiliser `System.Enum` dans une contrainte de classe de base (appelée [contrainte enum](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) pour spécifier qu’un paramètre de type est un type énumération.</span><span class="sxs-lookup"><span data-stu-id="5dff2-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="5dff2-126">Conversions</span><span class="sxs-lookup"><span data-stu-id="5dff2-126">Conversions</span></span>

<span data-ttu-id="5dff2-127">Pour tout type énumération, il existe des conversions explicites entre le type énumération et son type intégral sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="5dff2-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="5dff2-128">Si vous [effectuez un cast](../operators/type-testing-and-cast.md#cast-expression) d’une valeur enum en son type sous-jacent, le résultat est la valeur intégrale associée d’un membre Enum.</span><span class="sxs-lookup"><span data-stu-id="5dff2-128">If you [cast](../operators/type-testing-and-cast.md#cast-expression) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](snippets/shared/EnumType.cs#Conversions)]

<span data-ttu-id="5dff2-129">Utilisez la <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> méthode pour déterminer si un type énumération contient un membre enum avec la certaine valeur associée.</span><span class="sxs-lookup"><span data-stu-id="5dff2-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="5dff2-130">Pour tout type énumération, il existe des conversions [boxing et unboxing](../../programming-guide/types/boxing-and-unboxing.md) vers et à partir du <xref:System.Enum?displayProperty=nameWithType> type, respectivement.</span><span class="sxs-lookup"><span data-stu-id="5dff2-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5dff2-131">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="5dff2-131">C# language specification</span></span>

<span data-ttu-id="5dff2-132">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="5dff2-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5dff2-133">Énumérations</span><span class="sxs-lookup"><span data-stu-id="5dff2-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="5dff2-134">Valeurs et opérations des énumérations</span><span class="sxs-lookup"><span data-stu-id="5dff2-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="5dff2-135">Opérateurs logiques d’énumération</span><span class="sxs-lookup"><span data-stu-id="5dff2-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="5dff2-136">Opérateurs de comparaison d’énumération</span><span class="sxs-lookup"><span data-stu-id="5dff2-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="5dff2-137">Conversions d’énumération explicites</span><span class="sxs-lookup"><span data-stu-id="5dff2-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="5dff2-138">Conversions d’énumération implicites</span><span class="sxs-lookup"><span data-stu-id="5dff2-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="5dff2-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dff2-139">See also</span></span>

- [<span data-ttu-id="5dff2-140">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="5dff2-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5dff2-141">Chaînes de format d’énumération</span><span class="sxs-lookup"><span data-stu-id="5dff2-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="5dff2-142">Directives de conception-conception enum</span><span class="sxs-lookup"><span data-stu-id="5dff2-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="5dff2-143">Directives de conception-enum Naming conventions</span><span class="sxs-lookup"><span data-stu-id="5dff2-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="5dff2-144">Instruction switch</span><span class="sxs-lookup"><span data-stu-id="5dff2-144">switch statement</span></span>](../keywords/switch.md)
