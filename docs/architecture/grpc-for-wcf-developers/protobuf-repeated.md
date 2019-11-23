---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Comprenez comment les collections sont gérées par Protobuf et comment elles sont liées aux collections .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 17c579bc98ba62ea74b9452bdb28efd96fc51406
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967367"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="4ce7b-103">Champs répétés pour les listes et les tableaux</span><span class="sxs-lookup"><span data-stu-id="4ce7b-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="4ce7b-104">Les listes sont spécifiées dans Protobuf à l’aide du mot clé préfixe `repeated`.</span><span class="sxs-lookup"><span data-stu-id="4ce7b-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="4ce7b-105">L’exemple suivant montre comment créer une liste :</span><span class="sxs-lookup"><span data-stu-id="4ce7b-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="4ce7b-106">Dans le code généré, `repeated` champs sont représentés par le type générique `Google.Protobuf.Collections.RepeatedField<T>` au lieu de l’un des types de collections .NET intégrés.</span><span class="sxs-lookup"><span data-stu-id="4ce7b-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="4ce7b-107">Le type de `RepeatedField<T>` comprend le code requis pour sérialiser et désérialiser la liste au format de câble binaire.</span><span class="sxs-lookup"><span data-stu-id="4ce7b-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="4ce7b-108">Il implémente toutes les interfaces de collection .NET standard, telles que <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser des requêtes LINQ ou les convertir facilement en tableau ou une liste.</span><span class="sxs-lookup"><span data-stu-id="4ce7b-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4ce7b-109">[Précédent](protobuf-nested-types.md)
>[Suivant](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="4ce7b-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
