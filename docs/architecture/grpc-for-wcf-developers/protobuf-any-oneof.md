---
title: Protobuf tous les champs et OneOf pour les types variant-gRPC pour les développeurs WCF
description: Découvrez comment utiliser le type any et le mot clé OneOf pour représenter des types d’objets variants dans des messages.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9e730e96bfdb25ef6e07ee10967921408c6f2e84
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184280"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf tous les champs et OneOf pour les types variant

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

La gestion des types de propriétés dynamiques (autrement dit, `object`des propriétés de type) dans WCF est compliquée. Les sérialiseurs doivent être spécifiés, les attributs [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) doivent être fournis, et ainsi de suite.

Protobuf fournit deux options plus simples pour traiter les valeurs qui peuvent être de plus d’un type. Le `Any` type peut représenter n’importe quel type de message Protobuf connu `oneof` , tandis que le mot clé vous permet de spécifier qu’une seule plage de champs peut être définie dans un message donné.

## <a name="any"></a>Any

`Any`est l’un des « types connus » d’Protobuf : une collection de types de messages utiles et réutilisables avec des implémentations dans toutes les langues prises en charge. Pour utiliser le `Any` type, vous devez importer la `google/protobuf/any.proto` définition.

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

Dans le C# code, la `Any` classe fournit des méthodes pour définir le champ, extraire le message et vérifier le type.

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

Le `Descriptor` champ statique sur chaque type généré est utilisé par le code de réflexion interne de Protobuf `Any` pour résoudre les types de champs. Il y a également `TryUnpack<T>` une méthode, mais cela crée une instance non initialisée `T` de même en cas d’échec. il est donc préférable d' `Is` utiliser la méthode comme indiqué ci-dessus.

## <a name="oneof"></a>Oneof

Les champs OneOf sont une fonctionnalité de langage `oneof` : le mot clé est géré par le compilateur lors de la génération de la classe de message. L' `oneof` utilisation de pour `ChangeNotification` spécifier le message peut se présenter comme suit :

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

Les champs de `oneof` l’ensemble doivent avoir des numéros de champ uniques dans la déclaration globale du message.

Lorsque vous utilisez `oneof`, le code C# généré inclut une énumération qui spécifie les champs qui ont été définis. Vous pouvez tester l’énumération pour rechercher le champ défini. Les champs qui ne sont `null` pas définis retournent ou la valeur par défaut, plutôt que de lever une exception.

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

La définition d’un champ qui fait partie `oneof` d’un jeu efface automatiquement tous les autres champs de l’ensemble. Vous ne pouvez `repeated` pas `oneof`utiliser avec. Au lieu de cela, vous pouvez créer un message imbriqué avec le champ répété ou `oneof` le jeu pour contourner cette limitation.

>[!div class="step-by-step"]
>[Précédent](protobuf-reserved.md)
>[Suivant](protobuf-enums.md)
