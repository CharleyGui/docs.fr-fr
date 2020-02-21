---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Découvrez comment Protobuf gère les collections et comment elles sont liées aux collections .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 16f2b5a54b032f32c8fcb9d572d5284fe589cb01
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542957"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="bfad0-103">Champs répétés pour les listes et les tableaux</span><span class="sxs-lookup"><span data-stu-id="bfad0-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="bfad0-104">Vous spécifiez des listes dans la mémoire tampon de protocole (Protobuf) à l’aide du mot clé de préfixe `repeated`.</span><span class="sxs-lookup"><span data-stu-id="bfad0-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="bfad0-105">L’exemple suivant montre comment créer une liste :</span><span class="sxs-lookup"><span data-stu-id="bfad0-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="bfad0-106">Dans le code généré, `repeated` champs sont représentés par le type générique `Google.Protobuf.Collections.RepeatedField<T>` au lieu de l’un des types de collections .NET intégrés.</span><span class="sxs-lookup"><span data-stu-id="bfad0-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> 

<span data-ttu-id="bfad0-107">Le type de `RepeatedField<T>` comprend le code requis pour sérialiser et désérialiser la liste au format de câble binaire.</span><span class="sxs-lookup"><span data-stu-id="bfad0-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="bfad0-108">Il implémente toutes les interfaces de collection .NET standard, telles que <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="bfad0-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="bfad0-109">Vous pouvez utiliser des requêtes LINQ ou la convertir facilement en tableau ou une liste.</span><span class="sxs-lookup"><span data-stu-id="bfad0-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bfad0-110">[Précédent](protobuf-nested-types.md)
>[Suivant](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="bfad0-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
