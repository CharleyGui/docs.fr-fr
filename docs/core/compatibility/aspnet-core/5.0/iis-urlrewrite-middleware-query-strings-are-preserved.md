---
title: 'Modification avec rupture : IIS : les chaînes de requête d’intergiciel UrlRewrite sont conservées'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé IIS : les chaînes de requête middleware UrlRewrite sont conservées'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: e4d1ecba62f9e43e7377aba1138968f15f8895d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760836"
---
# <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="71086-103">IIS : les chaînes de requête d’intergiciel UrlRewrite sont conservées</span><span class="sxs-lookup"><span data-stu-id="71086-103">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="71086-104">Un défaut d’intergiciel (middleware) IIS UrlRewrite a empêché la conservation de la chaîne de requête dans les règles de réécriture.</span><span class="sxs-lookup"><span data-stu-id="71086-104">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="71086-105">Ce défaut a été résolu pour maintenir la cohérence avec le comportement du module UrlRewrite IIS.</span><span class="sxs-lookup"><span data-stu-id="71086-105">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="71086-106">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).</span><span class="sxs-lookup"><span data-stu-id="71086-106">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="71086-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="71086-107">Version introduced</span></span>

<span data-ttu-id="71086-108">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="71086-108">ASP.NET Core 5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="71086-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="71086-109">Old behavior</span></span>

<span data-ttu-id="71086-110">Examinez la règle de réécriture suivante :</span><span class="sxs-lookup"><span data-stu-id="71086-110">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="71086-111">La règle précédente n’ajoute pas la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="71086-111">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="71086-112">Un URI comme `/about?id=1` redirige vers `/contact` au lieu de `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="71086-112">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="71086-113">L' `appendQueryString` attribut a également la valeur par défaut `true` .</span><span class="sxs-lookup"><span data-stu-id="71086-113">The `appendQueryString` attribute defaults to `true` as well.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="71086-114">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="71086-114">New behavior</span></span>

<span data-ttu-id="71086-115">La chaîne de requête est conservée.</span><span class="sxs-lookup"><span data-stu-id="71086-115">The query string is preserved.</span></span> <span data-ttu-id="71086-116">L’URI de l’exemple dans l' [ancien comportement](#old-behavior) est `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="71086-116">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="71086-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="71086-117">Reason for change</span></span>

<span data-ttu-id="71086-118">L’ancien comportement ne correspondait pas au comportement du module UrlRewrite IIS.</span><span class="sxs-lookup"><span data-stu-id="71086-118">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="71086-119">Pour prendre en charge le portage entre l’intergiciel et le module, l’objectif est de maintenir des comportements cohérents.</span><span class="sxs-lookup"><span data-stu-id="71086-119">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="71086-120">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="71086-120">Recommended action</span></span>

<span data-ttu-id="71086-121">Si le comportement de la suppression de la chaîne de requête est recommandé, affectez à l’élément la valeur `action` `appendQueryString="false"` .</span><span class="sxs-lookup"><span data-stu-id="71086-121">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="71086-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="71086-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
