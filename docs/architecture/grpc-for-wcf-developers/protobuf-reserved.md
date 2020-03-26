---
title: Protobuf a réservé des champs - gRPC pour les développeurs WCF
description: Renseignez-vous sur les champs réservés à la compatibilité en version croisée.
ms.date: 09/09/2019
ms.openlocfilehash: f89513c4659a02cbc94e1c659baecb9e750acbdc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111034"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="d2fd6-103">Champs réservés Protobuf</span><span class="sxs-lookup"><span data-stu-id="d2fd6-103">Protobuf reserved fields</span></span>

<span data-ttu-id="d2fd6-104">Les garanties de compatibilité vers l’arrière dans Protocol Buffer (Protobuf) reposent sur des numéros de champ représentant toujours le même élément de données.</span><span class="sxs-lookup"><span data-stu-id="d2fd6-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="d2fd6-105">Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="d2fd6-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="d2fd6-106">Vous pouvez l’appliquer `reserved` en utilisant le mot clé.</span><span class="sxs-lookup"><span data-stu-id="d2fd6-106">You can enforce this by using the `reserved` keyword.</span></span>

<span data-ttu-id="d2fd6-107">Si `displayName` les `marketId` champs et les `Stock` champs ont été retirés du message défini plus tôt, leurs numéros de terrain doivent être réservés comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d2fd6-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="d2fd6-108">Vous pouvez également `reserved` utiliser le mot clé comme un espace réservé pour les champs qui pourraient être ajoutés à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="d2fd6-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="d2fd6-109">Vous pouvez exprimer des numéros de champ `to` contigus comme une plage en utilisant le mot clé.</span><span class="sxs-lookup"><span data-stu-id="d2fd6-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="d2fd6-110">[Suivant précédent](protobuf-repeated.md)
>[Next](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="d2fd6-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
