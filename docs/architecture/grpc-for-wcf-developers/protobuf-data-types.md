---
title: Types de données scalaires Protobuf - gRPC pour les développeurs WCF
description: Découvrez les types de données de base et bien connus que Protobuf et gRPC prennent en charge dans .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: a40f51fa32ddb97ba417ec01f31e1f0187f0d544
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148125"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="7b668-103">Types de données scalaires Protobuf</span><span class="sxs-lookup"><span data-stu-id="7b668-103">Protobuf scalar data types</span></span>

<span data-ttu-id="7b668-104">Protocol Buffer (Protobuf) prend en charge une gamme de types de valeur scalaire indigène.</span><span class="sxs-lookup"><span data-stu-id="7b668-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="7b668-105">Le tableau suivant les énumère tous avec leur type C équivalent :</span><span class="sxs-lookup"><span data-stu-id="7b668-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="7b668-106">Type Protobuf</span><span class="sxs-lookup"><span data-stu-id="7b668-106">Protobuf type</span></span> | <span data-ttu-id="7b668-107">Type C#</span><span class="sxs-lookup"><span data-stu-id="7b668-107">C# type</span></span>      | <span data-ttu-id="7b668-108">Notes</span><span class="sxs-lookup"><span data-stu-id="7b668-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="7b668-109">1</span><span class="sxs-lookup"><span data-stu-id="7b668-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="7b668-110">1</span><span class="sxs-lookup"><span data-stu-id="7b668-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="7b668-111">1</span><span class="sxs-lookup"><span data-stu-id="7b668-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="7b668-112">1</span><span class="sxs-lookup"><span data-stu-id="7b668-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="7b668-113">2</span><span class="sxs-lookup"><span data-stu-id="7b668-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="7b668-114">2</span><span class="sxs-lookup"><span data-stu-id="7b668-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="7b668-115">2</span><span class="sxs-lookup"><span data-stu-id="7b668-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="7b668-116">2</span><span class="sxs-lookup"><span data-stu-id="7b668-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="7b668-117">3</span><span class="sxs-lookup"><span data-stu-id="7b668-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="7b668-118">4</span><span class="sxs-lookup"><span data-stu-id="7b668-118">4</span></span>     |

<span data-ttu-id="7b668-119">Remarques :</span><span class="sxs-lookup"><span data-stu-id="7b668-119">Notes:</span></span>

1. <span data-ttu-id="7b668-120">L’encodage standard pour `int32` et `int64` est inefficace lorsque vous travaillez avec des valeurs signées.</span><span class="sxs-lookup"><span data-stu-id="7b668-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="7b668-121">Si votre champ est susceptible de `sint32` `sint64` contenir des nombres négatifs, utilisez ou à la place.</span><span class="sxs-lookup"><span data-stu-id="7b668-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="7b668-122">Ces types sont `int` cartographiques `long` pour les types et les types, respectivement.</span><span class="sxs-lookup"><span data-stu-id="7b668-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="7b668-123">Les `fixed` champs utilisent toujours le même nombre d’octets, quelle que soit la valeur.</span><span class="sxs-lookup"><span data-stu-id="7b668-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="7b668-124">Ce comportement rend la sérialisation et la désétérialisation plus rapidement pour de plus grandes valeurs.</span><span class="sxs-lookup"><span data-stu-id="7b668-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="7b668-125">Les cordes Protobuf sont codées UTF-8 (ou ASCII 7 bits).</span><span class="sxs-lookup"><span data-stu-id="7b668-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="7b668-126">La longueur codée ne peut pas être supérieure à 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="7b668-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="7b668-127">L’exécution Protobuf `ByteString` fournit un type qui cartographie `byte[]` facilement vers et depuis les tableaux de C.</span><span class="sxs-lookup"><span data-stu-id="7b668-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="7b668-128">Autres types primitifs .NET</span><span class="sxs-lookup"><span data-stu-id="7b668-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="7b668-129">Dates et heures</span><span class="sxs-lookup"><span data-stu-id="7b668-129">Dates and times</span></span>

<span data-ttu-id="7b668-130">Les types scalaires natifs ne prévoient pas les valeurs de <xref:System.DateTimeOffset> <xref:System.DateTime>date <xref:System.TimeSpan>et d’heure, équivalentes à celle de C, et .</span><span class="sxs-lookup"><span data-stu-id="7b668-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="7b668-131">Vous pouvez spécifier ces types en utilisant certaines des extensions "Well Known Types" de Google.</span><span class="sxs-lookup"><span data-stu-id="7b668-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="7b668-132">Ces extensions fournissent un support de génération de code et de temps d’exécution pour les types de terrain complexes sur les plates-formes prises en charge.</span><span class="sxs-lookup"><span data-stu-id="7b668-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="7b668-133">Le tableau suivant montre les types de date et d’heure :</span><span class="sxs-lookup"><span data-stu-id="7b668-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="7b668-134">Type C#</span><span class="sxs-lookup"><span data-stu-id="7b668-134">C# type</span></span> | <span data-ttu-id="7b668-135">Protobuf type bien connu</span><span class="sxs-lookup"><span data-stu-id="7b668-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="7b668-136">Les propriétés générées dans la classe C ne sont pas les types de date et d’heure .NET.</span><span class="sxs-lookup"><span data-stu-id="7b668-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="7b668-137">Les propriétés `Timestamp` `Duration` utilisent le `Google.Protobuf.WellKnownTypes` et les classes dans l’espace nom.</span><span class="sxs-lookup"><span data-stu-id="7b668-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="7b668-138">Ces classes fournissent des méthodes `DateTimeOffset`pour `DateTime`convertir `TimeSpan`à et à partir de , et .</span><span class="sxs-lookup"><span data-stu-id="7b668-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="7b668-139">Le `Timestamp` type fonctionne avec les temps UTC.</span><span class="sxs-lookup"><span data-stu-id="7b668-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="7b668-140">`DateTimeOffset`valeurs ont toujours un décalage `DateTime.Kind` de zéro, et la propriété est toujours `DateTimeKind.Utc`.</span><span class="sxs-lookup"><span data-stu-id="7b668-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="7b668-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="7b668-141">System.Guid</span></span>

<span data-ttu-id="7b668-142">Protobuf ne prend pas <xref:System.Guid> directement en `UUID` charge le type, connu sous le nom de sur d’autres plates-formes.</span><span class="sxs-lookup"><span data-stu-id="7b668-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="7b668-143">Il n’y a pas de type bien connu pour ça.</span><span class="sxs-lookup"><span data-stu-id="7b668-143">There's no well-known type for it.</span></span>

<span data-ttu-id="7b668-144">La meilleure approche `Guid` est de `string` gérer les valeurs `8-4-4-4-12` comme un champ, en `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`utilisant le format hexadecimal standard (par exemple, ).</span><span class="sxs-lookup"><span data-stu-id="7b668-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="7b668-145">Toutes les langues et plates-formes peuvent analyser ce format.</span><span class="sxs-lookup"><span data-stu-id="7b668-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="7b668-146">N’utilisez pas `bytes` de `Guid` champ pour les valeurs.</span><span class="sxs-lookup"><span data-stu-id="7b668-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="7b668-147">Les problèmes *d’endianness* [(définition de Wikipédia](https://en.wikipedia.org/wiki/Endianness)) peuvent entraîner un comportement erratique lorsque Protobuf interagit avec d’autres plates-formes, comme Java.</span><span class="sxs-lookup"><span data-stu-id="7b668-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="7b668-148">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="7b668-148">Nullable types</span></span>

<span data-ttu-id="7b668-149">La génération de code Protobuf pour C `int` utilise `int32`les types indigènes, tels que pour .</span><span class="sxs-lookup"><span data-stu-id="7b668-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="7b668-150">Ainsi, les valeurs sont toujours incluses et ne peuvent pas être nulles.</span><span class="sxs-lookup"><span data-stu-id="7b668-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="7b668-151">Pour les valeurs qui nécessitent `int?` des nullité explicites, telles que l’utilisation dans votre code C, les « types bien connus » de Protobuf comprennent des emballages qui sont compilés selon des types Cmd annulés.</span><span class="sxs-lookup"><span data-stu-id="7b668-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="7b668-152">Pour les utiliser, `wrappers.proto` `.proto` importez dans votre fichier, comme ceci :</span><span class="sxs-lookup"><span data-stu-id="7b668-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="7b668-153">Protobuf utilisera `T?` le simple `int?`(par exemple, ) pour la propriété de message généré.</span><span class="sxs-lookup"><span data-stu-id="7b668-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="7b668-154">Le tableau suivant montre la liste complète des types d’emballages avec leur type équivalent C :</span><span class="sxs-lookup"><span data-stu-id="7b668-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="7b668-155">Type C#</span><span class="sxs-lookup"><span data-stu-id="7b668-155">C# type</span></span>   | <span data-ttu-id="7b668-156">Emballage de type bien connu</span><span class="sxs-lookup"><span data-stu-id="7b668-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="7b668-157">Les types `Timestamp` bien `Duration` connus et sont représentés dans .NET comme classes, il n’y a donc pas besoin d’une version nulle.</span><span class="sxs-lookup"><span data-stu-id="7b668-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version.</span></span> <span data-ttu-id="7b668-158">Mais il est important de vérifier les nons sur les `DateTimeOffset` propriétés de ces types lorsque vous convertissez à ou `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="7b668-158">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="7b668-159">Décimales</span><span class="sxs-lookup"><span data-stu-id="7b668-159">Decimals</span></span>

<span data-ttu-id="7b668-160">Protobuf ne supporte pas natif `decimal` le `double` type `float`.NET, juste et .</span><span class="sxs-lookup"><span data-stu-id="7b668-160">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="7b668-161">Il ya une discussion en cours dans le projet Protobuf sur la possibilité d’ajouter un type standard `Decimal` aux types bien connus, avec le soutien de la plate-forme pour les langues et les cadres qui le soutiennent.</span><span class="sxs-lookup"><span data-stu-id="7b668-161">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="7b668-162">Rien n’a encore été mis en œuvre.</span><span class="sxs-lookup"><span data-stu-id="7b668-162">Nothing has been implemented yet.</span></span>

<span data-ttu-id="7b668-163">Il est possible de créer une `decimal` définition de message pour représenter le type qui fonctionnerait pour la sérialisation sécurisée entre les clients .NET et les serveurs.</span><span class="sxs-lookup"><span data-stu-id="7b668-163">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="7b668-164">Mais les développeurs sur d’autres plates-formes devraient comprendre le format utilisé et mettre en œuvre leur propre manipulation pour elle.</span><span class="sxs-lookup"><span data-stu-id="7b668-164">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="7b668-165">Création d’un type décimal personnalisé pour Protobuf</span><span class="sxs-lookup"><span data-stu-id="7b668-165">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="7b668-166">Une mise en œuvre simple `Money` peut être similaire au type `currency` non standard que certaines API Google utilisent, sans le champ.</span><span class="sxs-lookup"><span data-stu-id="7b668-166">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="7b668-167">Le `nanos` domaine représente `0.999_999_999` `-0.999_999_999`des valeurs de .</span><span class="sxs-lookup"><span data-stu-id="7b668-167">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="7b668-168">Par exemple, `decimal` `1.5m` la valeur serait `{ units = 1, nanos = 500_000_000 }`représentée comme .</span><span class="sxs-lookup"><span data-stu-id="7b668-168">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="7b668-169">C’est `nanos` pourquoi le champ `sfixed32` dans cet exemple utilise le `int32` type, qui code plus efficacement que pour les valeurs plus grandes.</span><span class="sxs-lookup"><span data-stu-id="7b668-169">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="7b668-170">Si `units` le champ est `nanos` négatif, le champ doit également être négatif.</span><span class="sxs-lookup"><span data-stu-id="7b668-170">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="7b668-171">Il existe plusieurs autres algorithmes pour l’encodage des `decimal` valeurs comme des chaînes d’endage, mais ce message est plus facile à comprendre que n’importe lequel d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="7b668-171">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="7b668-172">Les valeurs ne sont pas affectées par l’endianness sur différentes plates-formes.</span><span class="sxs-lookup"><span data-stu-id="7b668-172">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="7b668-173">La conversion entre ce `decimal` type et le type BCL peut être implémentée dans C ' comme ceci :</span><span class="sxs-lookup"><span data-stu-id="7b668-173">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="7b668-174">Chaque fois que vous utilisez *must* des types de `.proto`messages personnalisés comme celui-ci, vous devez les documenter avec des commentaires dans .</span><span class="sxs-lookup"><span data-stu-id="7b668-174">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="7b668-175">D’autres développeurs peuvent ensuite implémenter la conversion vers et depuis le type équivalent dans leur propre langue ou cadre.</span><span class="sxs-lookup"><span data-stu-id="7b668-175">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7b668-176">[Suivant précédent](protobuf-messages.md)
>[Next](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="7b668-176">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
