---
ms.openlocfilehash: 0fe07ac21effacffc56d37ccb46a121f443acd20
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619938"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="08fac-101">Le partage de l’état de session avec Asp.Net StateServer nécessite que tous les serveurs de la batterie de serveurs web utilisent la même version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="08fac-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="08fac-102">Détails</span><span class="sxs-lookup"><span data-stu-id="08fac-102">Details</span></span>

<span data-ttu-id="08fac-103">Lors de l’activation de l’état de session <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>, tous les serveurs dans la batterie de serveurs web donnée doivent utiliser la même version du .NET Framework pour que l’état soit correctement partagé.</span><span class="sxs-lookup"><span data-stu-id="08fac-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="08fac-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="08fac-104">Suggestion</span></span>

<span data-ttu-id="08fac-105">Veillez à mettre à niveau les versions du .NET Framework sur les serveurs web qui partagent l’état en même temps.</span><span class="sxs-lookup"><span data-stu-id="08fac-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="08fac-106">Nom</span><span class="sxs-lookup"><span data-stu-id="08fac-106">Name</span></span>    | <span data-ttu-id="08fac-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="08fac-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="08fac-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="08fac-108">Scope</span></span>   |<span data-ttu-id="08fac-109">Edge</span><span class="sxs-lookup"><span data-stu-id="08fac-109">Edge</span></span>|
|<span data-ttu-id="08fac-110">Version</span><span class="sxs-lookup"><span data-stu-id="08fac-110">Version</span></span>|<span data-ttu-id="08fac-111">4,5</span><span class="sxs-lookup"><span data-stu-id="08fac-111">4.5</span></span>|
|<span data-ttu-id="08fac-112">Type</span><span class="sxs-lookup"><span data-stu-id="08fac-112">Type</span></span>|<span data-ttu-id="08fac-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="08fac-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="08fac-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="08fac-114">Affected APIs</span></span>

-<xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
