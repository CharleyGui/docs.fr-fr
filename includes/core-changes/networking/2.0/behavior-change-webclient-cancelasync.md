---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859613"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a><span data-ttu-id="733c9-101">WebClient. CancelAsync n’est pas toujours annulé immédiatement</span><span class="sxs-lookup"><span data-stu-id="733c9-101">WebClient.CancelAsync doesn't always cancel immediately</span></span>

<span data-ttu-id="733c9-102">À compter de .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> l’appel de n’annule pas immédiatement la requête si la réponse a commencé à extraire.</span><span class="sxs-lookup"><span data-stu-id="733c9-102">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> doesn't cancel the request immediately if the response has started to fetch.</span></span>

#### <a name="change-description"></a><span data-ttu-id="733c9-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="733c9-103">Change description</span></span>

<span data-ttu-id="733c9-104">Précédemment, l' <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> appel de a annulé la demande immédiatement.</span><span class="sxs-lookup"><span data-stu-id="733c9-104">Previously, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> canceled the request immediately.</span></span> <span data-ttu-id="733c9-105">À compter de .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> l’appel de annule la demande immédiatement uniquement si la réponse n’a pas commencé la récupération.</span><span class="sxs-lookup"><span data-stu-id="733c9-105">Starting in .NET Core 2.0, calling <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> cancels the request immediately only if the response hasn't started fetching.</span></span> <span data-ttu-id="733c9-106">Si la réponse a commencé l’extraction, la demande est annulée uniquement après la lecture d’une réponse complète.</span><span class="sxs-lookup"><span data-stu-id="733c9-106">If the response has started to fetch, the request is cancelled only after a complete response is read.</span></span>

<span data-ttu-id="733c9-107">Cette modification a été implémentée <xref:System.Net.WebClient> , car l’API est déconseillée en faveur de <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="733c9-107">This change was implemented because the <xref:System.Net.WebClient> API is deprecated in favor of <xref:System.Net.Http.HttpClient>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="733c9-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="733c9-108">Version introduced</span></span>

<span data-ttu-id="733c9-109">2.0</span><span class="sxs-lookup"><span data-stu-id="733c9-109">2.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="733c9-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="733c9-110">Recommended action</span></span>

<span data-ttu-id="733c9-111">Utilisez la <xref:System.Net.Http.HttpClient?displayProperty=fullName> classe au lieu <xref:System.Net.WebClient?displayProperty=fullName>de, qui est déconseillé.</span><span class="sxs-lookup"><span data-stu-id="733c9-111">Use the <xref:System.Net.Http.HttpClient?displayProperty=fullName> class instead of <xref:System.Net.WebClient?displayProperty=fullName>, which is deprecated.</span></span>

#### <a name="category"></a><span data-ttu-id="733c9-112">Catégorie</span><span class="sxs-lookup"><span data-stu-id="733c9-112">Category</span></span>

<span data-ttu-id="733c9-113">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="733c9-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="733c9-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="733c9-114">Affected APIs</span></span>

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
