---
title: Champs répétés pour les listes et les tableaux - gRPC pour les développeurs WCF
description: Comprendre comment Protobuf gère les collections et comment elles se rapportent aux collections .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 63d99532d14deea7800673dd5a6350dd9362ad54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147969"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="fa0b0-103">Champs répétés pour les listes et les tableaux</span><span class="sxs-lookup"><span data-stu-id="fa0b0-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="fa0b0-104">Vous spécifiez des listes dans `repeated` Protocol Buffer (Protobuf) en utilisant le mot clé préfixe.</span><span class="sxs-lookup"><span data-stu-id="fa0b0-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="fa0b0-105">L’exemple suivant montre comment créer une liste :</span><span class="sxs-lookup"><span data-stu-id="fa0b0-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="fa0b0-106">Dans le code `repeated` généré, les `Google.Protobuf.Collections.RepeatedField<T>` champs sont représentés par le type générique plutôt que par l’un des types de collecte .NET intégrés.</span><span class="sxs-lookup"><span data-stu-id="fa0b0-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span>

<span data-ttu-id="fa0b0-107">Le `RepeatedField<T>` type comprend le code nécessaire pour sérialiser et déséialiser la liste au format de fil binaire.</span><span class="sxs-lookup"><span data-stu-id="fa0b0-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="fa0b0-108">Il implémente toutes les interfaces <xref:System.Collections.Generic.IList%601> de <xref:System.Collections.Generic.IEnumerable%601>collecte .NET standard, telles que et .</span><span class="sxs-lookup"><span data-stu-id="fa0b0-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="fa0b0-109">Ainsi, vous pouvez utiliser des requêtes LINQ ou la convertir en un tableau ou une liste facilement.</span><span class="sxs-lookup"><span data-stu-id="fa0b0-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fa0b0-110">[Suivant précédent](protobuf-nested-types.md)
>[Next](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="fa0b0-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
