---
title: Protobufs Maps for dictionaries-gRPC pour les développeurs WCF
description: Découvrez comment utiliser Protobufs Maps pour représenter des types de dictionnaire dans .NET.
ms.date: 09/09/2019
ms.openlocfilehash: bf848bbc7e3618f6d78e280fcd85d5eb88d5cfae
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543129"
---
# <a name="protobuf-maps-for-dictionaries"></a>Mappages Protobuf pour les dictionnaires

Il est important de pouvoir représenter des collections arbitraires de valeurs nommées dans des messages. Dans .NET, cela est généralement géré par le biais de types de dictionnaires. L’équivalent du type de <xref:System.Collections.Generic.IDictionary%602> .NET dans la mémoire tampon de protocole (Protobuf) est le type de `map<key_type, value_type>`. Cette section montre comment déclarer un type de `map` dans Protobuf et comment utiliser le code généré.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Dans le code généré, `map` champs utilisent la classe `Google.Protobuf.Collections.MapField<TKey, TValue>`. Cette classe implémente les interfaces de collection .NET standard, y compris <xref:System.Collections.Generic.IDictionary%602>.

Les champs de mappage ne peuvent pas être répétés directement dans une définition de message. Toutefois, vous pouvez créer un message imbriqué qui contient une carte et utiliser `repeated` sur le type de message, comme dans l’exemple suivant :

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Utilisation des propriétés MapField dans le code

Les propriétés `MapField` générées à partir de `map` champs sont en lecture seule et ne sont jamais `null`. Pour définir une propriété de mappage, utilisez la méthode `Add(IDictionary<TKey,TValue> values)` sur la propriété `MapField` vide pour copier les valeurs de n’importe quel dictionnaire .NET.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Lectures supplémentaires

Pour plus d’informations sur Protobuf, consultez la [documentation](https://developers.google.com/protocol-buffers/docs/overview)officielle de Protobuf.

>[!div class="step-by-step"]
>[Précédent](protobuf-enums.md)
>[Suivant](wcf-services-to-grpc-comparison.md)
