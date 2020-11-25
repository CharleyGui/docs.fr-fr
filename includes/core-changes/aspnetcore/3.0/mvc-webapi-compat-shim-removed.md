---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032625"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="5a135-101">MVC : Shim de compatibilité de l’API Web supprimé</span><span class="sxs-lookup"><span data-stu-id="5a135-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="5a135-102">À compter de ASP.NET Core 3,0, le `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="5a135-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5a135-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="5a135-103">Change description</span></span>

<span data-ttu-id="5a135-104">Le `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package (WebApiCompatShim) fournit une compatibilité partielle dans ASP.net core avec l’API Web 2 ASP.net 4. x afin de simplifier la migration des implémentations d’API Web existantes vers ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="5a135-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="5a135-105">Toutefois, les applications qui utilisent WebApiCompatShim ne bénéficient pas des fonctionnalités d’API fournies dans les versions récentes de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a135-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="5a135-106">Ces fonctionnalités incluent la génération améliorée des spécifications d’API Open, la gestion standardisée des erreurs et la génération de code client.</span><span class="sxs-lookup"><span data-stu-id="5a135-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="5a135-107">Pour mieux cibler les efforts des API dans 3,0, WebApiCompatShim a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="5a135-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="5a135-108">Les applications existantes utilisant WebApiCompatShim doivent migrer vers le `[ApiController]` modèle plus récent.</span><span class="sxs-lookup"><span data-stu-id="5a135-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5a135-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5a135-109">Version introduced</span></span>

<span data-ttu-id="5a135-110">3.0</span><span class="sxs-lookup"><span data-stu-id="5a135-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5a135-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="5a135-111">Reason for change</span></span>

<span data-ttu-id="5a135-112">Le shim de compatibilité des API Web était un outil de migration.</span><span class="sxs-lookup"><span data-stu-id="5a135-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="5a135-113">Elle restreint l’accès utilisateur aux nouvelles fonctionnalités ajoutées dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a135-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5a135-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5a135-114">Recommended action</span></span>

<span data-ttu-id="5a135-115">Supprimez l’utilisation de ce shim et migrez directement vers la fonctionnalité similaire dans ASP.NET Core lui-même.</span><span class="sxs-lookup"><span data-stu-id="5a135-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="5a135-116">Category</span><span class="sxs-lookup"><span data-stu-id="5a135-116">Category</span></span>

<span data-ttu-id="5a135-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5a135-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5a135-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="5a135-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
