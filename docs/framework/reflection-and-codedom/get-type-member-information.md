---
title: 'Procédure : Récupération d’informations sur les types et les membres à l’aide de la réflexion'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: da71845ea276267220636cfd661465ea02b2b50d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972920"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="65dda-102">Procédure : Récupération d’informations sur les types et les membres à l’aide de la réflexion</span><span class="sxs-lookup"><span data-stu-id="65dda-102">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="65dda-103">L' <xref:System.Reflection> espace de noms contient de nombreuses méthodes pour obtenir des informations sur les types et leurs membres.</span><span class="sxs-lookup"><span data-stu-id="65dda-103">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="65dda-104">Cet article illustre l’une de ces méthodes <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>,.</span><span class="sxs-lookup"><span data-stu-id="65dda-104">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="65dda-105">Pour plus d’informations, consultez [vue d’ensemble](reflection.md)de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="65dda-105">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="65dda-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="65dda-106">Example</span></span>

<span data-ttu-id="65dda-107">L’exemple suivant obtient des informations sur les types et les membres à l’aide de la réflexion :</span><span class="sxs-lookup"><span data-stu-id="65dda-107">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="65dda-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65dda-108">See also</span></span>

- [<span data-ttu-id="65dda-109">Programmer avec des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="65dda-109">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="65dda-110">Réflexion</span><span class="sxs-lookup"><span data-stu-id="65dda-110">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="65dda-111">Utiliser des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="65dda-111">Use application domains</span></span>](../app-domains/use.md)
