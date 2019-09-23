---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Comprenez comment les collections sont gérées par Protobuf et comment elles sont liées aux collections .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ad06551bf3eaec795865af227815b78c9601d0db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184182"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="68925-103">Champs répétés pour les listes et les tableaux</span><span class="sxs-lookup"><span data-stu-id="68925-103">Repeated fields for lists and arrays</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="68925-104">Les listes sont spécifiées dans Protobuf `repeated` à l’aide du mot clé prefix.</span><span class="sxs-lookup"><span data-stu-id="68925-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="68925-105">L’exemple suivant montre comment créer une liste :</span><span class="sxs-lookup"><span data-stu-id="68925-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="68925-106">Dans le code généré, `repeated` les champs sont représentés par `Google.Protobuf.Collections.RepeatedField<T>` le type générique plutôt que par les types de collections .net intégrés.</span><span class="sxs-lookup"><span data-stu-id="68925-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="68925-107">Le `RepeatedField<T>` type comprend le code requis pour sérialiser et désérialiser la liste au format de câble binaire.</span><span class="sxs-lookup"><span data-stu-id="68925-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="68925-108">Il implémente toutes les interfaces de collection .NET standard, <xref:System.Collections.Generic.IList%601> telles <xref:System.Collections.Generic.IEnumerable%601>que et, vous pouvez utiliser des requêtes LINQ ou les convertir facilement en tableau ou une liste.</span><span class="sxs-lookup"><span data-stu-id="68925-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="68925-109">[Précédent](protobuf-nested-types.md)
>[Suivant](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="68925-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
