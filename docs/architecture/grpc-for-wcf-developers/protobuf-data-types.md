---
title: Types de données scalaires Protobuf-gRPC pour les développeurs WCF
description: En savoir plus sur les types de données de base et connus pris en charge par Protobuf et gRPC dans .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: ae7f5f48099000dff0eefb36e23cb9b9f2ac517c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971551"
---
# <a name="protobuf-scalar-data-types"></a>Types de données scalaires Protobuf

Protobuf prend en charge une plage de types valeur scalaire native. Le tableau suivant les répertorie avec leur type C# équivalent :

| Type Protobuf | Type C#      | Remarques |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | 1     |
| `int64`       | `long`       | 1     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | 1     |
| `sint64`      | `long`       | 1     |
| `fixed32`     | `uint`       | 2     |
| `fixed64`     | `ulong`      | 2     |
| `sfixed32`    | `int`        | 2     |
| `sfixed64`    | `long`       | 2     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | 3     |
| `bytes`       | `ByteString` | 4     |

## <a name="notes"></a>Remarques

1. L’encodage standard pour `int32` et `int64` est inefficace lorsque vous utilisez des valeurs signées. Si votre champ est susceptible de contenir des nombres négatifs, utilisez `sint32` ou `sint64` à la place. Les deux types sont mappés respectivement aux types C# `int` et `long`.
2. Les champs `fixed` utilisent toujours le même nombre d’octets, quelle que soit la valeur de. Ce comportement permet d’accélérer la sérialisation et la désérialisation des valeurs plus élevées.
3. Les chaînes Protobuf sont encodées en UTF-8 (ou ASCII 7 bits), et la longueur encodée ne peut pas être supérieure à 2<sup>32</sup>.
4. Le runtime Protobuf fournit un type de `ByteString` qui est facilement mappé vers C# et à partir de `byte[]` tableaux.

## <a name="other-net-primitive-types"></a>Autres types primitifs .NET

### <a name="dates-and-times"></a>Dates et heures

Les types scalaires natifs ne fournissent pas de valeurs de date et C#d’heure, ce qui équivaut à <xref:System.DateTimeOffset>, <xref:System.DateTime>et <xref:System.TimeSpan>. Ces types peuvent être spécifiés à l’aide d’extensions de type « bien connu » de Google, qui assurent la génération de code et la prise en charge du runtime pour les types de champs plus complexes sur les plateformes prises en charge. Le tableau suivant indique les types de date et d’heure :

| Type C# | Protobuf, type connu |
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

Les propriétés générées dans C# la classe ne sont pas les types de date et d’heure .net. Les propriétés utilisent les classes `Timestamp` et `Duration` dans l’espace de noms `Google.Protobuf.WellKnownTypes`, qui fournissent des méthodes pour la conversion vers et à partir de `DateTimeOffset`, `DateTime`et `TimeSpan`.

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
> Le type de `Timestamp` fonctionne avec les heures UTC ; `DateTimeOffset` valeurs ont toujours un décalage égal à zéro et la propriété `DateTime.Kind` sera toujours `DateTimeKind.Utc`.

### <a name="systemguid"></a>System.Guid

Le type de <xref:System.Guid>, connu sous le nom de `UUID` sur d’autres plateformes, n’est pas directement pris en charge par Protobuf et il n’y a aucun type connu pour celui-ci. La meilleure approche consiste à gérer les valeurs `Guid` comme `string` champ, en utilisant le format hexadécimal `8-4-4-4-12` standard (par exemple, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), qui peut être analysé par tous les langages et toutes les plateformes. N’utilisez pas de champ de `bytes` pour les valeurs de `Guid`, car les problèmes de endianness peuvent entraîner un comportement erratique lors de l’interaction avec d’autres plateformes, telles que Java.

### <a name="nullable-types"></a>Types Nullable

La génération de code Protobuf C# pour utilise les types natifs, tels que `int` pour les `int32`. Cela signifie que les valeurs sont toujours incluses et ne peuvent pas être null. Pour les valeurs qui requièrent une valeur null explicite, telles que C# l’utilisation de `int?` dans votre code, les « types connus » de Protobuf incluent des C# wrappers qui sont compilés en types Nullable. Pour les utiliser, importez `wrappers.proto` dans votre fichier `.proto`, comme suit :

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf utilise le `T?` simple (par exemple, `int?`) pour la propriété de message générée.

Le tableau suivant présente la liste complète des types de wrappers avec C# leur type équivalent :

| Type C#   | Wrapper de type connu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Les types connus `Timestamp` et `Duration` sont représentés dans .NET en tant que classes. il n’est donc pas nécessaire de disposer d’une version Nullable, mais il est important de vérifier la présence de valeurs NULL sur les propriétés de ces types lors de la conversion en `DateTimeOffset` ou `TimeSpan`.

## <a name="decimals"></a>Décimales

Protobuf ne prend pas en charge en mode natif le type de `decimal` .NET, mais simplement `double` et `float`. Il existe une discussion continue dans le projet Protobuf sur la possibilité d’ajouter un type de `Decimal` standard aux types connus, avec la prise en charge de plateforme pour les langages et les infrastructures qui le prennent en charge, mais rien n’a encore été implémenté.

Il est possible de créer une définition de message pour représenter le type de `decimal` qui fonctionnerait pour la sérialisation sécurisée entre les clients et les serveurs .NET, mais les développeurs sur d’autres plateformes doivent comprendre le format utilisé et implémenter leur propre gestion.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Création d’un type décimal personnalisé pour Protobuf

Une implémentation très simple peut être similaire au type de `Money` non standard utilisé par certaines API Google, sans le champ `currency`.

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

Le champ `nanos` représente les valeurs de `0.999_999_999` à `-0.999_999_999`. Par exemple, la valeur `decimal` `1.5m` serait représentée comme `{ units = 1, nanos = 500_000_000 }` (c’est pourquoi le champ `nanos` dans cet exemple utilise le type `sfixed32`, qui encode plus efficacement que `int32` pour les valeurs plus élevées). Si le champ `units` est négatif, le champ `nanos` doit également être négatif.

> [!NOTE]
> Il existe plusieurs autres algorithmes pour l’encodage de valeurs `decimal` en tant que chaînes d’octets, mais ce message est beaucoup plus facile à comprendre que l’un d’entre eux, et les valeurs ne sont pas affectées par *[endianness](https://en.wikipedia.org/wiki/Endianness)* sur différentes plateformes.

La conversion entre ce type et le type de `decimal` BCL peut être C# implémentée dans comme ceci.

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
> Chaque fois que vous utilisez des types de messages d’utilitaire personnalisés comme celui-ci, vous **devez** les documenter avec des commentaires dans le `.proto` afin que d’autres développeurs puissent implémenter la conversion vers et à partir du type équivalent dans leur propre langage ou infrastructure.

>[!div class="step-by-step"]
>[Précédent](protobuf-messages.md)
>[Suivant](protobuf-nested-types.md)
