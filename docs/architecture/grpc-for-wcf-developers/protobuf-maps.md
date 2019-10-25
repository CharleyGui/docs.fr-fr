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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="cf010-103">Mappages Protobuf pour les dictionnaires</span><span class="sxs-lookup"><span data-stu-id="cf010-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="cf010-104">Il est important de pouvoir représenter des collections arbitraires de valeurs nommées dans des messages.</span><span class="sxs-lookup"><span data-stu-id="cf010-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="cf010-105">Dans .NET, cela est généralement géré à l’aide des types de dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="cf010-105">In .NET this is commonly handled using dictionary types.</span></span> <span data-ttu-id="cf010-106">L’équivalent de Protobuf du type de <xref:System.Collections.Generic.IDictionary%602> .NET est le type de `map<key_type, value_type>`.</span><span class="sxs-lookup"><span data-stu-id="cf010-106">Protobuf's equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="cf010-107">Cette section montre comment déclarer un `map` dans Protobuf et comment utiliser le code généré.</span><span class="sxs-lookup"><span data-stu-id="cf010-107">This section shows how to declare a `map` in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="cf010-108">Dans le code généré, `map` champs utilisent la classe `Google.Protobuf.Collections.MapField<TKey, TValue>`, qui implémente les interfaces de collection .NET standard, y compris les <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="cf010-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class, which implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="cf010-109">Les champs de mappage ne peuvent pas être répétés directement dans une définition de message, mais vous pouvez créer un message imbriqué contenant une carte et utiliser `repeated` sur le type de message, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cf010-109">Map fields can't be directly repeated in a message definition, but you can create a nested message containing a map and use `repeated` on the message type, like in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="cf010-110">Utilisation des propriétés MapField dans le code</span><span class="sxs-lookup"><span data-stu-id="cf010-110">Using MapField properties in code</span></span>

<span data-ttu-id="cf010-111">Les propriétés `MapField` générées à partir de `map` champs sont en lecture seule et ne sont jamais `null`.</span><span class="sxs-lookup"><span data-stu-id="cf010-111">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="cf010-112">Pour définir une propriété de mappage, utilisez la méthode `Add(IDictionary<TKey,TValue> values)` sur la propriété `MapField` vide pour copier les valeurs de n’importe quel dictionnaire .NET.</span><span class="sxs-lookup"><span data-stu-id="cf010-112">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="cf010-113">Compléments de lecture</span><span class="sxs-lookup"><span data-stu-id="cf010-113">Further reading</span></span>

<span data-ttu-id="cf010-114">Pour plus d’informations sur Protobuf, consultez la [documentation](https://developers.google.com/protocol-buffers/docs/overview)officielle de Protobuf.</span><span class="sxs-lookup"><span data-stu-id="cf010-114">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cf010-115">[Précédent](protobuf-enums.md)
>[Suivant](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="cf010-115">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
