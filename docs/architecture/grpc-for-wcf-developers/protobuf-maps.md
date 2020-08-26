---
title: Protobufs Maps for dictionaries-gRPC pour les développeurs WCF
description: Découvrez comment utiliser Protobufs Maps pour représenter des types de dictionnaire dans .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 2c2ae76d47b2309227d22235b5acbe2afa794158
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867463"
---
# <a name="protobuf-maps-for-dictionaries"></a>Mappages Protobuf pour les dictionnaires

Il est important de pouvoir représenter des collections arbitraires de valeurs nommées dans des messages. Dans .NET, cela est généralement géré par le biais de types de dictionnaires. L’équivalent du type .NET <xref:System.Collections.Generic.IDictionary%602> dans la mémoire tampon de protocole (Protobuf) est le `map<key_type, value_type>` type. Cette section montre comment déclarer un `map` type dans Protobuf et comment utiliser le code généré.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Dans le code généré, les `map` champs sont représentés par les propriétés en lecture seule du [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] type. Ce type implémente les interfaces de collection .NET standard, y compris <xref:System.Collections.Generic.IDictionary%602> .

Les champs de mappage ne peuvent pas être répétés directement dans une définition de message. Toutefois, vous pouvez créer un message imbriqué qui contient une carte et une utilisation `repeated` sur le type de message, comme dans l’exemple suivant :

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Utilisation des propriétés MapField dans le code

Les `MapField` Propriétés générées à partir des `map` champs sont en lecture seule et ne seront jamais `null` . Pour définir une propriété de mappage, utilisez la `Add(IDictionary<TKey,TValue> values)` méthode sur la `MapField` propriété Empty pour copier les valeurs de n’importe quel dictionnaire .net.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Pour aller plus loin

Pour plus d’informations sur Protobuf, consultez la [documentation](https://developers.google.com/protocol-buffers/docs/overview)officielle de Protobuf.

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
>[Précédent](protobuf-enums.md) 
> [Suivant](wcf-services-to-grpc-comparison.md)
