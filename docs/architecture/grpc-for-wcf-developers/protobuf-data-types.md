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
# <a name="protobuf-scalar-data-types"></a>Types de données scalaires Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf prend en charge une plage de types valeur scalaire native. Le tableau suivant les répertorie avec leur type C# équivalent :

| Type Protobuf | Type C#      | Notes |
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

## <a name="notes"></a>Notes

1. L’encodage standard `int32` pour `int64` et est inefficace lorsque vous utilisez des valeurs signées. Si votre champ est susceptible de contenir des nombres négatifs, `sint32` utilisez `sint64` ou à la place. Les deux types sont mappés `long` aux C# `int` types et, respectivement.
2. Les `fixed` champs utilisent toujours le même nombre d’octets, quelle que soit la valeur de. Ce comportement permet d’accélérer la sérialisation et la désérialisation des valeurs plus élevées.
3. Les chaînes Protobuf sont encodées en UTF-8 (ou ASCII 7 bits), et la longueur encodée ne peut pas être supérieure à 2<sup>32</sup>.
4. Le runtime Protobuf fournit un `ByteString` type qui est facilement mappé à et C# `byte[]` à partir de tableaux.

## <a name="other-net-primitive-types"></a>Autres types primitifs .NET

### <a name="dates-and-times"></a>Dates et heures

Les types scalaires natifs ne fournissent pas de valeurs de date et C#d' <xref:System.DateTimeOffset>heure <xref:System.DateTime>, ce <xref:System.TimeSpan>qui équivaut à, et. Ces types peuvent être spécifiés à l’aide d’extensions de type « bien connu » de Google, qui assurent la génération de code et la prise en charge du runtime pour les types de champs plus complexes sur les plateformes prises en charge. Le tableau suivant indique les types de date et d’heure :

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

Les propriétés générées dans C# la classe ne sont pas les types de date et d’heure .net. Les propriétés utilisent les `Timestamp` classes `Duration` et dans l' `Google.Protobuf.WellKnownTypes` espace de noms, qui fournissent des méthodes pour la `DateTimeOffset`conversion vers et `TimeSpan`à partir de, `DateTime`et.

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
> Le `Timestamp` type fonctionne avec les heures UTC ; les valeurs ont toujours un décalage égal à `DateTimeKind.Utc`zéro, `DateTime.Kind` et la propriété est toujours. `DateTimeOffset`

### <a name="systemguid"></a>System.Guid

Le <xref:System.Guid> type, connu sous `UUID` le nom d’autres plateformes, n’est pas directement pris en charge par Protobuf et il n’y a aucun type connu pour celui-ci. La meilleure approche consiste à gérer `Guid` les valeurs `string` en tant que champ, `8-4-4-4-12` en utilisant le format hexadécimal standard `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`(par exemple,), qui peut être analysé par tous les langages et toutes les plateformes. N’utilisez `bytes` pas de champ `Guid` pour les valeurs, car des problèmes avec endianness peuvent entraîner un comportement erratique lors de l’interaction avec d’autres plateformes, telles que Java.

### <a name="nullable-types"></a>Types Nullable

La génération de code Protobuf C# pour utilise les types natifs, `int` tels `int32`que pour. Cela signifie que les valeurs sont toujours incluses et ne peuvent pas être null. Pour les valeurs qui requièrent une valeur null explicite `int?` , telles C# que l’utilisation de dans votre code, les « types bien connus » de Protobuf incluent C# des wrappers qui sont compilés en types Nullable. Pour les utiliser, `wrappers.proto` importez `.proto` dans votre fichier, comme suit :

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf utilise le simple `T?` (par exemple, `int?`) pour la propriété de message générée.

Le tableau suivant présente la liste complète des types de wrappers avec C# leur type équivalent :

| Type C#   | Wrapper de type connu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Les types `Timestamp` connus et `Duration` sont représentés dans .net en tant que classes. il n’est donc pas nécessaire de disposer d’une version Nullable, mais il est important de vérifier la présence de NULL sur les propriétés `DateTimeOffset` de ces types lors de la conversion vers ou `TimeSpan`.

## <a name="decimals"></a>Décimales

Protobuf ne prend pas en charge en `decimal` mode natif le `double` type `float`.net, juste et. Il existe une discussion en continu dans le projet Protobuf sur la possibilité d’ajouter un `Decimal` type standard aux types connus, avec la prise en charge de plateforme pour les langages et les infrastructures qui le prennent en charge, mais rien n’a encore été implémenté.

Il est possible de créer une définition de message pour représenter `decimal` le type qui fonctionnerait pour la sérialisation sécurisée entre les clients et les serveurs .net, mais les développeurs sur d’autres plateformes doivent comprendre le format utilisé et implémenter leur propre format. traitement pour celui-ci.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Création d’un type décimal personnalisé pour Protobuf

Une implémentation très simple peut être similaire au type non standard `Money` utilisé par certaines API Google, sans le `currency` champ.

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

Le `nanos` champ représente les valeurs `0.999_999_999` de `-0.999_999_999`à. Par exemple, la `decimal` valeur `1.5m` est représentée comme `{ units = 1, nanos = 500_000_000 }` (c’est la raison pour `nanos` laquelle le champ de cet exemple `sfixed32` utilise le type, qui s’encode plus efficacement `int32` que pour les valeurs plus élevées). Si le `units` champ est négatif, le `nanos` champ doit également être négatif.

> [!NOTE]
> Il existe plusieurs autres algorithmes pour l' `decimal` encodage de valeurs en tant que chaînes d’octets, mais ce message est beaucoup plus facile à comprendre que l’un d’entre eux, et les valeurs ne sont pas affectées par *[endianness](https://en.wikipedia.org/wiki/Endianness)* sur différentes plateformes.

La conversion entre ce type et le `decimal` type BCL peut être implémentée dans C# comme ceci.

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
> Chaque fois que vous utilisez des types de messages d’utilitaire personnalisés comme celui-ci, vous `.proto` devez les documenter avec des commentaires dans le afin que d’autres développeurs puissent implémenter la conversion vers et à partir du type équivalent dans leur propre langage ou infrastructure.

>[!div class="step-by-step"]
>[Précédent](protobuf-messages.md)
>[Suivant](protobuf-nested-types.md)
