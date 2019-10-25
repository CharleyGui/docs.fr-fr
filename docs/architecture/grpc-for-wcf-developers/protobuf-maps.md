---
title: Protobufs Maps for dictionaries-gRPC pour les développeurs WCF
description: Comprendre comment utiliser les mappages Protobuf pour représenter. Types de dictionnaires du réseau.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: aef6b0f378e7a63f362ec42642cae15b32d49a08
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846334"
---
# <a name="protobuf-maps-for-dictionaries"></a>Mappages Protobuf pour les dictionnaires

Il est important de pouvoir représenter des collections arbitraires de valeurs nommées dans des messages. Dans .NET, cela est généralement géré à l’aide des types de dictionnaire. L’équivalent de Protobuf du type de <xref:System.Collections.Generic.IDictionary%602> .NET est le type de `map<key_type, value_type>`. Cette section montre comment déclarer un `map` dans Protobuf et comment utiliser le code généré.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Dans le code généré, `map` champs utilisent la classe `Google.Protobuf.Collections.MapField<TKey, TValue>`, qui implémente les interfaces de collection .NET standard, y compris les <xref:System.Collections.Generic.IDictionary%602>.

Les champs de mappage ne peuvent pas être répétés directement dans une définition de message, mais vous pouvez créer un message imbriqué contenant une carte et utiliser `repeated` sur le type de message, comme dans l’exemple suivant :

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

## <a name="further-reading"></a>Compléments de lecture

Pour plus d’informations sur Protobuf, consultez la [documentation](https://developers.google.com/protocol-buffers/docs/overview)officielle de Protobuf.

>[!div class="step-by-step"]
>[Précédent](protobuf-enums.md)
>[Suivant](wcf-services-to-grpc-comparison.md)
