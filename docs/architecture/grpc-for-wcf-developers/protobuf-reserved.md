---
title: Champs réservés Protobuf-gRPC pour les développeurs WCF
description: En savoir plus sur les champs réservés pour la compatibilité entre les versions.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d4d40ca12d41ec37e0baebf10de9d0690e4297cc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184175"
---
# <a name="protobuf-reserved-fields"></a>Champs réservés Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les garanties de compatibilité descendante de Protobuf s’appuient sur les numéros de champ qui représentent toujours le même élément de données. Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé. Cela peut être appliqué à l’aide du `reserved` mot clé. Si les `displayName` `marketId`champset ont été supprimés du messagedéfiniprécédemment,leursnumérosdechampdoiventêtreréservéscommedansl’exemplesuivant.`Stock`

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Le `reserved` mot clé peut également être utilisé comme espace réservé pour les champs qui peuvent être ajoutés à l’avenir. Les numéros de champ contigus peuvent être exprimés sous `to` la forme d’une plage à l’aide du mot clé.

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
