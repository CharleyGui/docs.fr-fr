---
title: Champs réservés Protobuf-gRPC pour les développeurs WCF
description: En savoir plus sur les champs réservés pour la compatibilité entre les versions.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 34697371299bdc5d9a58c0696c1ce7d19816ca87
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846326"
---
# <a name="protobuf-reserved-fields"></a>Champs réservés Protobuf

Les garanties de compatibilité descendante de Protobuf s’appuient sur les numéros de champ qui représentent toujours le même élément de données. Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé. Cela peut être appliqué à l’aide du mot clé `reserved`. Si les champs `displayName` et `marketId` ont été supprimés du message `Stock` défini précédemment, leurs numéros de champ doivent être réservés comme dans l’exemple suivant.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Le mot clé `reserved` peut également être utilisé comme espace réservé pour les champs qui peuvent être ajoutés ultérieurement. Les numéros de champ contigus peuvent être exprimés sous la forme d’une plage à l’aide du mot clé `to`.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Précédent](protobuf-repeated.md)
>[Suivant](protobuf-any-oneof.md)
