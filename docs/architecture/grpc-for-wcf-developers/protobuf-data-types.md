---
title: Types de données scalaires Protobuf-gRPC pour les développeurs WCF
description: Découvrez les types de données de base et connus que Protobuf et gRPC prennent en charge dans .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: 5447067b953d257258950d020636e0b38245e20d
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91573642"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="c6be8-103">Types de données scalaires Protobuf</span><span class="sxs-lookup"><span data-stu-id="c6be8-103">Protobuf scalar data types</span></span>

<span data-ttu-id="c6be8-104">La mémoire tampon de protocole (Protobuf) prend en charge une plage de types valeur scalaire native.</span><span class="sxs-lookup"><span data-stu-id="c6be8-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="c6be8-105">Le tableau suivant les répertorie avec leur type C# équivalent :</span><span class="sxs-lookup"><span data-stu-id="c6be8-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="c6be8-106">Type Protobuf</span><span class="sxs-lookup"><span data-stu-id="c6be8-106">Protobuf type</span></span> | <span data-ttu-id="c6be8-107">Type C#</span><span class="sxs-lookup"><span data-stu-id="c6be8-107">C# type</span></span>      | <span data-ttu-id="c6be8-108">Notes</span><span class="sxs-lookup"><span data-stu-id="c6be8-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="c6be8-109">1</span><span class="sxs-lookup"><span data-stu-id="c6be8-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="c6be8-110">1</span><span class="sxs-lookup"><span data-stu-id="c6be8-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="c6be8-111">1</span><span class="sxs-lookup"><span data-stu-id="c6be8-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="c6be8-112">1</span><span class="sxs-lookup"><span data-stu-id="c6be8-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="c6be8-113">2</span><span class="sxs-lookup"><span data-stu-id="c6be8-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="c6be8-114">2</span><span class="sxs-lookup"><span data-stu-id="c6be8-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="c6be8-115">2</span><span class="sxs-lookup"><span data-stu-id="c6be8-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="c6be8-116">2</span><span class="sxs-lookup"><span data-stu-id="c6be8-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="c6be8-117">3</span><span class="sxs-lookup"><span data-stu-id="c6be8-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="c6be8-118">4</span><span class="sxs-lookup"><span data-stu-id="c6be8-118">4</span></span>     |

<span data-ttu-id="c6be8-119">Remarques :</span><span class="sxs-lookup"><span data-stu-id="c6be8-119">Notes:</span></span>

1. <span data-ttu-id="c6be8-120">L’encodage standard pour `int32` et `int64` est inefficace lorsque vous utilisez des valeurs signées.</span><span class="sxs-lookup"><span data-stu-id="c6be8-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="c6be8-121">Si votre champ est susceptible de contenir des nombres négatifs, utilisez ou à la `sint32` `sint64` place.</span><span class="sxs-lookup"><span data-stu-id="c6be8-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="c6be8-122">Ces types sont mappés aux `int` types C# et `long` , respectivement.</span><span class="sxs-lookup"><span data-stu-id="c6be8-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="c6be8-123">Les `fixed` champs utilisent toujours le même nombre d’octets, quelle que soit la valeur de.</span><span class="sxs-lookup"><span data-stu-id="c6be8-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="c6be8-124">Ce comportement permet d’accélérer la sérialisation et la désérialisation des valeurs plus élevées.</span><span class="sxs-lookup"><span data-stu-id="c6be8-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="c6be8-125">Les chaînes Protobuf sont encodées en UTF-8 (ou ASCII 7 bits).</span><span class="sxs-lookup"><span data-stu-id="c6be8-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="c6be8-126">La longueur encodée ne peut pas être supérieure à 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="c6be8-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="c6be8-127">Le runtime Protobuf fournit un `ByteString` type qui est facilement mappé à et à partir de `byte[]` tableaux C#.</span><span class="sxs-lookup"><span data-stu-id="c6be8-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="c6be8-128">Autres types primitifs .NET</span><span class="sxs-lookup"><span data-stu-id="c6be8-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="c6be8-129">Des dates et heures</span><span class="sxs-lookup"><span data-stu-id="c6be8-129">Dates and times</span></span>

<span data-ttu-id="c6be8-130">Les types scalaires natifs ne fournissent pas de valeurs de date et d’heure, équivalentes à C# <xref:System.DateTimeOffset> , <xref:System.DateTime> et <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="c6be8-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="c6be8-131">Vous pouvez spécifier ces types à l’aide d’extensions de type « bien connu » de Google.</span><span class="sxs-lookup"><span data-stu-id="c6be8-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="c6be8-132">Ces extensions fournissent la génération de code et la prise en charge du runtime pour les types de champs complexes sur les plateformes prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c6be8-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="c6be8-133">Le tableau suivant indique les types de date et d’heure :</span><span class="sxs-lookup"><span data-stu-id="c6be8-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="c6be8-134">Type C#</span><span class="sxs-lookup"><span data-stu-id="c6be8-134">C# type</span></span> | <span data-ttu-id="c6be8-135">Protobuf, type connu</span><span class="sxs-lookup"><span data-stu-id="c6be8-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="c6be8-136">Les propriétés générées dans la classe C# ne sont pas les types de date et d’heure .NET.</span><span class="sxs-lookup"><span data-stu-id="c6be8-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="c6be8-137">Les propriétés utilisent les `Timestamp` `Duration` classes et dans l' `Google.Protobuf.WellKnownTypes` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c6be8-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="c6be8-138">Ces classes fournissent des méthodes pour la conversion vers et à partir de `DateTimeOffset` , `DateTime` et `TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="c6be8-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="c6be8-139">Le `Timestamp` type fonctionne avec des heures UTC.</span><span class="sxs-lookup"><span data-stu-id="c6be8-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="c6be8-140">`DateTimeOffset` les valeurs ont toujours un offset égal à zéro, et la `DateTime.Kind` propriété est toujours `DateTimeKind.Utc` .</span><span class="sxs-lookup"><span data-stu-id="c6be8-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="c6be8-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="c6be8-141">System.Guid</span></span>

<span data-ttu-id="c6be8-142">Protobuf ne prend pas directement en charge le <xref:System.Guid> type, connu sous le nom `UUID` d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="c6be8-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="c6be8-143">Il n’y a aucun type connu pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c6be8-143">There's no well-known type for it.</span></span>

<span data-ttu-id="c6be8-144">La meilleure approche consiste à gérer les `Guid` valeurs comme un `string` champ, en utilisant le `8-4-4-4-12` format hexadécimal standard (par exemple, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3` ).</span><span class="sxs-lookup"><span data-stu-id="c6be8-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="c6be8-145">Tous les langages et plateformes peuvent analyser ce format.</span><span class="sxs-lookup"><span data-stu-id="c6be8-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="c6be8-146">N’utilisez pas `bytes` de champ pour les `Guid` valeurs.</span><span class="sxs-lookup"><span data-stu-id="c6be8-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="c6be8-147">Les problèmes liés à *endianness* ([définition Wikipédia](https://en.wikipedia.org/wiki/Endianness)) peuvent entraîner un comportement erratique lorsque Protobuf interagit avec d’autres plateformes, telles que Java.</span><span class="sxs-lookup"><span data-stu-id="c6be8-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="c6be8-148">Types Nullable</span><span class="sxs-lookup"><span data-stu-id="c6be8-148">Nullable types</span></span>

<span data-ttu-id="c6be8-149">La génération de code Protobuf pour C# utilise les types natifs, tels que `int` pour `int32` .</span><span class="sxs-lookup"><span data-stu-id="c6be8-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="c6be8-150">Par conséquent, les valeurs sont toujours incluses et ne peuvent pas être null.</span><span class="sxs-lookup"><span data-stu-id="c6be8-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="c6be8-151">Pour les valeurs qui requièrent une valeur null explicite, telles que l’utilisation `int?` de dans votre code C#, les « types connus » de Protobuf incluent des wrappers qui sont compilés en types C# Nullable.</span><span class="sxs-lookup"><span data-stu-id="c6be8-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="c6be8-152">Pour les utiliser, importez `wrappers.proto` dans votre `.proto` fichier, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c6be8-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="c6be8-153">Protobuf utilise le simple `T?` (par exemple, `int?` ) pour la propriété de message générée.</span><span class="sxs-lookup"><span data-stu-id="c6be8-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="c6be8-154">Le tableau suivant présente la liste complète des types de wrappers avec leur type C# équivalent :</span><span class="sxs-lookup"><span data-stu-id="c6be8-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="c6be8-155">Type C#</span><span class="sxs-lookup"><span data-stu-id="c6be8-155">C# type</span></span>   | <span data-ttu-id="c6be8-156">Wrapper de type connu</span><span class="sxs-lookup"><span data-stu-id="c6be8-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="c6be8-157">Les types connus `Timestamp` et `Duration` sont représentés dans .net en tant que classes.</span><span class="sxs-lookup"><span data-stu-id="c6be8-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes.</span></span> <span data-ttu-id="c6be8-158">En C# 8 et versions ultérieures, vous pouvez utiliser des types de référence Nullable.</span><span class="sxs-lookup"><span data-stu-id="c6be8-158">In C# 8 and beyond, you can use nullable reference types.</span></span> <span data-ttu-id="c6be8-159">Mais il est important de vérifier la valeur NULL sur les propriétés de ces types lorsque vous effectuez une conversion vers `DateTimeOffset` ou `TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="c6be8-159">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="c6be8-160">Décimales</span><span class="sxs-lookup"><span data-stu-id="c6be8-160">Decimals</span></span>

<span data-ttu-id="c6be8-161">Protobuf ne prend pas en charge en mode natif le `decimal` type .net, juste `double` et `float` .</span><span class="sxs-lookup"><span data-stu-id="c6be8-161">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="c6be8-162">Il existe une discussion continue dans le projet Protobuf sur la possibilité d’ajouter un `Decimal` type standard aux types connus, avec la prise en charge de plateforme pour les langages et les infrastructures qui le prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="c6be8-162">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="c6be8-163">Rien n’a encore été implémenté.</span><span class="sxs-lookup"><span data-stu-id="c6be8-163">Nothing has been implemented yet.</span></span>

<span data-ttu-id="c6be8-164">Il est possible de créer une définition de message pour représenter le `decimal` type qui fonctionnerait pour la sérialisation sécurisée entre les clients et les serveurs .net.</span><span class="sxs-lookup"><span data-stu-id="c6be8-164">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="c6be8-165">Toutefois, les développeurs sur d’autres plateformes doivent comprendre le format utilisé et implémenter leur propre gestion.</span><span class="sxs-lookup"><span data-stu-id="c6be8-165">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="c6be8-166">Création d’un type décimal personnalisé pour Protobuf</span><span class="sxs-lookup"><span data-stu-id="c6be8-166">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="c6be8-167">Une implémentation simple peut être similaire au type non standard `Money` utilisé par certaines API Google, sans le `currency` champ.</span><span class="sxs-lookup"><span data-stu-id="c6be8-167">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message DecimalValue {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

<span data-ttu-id="c6be8-168">Le `nanos` champ représente les valeurs de `0.999_999_999` à `-0.999_999_999` .</span><span class="sxs-lookup"><span data-stu-id="c6be8-168">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="c6be8-169">Par exemple, la `decimal` valeur est `1.5m` représentée sous la forme `{ units = 1, nanos = 500_000_000 }` .</span><span class="sxs-lookup"><span data-stu-id="c6be8-169">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="c6be8-170">C’est la raison pour laquelle le `nanos` champ de cet exemple utilise le `sfixed32` type, qui s’encode plus efficacement que `int32` pour les valeurs plus élevées.</span><span class="sxs-lookup"><span data-stu-id="c6be8-170">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="c6be8-171">Si le `units` champ est négatif, le `nanos` champ doit également être négatif.</span><span class="sxs-lookup"><span data-stu-id="c6be8-171">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="c6be8-172">Il existe plusieurs autres algorithmes pour l’encodage de `decimal` valeurs en tant que chaînes d’octets, mais ce message est plus facile à comprendre que l’un d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="c6be8-172">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="c6be8-173">Les valeurs ne sont pas affectées par endianness sur différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="c6be8-173">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="c6be8-174">La conversion entre ce type et le `decimal` type BCL peut être implémentée en C# comme suit :</span><span class="sxs-lookup"><span data-stu-id="c6be8-174">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

```csharp
namespace CustomTypes
{
    public partial class DecimalValue
    {
        private const decimal NanoFactor = 1_000_000_000;
        public DecimalValue(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.DecimalValue grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.DecimalValue(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.DecimalValue(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="c6be8-175">Chaque fois que vous utilisez des types de messages personnalisés comme celui-ci, vous *devez* les documenter avec des commentaires dans `.proto` .</span><span class="sxs-lookup"><span data-stu-id="c6be8-175">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="c6be8-176">D’autres développeurs peuvent ensuite implémenter la conversion vers et à partir du type équivalent dans leur propre langage ou infrastructure.</span><span class="sxs-lookup"><span data-stu-id="c6be8-176">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c6be8-177">[Précédent](protobuf-messages.md) 
> [Suivant](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="c6be8-177">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
