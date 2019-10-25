---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Comprenez comment les collections sont gérées par Protobuf et comment elles sont liées aux collections .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 740af8af39af9bf31be17ad831f481176e30d81f
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846318"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="6b490-103">Champs répétés pour les listes et les tableaux</span><span class="sxs-lookup"><span data-stu-id="6b490-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="6b490-104">Les listes sont spécifiées dans Protobuf à l’aide du mot clé préfixe `repeated`.</span><span class="sxs-lookup"><span data-stu-id="6b490-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="6b490-105">L’exemple suivant montre comment créer une liste :</span><span class="sxs-lookup"><span data-stu-id="6b490-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="6b490-106">Dans le code généré, `repeated` champs sont représentés par le type générique `Google.Protobuf.Collections.RepeatedField<T>` au lieu de l’un des types de collections .NET intégrés.</span><span class="sxs-lookup"><span data-stu-id="6b490-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="6b490-107">Le type de `RepeatedField<T>` comprend le code requis pour sérialiser et désérialiser la liste au format de câble binaire.</span><span class="sxs-lookup"><span data-stu-id="6b490-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="6b490-108">Il implémente toutes les interfaces de collection .NET standard, telles que <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez utiliser des requêtes LINQ ou les convertir facilement en tableau ou une liste.</span><span class="sxs-lookup"><span data-stu-id="6b490-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6b490-109">[Précédent](protobuf-nested-types.md)
>[Suivant](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="6b490-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
