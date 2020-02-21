---
title: Protobuf tous les champs et OneOf pour les types variant-gRPC pour les développeurs WCF
description: Découvrez comment utiliser le type any et le mot clé OneOf pour représenter des types d’objets variants dans des messages.
ms.date: 09/09/2019
ms.openlocfilehash: 6fe7acbd1ec35289f7ad6f3acee8509ab934619d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543194"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf tous les champs et OneOf pour les types variant

La gestion des types de propriétés dynamiques (autrement dit, les propriétés de type `object`) dans Windows Communication Foundation (WCF) est complexe. Par exemple, vous devez spécifier des sérialiseurs et fournir des attributs [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) .

La mémoire tampon de protocole (Protobuf) fournit deux options plus simples pour traiter les valeurs qui peuvent être de plusieurs types. Le type de `Any` peut représenter n’importe quel type de message Protobuf connu. Vous pouvez utiliser le mot clé `oneof` pour spécifier qu’une seule plage de champs peut être définie dans un message.

## <a name="any"></a>Quelconque

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

Le code de réflexion interne de Protobuf utilise le champ statique `Descriptor` sur chaque type généré pour résoudre `Any` types de champs. Il y a également une méthode `TryUnpack<T>`, mais cela crée une instance non initialisée de `T` même en cas d’échec. Il est préférable d’utiliser la méthode `Is` comme indiqué plus haut.

## <a name="oneof"></a>Oneof

Les champs OneOf sont une fonctionnalité de langage : le compilateur gère le mot clé `oneof` lors de la génération de la classe message. L’utilisation de `oneof` pour spécifier le message `ChangeNotification` peut se présenter comme suit :

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

La définition de n’importe quel champ qui fait partie d’un `oneof` jeu efface automatiquement tous les autres champs de l’ensemble. Vous ne pouvez pas utiliser `repeated` avec `oneof`. Au lieu de cela, vous pouvez créer un message imbriqué avec le champ répété ou le `oneof` défini pour contourner cette limitation.

>[!div class="step-by-step"]
>[Précédent](protobuf-reserved.md)
>[Suivant](protobuf-enums.md)
