---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032325"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="03adb-101">Authentification : Google + déconseillé et remplacé</span><span class="sxs-lookup"><span data-stu-id="03adb-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="03adb-102">Google commence à arrêter Google + Connect pour les applications dès [le](https://developers.google.com/+/api-shutdown) 28 janvier 2019.</span><span class="sxs-lookup"><span data-stu-id="03adb-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="03adb-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="03adb-103">Change description</span></span>

<span data-ttu-id="03adb-104">ASP.NET 4. x et ASP.NET Core utilisent les API de connexion Google + pour authentifier les utilisateurs de compte Google dans Web Apps.</span><span class="sxs-lookup"><span data-stu-id="03adb-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="03adb-105">Les packages NuGet affectés sont [Microsoft. AspNetCore. Authentication. Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) pour ASP.net Core et [Microsoft. Owin. Security. google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) pour `Microsoft.Owin` avec ASP.NET Web Forms et MVC.</span><span class="sxs-lookup"><span data-stu-id="03adb-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="03adb-106">Les API de remplacement de Google utilisent une source de données et un format différents.</span><span class="sxs-lookup"><span data-stu-id="03adb-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="03adb-107">Les solutions de contournement et les solutions proposées ci-dessous comportent des modifications structurelles.</span><span class="sxs-lookup"><span data-stu-id="03adb-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="03adb-108">Les applications doivent vérifier que les données elles-mêmes satisfont toujours à leurs exigences.</span><span class="sxs-lookup"><span data-stu-id="03adb-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="03adb-109">Par exemple, les noms, les adresses de messagerie, les liens de profil et les photos de profil peuvent fournir des valeurs légèrement différentes de celles antérieures à.</span><span class="sxs-lookup"><span data-stu-id="03adb-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="03adb-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="03adb-110">Version introduced</span></span>

<span data-ttu-id="03adb-111">Toutes les versions.</span><span class="sxs-lookup"><span data-stu-id="03adb-111">All versions.</span></span> <span data-ttu-id="03adb-112">Cette modification est externe à ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="03adb-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="03adb-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="03adb-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="03adb-114">Owin avec ASP.NET Web Forms et MVC</span><span class="sxs-lookup"><span data-stu-id="03adb-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="03adb-115">Pour `Microsoft.Owin` 3.1.0 et versions ultérieures, une atténuation temporaire est décrite [ici](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span><span class="sxs-lookup"><span data-stu-id="03adb-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="03adb-116">Les applications doivent effectuer des tests avec l’atténuation pour vérifier les modifications apportées au format de données.</span><span class="sxs-lookup"><span data-stu-id="03adb-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="03adb-117">Il est prévu de publier `Microsoft.Owin` 4.0.1 avec un correctif.</span><span class="sxs-lookup"><span data-stu-id="03adb-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="03adb-118">Les applications qui utilisent une version antérieure doivent être mises à jour vers la version 4.0.1.</span><span class="sxs-lookup"><span data-stu-id="03adb-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="03adb-119">ASP.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="03adb-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="03adb-120">L’atténuation dans [Owin avec ASP.NET Web Forms et MVC](#owin-with-aspnet-web-forms-and-mvc) peut être adaptée à ASP.net Core 1. x.</span><span class="sxs-lookup"><span data-stu-id="03adb-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="03adb-121">Les correctifs de package NuGet ne sont pas planifiés, car 1. x a atteint l’état [de fin de vie](https://dotnet.microsoft.com/platform/support-policy) .</span><span class="sxs-lookup"><span data-stu-id="03adb-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="03adb-122">ASP.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="03adb-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="03adb-123">Pour `Microsoft.AspNetCore.Authentication.Google` la version 2. x, remplacez votre appel existant à `AddGoogle` dans `Startup.ConfigureServices` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="03adb-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

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

<span data-ttu-id="03adb-124">Les correctifs de février 2,1 et 2,2 incorporaient la reconfiguration précédente comme nouvelle valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="03adb-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="03adb-125">Aucun correctif n’est prévu pour ASP.NET Core 2,0, car il a atteint la [fin de vie](https://dotnet.microsoft.com/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="03adb-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="03adb-126">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="03adb-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="03adb-127">L’atténuation donnée pour ASP.NET Core 2. x peut également être utilisée pour ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="03adb-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="03adb-128">Dans les prochaines versions préliminaires de 3,0, le `Microsoft.AspNetCore.Authentication.Google` package peut être supprimé.</span><span class="sxs-lookup"><span data-stu-id="03adb-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="03adb-129">Les utilisateurs sont dirigés vers à la `Microsoft.AspNetCore.Authentication.OpenIdConnect` place.</span><span class="sxs-lookup"><span data-stu-id="03adb-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="03adb-130">Le code suivant montre comment remplacer `AddGoogle` par `AddOpenIdConnect` dans `Startup.ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="03adb-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="03adb-131">Ce remplacement peut être utilisé avec ASP.NET Core 2,0 et versions ultérieures et peut être adapté pour ASP.NET Core 1. x si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="03adb-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

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

#### <a name="category"></a><span data-ttu-id="03adb-132">Category</span><span class="sxs-lookup"><span data-stu-id="03adb-132">Category</span></span>

<span data-ttu-id="03adb-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="03adb-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03adb-134">API affectées</span><span class="sxs-lookup"><span data-stu-id="03adb-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
