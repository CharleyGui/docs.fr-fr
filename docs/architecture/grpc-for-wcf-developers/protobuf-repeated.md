---
title: Champs répétés pour les listes et les tableaux-gRPC pour les développeurs WCF
description: Découvrez comment Protobuf gère les collections et comment elles sont liées aux collections .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 7320c76ddc58bcf5cd81150923e8cb635e510047
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867501"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="86d56-103">Champs répétés pour les listes et les tableaux</span><span class="sxs-lookup"><span data-stu-id="86d56-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="86d56-104">Vous spécifiez des listes dans la mémoire tampon de protocole (Protobuf) à l’aide du `repeated` mot clé prefix.</span><span class="sxs-lookup"><span data-stu-id="86d56-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="86d56-105">L’exemple suivant montre comment créer une liste :</span><span class="sxs-lookup"><span data-stu-id="86d56-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="86d56-106">Dans le code généré, les `repeated` champs sont représentés par les propriétés en lecture seule du [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] type au lieu de l’un des types de collections .net intégrés.</span><span class="sxs-lookup"><span data-stu-id="86d56-106">In the generated code, `repeated` fields are represented by read-only properties of the [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="86d56-107">Ce type implémente toutes les interfaces de collection .NET standard, telles que <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="86d56-107">This type implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="86d56-108">Vous pouvez utiliser des requêtes LINQ ou la convertir facilement en tableau ou une liste.</span><span class="sxs-lookup"><span data-stu-id="86d56-108">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

<span data-ttu-id="86d56-109">Le `RepeatedField<T>` type comprend le code requis pour sérialiser et désérialiser la liste au format de câble binaire.</span><span class="sxs-lookup"><span data-stu-id="86d56-109">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span>

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
><span data-ttu-id="86d56-110">[Précédent](protobuf-nested-types.md) 
> [Suivant](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="86d56-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
