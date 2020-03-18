---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282524"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="c7eee-101">HTTP: Certains cookies SameSite défauts changés à Aucun</span><span class="sxs-lookup"><span data-stu-id="c7eee-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="c7eee-102">`SameSite`est une option pour les cookies qui peuvent aider à atténuer certaines attaques cross-Site Request Forgery (CSRF).</span><span class="sxs-lookup"><span data-stu-id="c7eee-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="c7eee-103">Lorsque cette option a été introduite au départ, des défauts de paiement incohérents ont été utilisés dans divers ASP.NET API de base.</span><span class="sxs-lookup"><span data-stu-id="c7eee-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="c7eee-104">L’incohérence a conduit à des résultats confus.</span><span class="sxs-lookup"><span data-stu-id="c7eee-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="c7eee-105">En ce qui concerne ASP.NET Core 3.0, ces défauts sont mieux alignés.</span><span class="sxs-lookup"><span data-stu-id="c7eee-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="c7eee-106">Vous devez adhérer à cette fonctionnalité par composante.</span><span class="sxs-lookup"><span data-stu-id="c7eee-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c7eee-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c7eee-107">Version introduced</span></span>

<span data-ttu-id="c7eee-108">3.0</span><span class="sxs-lookup"><span data-stu-id="c7eee-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c7eee-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="c7eee-109">Old behavior</span></span>

<span data-ttu-id="c7eee-110">Des API de base similaires <xref:Microsoft.AspNetCore.Http.SameSiteMode> ASP.NET ont utilisé différentes valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="c7eee-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="c7eee-111">Un exemple de l’incohérence est `HttpResponse.Cookies.Append(String, String)` `HttpResponse.Cookies.Append(String, String, CookieOptions)`vu dans et `SameSiteMode.None` `SameSiteMode.Lax`, qui a manqué à et , respectivement.</span><span class="sxs-lookup"><span data-stu-id="c7eee-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c7eee-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="c7eee-112">New behavior</span></span>

<span data-ttu-id="c7eee-113">Toutes les API `SameSiteMode.None`affectées par défaut à .</span><span class="sxs-lookup"><span data-stu-id="c7eee-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c7eee-114">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="c7eee-114">Reason for change</span></span>

<span data-ttu-id="c7eee-115">La valeur par défaut `SameSite` a été modifiée pour faire une fonction d’opt-in.</span><span class="sxs-lookup"><span data-stu-id="c7eee-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c7eee-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c7eee-116">Recommended action</span></span>

<span data-ttu-id="c7eee-117">Chaque composant qui émet des `SameSite` cookies doit décider s’il est approprié pour ses scénarios.</span><span class="sxs-lookup"><span data-stu-id="c7eee-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="c7eee-118">Examinez votre utilisation des API `SameSite` touchées et reconfigurez au besoin.</span><span class="sxs-lookup"><span data-stu-id="c7eee-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="c7eee-119">Category</span><span class="sxs-lookup"><span data-stu-id="c7eee-119">Category</span></span>

<span data-ttu-id="c7eee-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c7eee-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c7eee-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="c7eee-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
