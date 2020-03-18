---
title: Champs répétés pour les listes et les tableaux - gRPC pour les développeurs WCF
description: Comprendre comment Protobuf gère les collections et comment elles se rapportent aux collections .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 63d99532d14deea7800673dd5a6350dd9362ad54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147969"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Champs répétés pour les listes et les tableaux

Vous spécifiez des listes dans `repeated` Protocol Buffer (Protobuf) en utilisant le mot clé préfixe. L’exemple suivant montre comment créer une liste :

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Dans le code `repeated` généré, les `Google.Protobuf.Collections.RepeatedField<T>` champs sont représentés par le type générique plutôt que par l’un des types de collecte .NET intégrés.

Le `RepeatedField<T>` type comprend le code nécessaire pour sérialiser et déséialiser la liste au format de fil binaire. Il implémente toutes les interfaces <xref:System.Collections.Generic.IList%601> de <xref:System.Collections.Generic.IEnumerable%601>collecte .NET standard, telles que et . Ainsi, vous pouvez utiliser des requêtes LINQ ou la convertir en un tableau ou une liste facilement.

>[!div class="step-by-step"]
>[Suivant précédent](protobuf-nested-types.md)
>[Next](protobuf-reserved.md)
