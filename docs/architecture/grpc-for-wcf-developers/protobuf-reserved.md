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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="c2bac-103">Champs réservés Protobuf</span><span class="sxs-lookup"><span data-stu-id="c2bac-103">Protobuf reserved fields</span></span>

<span data-ttu-id="c2bac-104">Les garanties de compatibilité descendante dans la mémoire tampon de protocole (Protobuf) s’appuient sur les numéros de champ qui représentent toujours le même élément de données.</span><span class="sxs-lookup"><span data-stu-id="c2bac-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="c2bac-105">Si un champ est supprimé d’un message dans une nouvelle version du service, ce numéro de champ ne doit jamais être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="c2bac-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="c2bac-106">Vous pouvez appliquer ce comportement à l’aide du `reserved` mot clé.</span><span class="sxs-lookup"><span data-stu-id="c2bac-106">You can enforce this behavior by using the `reserved` keyword.</span></span>

<span data-ttu-id="c2bac-107">Si les `displayName` `marketId` champs et ont été supprimés du `Stock` message défini précédemment, leurs numéros de champ doivent être réservés comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c2bac-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="c2bac-108">Vous pouvez également utiliser le `reserved` mot clé en tant qu’espace réservé pour les champs qui peuvent être ajoutés ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="c2bac-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="c2bac-109">Vous pouvez exprimer des nombres de champs contigus sous la forme d’une plage à l’aide du `to` mot clé.</span><span class="sxs-lookup"><span data-stu-id="c2bac-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="c2bac-110">[Précédent](protobuf-repeated.md) 
> [Suivant](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="c2bac-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
