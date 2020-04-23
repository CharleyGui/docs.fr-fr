---
title: 'Comment : récupérer des informations sur les types et les membres à l’aide de la réflexion'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 9ffc173bbd0ed12eedea0c191f6d39baf181793a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130217"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="82d6f-102">Comment : récupérer des informations sur les types et les membres à l’aide de la réflexion</span><span class="sxs-lookup"><span data-stu-id="82d6f-102">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="82d6f-103">L' <xref:System.Reflection> espace de noms contient de nombreuses méthodes pour obtenir des informations sur les types et leurs membres.</span><span class="sxs-lookup"><span data-stu-id="82d6f-103">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="82d6f-104">Cet article illustre l’une de ces méthodes <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>,.</span><span class="sxs-lookup"><span data-stu-id="82d6f-104">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="82d6f-105">Pour plus d’informations, consultez [vue d’ensemble](reflection.md)de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="82d6f-105">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="82d6f-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="82d6f-106">Example</span></span>

<span data-ttu-id="82d6f-107">L’exemple suivant obtient des informations sur les types et les membres à l’aide de la réflexion :</span><span class="sxs-lookup"><span data-stu-id="82d6f-107">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="82d6f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82d6f-108">See also</span></span>

- [<span data-ttu-id="82d6f-109">Programmer avec des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="82d6f-109">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="82d6f-110">Réflexion</span><span class="sxs-lookup"><span data-stu-id="82d6f-110">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="82d6f-111">Utiliser des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="82d6f-111">Use application domains</span></span>](../app-domains/use.md)
