---
title: Types de données scalaires Protobuf-gRPC pour les développeurs WCF
description: Découvrez les types de données de base et connus que Protobuf et gRPC prennent en charge dans .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: f5215550a6a2d54dfe2e859c574a34f641fdb68d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543155"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="e2805-103">Types de données scalaires Protobuf</span><span class="sxs-lookup"><span data-stu-id="e2805-103">Protobuf scalar data types</span></span>

<span data-ttu-id="e2805-104">La mémoire tampon de protocole (Protobuf) prend en charge une plage de types valeur scalaire native.</span><span class="sxs-lookup"><span data-stu-id="e2805-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="e2805-105">Le tableau suivant les répertorie avec leur type C# équivalent :</span><span class="sxs-lookup"><span data-stu-id="e2805-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="e2805-106">Type Protobuf</span><span class="sxs-lookup"><span data-stu-id="e2805-106">Protobuf type</span></span> | <span data-ttu-id="e2805-107">Type C#</span><span class="sxs-lookup"><span data-stu-id="e2805-107">C# type</span></span>      | <span data-ttu-id="e2805-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e2805-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="e2805-109">1</span><span class="sxs-lookup"><span data-stu-id="e2805-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="e2805-110">1</span><span class="sxs-lookup"><span data-stu-id="e2805-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="e2805-111">1</span><span class="sxs-lookup"><span data-stu-id="e2805-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="e2805-112">1</span><span class="sxs-lookup"><span data-stu-id="e2805-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="e2805-113">2</span><span class="sxs-lookup"><span data-stu-id="e2805-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="e2805-114">2</span><span class="sxs-lookup"><span data-stu-id="e2805-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="e2805-115">2</span><span class="sxs-lookup"><span data-stu-id="e2805-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="e2805-116">2</span><span class="sxs-lookup"><span data-stu-id="e2805-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="e2805-117">3</span><span class="sxs-lookup"><span data-stu-id="e2805-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="e2805-118">4</span><span class="sxs-lookup"><span data-stu-id="e2805-118">4</span></span>     |

<span data-ttu-id="e2805-119">Remarques :</span><span class="sxs-lookup"><span data-stu-id="e2805-119">Notes:</span></span>

1. <span data-ttu-id="e2805-120">L’encodage standard pour `int32` et `int64` est inefficace lorsque vous utilisez des valeurs signées.</span><span class="sxs-lookup"><span data-stu-id="e2805-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="e2805-121">Si votre champ est susceptible de contenir des nombres négatifs, utilisez `sint32` ou `sint64` à la place.</span><span class="sxs-lookup"><span data-stu-id="e2805-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="e2805-122">Ces types sont mappés C# respectivement aux types `int` et `long`.</span><span class="sxs-lookup"><span data-stu-id="e2805-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="e2805-123">Les champs `fixed` utilisent toujours le même nombre d’octets, quelle que soit la valeur de.</span><span class="sxs-lookup"><span data-stu-id="e2805-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="e2805-124">Ce comportement permet d’accélérer la sérialisation et la désérialisation des valeurs plus élevées.</span><span class="sxs-lookup"><span data-stu-id="e2805-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="e2805-125">Les chaînes Protobuf sont encodées en UTF-8 (ou ASCII 7 bits).</span><span class="sxs-lookup"><span data-stu-id="e2805-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="e2805-126">La longueur encodée ne peut pas être supérieure à 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="e2805-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="e2805-127">Le runtime Protobuf fournit un type de `ByteString` qui est facilement mappé vers C# et à partir de `byte[]` tableaux.</span><span class="sxs-lookup"><span data-stu-id="e2805-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="e2805-128">Autres types primitifs .NET</span><span class="sxs-lookup"><span data-stu-id="e2805-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="e2805-129">Dates et heures</span><span class="sxs-lookup"><span data-stu-id="e2805-129">Dates and times</span></span>

<span data-ttu-id="e2805-130">Les types scalaires natifs ne fournissent pas de valeurs de date et C#d’heure, ce qui équivaut à <xref:System.DateTimeOffset>, <xref:System.DateTime>et <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="e2805-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="e2805-131">Vous pouvez spécifier ces types à l’aide d’extensions de type « bien connu » de Google.</span><span class="sxs-lookup"><span data-stu-id="e2805-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="e2805-132">Ces extensions fournissent la génération de code et la prise en charge du runtime pour les types de champs complexes sur les plateformes prises en charge.</span><span class="sxs-lookup"><span data-stu-id="e2805-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span> 

<span data-ttu-id="e2805-133">Le tableau suivant indique les types de date et d’heure :</span><span class="sxs-lookup"><span data-stu-id="e2805-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="e2805-134">Type C#</span><span class="sxs-lookup"><span data-stu-id="e2805-134">C# type</span></span> | <span data-ttu-id="e2805-135">Protobuf, type connu</span><span class="sxs-lookup"><span data-stu-id="e2805-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="e2805-136">Les propriétés générées dans C# la classe ne sont pas les types de date et d’heure .net.</span><span class="sxs-lookup"><span data-stu-id="e2805-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="e2805-137">Les propriétés utilisent les classes `Timestamp` et `Duration` dans l’espace de noms `Google.Protobuf.WellKnownTypes`.</span><span class="sxs-lookup"><span data-stu-id="e2805-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="e2805-138">Ces classes fournissent des méthodes pour la conversion vers et à partir de `DateTimeOffset`, `DateTime`et `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="e2805-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="e2805-139">Le type de `Timestamp` fonctionne avec des heures UTC.</span><span class="sxs-lookup"><span data-stu-id="e2805-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="e2805-140">`DateTimeOffset` valeurs ont toujours un décalage égal à zéro et la propriété `DateTime.Kind` est toujours `DateTimeKind.Utc`.</span><span class="sxs-lookup"><span data-stu-id="e2805-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="e2805-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="e2805-141">System.Guid</span></span>

<span data-ttu-id="e2805-142">Protobuf ne prend pas directement en charge le type de <xref:System.Guid>, connu sous le nom de `UUID` sur d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="e2805-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="e2805-143">Il n’y a aucun type connu pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="e2805-143">There's no well-known type for it.</span></span> 

<span data-ttu-id="e2805-144">La meilleure approche consiste à gérer les valeurs de `Guid` en tant que champ de `string`, en utilisant le format hexadécimal `8-4-4-4-12` standard (par exemple, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span><span class="sxs-lookup"><span data-stu-id="e2805-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="e2805-145">Tous les langages et plateformes peuvent analyser ce format.</span><span class="sxs-lookup"><span data-stu-id="e2805-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="e2805-146">N’utilisez pas de champ `bytes` pour les valeurs `Guid`.</span><span class="sxs-lookup"><span data-stu-id="e2805-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="e2805-147">Les problèmes liés à *endianness* ([définition Wikipédia](https://en.wikipedia.org/wiki/Endianness)) peuvent entraîner un comportement erratique lorsque Protobuf interagit avec d’autres plateformes, telles que Java.</span><span class="sxs-lookup"><span data-stu-id="e2805-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="e2805-148">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="e2805-148">Nullable types</span></span>

<span data-ttu-id="e2805-149">La génération de code Protobuf C# pour utilise les types natifs, tels que `int` pour les `int32`.</span><span class="sxs-lookup"><span data-stu-id="e2805-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="e2805-150">Par conséquent, les valeurs sont toujours incluses et ne peuvent pas être null.</span><span class="sxs-lookup"><span data-stu-id="e2805-150">So the values are always included and can't be null.</span></span> 

<span data-ttu-id="e2805-151">Pour les valeurs qui requièrent une valeur null explicite, telles que C# l’utilisation de `int?` dans votre code, les « types connus » de Protobuf incluent des C# wrappers qui sont compilés en types Nullable.</span><span class="sxs-lookup"><span data-stu-id="e2805-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="e2805-152">Pour les utiliser, importez `wrappers.proto` dans votre fichier `.proto`, comme suit :</span><span class="sxs-lookup"><span data-stu-id="e2805-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="e2805-153">Protobuf utilise le `T?` simple (par exemple, `int?`) pour la propriété de message générée.</span><span class="sxs-lookup"><span data-stu-id="e2805-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="e2805-154">Le tableau suivant présente la liste complète des types de wrappers avec C# leur type équivalent :</span><span class="sxs-lookup"><span data-stu-id="e2805-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="e2805-155">Type C#</span><span class="sxs-lookup"><span data-stu-id="e2805-155">C# type</span></span>   | <span data-ttu-id="e2805-156">Wrapper de type connu</span><span class="sxs-lookup"><span data-stu-id="e2805-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="e2805-157">Les types connus `Timestamp` et `Duration` sont représentés dans .NET en tant que classes. il n’est donc pas nécessaire de disposer d’une version Nullable.</span><span class="sxs-lookup"><span data-stu-id="e2805-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version.</span></span> <span data-ttu-id="e2805-158">Toutefois, il est important de vérifier la valeur NULL sur les propriétés de ces types lorsque vous effectuez une conversion vers `DateTimeOffset` ou `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="e2805-158">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="e2805-159">Décimales</span><span class="sxs-lookup"><span data-stu-id="e2805-159">Decimals</span></span>

<span data-ttu-id="e2805-160">Protobuf ne prend pas en charge en mode natif le type de `decimal` .NET, mais simplement `double` et `float`.</span><span class="sxs-lookup"><span data-stu-id="e2805-160">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="e2805-161">Il existe une discussion continue dans le projet Protobuf sur la possibilité d’ajouter un type de `Decimal` standard aux types connus, avec la prise en charge de plateforme pour les langages et les infrastructures qui le prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="e2805-161">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="e2805-162">Rien n’a encore été implémenté.</span><span class="sxs-lookup"><span data-stu-id="e2805-162">Nothing has been implemented yet.</span></span>

<span data-ttu-id="e2805-163">Il est possible de créer une définition de message pour représenter le type de `decimal` qui fonctionnerait pour la sérialisation sécurisée entre les clients et les serveurs .NET.</span><span class="sxs-lookup"><span data-stu-id="e2805-163">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="e2805-164">Toutefois, les développeurs sur d’autres plateformes doivent comprendre le format utilisé et implémenter leur propre gestion.</span><span class="sxs-lookup"><span data-stu-id="e2805-164">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="e2805-165">Création d’un type décimal personnalisé pour Protobuf</span><span class="sxs-lookup"><span data-stu-id="e2805-165">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="e2805-166">Une implémentation simple peut être similaire au type de `Money` non standard que certaines API Google utilisent, sans le champ `currency`.</span><span class="sxs-lookup"><span data-stu-id="e2805-166">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="e2805-167">Le champ `nanos` représente les valeurs de `0.999_999_999` à `-0.999_999_999`.</span><span class="sxs-lookup"><span data-stu-id="e2805-167">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="e2805-168">Par exemple, la valeur `decimal` `1.5m` est représentée comme `{ units = 1, nanos = 500_000_000 }`.</span><span class="sxs-lookup"><span data-stu-id="e2805-168">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="e2805-169">C’est la raison pour laquelle le champ `nanos` dans cet exemple utilise le type `sfixed32`, qui encode plus efficacement que `int32` pour les valeurs plus élevées.</span><span class="sxs-lookup"><span data-stu-id="e2805-169">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="e2805-170">Si le champ `units` est négatif, le champ `nanos` doit également être négatif.</span><span class="sxs-lookup"><span data-stu-id="e2805-170">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="e2805-171">Il existe plusieurs autres algorithmes pour l’encodage de valeurs `decimal` en tant que chaînes d’octets, mais ce message est plus facile à comprendre que l’un d’eux.</span><span class="sxs-lookup"><span data-stu-id="e2805-171">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="e2805-172">Les valeurs ne sont pas affectées par endianness sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="e2805-172">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="e2805-173">La conversion entre ce type et le type de `decimal` BCL peut être C# implémentée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="e2805-173">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="e2805-174">Chaque fois que vous utilisez des types de messages personnalisés comme celui-ci, vous *devez* les documenter avec des commentaires dans `.proto`.</span><span class="sxs-lookup"><span data-stu-id="e2805-174">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="e2805-175">D’autres développeurs peuvent ensuite implémenter la conversion vers et à partir du type équivalent dans leur propre langage ou infrastructure.</span><span class="sxs-lookup"><span data-stu-id="e2805-175">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e2805-176">[Précédent](protobuf-messages.md)
>[Suivant](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="e2805-176">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
