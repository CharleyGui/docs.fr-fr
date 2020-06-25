---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325238"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="21e78-101">IIS : les chaînes de requête d’intergiciel UrlRewrite sont conservées</span><span class="sxs-lookup"><span data-stu-id="21e78-101">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="21e78-102">Un défaut d’intergiciel (middleware) IIS UrlRewrite a empêché la conservation de la chaîne de requête dans les règles de réécriture.</span><span class="sxs-lookup"><span data-stu-id="21e78-102">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="21e78-103">Ce défaut a été résolu pour maintenir la cohérence avec le comportement du module UrlRewrite IIS.</span><span class="sxs-lookup"><span data-stu-id="21e78-103">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="21e78-104">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).</span><span class="sxs-lookup"><span data-stu-id="21e78-104">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="21e78-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="21e78-105">Version introduced</span></span>

<span data-ttu-id="21e78-106">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="21e78-106">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="21e78-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="21e78-107">Old behavior</span></span>

<span data-ttu-id="21e78-108">Examinez la règle de réécriture suivante :</span><span class="sxs-lookup"><span data-stu-id="21e78-108">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="21e78-109">La règle précédente n’ajoute pas la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="21e78-109">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="21e78-110">Un URI comme `/about?id=1` redirige vers `/contact` au lieu de `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="21e78-110">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="21e78-111">L' `appendQueryString` attribut a également la valeur par défaut `true` .</span><span class="sxs-lookup"><span data-stu-id="21e78-111">The `appendQueryString` attribute defaults to `true` as well.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="21e78-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="21e78-112">New behavior</span></span>

<span data-ttu-id="21e78-113">La chaîne de requête est conservée.</span><span class="sxs-lookup"><span data-stu-id="21e78-113">The query string is preserved.</span></span> <span data-ttu-id="21e78-114">L’URI de l’exemple dans l' [ancien comportement](#old-behavior) est `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="21e78-114">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="21e78-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="21e78-115">Reason for change</span></span>

<span data-ttu-id="21e78-116">L’ancien comportement ne correspondait pas au comportement du module UrlRewrite IIS.</span><span class="sxs-lookup"><span data-stu-id="21e78-116">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="21e78-117">Pour prendre en charge le portage entre l’intergiciel et le module, l’objectif est de maintenir des comportements cohérents.</span><span class="sxs-lookup"><span data-stu-id="21e78-117">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="21e78-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="21e78-118">Recommended action</span></span>

<span data-ttu-id="21e78-119">Si le comportement de la suppression de la chaîne de requête est recommandé, affectez à l’élément la valeur `action` `appendQueryString="false"` .</span><span class="sxs-lookup"><span data-stu-id="21e78-119">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

#### <a name="category"></a><span data-ttu-id="21e78-120">Category</span><span class="sxs-lookup"><span data-stu-id="21e78-120">Category</span></span>

<span data-ttu-id="21e78-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="21e78-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="21e78-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="21e78-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
