---
ms.openlocfilehash: e450c53008e7562e37518fdfd6872ff9b63b6ac3
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609130"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="070ae-101">L’état de session de partage avec ASP.NET StateServer nécessite que tous les serveurs de la batterie de serveurs Web utilisent la même version de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="070ae-101">Sharing session state with ASP.NET StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="070ae-102">Détails</span><span class="sxs-lookup"><span data-stu-id="070ae-102">Details</span></span>

<span data-ttu-id="070ae-103">Lors de l’activation de l’état de session <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName>, tous les serveurs dans la batterie de serveurs web donnée doivent utiliser la même version du .NET Framework pour que l’état soit correctement partagé.</span><span class="sxs-lookup"><span data-stu-id="070ae-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="070ae-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="070ae-104">Suggestion</span></span>

<span data-ttu-id="070ae-105">Veillez à mettre à niveau les versions du .NET Framework sur les serveurs web qui partagent l’état en même temps.</span><span class="sxs-lookup"><span data-stu-id="070ae-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="070ae-106">Name</span><span class="sxs-lookup"><span data-stu-id="070ae-106">Name</span></span>    | <span data-ttu-id="070ae-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="070ae-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="070ae-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="070ae-108">Scope</span></span>   |<span data-ttu-id="070ae-109">Edge</span><span class="sxs-lookup"><span data-stu-id="070ae-109">Edge</span></span>|
|<span data-ttu-id="070ae-110">Version</span><span class="sxs-lookup"><span data-stu-id="070ae-110">Version</span></span>|<span data-ttu-id="070ae-111">4.5</span><span class="sxs-lookup"><span data-stu-id="070ae-111">4.5</span></span>|
|<span data-ttu-id="070ae-112">Type</span><span class="sxs-lookup"><span data-stu-id="070ae-112">Type</span></span>|<span data-ttu-id="070ae-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="070ae-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="070ae-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="070ae-114">Affected APIs</span></span>

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->
