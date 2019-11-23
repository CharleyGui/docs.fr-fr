---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Comprenez comment les collections sont gérées par Protobuf et comment elles sont liées aux collections .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 17c579bc98ba62ea74b9452bdb28efd96fc51406
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967367"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Champs répétés pour les listes et les tableaux

Les listes sont spécifiées dans Protobuf à l’aide du mot clé préfixe `repeated`. L’exemple suivant montre comment créer une liste :

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Dans le code généré, `repeated` champs sont représentés par le type générique `Google.Protobuf.Collections.RepeatedField<T>` au lieu de l’un des types de collections .NET intégrés. Le type de `RepeatedField<T>` comprend le code requis pour sérialiser et désérialiser la liste au format de câble binaire. Il implémente toutes les interfaces de collection .NET standard, telles que <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser des requêtes LINQ ou les convertir facilement en tableau ou une liste.

>[!div class="step-by-step"]
>[Précédent](protobuf-nested-types.md)
>[Suivant](protobuf-reserved.md)
