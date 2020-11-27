---
title: 'Procédure : Obtenir des informations de type et de membre à l’aide de la réflexion'
description: Découvrez comment obtenir des informations sur les types et les membres avec la réflexion, à l’aide de l’espace de noms System. Reflection.
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 771917bb2ae5cae56c775ae23119d5eda9701df1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266322"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="0e8eb-103">Procédure : Obtenir des informations de type et de membre à l’aide de la réflexion</span><span class="sxs-lookup"><span data-stu-id="0e8eb-103">How to: Get type and member information by using reflection</span></span>

<span data-ttu-id="0e8eb-104">L' <xref:System.Reflection> espace de noms contient de nombreuses méthodes pour obtenir des informations sur les types et leurs membres.</span><span class="sxs-lookup"><span data-stu-id="0e8eb-104">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="0e8eb-105">Cet article illustre l’une de ces méthodes, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e8eb-105">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0e8eb-106">Pour plus d’informations, consultez [vue d’ensemble](reflection.md)de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="0e8eb-106">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="0e8eb-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0e8eb-107">Example</span></span>

<span data-ttu-id="0e8eb-108">L’exemple suivant obtient des informations sur les types et les membres à l’aide de la réflexion :</span><span class="sxs-lookup"><span data-stu-id="0e8eb-108">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="0e8eb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e8eb-109">See also</span></span>

- [<span data-ttu-id="0e8eb-110">Programmer avec des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="0e8eb-110">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="0e8eb-111">Réflexion</span><span class="sxs-lookup"><span data-stu-id="0e8eb-111">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="0e8eb-112">Utiliser des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="0e8eb-112">Use application domains</span></span>](../app-domains/use.md)
