---
title: Types d’énumération - Référence C
description: Renseignez-vous sur les types d’énumération CMD qui représentent un choix ou une combinaison de choix
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
ms.openlocfilehash: ab5eb1679f846bf0e25d90a4d0e0a71f0bdb0096
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847705"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="53604-103">Types d’énumération (référence C)</span><span class="sxs-lookup"><span data-stu-id="53604-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="53604-104">Un *type d’énumération* (ou *type enum*) est un type de [valeur](value-types.md) défini par un ensemble de constantes nommées du type [numérique intégral](integral-numeric-types.md) sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="53604-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="53604-105">Pour définir un type d’énumération, utilisez le `enum` mot clé et spécifiez les noms des membres *enum*:</span><span class="sxs-lookup"><span data-stu-id="53604-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="53604-106">Par défaut, les valeurs constantes associées `int`des membres enum sont de type ; ils commencent par zéro et augmentent d’un à la suite de l’ordre de texte de définition.</span><span class="sxs-lookup"><span data-stu-id="53604-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="53604-107">Vous pouvez spécifier explicitement tout autre type [numérique intégral](integral-numeric-types.md) comme type sous-jacent d’un type d’énumération.</span><span class="sxs-lookup"><span data-stu-id="53604-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="53604-108">Vous pouvez également spécifier explicitement les valeurs constantes associées, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="53604-108">You also can explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="53604-109">Vous ne pouvez pas définir une méthode à l’intérieur de la définition d’un type d’énumération.</span><span class="sxs-lookup"><span data-stu-id="53604-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="53604-110">Pour ajouter des fonctionnalités à un type d’énumération, créez une [méthode d’extension.](../../programming-guide/classes-and-structs/extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="53604-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="53604-111">La valeur par défaut d’un type `E` d’énumération est la valeur produite par l’expression `(E)0`, même si zéro n’a pas le membre enum correspondant.</span><span class="sxs-lookup"><span data-stu-id="53604-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="53604-112">Vous utilisez un type d’énumération pour représenter un choix à partir d’un ensemble de valeurs mutuellement exclusives ou d’une combinaison de choix.</span><span class="sxs-lookup"><span data-stu-id="53604-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="53604-113">Pour représenter une combinaison de choix, définissez un type d’énumération comme des drapeaux bit.</span><span class="sxs-lookup"><span data-stu-id="53604-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="53604-114">Types énumération comme indicateurs binaires</span><span class="sxs-lookup"><span data-stu-id="53604-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="53604-115">Si vous voulez un type d’énumération pour représenter une combinaison de choix, définissez les membres enum pour ces choix de telle sorte qu’un choix individuel est un peu de champ.</span><span class="sxs-lookup"><span data-stu-id="53604-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="53604-116">Autrement dit, les valeurs associées de ces membres enum devraient être les pouvoirs de deux.</span><span class="sxs-lookup"><span data-stu-id="53604-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="53604-117">Ensuite, vous pouvez utiliser [les `|` `&` opérateurs logiques bitwise ou](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) pour combiner des choix ou de croiser des combinaisons de choix, respectivement.</span><span class="sxs-lookup"><span data-stu-id="53604-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="53604-118">Pour indiquer qu’un type d’énumération déclare les champs bits, appliquez l’attribut [drapeaux](xref:System.FlagsAttribute) à elle.</span><span class="sxs-lookup"><span data-stu-id="53604-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="53604-119">Comme le montre l’exemple suivant, vous pouvez également inclure quelques combinaisons typiques dans la définition d’un type d’énumération.</span><span class="sxs-lookup"><span data-stu-id="53604-119">As the following example shows, you also can include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

<span data-ttu-id="53604-120">Pour plus d’informations <xref:System.FlagsAttribute?displayProperty=nameWithType> et d’exemples, consultez la page de référence <xref:System.Enum?displayProperty=nameWithType> de l’API et les membres non exclusifs et la section [d’attributs Drapeaux](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) de la page de référence API.</span><span class="sxs-lookup"><span data-stu-id="53604-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="53604-121">Le type System.Enum et la contrainte enum</span><span class="sxs-lookup"><span data-stu-id="53604-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="53604-122">Le <xref:System.Enum?displayProperty=nameWithType> type est la classe de base abstraite de tous les types d’énumération.</span><span class="sxs-lookup"><span data-stu-id="53604-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="53604-123">Il fournit un certain nombre de méthodes pour obtenir des informations sur un type de recensement et ses valeurs.</span><span class="sxs-lookup"><span data-stu-id="53604-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="53604-124">Pour plus d’informations <xref:System.Enum?displayProperty=nameWithType> et d’exemples, consultez la page de référence de l’API.</span><span class="sxs-lookup"><span data-stu-id="53604-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="53604-125">En commençant par le C 7.3, vous pouvez utiliser `System.Enum` dans une contrainte de classe de base (qui est connue sous le nom de contrainte [d’enum](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) pour spécifier qu’un paramètre de type est un type d’énumération.</span><span class="sxs-lookup"><span data-stu-id="53604-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="53604-126">Conversions</span><span class="sxs-lookup"><span data-stu-id="53604-126">Conversions</span></span>

<span data-ttu-id="53604-127">Pour tout type d’énumération, il existe des conversions explicites entre le type d’énumération et son type intégral sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="53604-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="53604-128">Si vous [lancez](../operators/type-testing-and-cast.md#cast-operator-) une valeur enum à son type sous-jacent, le résultat est la valeur intégrale associée d’un membre enum.</span><span class="sxs-lookup"><span data-stu-id="53604-128">If you [cast](../operators/type-testing-and-cast.md#cast-operator-) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

<span data-ttu-id="53604-129">Utilisez <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> la méthode pour déterminer si un type d’énumération contient un membre enum avec la valeur associée certaine.</span><span class="sxs-lookup"><span data-stu-id="53604-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="53604-130">Pour tout type d’énumération, il existe des conversions <xref:System.Enum?displayProperty=nameWithType> de boxe et de [déballage](../../programming-guide/types/boxing-and-unboxing.md) pour et depuis le type, respectivement.</span><span class="sxs-lookup"><span data-stu-id="53604-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="53604-131">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="53604-131">C# language specification</span></span>

<span data-ttu-id="53604-132">Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :</span><span class="sxs-lookup"><span data-stu-id="53604-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="53604-133">Enums</span><span class="sxs-lookup"><span data-stu-id="53604-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="53604-134">Valeurs et opérations des énumérations</span><span class="sxs-lookup"><span data-stu-id="53604-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="53604-135">Opérateurs logiques d’énumération</span><span class="sxs-lookup"><span data-stu-id="53604-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="53604-136">Opérateurs de comparaison de recensement</span><span class="sxs-lookup"><span data-stu-id="53604-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="53604-137">Conversions explicites de recensement</span><span class="sxs-lookup"><span data-stu-id="53604-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="53604-138">Conversions implicites de recensement</span><span class="sxs-lookup"><span data-stu-id="53604-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="53604-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53604-139">See also</span></span>

- [<span data-ttu-id="53604-140">Référence C#</span><span class="sxs-lookup"><span data-stu-id="53604-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="53604-141">Chaînes de format d'énumération</span><span class="sxs-lookup"><span data-stu-id="53604-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="53604-142">Lignes directrices de conception - Conception Enum</span><span class="sxs-lookup"><span data-stu-id="53604-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="53604-143">Lignes directrices de conception - Enum nommant des conventions</span><span class="sxs-lookup"><span data-stu-id="53604-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="53604-144">instruction switch</span><span class="sxs-lookup"><span data-stu-id="53604-144">switch statement</span></span>](../keywords/switch.md)
