---
title: Types de données scalaires Protobuf-gRPC pour les développeurs WCF
description: En savoir plus sur les types de données de base et connus pris en charge par Protobuf et gRPC dans .NET Core.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 8c8db795e927a44e9f75ec828336630ec9978eb6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184266"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="72239-103">Types de données scalaires Protobuf</span><span class="sxs-lookup"><span data-stu-id="72239-103">Protobuf scalar data types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="72239-104">Protobuf prend en charge une plage de types valeur scalaire native.</span><span class="sxs-lookup"><span data-stu-id="72239-104">Protobuf supports a range of native scalar value types.</span></span> <span data-ttu-id="72239-105">Le tableau suivant les répertorie avec leur type C# équivalent :</span><span class="sxs-lookup"><span data-stu-id="72239-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="72239-106">Type Protobuf</span><span class="sxs-lookup"><span data-stu-id="72239-106">Protobuf type</span></span> | <span data-ttu-id="72239-107">Type C#</span><span class="sxs-lookup"><span data-stu-id="72239-107">C# type</span></span>      | <span data-ttu-id="72239-108">Notes</span><span class="sxs-lookup"><span data-stu-id="72239-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="72239-109">1</span><span class="sxs-lookup"><span data-stu-id="72239-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="72239-110">1</span><span class="sxs-lookup"><span data-stu-id="72239-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="72239-111">1</span><span class="sxs-lookup"><span data-stu-id="72239-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="72239-112">1</span><span class="sxs-lookup"><span data-stu-id="72239-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="72239-113">2</span><span class="sxs-lookup"><span data-stu-id="72239-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="72239-114">2</span><span class="sxs-lookup"><span data-stu-id="72239-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="72239-115">2</span><span class="sxs-lookup"><span data-stu-id="72239-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="72239-116">2</span><span class="sxs-lookup"><span data-stu-id="72239-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="72239-117">3</span><span class="sxs-lookup"><span data-stu-id="72239-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="72239-118">4</span><span class="sxs-lookup"><span data-stu-id="72239-118">4</span></span>     |

## <a name="notes"></a><span data-ttu-id="72239-119">Notes</span><span class="sxs-lookup"><span data-stu-id="72239-119">Notes</span></span>

1. <span data-ttu-id="72239-120">L’encodage standard `int32` pour `int64` et est inefficace lorsque vous utilisez des valeurs signées.</span><span class="sxs-lookup"><span data-stu-id="72239-120">The standard encoding for `int32` and `int64` is inefficient when working with signed values.</span></span> <span data-ttu-id="72239-121">Si votre champ est susceptible de contenir des nombres négatifs, `sint32` utilisez `sint64` ou à la place.</span><span class="sxs-lookup"><span data-stu-id="72239-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="72239-122">Les deux types sont mappés `long` aux C# `int` types et, respectivement.</span><span class="sxs-lookup"><span data-stu-id="72239-122">Both types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="72239-123">Les `fixed` champs utilisent toujours le même nombre d’octets, quelle que soit la valeur de.</span><span class="sxs-lookup"><span data-stu-id="72239-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="72239-124">Ce comportement permet d’accélérer la sérialisation et la désérialisation des valeurs plus élevées.</span><span class="sxs-lookup"><span data-stu-id="72239-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="72239-125">Les chaînes Protobuf sont encodées en UTF-8 (ou ASCII 7 bits), et la longueur encodée ne peut pas être supérieure à 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="72239-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded, and the encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="72239-126">Le runtime Protobuf fournit un `ByteString` type qui est facilement mappé à et C# `byte[]` à partir de tableaux.</span><span class="sxs-lookup"><span data-stu-id="72239-126">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="72239-127">Autres types primitifs .NET</span><span class="sxs-lookup"><span data-stu-id="72239-127">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="72239-128">Dates et heures</span><span class="sxs-lookup"><span data-stu-id="72239-128">Dates and times</span></span>

<span data-ttu-id="72239-129">Les types scalaires natifs ne fournissent pas de valeurs de date et C#d' <xref:System.DateTimeOffset>heure <xref:System.DateTime>, ce <xref:System.TimeSpan>qui équivaut à, et.</span><span class="sxs-lookup"><span data-stu-id="72239-129">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="72239-130">Ces types peuvent être spécifiés à l’aide d’extensions de type « bien connu » de Google, qui assurent la génération de code et la prise en charge du runtime pour les types de champs plus complexes sur les plateformes prises en charge.</span><span class="sxs-lookup"><span data-stu-id="72239-130">These types can be specified using some of Google's "Well Known Types" extensions, which provide code generation and runtime support for more complex field types across the supported platforms.</span></span> <span data-ttu-id="72239-131">Le tableau suivant indique les types de date et d’heure :</span><span class="sxs-lookup"><span data-stu-id="72239-131">The following table shows the date and time types:</span></span>

| <span data-ttu-id="72239-132">Type C#</span><span class="sxs-lookup"><span data-stu-id="72239-132">C# type</span></span> | <span data-ttu-id="72239-133">Protobuf, type connu</span><span class="sxs-lookup"><span data-stu-id="72239-133">Protobuf well-known type</span></span> |
| ------- | ------------------------ |
| `DateTimeOffset` | `google.protobuf.Timestamp` |
| `DateTime` | `google.protobuf.Timestamp` |
| `TimeSpan` | `google.protobuf.Duration` |

```protobuf  
syntax = "proto3"

import "google/protobuf/duration.proto";  
import "google/protobuf/timestamp.proto";

message Meeting {

    string subject = 1;
    google.protobuf.Timestamp time = 2;
    google.protobuf.Duration duration = 3;

}  
```

<span data-ttu-id="72239-134">Les propriétés générées dans C# la classe ne sont pas les types de date et d’heure .net.</span><span class="sxs-lookup"><span data-stu-id="72239-134">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="72239-135">Les propriétés utilisent les `Timestamp` classes `Duration` et dans l' `Google.Protobuf.WellKnownTypes` espace de noms, qui fournissent des méthodes pour la `DateTimeOffset`conversion vers et `TimeSpan`à partir de, `DateTime`et.</span><span class="sxs-lookup"><span data-stu-id="72239-135">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace, which provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

```csharp
// Create Timestamp and Duration from .NET DateTimeOffset and TimeSpan
var meeting = new Meeting
{
    Time = Timestamp.FromDateTimeOffset(meetingTime), // also FromDateTime()
    Duration = Duration.FromTimeSpan(meetingLength)
};

// Convert Timestamp and Duration to .NET DateTimeOffset and TimeSpan
DateTimeOffset time = meeting.Time.ToDateTimeOffset();
TimeSpan? duration = meeting.Duration?.ToTimeSpan();
```

> [!NOTE]
> <span data-ttu-id="72239-136">Le `Timestamp` type fonctionne avec les heures UTC ; les valeurs ont toujours un décalage égal à `DateTimeKind.Utc`zéro, `DateTime.Kind` et la propriété est toujours. `DateTimeOffset`</span><span class="sxs-lookup"><span data-stu-id="72239-136">The `Timestamp` type works with UTC times; `DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property will always be `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="72239-137">System.Guid</span><span class="sxs-lookup"><span data-stu-id="72239-137">System.Guid</span></span>

<span data-ttu-id="72239-138">Le <xref:System.Guid> type, connu sous `UUID` le nom d’autres plateformes, n’est pas directement pris en charge par Protobuf et il n’y a aucun type connu pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="72239-138">The <xref:System.Guid> type, known as `UUID` on other platforms, isn't directly supported by Protobuf and there's no well-known type for it.</span></span> <span data-ttu-id="72239-139">La meilleure approche consiste à gérer `Guid` les valeurs `string` en tant que champ, `8-4-4-4-12` en utilisant le format hexadécimal standard `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`(par exemple,), qui peut être analysé par tous les langages et toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="72239-139">The best approach is to handle `Guid` values as `string` field, using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), which can be parsed by all languages and platforms.</span></span> <span data-ttu-id="72239-140">N’utilisez `bytes` pas de champ `Guid` pour les valeurs, car des problèmes avec endianness peuvent entraîner un comportement erratique lors de l’interaction avec d’autres plateformes, telles que Java.</span><span class="sxs-lookup"><span data-stu-id="72239-140">Don't use a `bytes` field for `Guid` values, as problems with endianness can result in erratic behavior when interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="72239-141">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="72239-141">Nullable types</span></span>

<span data-ttu-id="72239-142">La génération de code Protobuf C# pour utilise les types natifs, `int` tels `int32`que pour.</span><span class="sxs-lookup"><span data-stu-id="72239-142">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="72239-143">Cela signifie que les valeurs sont toujours incluses et ne peuvent pas être null.</span><span class="sxs-lookup"><span data-stu-id="72239-143">This means that the values are always included and can't be null.</span></span> <span data-ttu-id="72239-144">Pour les valeurs qui requièrent une valeur null explicite `int?` , telles C# que l’utilisation de dans votre code, les « types bien connus » de Protobuf incluent C# des wrappers qui sont compilés en types Nullable.</span><span class="sxs-lookup"><span data-stu-id="72239-144">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="72239-145">Pour les utiliser, `wrappers.proto` importez `.proto` dans votre fichier, comme suit :</span><span class="sxs-lookup"><span data-stu-id="72239-145">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="72239-146">Protobuf utilise le simple `T?` (par exemple, `int?`) pour la propriété de message générée.</span><span class="sxs-lookup"><span data-stu-id="72239-146">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="72239-147">Le tableau suivant présente la liste complète des types de wrappers avec C# leur type équivalent :</span><span class="sxs-lookup"><span data-stu-id="72239-147">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="72239-148">Type C#</span><span class="sxs-lookup"><span data-stu-id="72239-148">C# type</span></span>   | <span data-ttu-id="72239-149">Wrapper de type connu</span><span class="sxs-lookup"><span data-stu-id="72239-149">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="72239-150">Les types `Timestamp` connus et `Duration` sont représentés dans .net en tant que classes. il n’est donc pas nécessaire de disposer d’une version Nullable, mais il est important de vérifier la présence de NULL sur les propriétés `DateTimeOffset` de ces types lors de la conversion vers ou `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="72239-150">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version, but it's important to check for null on properties of those types when converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="72239-151">Décimales</span><span class="sxs-lookup"><span data-stu-id="72239-151">Decimals</span></span>

<span data-ttu-id="72239-152">Protobuf ne prend pas en charge en `decimal` mode natif le `double` type `float`.net, juste et.</span><span class="sxs-lookup"><span data-stu-id="72239-152">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="72239-153">Il existe une discussion en continu dans le projet Protobuf sur la possibilité d’ajouter un `Decimal` type standard aux types connus, avec la prise en charge de plateforme pour les langages et les infrastructures qui le prennent en charge, mais rien n’a encore été implémenté.</span><span class="sxs-lookup"><span data-stu-id="72239-153">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it, but nothing has been implemented yet.</span></span>

<span data-ttu-id="72239-154">Il est possible de créer une définition de message pour représenter `decimal` le type qui fonctionnerait pour la sérialisation sécurisée entre les clients et les serveurs .net, mais les développeurs sur d’autres plateformes doivent comprendre le format utilisé et implémenter leur propre format. traitement pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="72239-154">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers, but developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="72239-155">Création d’un type décimal personnalisé pour Protobuf</span><span class="sxs-lookup"><span data-stu-id="72239-155">Creating a custom Decimal type for Protobuf</span></span>

<span data-ttu-id="72239-156">Une implémentation très simple peut être similaire au type non standard `Money` utilisé par certaines API Google, sans le `currency` champ.</span><span class="sxs-lookup"><span data-stu-id="72239-156">A very simple implementation could be similar to the non-standard `Money` type used by some Google APIs, without the `currency` field.</span></span>

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message Decimal {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

<span data-ttu-id="72239-157">Le `nanos` champ représente les valeurs `0.999_999_999` de `-0.999_999_999`à.</span><span class="sxs-lookup"><span data-stu-id="72239-157">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="72239-158">Par exemple, la `decimal` valeur `1.5m` est représentée comme `{ units = 1, nanos = 500_000_000 }` (c’est la raison pour `nanos` laquelle le champ de cet exemple `sfixed32` utilise le type, qui s’encode plus efficacement `int32` que pour les valeurs plus élevées).</span><span class="sxs-lookup"><span data-stu-id="72239-158">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }` (this is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values).</span></span> <span data-ttu-id="72239-159">Si le `units` champ est négatif, le `nanos` champ doit également être négatif.</span><span class="sxs-lookup"><span data-stu-id="72239-159">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="72239-160">Il existe plusieurs autres algorithmes pour l' `decimal` encodage de valeurs en tant que chaînes d’octets, mais ce message est beaucoup plus facile à comprendre que l’un d’entre eux, et les valeurs ne sont pas affectées par *[endianness](https://en.wikipedia.org/wiki/Endianness)* sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="72239-160">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is much easier to understand than any of them, and the values are not affected by *[endianness](https://en.wikipedia.org/wiki/Endianness)* on different platforms.</span></span>

<span data-ttu-id="72239-161">La conversion entre ce type et le `decimal` type BCL peut être implémentée dans C# comme ceci.</span><span class="sxs-lookup"><span data-stu-id="72239-161">Conversion between this type and the BCL `decimal` type could be implemented in C# like this.</span></span>

```csharp
namespace CustomTypes
{
    public partial class GrpcDecimal
    {
        private const decimal NanoFactor = 1_000_000_000;
        public GrpcDecimal(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.Decimal grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.Decimal(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.Decimal(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="72239-162">Chaque fois que vous utilisez des types de messages d’utilitaire personnalisés comme celui-ci, vous `.proto` devez les documenter avec des commentaires dans le afin que d’autres développeurs puissent implémenter la conversion vers et à partir du type équivalent dans leur propre langage ou infrastructure.</span><span class="sxs-lookup"><span data-stu-id="72239-162">Whenever you use custom utility message types like this, you **must** document them with comments in the `.proto` so that other developers can implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="72239-163">[Précédent](protobuf-messages.md)
>[Suivant](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="72239-163">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
