---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394143"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="b84d1-101">Authentification : GoogleMD déprécié et remplacé</span><span class="sxs-lookup"><span data-stu-id="b84d1-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="b84d1-102">Google commence à [fermer](https://developers.google.com/+/api-shutdown) Googlemd Connect-in pour les applications dès le 28 janvier 2019.</span><span class="sxs-lookup"><span data-stu-id="b84d1-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b84d1-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="b84d1-103">Change description</span></span>

<span data-ttu-id="b84d1-104">ASP.NET 4.x et ASP.NET Core utilisent les API De connexion Google POUR authentifier les utilisateurs de comptes Google dans les applications Web.</span><span class="sxs-lookup"><span data-stu-id="b84d1-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="b84d1-105">Les forfaits NuGet concernés sont [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) pour ASP.NET Core et [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) pour `Microsoft.Owin` avec ASP.NET Web Forms et MVC.</span><span class="sxs-lookup"><span data-stu-id="b84d1-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="b84d1-106">Les API de remplacement de Google utilisent une source et un format de données différents.</span><span class="sxs-lookup"><span data-stu-id="b84d1-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="b84d1-107">Les mesures d’atténuation et les solutions fournies ci-dessous tiennent compte des changements structurels.</span><span class="sxs-lookup"><span data-stu-id="b84d1-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="b84d1-108">Les applications doivent vérifier que les données elles-mêmes satisfont toujours à leurs exigences.</span><span class="sxs-lookup"><span data-stu-id="b84d1-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="b84d1-109">Par exemple, les noms, adresses e-mail, liens de profil et photos de profil peuvent fournir des valeurs subtilement différentes de ce qu’auparavant.</span><span class="sxs-lookup"><span data-stu-id="b84d1-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b84d1-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b84d1-110">Version introduced</span></span>

<span data-ttu-id="b84d1-111">Toutes les versions.</span><span class="sxs-lookup"><span data-stu-id="b84d1-111">All versions.</span></span> <span data-ttu-id="b84d1-112">Ce changement est externe à ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b84d1-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b84d1-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b84d1-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="b84d1-114">Owin avec ASP.NET Web Forms et MVC</span><span class="sxs-lookup"><span data-stu-id="b84d1-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="b84d1-115">Pour `Microsoft.Owin` 3.1.0 et plus tard, une atténuation temporaire est décrite [ici](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span><span class="sxs-lookup"><span data-stu-id="b84d1-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="b84d1-116">Les applications doivent effectuer des tests avec l’atténuation pour vérifier les changements dans le format de données.</span><span class="sxs-lookup"><span data-stu-id="b84d1-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="b84d1-117">Il est prévu `Microsoft.Owin` de libérer 4.0.1 avec un correctif.</span><span class="sxs-lookup"><span data-stu-id="b84d1-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="b84d1-118">Les applications utilisant n’importe quelle version précédente doivent mettre à jour à la version 4.0.1.</span><span class="sxs-lookup"><span data-stu-id="b84d1-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="b84d1-119">ASP.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b84d1-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="b84d1-120">L’atténuation [d’Owin avec ASP.NET Web Forms et MVC](#owin-with-aspnet-web-forms-and-mvc) peut être adaptée à ASP.NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="b84d1-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="b84d1-121">Les correctifs de paquets NuGet ne sont pas prévus parce que 1.x a atteint le statut [de fin de vie.](https://dotnet.microsoft.com/platform/support-policy)</span><span class="sxs-lookup"><span data-stu-id="b84d1-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="b84d1-122">ASP.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b84d1-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="b84d1-123">Pour `Microsoft.AspNetCore.Authentication.Google` la version 2.x, `AddGoogle` remplacez votre appel existant `Startup.ConfigureServices` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b84d1-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

<span data-ttu-id="b84d1-124">Les patchs 2.1 et 2.2 de février ont incorporé la reconfiguration précédente comme le nouveau défaut.</span><span class="sxs-lookup"><span data-stu-id="b84d1-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="b84d1-125">Aucun patch n’est prévu pour ASP.NET Core 2.0 depuis qu’il a atteint [la fin de la vie](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="b84d1-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="b84d1-126">ASP.NET Noyau 3.0</span><span class="sxs-lookup"><span data-stu-id="b84d1-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="b84d1-127">L’atténuation donnée pour ASP.NET Core 2.x peut également être utilisée pour ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="b84d1-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="b84d1-128">Dans les aperçus futurs de `Microsoft.AspNetCore.Authentication.Google` 3.0, le paquet peut être supprimé.</span><span class="sxs-lookup"><span data-stu-id="b84d1-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="b84d1-129">Les utilisateurs seraient `Microsoft.AspNetCore.Authentication.OpenIdConnect` dirigés vers la place.</span><span class="sxs-lookup"><span data-stu-id="b84d1-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="b84d1-130">Le code suivant montre `AddGoogle` `AddOpenIdConnect` comment `Startup.ConfigureServices`remplacer par in .</span><span class="sxs-lookup"><span data-stu-id="b84d1-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="b84d1-131">Ce remplacement peut être utilisé avec ASP.NET Core 2.0 et plus tard et peut être adapté pour ASP.NET Core 1.x au besoin.</span><span class="sxs-lookup"><span data-stu-id="b84d1-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="b84d1-132">Category</span><span class="sxs-lookup"><span data-stu-id="b84d1-132">Category</span></span>

<span data-ttu-id="b84d1-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b84d1-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b84d1-134">API affectées</span><span class="sxs-lookup"><span data-stu-id="b84d1-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
