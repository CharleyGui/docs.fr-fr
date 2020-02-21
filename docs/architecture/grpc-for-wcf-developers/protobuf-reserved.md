---
title: Champs réservés Protobuf-gRPC pour les développeurs WCF
description: En savoir plus sur les champs réservés pour la compatibilité entre les versions.
ms.date: 09/09/2019
ms.openlocfilehash: 50082a1aab2e7707a1839b9d56455124a9e4a6a1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542974"
---
# <a name="protobuf-reserved-fields"></a>Champs réservés Protobuf

Les garanties de compatibilité descendante dans la mémoire tampon de protocole (Protobuf) s’appuient sur les numéros de champ qui représentent toujours le même élément de données. Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé. Pour ce faire, vous pouvez utiliser le mot clé `reserved`. 

Si les champs `displayName` et `marketId` ont été supprimés du message `Stock` défini précédemment, leurs numéros de champ doivent être réservés comme dans l’exemple suivant.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Vous pouvez également utiliser le mot clé `reserved` en tant qu’espace réservé pour les champs qui peuvent être ajoutés ultérieurement. Vous pouvez exprimer des nombres de champs contigus sous la forme d’une plage à l’aide du mot clé `to`.

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
