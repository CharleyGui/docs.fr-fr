---
title: Protobufs Maps for dictionaries-gRPC pour les développeurs WCF
description: Comprendre comment utiliser les mappages Protobuf pour représenter. Types de dictionnaires du réseau.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6a71fb7940145571a94eaf5c8bae9dfc91a30db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184210"
---
# <a name="protobuf-maps-for-dictionaries"></a>Protobuf Maps pour les dictionnaires

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Il est important de pouvoir représenter des collections arbitraires de valeurs nommées dans des messages. Dans .NET, cela est généralement géré à l’aide des types de dictionnaire. L’équivalent de Protobuf du type <xref:System.Collections.Generic.IDictionary%602> .net est le `map<key_type, value_type>` type. Cette section montre comment déclarer un `map` dans Protobuf et comment utiliser le code généré.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Dans le code généré, `map` les champs utilisent `Google.Protobuf.Collections.MapField<TKey, TValue>` la classe, qui implémente les interfaces de collection .NET standard <xref:System.Collections.Generic.IDictionary%602>, y compris.

Les champs de mappage ne peuvent pas être répétés directement dans une définition de message, mais vous pouvez créer un message imbriqué `repeated` contenant un mappage et utiliser sur le type de message, comme dans l’exemple suivant :

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Utilisation des propriétés MapField dans le code

Les `MapField` propriétés générées `map` à partir des champs sont en lecture seule et ne `null`seront jamais. Pour définir une propriété de mappage, utilisez `Add(IDictionary<TKey,TValue> values)` la méthode sur la `MapField` propriété Empty pour copier les valeurs de n’importe quel dictionnaire .net.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Informations supplémentaires

Pour plus d’informations sur Protobuf, consultez la [documentation](https://developers.google.com/protocol-buffers/docs/overview)officielle de Protobuf.

>[!div class="step-by-step"]
>[Précédent](protobuf-enums.md)
>[Suivant](wcf-services-to-grpc-comparison.md)
