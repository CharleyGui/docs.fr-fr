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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="5e79f-103">Champs réservés Protobuf</span><span class="sxs-lookup"><span data-stu-id="5e79f-103">Protobuf reserved fields</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5e79f-104">Les garanties de compatibilité descendante de Protobuf s’appuient sur les numéros de champ qui représentent toujours le même élément de données.</span><span class="sxs-lookup"><span data-stu-id="5e79f-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="5e79f-105">Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="5e79f-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="5e79f-106">Cela peut être appliqué à l’aide du `reserved` mot clé.</span><span class="sxs-lookup"><span data-stu-id="5e79f-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="5e79f-107">Si les `displayName` `marketId`champset ont été supprimés du messagedéfiniprécédemment,leursnumérosdechampdoiventêtreréservéscommedansl’exemplesuivant.`Stock`</span><span class="sxs-lookup"><span data-stu-id="5e79f-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="5e79f-108">Le `reserved` mot clé peut également être utilisé comme espace réservé pour les champs qui peuvent être ajoutés à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="5e79f-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="5e79f-109">Les numéros de champ contigus peuvent être exprimés sous `to` la forme d’une plage à l’aide du mot clé.</span><span class="sxs-lookup"><span data-stu-id="5e79f-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="5e79f-110">[Précédent](protobuf-repeated.md)
>[Suivant](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="5e79f-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
