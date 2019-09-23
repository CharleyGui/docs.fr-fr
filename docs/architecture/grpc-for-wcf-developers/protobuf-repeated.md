---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Comprenez comment les collections sont gérées par Protobuf et comment elles sont liées aux collections .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ad06551bf3eaec795865af227815b78c9601d0db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184182"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Champs répétés pour les listes et les tableaux

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les listes sont spécifiées dans Protobuf `repeated` à l’aide du mot clé prefix. L’exemple suivant montre comment créer une liste :

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Dans le code généré, `repeated` les champs sont représentés par `Google.Protobuf.Collections.RepeatedField<T>` le type générique plutôt que par les types de collections .net intégrés. Le `RepeatedField<T>` type comprend le code requis pour sérialiser et désérialiser la liste au format de câble binaire. Il implémente toutes les interfaces de collection .NET standard, <xref:System.Collections.Generic.IList%601> telles <xref:System.Collections.Generic.IEnumerable%601>que et, vous pouvez utiliser des requêtes LINQ ou les convertir facilement en tableau ou une liste.

>[!div class="step-by-step"]
>[Précédent](protobuf-nested-types.md)
>[Suivant](protobuf-reserved.md)
