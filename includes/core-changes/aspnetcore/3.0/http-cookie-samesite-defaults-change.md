---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282524"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="046c6-101">HTTP : certaines valeurs par défaut de SameSite de cookie ont été remplacées par None</span><span class="sxs-lookup"><span data-stu-id="046c6-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="046c6-102">`SameSite`est une option pour les cookies qui peuvent aider à atténuer certaines attaques de falsification de requête intersites (CSRF).</span><span class="sxs-lookup"><span data-stu-id="046c6-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="046c6-103">Lorsque cette option a été introduite pour la première fois, des valeurs par défaut incohérentes ont été utilisées dans plusieurs API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="046c6-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="046c6-104">L’incohérence a conduit à des résultats confuss.</span><span class="sxs-lookup"><span data-stu-id="046c6-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="046c6-105">À partir de ASP.NET Core 3,0, ces valeurs par défaut sont mieux alignées.</span><span class="sxs-lookup"><span data-stu-id="046c6-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="046c6-106">Vous devez accepter cette fonctionnalité en fonction de chaque composant.</span><span class="sxs-lookup"><span data-stu-id="046c6-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="046c6-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="046c6-107">Version introduced</span></span>

<span data-ttu-id="046c6-108">3.0</span><span class="sxs-lookup"><span data-stu-id="046c6-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="046c6-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="046c6-109">Old behavior</span></span>

<span data-ttu-id="046c6-110">Les API de ASP.NET Core similaires utilisaient des valeurs par défaut <xref:Microsoft.AspNetCore.Http.SameSiteMode> différentes.</span><span class="sxs-lookup"><span data-stu-id="046c6-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="046c6-111">Un exemple de l’incohérence est visible dans `HttpResponse.Cookies.Append(String, String)` et `HttpResponse.Cookies.Append(String, String, CookieOptions)`, qui est défini par `SameSiteMode.None` défaut `SameSiteMode.Lax`respectivement sur et.</span><span class="sxs-lookup"><span data-stu-id="046c6-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="046c6-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="046c6-112">New behavior</span></span>

<span data-ttu-id="046c6-113">Toutes les API affectées ont `SameSiteMode.None`par défaut la valeur.</span><span class="sxs-lookup"><span data-stu-id="046c6-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="046c6-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="046c6-114">Reason for change</span></span>

<span data-ttu-id="046c6-115">La valeur par défaut a été modifiée `SameSite` pour rendre une fonctionnalité d’abonnement.</span><span class="sxs-lookup"><span data-stu-id="046c6-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="046c6-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="046c6-116">Recommended action</span></span>

<span data-ttu-id="046c6-117">Chaque composant qui émet des cookies doit décider si `SameSite` est approprié pour ses scénarios.</span><span class="sxs-lookup"><span data-stu-id="046c6-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="046c6-118">Passez en revue l’utilisation des API affectées et `SameSite` Reconfigurez-les en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="046c6-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="046c6-119">Category</span><span class="sxs-lookup"><span data-stu-id="046c6-119">Category</span></span>

<span data-ttu-id="046c6-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="046c6-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="046c6-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="046c6-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
