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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="98f94-103">Mappages Protobuf pour les dictionnaires</span><span class="sxs-lookup"><span data-stu-id="98f94-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="98f94-104">Il est important de pouvoir représenter des collections arbitraires de valeurs nommées dans des messages.</span><span class="sxs-lookup"><span data-stu-id="98f94-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="98f94-105">Dans .NET, cela est généralement géré par le biais de types de dictionnaires.</span><span class="sxs-lookup"><span data-stu-id="98f94-105">In .NET, this is commonly handled through dictionary types.</span></span> <span data-ttu-id="98f94-106">L’équivalent du type .NET <xref:System.Collections.Generic.IDictionary%602> dans la mémoire tampon de protocole (Protobuf) est le `map<key_type, value_type>` type.</span><span class="sxs-lookup"><span data-stu-id="98f94-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="98f94-107">Cette section montre comment déclarer un `map` type dans Protobuf et comment utiliser le code généré.</span><span class="sxs-lookup"><span data-stu-id="98f94-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="98f94-108">Dans le code généré, les `map` champs sont représentés par les propriétés en lecture seule du [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] type.</span><span class="sxs-lookup"><span data-stu-id="98f94-108">In the generated code, `map` fields are represented by read-only properties of the [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] type.</span></span> <span data-ttu-id="98f94-109">Ce type implémente les interfaces de collection .NET standard, y compris <xref:System.Collections.Generic.IDictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="98f94-109">This type implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="98f94-110">Les champs de mappage ne peuvent pas être répétés directement dans une définition de message.</span><span class="sxs-lookup"><span data-stu-id="98f94-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="98f94-111">Toutefois, vous pouvez créer un message imbriqué qui contient une carte et une utilisation `repeated` sur le type de message, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="98f94-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="98f94-112">Utilisation des propriétés MapField dans le code</span><span class="sxs-lookup"><span data-stu-id="98f94-112">Using MapField properties in code</span></span>

<span data-ttu-id="98f94-113">Les `MapField` Propriétés générées à partir des `map` champs sont en lecture seule et ne seront jamais `null` .</span><span class="sxs-lookup"><span data-stu-id="98f94-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="98f94-114">Pour définir une propriété de mappage, utilisez la `Add(IDictionary<TKey,TValue> values)` méthode sur la `MapField` propriété Empty pour copier les valeurs de n’importe quel dictionnaire .net.</span><span class="sxs-lookup"><span data-stu-id="98f94-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="98f94-115">Pour aller plus loin</span><span class="sxs-lookup"><span data-stu-id="98f94-115">Further reading</span></span>

<span data-ttu-id="98f94-116">Pour plus d’informations sur Protobuf, consultez la [documentation](https://developers.google.com/protocol-buffers/docs/overview)officielle de Protobuf.</span><span class="sxs-lookup"><span data-stu-id="98f94-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
><span data-ttu-id="98f94-117">[Précédent](protobuf-enums.md) 
> [Suivant](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="98f94-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
