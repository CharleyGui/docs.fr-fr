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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="9ce9e-103">Champs réservés Protobuf</span><span class="sxs-lookup"><span data-stu-id="9ce9e-103">Protobuf reserved fields</span></span>

<span data-ttu-id="9ce9e-104">Les garanties de compatibilité descendante de Protobuf s’appuient sur les numéros de champ qui représentent toujours le même élément de données.</span><span class="sxs-lookup"><span data-stu-id="9ce9e-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="9ce9e-105">Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="9ce9e-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="9ce9e-106">Cela peut être appliqué à l’aide du mot clé `reserved`.</span><span class="sxs-lookup"><span data-stu-id="9ce9e-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="9ce9e-107">Si les champs `displayName` et `marketId` ont été supprimés du message `Stock` défini précédemment, leurs numéros de champ doivent être réservés comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9ce9e-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="9ce9e-108">Le mot clé `reserved` peut également être utilisé comme espace réservé pour les champs qui peuvent être ajoutés ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="9ce9e-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="9ce9e-109">Les numéros de champ contigus peuvent être exprimés sous la forme d’une plage à l’aide du mot clé `to`.</span><span class="sxs-lookup"><span data-stu-id="9ce9e-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="9ce9e-110">[Précédent](protobuf-repeated.md)
>[Suivant](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="9ce9e-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
