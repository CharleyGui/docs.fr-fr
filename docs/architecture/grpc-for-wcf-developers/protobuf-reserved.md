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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="493a0-103">Champs réservés Protobuf</span><span class="sxs-lookup"><span data-stu-id="493a0-103">Protobuf reserved fields</span></span>

<span data-ttu-id="493a0-104">Les garanties de compatibilité descendante dans la mémoire tampon de protocole (Protobuf) s’appuient sur les numéros de champ qui représentent toujours le même élément de données.</span><span class="sxs-lookup"><span data-stu-id="493a0-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="493a0-105">Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="493a0-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="493a0-106">Pour ce faire, vous pouvez utiliser le mot clé `reserved`.</span><span class="sxs-lookup"><span data-stu-id="493a0-106">You can enfore this by using the `reserved` keyword.</span></span> 

<span data-ttu-id="493a0-107">Si les champs `displayName` et `marketId` ont été supprimés du message `Stock` défini précédemment, leurs numéros de champ doivent être réservés comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="493a0-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="493a0-108">Vous pouvez également utiliser le mot clé `reserved` en tant qu’espace réservé pour les champs qui peuvent être ajoutés ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="493a0-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="493a0-109">Vous pouvez exprimer des nombres de champs contigus sous la forme d’une plage à l’aide du mot clé `to`.</span><span class="sxs-lookup"><span data-stu-id="493a0-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="493a0-110">[Précédent](protobuf-repeated.md)
>[Suivant](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="493a0-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
