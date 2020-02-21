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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="866b9-103">Mappages Protobuf pour les dictionnaires</span><span class="sxs-lookup"><span data-stu-id="866b9-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="866b9-104">Il est important de pouvoir représenter des collections arbitraires de valeurs nommées dans des messages.</span><span class="sxs-lookup"><span data-stu-id="866b9-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="866b9-105">Dans .NET, cela est généralement géré par le biais de types de dictionnaires.</span><span class="sxs-lookup"><span data-stu-id="866b9-105">In .NET, this is commonly handled through dictionary types.</span></span> <span data-ttu-id="866b9-106">L’équivalent du type de <xref:System.Collections.Generic.IDictionary%602> .NET dans la mémoire tampon de protocole (Protobuf) est le type de `map<key_type, value_type>`.</span><span class="sxs-lookup"><span data-stu-id="866b9-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="866b9-107">Cette section montre comment déclarer un type de `map` dans Protobuf et comment utiliser le code généré.</span><span class="sxs-lookup"><span data-stu-id="866b9-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="866b9-108">Dans le code généré, `map` champs utilisent la classe `Google.Protobuf.Collections.MapField<TKey, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="866b9-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class.</span></span> <span data-ttu-id="866b9-109">Cette classe implémente les interfaces de collection .NET standard, y compris <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="866b9-109">This class implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="866b9-110">Les champs de mappage ne peuvent pas être répétés directement dans une définition de message.</span><span class="sxs-lookup"><span data-stu-id="866b9-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="866b9-111">Toutefois, vous pouvez créer un message imbriqué qui contient une carte et utiliser `repeated` sur le type de message, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="866b9-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="866b9-112">Utilisation des propriétés MapField dans le code</span><span class="sxs-lookup"><span data-stu-id="866b9-112">Using MapField properties in code</span></span>

<span data-ttu-id="866b9-113">Les propriétés `MapField` générées à partir de `map` champs sont en lecture seule et ne sont jamais `null`.</span><span class="sxs-lookup"><span data-stu-id="866b9-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="866b9-114">Pour définir une propriété de mappage, utilisez la méthode `Add(IDictionary<TKey,TValue> values)` sur la propriété `MapField` vide pour copier les valeurs de n’importe quel dictionnaire .NET.</span><span class="sxs-lookup"><span data-stu-id="866b9-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="866b9-115">Lectures supplémentaires</span><span class="sxs-lookup"><span data-stu-id="866b9-115">Further reading</span></span>

<span data-ttu-id="866b9-116">Pour plus d’informations sur Protobuf, consultez la [documentation](https://developers.google.com/protocol-buffers/docs/overview)officielle de Protobuf.</span><span class="sxs-lookup"><span data-stu-id="866b9-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="866b9-117">[Précédent](protobuf-enums.md)
>[Suivant](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="866b9-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
