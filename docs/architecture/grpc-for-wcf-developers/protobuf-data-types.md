---
title: Types de données scalaires Protobuf - gRPC pour les développeurs WCF
description: Découvrez les types de données de base et bien connus que Protobuf et gRPC prennent en charge dans .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: ea3b53426ecf6f50f3bae22a537e227b07248508
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249433"
---
# <a name="protobuf-scalar-data-types"></a>Types de données scalaires Protobuf

Protocol Buffer (Protobuf) prend en charge une gamme de types de valeur scalaire indigène. Le tableau suivant les énumère tous avec leur type C équivalent :

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

Remarques :

1. L’encodage standard pour `int32` et `int64` est inefficace lorsque vous travaillez avec des valeurs signées. Si votre champ est susceptible de `sint32` `sint64` contenir des nombres négatifs, utilisez ou à la place. Ces types sont `int` cartographiques `long` pour les types et les types, respectivement.
2. Les `fixed` champs utilisent toujours le même nombre d’octets, quelle que soit la valeur. Ce comportement rend la sérialisation et la désétérialisation plus rapidement pour de plus grandes valeurs.
3. Les cordes Protobuf sont codées UTF-8 (ou ASCII 7 bits). La longueur codée ne peut pas être supérieure à 2<sup>32</sup>.
4. L’exécution Protobuf `ByteString` fournit un type qui cartographie `byte[]` facilement vers et depuis les tableaux de C.

## <a name="other-net-primitive-types"></a>Autres types primitifs .NET

### <a name="dates-and-times"></a>Dates et heures

Les types scalaires natifs ne prévoient pas les valeurs de <xref:System.DateTimeOffset> <xref:System.DateTime>date <xref:System.TimeSpan>et d’heure, équivalentes à celle de C, et . Vous pouvez spécifier ces types en utilisant certaines des extensions "Well Known Types" de Google. Ces extensions fournissent un support de génération de code et de temps d’exécution pour les types de terrain complexes sur les plates-formes prises en charge.

Le tableau suivant montre les types de date et d’heure :

| Type C# | Protobuf type bien connu |
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

Les propriétés générées dans la classe C ne sont pas les types de date et d’heure .NET. Les propriétés `Timestamp` `Duration` utilisent le `Google.Protobuf.WellKnownTypes` et les classes dans l’espace nom. Ces classes fournissent des méthodes `DateTimeOffset`pour `DateTime`convertir `TimeSpan`à et à partir de , et .

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
> Le `Timestamp` type fonctionne avec les temps UTC. `DateTimeOffset`valeurs ont toujours un décalage `DateTime.Kind` de zéro, et la propriété est toujours `DateTimeKind.Utc`.

### <a name="systemguid"></a>System.Guid

Protobuf ne prend pas <xref:System.Guid> directement en `UUID` charge le type, connu sous le nom de sur d’autres plates-formes. Il n’y a pas de type bien connu pour ça.

La meilleure approche `Guid` est de `string` gérer les valeurs `8-4-4-4-12` comme un champ, en `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`utilisant le format hexadecimal standard (par exemple, ). Toutes les langues et plates-formes peuvent analyser ce format.

N’utilisez pas `bytes` de `Guid` champ pour les valeurs. Les problèmes *d’endianness* [(définition de Wikipédia](https://en.wikipedia.org/wiki/Endianness)) peuvent entraîner un comportement erratique lorsque Protobuf interagit avec d’autres plates-formes, comme Java.

### <a name="nullable-types"></a>Types Nullable

La génération de code Protobuf pour C `int` utilise `int32`les types indigènes, tels que pour . Ainsi, les valeurs sont toujours incluses et ne peuvent pas être nulles.

Pour les valeurs qui nécessitent `int?` des nullité explicites, telles que l’utilisation dans votre code C, les « types bien connus » de Protobuf comprennent des emballages qui sont compilés selon des types Cmd annulés. Pour les utiliser, `wrappers.proto` `.proto` importez dans votre fichier, comme ceci :

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf utilisera `T?` le simple `int?`(par exemple, ) pour la propriété de message généré.

Le tableau suivant montre la liste complète des types d’emballages avec leur type équivalent C :

| Type C#   | Emballage de type bien connu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Les types `Timestamp` bien `Duration` connus et sont représentés dans .NET comme classes. Dans le C 8 et au-delà, vous pouvez utiliser des types de référence nuls. Mais il est important de vérifier les nons sur les `DateTimeOffset` propriétés de ces types lorsque vous convertissez à ou `TimeSpan`.

## <a name="decimals"></a>Décimales

Protobuf ne supporte pas natif `decimal` le `double` type `float`.NET, juste et . Il ya une discussion en cours dans le projet Protobuf sur la possibilité d’ajouter un type standard `Decimal` aux types bien connus, avec le soutien de la plate-forme pour les langues et les cadres qui le soutiennent. Rien n’a encore été mis en œuvre.

Il est possible de créer une `decimal` définition de message pour représenter le type qui fonctionnerait pour la sérialisation sécurisée entre les clients .NET et les serveurs. Mais les développeurs sur d’autres plates-formes devraient comprendre le format utilisé et mettre en œuvre leur propre manipulation pour elle.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Création d’un type décimal personnalisé pour Protobuf

Une mise en œuvre simple `Money` peut être similaire au type `currency` non standard que certaines API Google utilisent, sans le champ.

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

Le `nanos` domaine représente `0.999_999_999` `-0.999_999_999`des valeurs de . Par exemple, `decimal` `1.5m` la valeur serait `{ units = 1, nanos = 500_000_000 }`représentée comme . C’est `nanos` pourquoi le champ `sfixed32` dans cet exemple utilise le `int32` type, qui code plus efficacement que pour les valeurs plus grandes. Si `units` le champ est `nanos` négatif, le champ doit également être négatif.

> [!NOTE]
> Il existe plusieurs autres algorithmes pour l’encodage des `decimal` valeurs comme des chaînes d’endage, mais ce message est plus facile à comprendre que n’importe lequel d’entre eux. Les valeurs ne sont pas affectées par l’endianness sur différentes plates-formes.

La conversion entre ce `decimal` type et le type BCL peut être implémentée dans C ' comme ceci :

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
> Chaque fois que vous utilisez *must* des types de `.proto`messages personnalisés comme celui-ci, vous devez les documenter avec des commentaires dans . D’autres développeurs peuvent ensuite implémenter la conversion vers et depuis le type équivalent dans leur propre langue ou cadre.

>[!div class="step-by-step"]
>[Suivant précédent](protobuf-messages.md)
>[Next](protobuf-nested-types.md)
