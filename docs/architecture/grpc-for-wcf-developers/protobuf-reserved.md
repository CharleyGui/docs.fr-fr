---
title: Champs réservés Protobuf-gRPC pour les développeurs WCF
description: En savoir plus sur les champs réservés pour la compatibilité entre les versions.
ms.date: 12/15/2020
ms.openlocfilehash: d82043d619c5b3b81091ae4ea381e4778c1cf6ba
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938518"
---
# <a name="protobuf-reserved-fields"></a>Champs réservés Protobuf

Les garanties de compatibilité descendante dans la mémoire tampon de protocole (Protobuf) s’appuient sur les numéros de champ qui représentent toujours le même élément de données. Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé. Vous pouvez appliquer ce comportement à l’aide du `reserved` mot clé.

Si les `displayName` `marketId` champs et ont été supprimés du `Stock` message défini précédemment, leurs numéros de champ doivent être réservés comme dans l’exemple suivant.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Vous pouvez également utiliser le `reserved` mot clé en tant qu’espace réservé pour les champs qui peuvent être ajoutés ultérieurement. Vous pouvez exprimer des nombres de champs contigus sous la forme d’une plage à l’aide du `to` mot clé.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Précédent](protobuf-repeated.md) 
> [Suivant](protobuf-any-oneof.md)
