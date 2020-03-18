---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393972"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="2482f-101">MVC: Web API cal de compatibilité supprimé</span><span class="sxs-lookup"><span data-stu-id="2482f-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="2482f-102">En commençant par ASP.NET Core 3.0, le `Microsoft.AspNetCore.Mvc.WebApiCompatShim` forfait n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="2482f-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2482f-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="2482f-103">Change description</span></span>

<span data-ttu-id="2482f-104">Le `Microsoft.AspNetCore.Mvc.WebApiCompatShim` forfait (WebApiCompatShim) offre une compatibilité partielle dans ASP.NET Core avec ASP.NET 4.x Web API 2 pour simplifier la migration des implémentations existantes d’API Web à ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2482f-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="2482f-105">Toutefois, les applications utilisant le WebApiCompatShim ne bénéficient pas des fonctionnalités liées à l’API lors des dernières versions ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2482f-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="2482f-106">Ces fonctionnalités comprennent l’amélioration de la génération de spécifications Open API, la gestion normalisée des erreurs et la génération de code client.</span><span class="sxs-lookup"><span data-stu-id="2482f-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="2482f-107">Pour mieux concentrer les efforts de l’API en 3.0, WebApiCompatShim a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="2482f-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="2482f-108">Les applications existantes utilisant le WebApiCompatShim devraient migrer vers le `[ApiController]` nouveau modèle.</span><span class="sxs-lookup"><span data-stu-id="2482f-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2482f-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2482f-109">Version introduced</span></span>

<span data-ttu-id="2482f-110">3.0</span><span class="sxs-lookup"><span data-stu-id="2482f-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2482f-111">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="2482f-111">Reason for change</span></span>

<span data-ttu-id="2482f-112">Le shim de compatibilité Web API était un outil de migration.</span><span class="sxs-lookup"><span data-stu-id="2482f-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="2482f-113">Il restreint l’accès des utilisateurs aux nouvelles fonctionnalités ajoutées dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2482f-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2482f-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2482f-114">Recommended action</span></span>

<span data-ttu-id="2482f-115">Supprimer l’utilisation de cette cale et migrer directement vers la fonctionnalité similaire dans ASP.NET Core lui-même.</span><span class="sxs-lookup"><span data-stu-id="2482f-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="2482f-116">Category</span><span class="sxs-lookup"><span data-stu-id="2482f-116">Category</span></span>

<span data-ttu-id="2482f-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2482f-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2482f-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="2482f-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
