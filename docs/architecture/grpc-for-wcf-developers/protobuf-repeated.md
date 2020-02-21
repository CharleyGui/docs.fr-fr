---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Découvrez comment Protobuf gère les collections et comment elles sont liées aux collections .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 16f2b5a54b032f32c8fcb9d572d5284fe589cb01
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542957"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Champs répétés pour les listes et les tableaux

Vous spécifiez des listes dans la mémoire tampon de protocole (Protobuf) à l’aide du mot clé de préfixe `repeated`. L’exemple suivant montre comment créer une liste :

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Dans le code généré, `repeated` champs sont représentés par le type générique `Google.Protobuf.Collections.RepeatedField<T>` au lieu de l’un des types de collections .NET intégrés. 

Le type de `RepeatedField<T>` comprend le code requis pour sérialiser et désérialiser la liste au format de câble binaire. Il implémente toutes les interfaces de collection .NET standard, telles que <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IEnumerable%601>. Vous pouvez utiliser des requêtes LINQ ou la convertir facilement en tableau ou une liste.

>[!div class="step-by-step"]
>[Précédent](protobuf-nested-types.md)
>[Suivant](protobuf-reserved.md)
