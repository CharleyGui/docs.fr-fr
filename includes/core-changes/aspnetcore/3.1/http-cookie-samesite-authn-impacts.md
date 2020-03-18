---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78967934"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="7dbbc-101">HTTP: Navigateur SameSite changements d’impact authentification</span><span class="sxs-lookup"><span data-stu-id="7dbbc-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="7dbbc-102">Certains navigateurs, tels que Chrome et Firefox, ont `SameSite` apporté des modifications de rupture à leurs implémentations de cookies.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="7dbbc-103">Les changements ont un impact sur les scénarios d’authentification à distance, tels que OpenID Connect et WS-Federation, qui doivent se retirer en envoyant `SameSite=None`.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="7dbbc-104">Cependant, `SameSite=None` les pauses sur iOS 12 et quelques anciennes versions d’autres navigateurs.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="7dbbc-105">L’application doit renifler ces `SameSite`versions et omettre .</span><span class="sxs-lookup"><span data-stu-id="7dbbc-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="7dbbc-106">Pour discussion sur cette question, voir [dotnet/aspnetcore-14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7dbbc-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7dbbc-107">Version introduced</span></span>

<span data-ttu-id="7dbbc-108">3.1 Aperçu 1</span><span class="sxs-lookup"><span data-stu-id="7dbbc-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7dbbc-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="7dbbc-109">Old behavior</span></span>

<span data-ttu-id="7dbbc-110">`SameSite`est un projet d’extension standard 2016 aux cookies HTTP.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="7dbbc-111">Il vise à atténuer la contrefaçon de demandes inter-sites (CSRF).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="7dbbc-112">Ceci a été conçu à l’origine comme une fonctionnalité que les serveurs opteraient en ajoutant les nouveaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="7dbbc-113">ASP.NET Core 2.0 a ajouté `SameSite`un soutien initial pour .</span><span class="sxs-lookup"><span data-stu-id="7dbbc-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7dbbc-114">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="7dbbc-114">New behavior</span></span>

<span data-ttu-id="7dbbc-115">Google a proposé un nouveau projet de norme qui n’est pas compatible à l’envers.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="7dbbc-116">La norme modifie le `Lax` mode par `None` défaut et ajoute une nouvelle entrée pour se désinscrier. `Lax` suffit pour la plupart des cookies d’application ; cependant, il brise des scénarios inter-sites comme OpenID Connect et WS-Federation login.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="7dbbc-117">La plupart des connexions OAuth ne sont pas affectées en raison des différences dans la façon dont la demande circule.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="7dbbc-118">Le `None` nouveau paramètre cause des problèmes de compatibilité avec les clients qui ont mis en œuvre la norme de projet préalable (par exemple, iOS 12).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="7dbbc-119">Chrome 80 inclura les modifications.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="7dbbc-120">Voir [les mises à jour SameSite](https://www.chromium.org/updates/same-site) pour la chronologie de lancement du produit Chrome.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="7dbbc-121">ASP.NET Core 3.1 a été mis à `SameSite` jour pour mettre en œuvre le nouveau comportement.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="7dbbc-122">La mise à jour `SameSiteMode.None` redéfinit le comportement de l’émission `SameSite=None` et ajoute une nouvelle valeur `SameSiteMode.Unspecified` pour omettre l’attribut. `SameSite`</span><span class="sxs-lookup"><span data-stu-id="7dbbc-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="7dbbc-123">Toutes les API `Unspecified`cookie sont maintenant par défaut, bien que certains composants qui utilisent des cookies définis des valeurs plus spécifiques à leurs scénarios tels que la corrélation OpenID Connect et les cookies non-avantages.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="7dbbc-124">Pour d’autres changements récents dans ce domaine, voir [HTTP: Certains cookies SameSite défauts changé à Aucun](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="7dbbc-125">Dans ASP.NET Core 3.0, la plupart des <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> défauts ont été changés de (mais toujours en utilisant la norme antérieure).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7dbbc-126">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="7dbbc-126">Reason for change</span></span>

<span data-ttu-id="7dbbc-127">Navigateur et modifications de spécifications telles qu’indiquées dans le texte précédent.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7dbbc-128">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7dbbc-128">Recommended action</span></span>

<span data-ttu-id="7dbbc-129">Les applications qui interagissent avec des sites distants, par exemple par l’intermédiaire de connexion tierces, doivent :</span><span class="sxs-lookup"><span data-stu-id="7dbbc-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="7dbbc-130">Testez ces scénarios sur plusieurs navigateurs.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="7dbbc-131">Appliquer la stratégie de cookie navigateur renifler l’atténuation discutée dans [Support navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="7dbbc-132">Pour les instructions de test et de reniflement du navigateur, voir la section suivante.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="7dbbc-133">Déterminez si vous êtes affecté</span><span class="sxs-lookup"><span data-stu-id="7dbbc-133">Determine if you're affected</span></span>

<span data-ttu-id="7dbbc-134">Testez votre application web à l’aide d’une version client qui peut opter pour le nouveau comportement.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="7dbbc-135">Chrome, Firefox et Microsoft Edge Chromium ont tous de nouveaux drapeaux de fonctionnalité opt-in qui peuvent être utilisés pour les tests.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="7dbbc-136">Vérifiez que votre application est compatible avec les anciennes versions client après avoir appliqué les correctifs, en particulier Safari.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="7dbbc-137">Pour plus d’informations, voir [Support anciens navigateurs](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="7dbbc-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="7dbbc-138">Chrome</span></span>

<span data-ttu-id="7dbbc-139">Chrome 78 et plus tard donnent des résultats de test trompeurs.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="7dbbc-140">Ces versions ont une atténuation temporaire en place et permettent aux cookies de moins de deux minutes.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="7dbbc-141">Avec les indicateurs de test appropriés activés, Chrome 76 et 77 donnent des résultats plus précis.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="7dbbc-142">Pour tester le nouveau `chrome://flags/#same-site-by-default-cookies` comportement, basculer vers activé.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="7dbbc-143">Chrome 75 et plus tôt sont `None` signalés à l’échec avec le nouveau paramètre.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="7dbbc-144">Pour plus d’informations, voir [Support anciens navigateurs](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="7dbbc-145">Google ne rend pas les anciennes versions Chrome disponibles.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="7dbbc-146">Vous pouvez, cependant, télécharger des versions plus anciennes de Chrome, qui suffira pour les tests.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="7dbbc-147">Suivez les instructions à [Télécharger Chromium](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="7dbbc-148">Chrome 76 Win64</span><span class="sxs-lookup"><span data-stu-id="7dbbc-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="7dbbc-149">Chrome 74 Win64</span><span class="sxs-lookup"><span data-stu-id="7dbbc-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="7dbbc-150">Safari</span><span class="sxs-lookup"><span data-stu-id="7dbbc-150">Safari</span></span>

<span data-ttu-id="7dbbc-151">Safari 12 a strictement mis en œuvre `None` le projet précédent et échoue s’il voit la nouvelle valeur dans les cookies.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="7dbbc-152">Cela doit être évité via le code de reniflement du navigateur indiqué dans [Support navigateurs anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="7dbbc-153">Assurez-vous de tester Safari 12 et 13 ainsi que des connexions de style OS basées sur WebKit à l’aide de Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL) ou quelle que soit la bibliothèque que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="7dbbc-154">Le problème dépend de la version OS sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="7dbbc-155">OSX Mojave 10.14 et iOS 12 sont connus pour avoir des problèmes de compatibilité avec le nouveau comportement.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="7dbbc-156">La mise à niveau vers OSX Catalina 10.15 ou iOS 13 résout le problème.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="7dbbc-157">Safari n’a pas actuellement de drapeau d’opt-in pour tester le nouveau comportement de spécification.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="7dbbc-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="7dbbc-158">Firefox</span></span>

<span data-ttu-id="7dbbc-159">Le support Firefox pour la nouvelle norme peut être testé sur `about:config` la version 68 et plus tard en optant sur la page avec le drapeau `network.cookie.sameSite.laxByDefault`de fonctionnalité .</span><span class="sxs-lookup"><span data-stu-id="7dbbc-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="7dbbc-160">Aucun problème de compatibilité n’a été signalé sur les anciennes versions de Firefox.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="7dbbc-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7dbbc-161">Microsoft Edge</span></span>

<span data-ttu-id="7dbbc-162">Alors que Microsoft `SameSite` Edge prend en charge l’ancienne norme, à partir de la version 44, il n’a pas eu de problèmes de compatibilité avec la nouvelle norme.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="7dbbc-163">Chrome Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="7dbbc-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="7dbbc-164">Le drapeau `edge://flags/#same-site-by-default-cookies`caractéristique est .</span><span class="sxs-lookup"><span data-stu-id="7dbbc-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="7dbbc-165">Aucun problème de compatibilité n’a été observé lors des tests avec Microsoft Edge Chromium 78.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="7dbbc-166">Électron</span><span class="sxs-lookup"><span data-stu-id="7dbbc-166">Electron</span></span>

<span data-ttu-id="7dbbc-167">Les versions d’Electron incluent des versions plus anciennes de Chrome.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="7dbbc-168">Par exemple, la version d’Electron utilisée par Microsoft Teams est le chrome 66, qui montre le comportement plus ancien.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="7dbbc-169">Effectuez vos propres tests de compatibilité avec la version d’Electron votre produit utilise.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="7dbbc-170">Pour plus d’informations, voir [Support anciens navigateurs](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="7dbbc-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="7dbbc-171">Prendre en charge les anciens navigateurs</span><span class="sxs-lookup"><span data-stu-id="7dbbc-171">Support older browsers</span></span>

<span data-ttu-id="7dbbc-172">La norme de `SameSite` 2016 exigeait que `SameSite=Strict` les valeurs inconnues soient traitées comme des valeurs.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="7dbbc-173">Par conséquent, tous les navigateurs plus anciens qui `SameSite` prennent en charge `None`la norme d’origine peuvent se briser quand ils voient une propriété avec une valeur de .</span><span class="sxs-lookup"><span data-stu-id="7dbbc-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="7dbbc-174">Les applications Web doivent implémenter le navigateur si elles ont l’intention de prendre en charge ces anciens navigateurs.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="7dbbc-175">ASP.NET Core ne met pas en œuvre `User-Agent` le reniflement du navigateur pour vous parce que les valeurs d’en-tête de demande sont très instables et changent sur une base hebdomadaire.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="7dbbc-176">Au lieu de cela, un point `User-Agent`d’extension dans la stratégie de cookie vous permet d’ajouter une logique spécifique.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="7dbbc-177">Dans *Startup.cs*, ajouter le code suivant:</span><span class="sxs-lookup"><span data-stu-id="7dbbc-177">In *Startup.cs*, add the following code:</span></span>

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None)
    {
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here.
        if (/* UserAgent doesn't support new behavior */)
        {
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services)
{
    services.Configure<CookiePolicyOptions>(options =>
    {
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    });
}

public void Configure(IApplicationBuilder app)
{
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication();
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a><span data-ttu-id="7dbbc-178">Commutateurs d’opt-out</span><span class="sxs-lookup"><span data-stu-id="7dbbc-178">Opt-out switches</span></span>

<span data-ttu-id="7dbbc-179">Le `Microsoft.AspNetCore.SuppressSameSiteNone` commutateur de compatibilité vous permet de vous retirer temporairement du nouveau comportement de cookie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7dbbc-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="7dbbc-180">Ajoutez le JSON suivant à un fichier *runtimeconfig.template.json* dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="7dbbc-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="7dbbc-181">Autres versions</span><span class="sxs-lookup"><span data-stu-id="7dbbc-181">Other Versions</span></span>

<span data-ttu-id="7dbbc-182">Des `SameSite` correctifs connexes sont à venir pour:</span><span class="sxs-lookup"><span data-stu-id="7dbbc-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="7dbbc-183">ASP.NET Core 2.1, 2.2 et 3.0</span><span class="sxs-lookup"><span data-stu-id="7dbbc-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="7dbbc-184">`Microsoft.Owin`4.1</span><span class="sxs-lookup"><span data-stu-id="7dbbc-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="7dbbc-185">`System.Web`(pour .NET Framework 4.7.2 et plus tard)</span><span class="sxs-lookup"><span data-stu-id="7dbbc-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="7dbbc-186">Category</span><span class="sxs-lookup"><span data-stu-id="7dbbc-186">Category</span></span>

<span data-ttu-id="7dbbc-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7dbbc-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7dbbc-188">API affectées</span><span class="sxs-lookup"><span data-stu-id="7dbbc-188">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
