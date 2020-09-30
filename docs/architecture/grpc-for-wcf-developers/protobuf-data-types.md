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
# <a name="protobuf-scalar-data-types"></a>Types de données scalaires Protobuf

La mémoire tampon de protocole (Protobuf) prend en charge une plage de types valeur scalaire native. Le tableau suivant les répertorie avec leur type C# équivalent :

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

1. L’encodage standard pour `int32` et `int64` est inefficace lorsque vous utilisez des valeurs signées. Si votre champ est susceptible de contenir des nombres négatifs, utilisez ou à la `sint32` `sint64` place. Ces types sont mappés aux `int` types C# et `long` , respectivement.
2. Les `fixed` champs utilisent toujours le même nombre d’octets, quelle que soit la valeur de. Ce comportement permet d’accélérer la sérialisation et la désérialisation des valeurs plus élevées.
3. Les chaînes Protobuf sont encodées en UTF-8 (ou ASCII 7 bits). La longueur encodée ne peut pas être supérieure à 2<sup>32</sup>.
4. Le runtime Protobuf fournit un `ByteString` type qui est facilement mappé à et à partir de `byte[]` tableaux C#.

## <a name="other-net-primitive-types"></a>Autres types primitifs .NET

### <a name="dates-and-times"></a>Des dates et heures

Les types scalaires natifs ne fournissent pas de valeurs de date et d’heure, équivalentes à C# <xref:System.DateTimeOffset> , <xref:System.DateTime> et <xref:System.TimeSpan> . Vous pouvez spécifier ces types à l’aide d’extensions de type « bien connu » de Google. Ces extensions fournissent la génération de code et la prise en charge du runtime pour les types de champs complexes sur les plateformes prises en charge.

Le tableau suivant indique les types de date et d’heure :

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

Les propriétés générées dans la classe C# ne sont pas les types de date et d’heure .NET. Les propriétés utilisent les `Timestamp` `Duration` classes et dans l' `Google.Protobuf.WellKnownTypes` espace de noms. Ces classes fournissent des méthodes pour la conversion vers et à partir de `DateTimeOffset` , `DateTime` et `TimeSpan` .

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
> Le `Timestamp` type fonctionne avec des heures UTC. `DateTimeOffset` les valeurs ont toujours un offset égal à zéro, et la `DateTime.Kind` propriété est toujours `DateTimeKind.Utc` .

### <a name="systemguid"></a>System.Guid

Protobuf ne prend pas directement en charge le <xref:System.Guid> type, connu sous le nom `UUID` d’autres plateformes. Il n’y a aucun type connu pour celui-ci.

La meilleure approche consiste à gérer les `Guid` valeurs comme un `string` champ, en utilisant le `8-4-4-4-12` format hexadécimal standard (par exemple, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3` ). Tous les langages et plateformes peuvent analyser ce format.

N’utilisez pas `bytes` de champ pour les `Guid` valeurs. Les problèmes liés à *endianness* ([définition Wikipédia](https://en.wikipedia.org/wiki/Endianness)) peuvent entraîner un comportement erratique lorsque Protobuf interagit avec d’autres plateformes, telles que Java.

### <a name="nullable-types"></a>Types Nullable

La génération de code Protobuf pour C# utilise les types natifs, tels que `int` pour `int32` . Par conséquent, les valeurs sont toujours incluses et ne peuvent pas être null.

Pour les valeurs qui requièrent une valeur null explicite, telles que l’utilisation `int?` de dans votre code C#, les « types connus » de Protobuf incluent des wrappers qui sont compilés en types C# Nullable. Pour les utiliser, importez `wrappers.proto` dans votre `.proto` fichier, comme suit :

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf utilise le simple `T?` (par exemple, `int?` ) pour la propriété de message générée.

Le tableau suivant présente la liste complète des types de wrappers avec leur type C# équivalent :

| Type C#   | Wrapper de type connu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Les types connus `Timestamp` et `Duration` sont représentés dans .net en tant que classes. En C# 8 et versions ultérieures, vous pouvez utiliser des types de référence Nullable. Mais il est important de vérifier la valeur NULL sur les propriétés de ces types lorsque vous effectuez une conversion vers `DateTimeOffset` ou `TimeSpan` .

## <a name="decimals"></a>Décimales

Protobuf ne prend pas en charge en mode natif le `decimal` type .net, juste `double` et `float` . Il existe une discussion continue dans le projet Protobuf sur la possibilité d’ajouter un `Decimal` type standard aux types connus, avec la prise en charge de plateforme pour les langages et les infrastructures qui le prennent en charge. Rien n’a encore été implémenté.

Il est possible de créer une définition de message pour représenter le `decimal` type qui fonctionnerait pour la sérialisation sécurisée entre les clients et les serveurs .net. Toutefois, les développeurs sur d’autres plateformes doivent comprendre le format utilisé et implémenter leur propre gestion.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Création d’un type décimal personnalisé pour Protobuf

Une implémentation simple peut être similaire au type non standard `Money` utilisé par certaines API Google, sans le `currency` champ.

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

Le `nanos` champ représente les valeurs de `0.999_999_999` à `-0.999_999_999` . Par exemple, la `decimal` valeur est `1.5m` représentée sous la forme `{ units = 1, nanos = 500_000_000 }` . C’est la raison pour laquelle le `nanos` champ de cet exemple utilise le `sfixed32` type, qui s’encode plus efficacement que `int32` pour les valeurs plus élevées. Si le `units` champ est négatif, le `nanos` champ doit également être négatif.

> [!NOTE]
> Il existe plusieurs autres algorithmes pour l’encodage de `decimal` valeurs en tant que chaînes d’octets, mais ce message est plus facile à comprendre que l’un d’entre eux. Les valeurs ne sont pas affectées par endianness sur différentes plateformes.

La conversion entre ce type et le `decimal` type BCL peut être implémentée en C# comme suit :

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
> Chaque fois que vous utilisez des types de messages personnalisés comme celui-ci, vous *devez* les documenter avec des commentaires dans `.proto` . D’autres développeurs peuvent ensuite implémenter la conversion vers et à partir du type équivalent dans leur propre langage ou infrastructure.

>[!div class="step-by-step"]
>[Précédent](protobuf-messages.md) 
> [Suivant](protobuf-nested-types.md)
