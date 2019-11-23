---
title: Protobuf tous les champs et OneOf pour les types variant-gRPC pour les développeurs WCF
description: Découvrez comment utiliser le type any et le mot clé OneOf pour représenter des types d’objets variants dans des messages.
ms.date: 09/09/2019
ms.openlocfilehash: af3ba22c238aa80a8c6119f62d5d8914770cad68
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971614"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf tous les champs et OneOf pour les types variant

La gestion des types de propriétés dynamiques (autrement dit, les propriétés de type `object`) dans WCF est compliquée. Les sérialiseurs doivent être spécifiés, les attributs [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) doivent être fournis, et ainsi de suite.

Protobuf fournit deux options plus simples pour traiter les valeurs qui peuvent être de plus d’un type. Le type de `Any` peut représenter n’importe quel type de message Protobuf connu, tandis que le mot clé `oneof` vous permet de spécifier qu’une seule plage de champs peut être définie dans un message donné.

## <a name="any"></a>Tous

`Any` est l’un des « types connus » d’Protobuf : une collection de types de messages utiles et réutilisables avec des implémentations dans toutes les langues prises en charge. Pour utiliser le type de `Any`, vous devez importer la définition de la `google/protobuf/any.proto`.

```protobuf
syntax "proto3"

import "google/protobuf/any.proto"

message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
    int32 id = 1;
    google.protobuf.Any instrument = 2;
}
```

Dans le C# code, la classe `Any` fournit des méthodes pour définir le champ, extraire le message et vérifier le type.

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    if (change.Instrument.Is(Stock.Descriptor))
    {
        FormatStock(change.Instrument.Unpack<Stock>());
    }
    else if (change.Instrument.Is(Currency.Descriptor))
    {
        FormatCurrency(change.Instrument.Unpack<Currency>());
    }
    else
    {
        throw new ArgumentException("Unknown instrument type");
    }
}
```

Le `Descriptor` champ statique sur chaque type généré est utilisé par le code de réflexion interne de Protobuf pour résoudre `Any` types de champs. Il existe également une méthode `TryUnpack<T>`, mais qui crée une instance non initialisée de `T` même en cas d’échec. il est donc préférable d’utiliser la méthode `Is` comme indiqué ci-dessus.

## <a name="oneof"></a>Oneof

Les champs OneOf sont une fonctionnalité de langage : le mot clé `oneof` est géré par le compilateur lors de la génération de la classe de message. L’utilisation de `oneof` pour spécifier le message `ChangeNotification` peut se présenter comme suit :

```protobuf
message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
  int32 id = 1;
  oneof instrument {
    Stock stock = 2;
    Currency currency = 3;
  }
}
```

Les champs dans le jeu de `oneof` doivent avoir des numéros de champ uniques dans la déclaration globale du message.

Lorsque vous utilisez `oneof`, le code C# généré inclut une énumération qui spécifie les champs qui ont été définis. Vous pouvez tester l’énumération pour rechercher le champ défini. Les champs qui ne sont pas définis retournent `null` ou la valeur par défaut, au lieu de lever une exception.

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    switch (change.InstrumentCase)
    {
        case ChangeNotification.InstrumentOneofCase.None:
            return;
        case ChangeNotification.InstrumentOneofCase.Stock:
            FormatStock(change.Stock);
            break;
        case ChangeNotification.InstrumentOneofCase.Currency:
            FormatCurrency(change.Currency);
            break;
        default:
            throw new ArgumentException("Unknown instrument type");
    }
}
```

La définition d’un champ qui fait partie d’un `oneof` jeu efface automatiquement tous les autres champs de l’ensemble. Vous ne pouvez pas utiliser `repeated` avec `oneof`. Au lieu de cela, vous pouvez créer un message imbriqué avec le champ répété ou le `oneof` défini pour contourner cette limitation.

>[!div class="step-by-step"]
>[Précédent](protobuf-reserved.md)
>[Suivant](protobuf-enums.md)
