---
ms.openlocfilehash: 76425ca03c98cd6a23b8366257f9e0d53b486edb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497708"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="87255-101">Le partage de l’état de session avec Asp.Net StateServer nécessite que tous les serveurs de la batterie de serveurs web utilisent la même version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="87255-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="87255-102">Détails</span><span class="sxs-lookup"><span data-stu-id="87255-102">Details</span></span>

<span data-ttu-id="87255-103">Lors de l’activation de l’état de session <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>, tous les serveurs dans la batterie de serveurs web donnée doivent utiliser la même version du .NET Framework pour que l’état soit correctement partagé.</span><span class="sxs-lookup"><span data-stu-id="87255-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="87255-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="87255-104">Suggestion</span></span>

<span data-ttu-id="87255-105">Veillez à mettre à niveau les versions du .NET Framework sur les serveurs web qui partagent l’état en même temps.</span><span class="sxs-lookup"><span data-stu-id="87255-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="87255-106">Name</span><span class="sxs-lookup"><span data-stu-id="87255-106">Name</span></span>    | <span data-ttu-id="87255-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="87255-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="87255-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="87255-108">Scope</span></span>   |<span data-ttu-id="87255-109">Edge</span><span class="sxs-lookup"><span data-stu-id="87255-109">Edge</span></span>|
|<span data-ttu-id="87255-110">Version</span><span class="sxs-lookup"><span data-stu-id="87255-110">Version</span></span>|<span data-ttu-id="87255-111">4,5</span><span class="sxs-lookup"><span data-stu-id="87255-111">4.5</span></span>|
|<span data-ttu-id="87255-112">Type</span><span class="sxs-lookup"><span data-stu-id="87255-112">Type</span></span>|<span data-ttu-id="87255-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="87255-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="87255-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="87255-114">Affected APIs</span></span>

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->
