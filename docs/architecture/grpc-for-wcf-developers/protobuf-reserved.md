---
title: Protobuf a réservé des champs - gRPC pour les développeurs WCF
description: Renseignez-vous sur les champs réservés à la compatibilité en version croisée.
ms.date: 09/09/2019
ms.openlocfilehash: bde658c671e970b7ec841d71d5b4284eb91195f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147943"
---
# <a name="protobuf-reserved-fields"></a>Champs réservés Protobuf

Les garanties de compatibilité vers l’arrière dans Protocol Buffer (Protobuf) reposent sur des numéros de champ représentant toujours le même élément de données. Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé. Vous pouvez enfore cela `reserved` en utilisant le mot clé.

Si `displayName` les `marketId` champs et les `Stock` champs ont été retirés du message défini plus tôt, leurs numéros de terrain doivent être réservés comme dans l’exemple suivant.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Vous pouvez également `reserved` utiliser le mot clé comme un espace réservé pour les champs qui pourraient être ajoutés à l’avenir. Vous pouvez exprimer des numéros de champ `to` contigus comme une plage en utilisant le mot clé.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Suivant précédent](protobuf-repeated.md)
>[Next](protobuf-any-oneof.md)
