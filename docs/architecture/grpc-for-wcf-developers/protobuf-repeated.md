---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Comprenez comment les collections sont gérées par Protobuf et comment elles sont liées aux collections .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 740af8af39af9bf31be17ad831f481176e30d81f
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846318"
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
