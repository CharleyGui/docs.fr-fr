---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Découvrez comment Protobuf gère les collections et comment elles sont liées aux collections .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 7320c76ddc58bcf5cd81150923e8cb635e510047
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867501"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Champs répétés pour les listes et les tableaux

Vous spécifiez des listes dans la mémoire tampon de protocole (Protobuf) à l’aide du `repeated` mot clé prefix. L’exemple suivant montre comment créer une liste :

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Dans le code généré, les `repeated` champs sont représentés par les propriétés en lecture seule du [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] type au lieu de l’un des types de collections .net intégrés. Ce type implémente toutes les interfaces de collection .NET standard, telles que <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IEnumerable%601> . Vous pouvez utiliser des requêtes LINQ ou la convertir facilement en tableau ou une liste.

Le `RepeatedField<T>` type comprend le code requis pour sérialiser et désérialiser la liste au format de câble binaire.

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
>[Précédent](protobuf-nested-types.md) 
> [Suivant](protobuf-reserved.md)
