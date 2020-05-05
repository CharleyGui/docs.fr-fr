---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78967934"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="bdcb0-101">HTTP : le navigateur SameSite les modifications d’impact sur l’authentification</span><span class="sxs-lookup"><span data-stu-id="bdcb0-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="bdcb0-102">Certains navigateurs, tels que Chrome et Firefox, ont apporté des modifications importantes à leurs implémentations de `SameSite` pour les cookies.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="bdcb0-103">Les modifications ont un impact sur les scénarios d’authentification à distance, tels que OpenID Connect et WS-Federation, `SameSite=None`qui doivent refuser par l’envoi.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="bdcb0-104">Toutefois, `SameSite=None` s’arrête sur IOS 12 et certaines versions antérieures d’autres navigateurs.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="bdcb0-105">L’application doit détecter ces versions et omettre `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="bdcb0-106">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bdcb0-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="bdcb0-107">Version introduced</span></span>

<span data-ttu-id="bdcb0-108">3,1 preview 1</span><span class="sxs-lookup"><span data-stu-id="bdcb0-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bdcb0-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="bdcb0-109">Old behavior</span></span>

<span data-ttu-id="bdcb0-110">`SameSite`est une extension standard de 2016 pour les cookies HTTP.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="bdcb0-111">Elle est destinée à atténuer les falsifications de requête intersites (CSRF).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="bdcb0-112">Il a été conçu à l’origine comme une fonctionnalité permettant aux serveurs d’accepter les nouveaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="bdcb0-113">ASP.NET Core 2,0 a ajouté la prise `SameSite`en charge initiale de.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="bdcb0-114">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="bdcb0-114">New behavior</span></span>

<span data-ttu-id="bdcb0-115">Google a proposé un nouveau standard de norme qui n’est pas compatible avec les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="bdcb0-116">La norme modifie le mode par défaut `Lax` en et ajoute une nouvelle `None` entrée pour annuler l’abonnement. `Lax` suffit pour la plupart des cookies d’application ; Toutefois, il divise les scénarios inter-sites tels que OpenID Connect et WS-Federation login.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="bdcb0-117">La plupart des connexions OAuth ne sont pas affectées en raison de différences de flux de demande.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="bdcb0-118">Le nouveau `None` paramètre provoque des problèmes de compatibilité avec les clients qui ont implémenté la norme préliminaire précédente (par exemple, IOS 12).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="bdcb0-119">Chrome 80 inclut les modifications.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="bdcb0-120">Consultez [mises à jour SameSite](https://www.chromium.org/updates/same-site) pour la chronologie de lancement du produit chrome.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="bdcb0-121">ASP.NET Core 3,1 a été mis à jour pour implémenter le nouveau `SameSite` comportement.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="bdcb0-122">La mise à jour redéfinit le `SameSiteMode.None` comportement de `SameSite=None` pour émettre et ajoute une `SameSiteMode.Unspecified` nouvelle valeur pour `SameSite` omettre l’attribut.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="bdcb0-123">Toutes les API de `Unspecified`cookie sont désormais par défaut, bien que certains composants qui utilisent des cookies définissent des valeurs plus spécifiques à leurs scénarios, tels que la corrélation OpenID Connect et les cookies à usage unique.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="bdcb0-124">Pour les autres modifications récentes de cette zone, consultez [http : certaines valeurs par défaut de SameSite de cookie ont été remplacées par aucune](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="bdcb0-125">Dans ASP.NET Core 3,0, la plupart des valeurs par défaut <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> ont <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> été remplacées par (mais en utilisant toujours la norme précédente).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bdcb0-126">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="bdcb0-126">Reason for change</span></span>

<span data-ttu-id="bdcb0-127">Modifications des navigateurs et des spécifications comme indiqué dans le texte précédent.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bdcb0-128">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="bdcb0-128">Recommended action</span></span>

<span data-ttu-id="bdcb0-129">Les applications qui interagissent avec des sites distants, par exemple par le biais d’une connexion tierce, doivent :</span><span class="sxs-lookup"><span data-stu-id="bdcb0-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="bdcb0-130">Testez ces scénarios sur plusieurs navigateurs.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="bdcb0-131">Appliquez l’atténuation de la détection de l’Explorateur de stratégies de cookies décrite dans [prendre en charge les navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="bdcb0-132">Pour obtenir des instructions sur le test et la détection de navigateur, consultez la section suivante.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="bdcb0-133">Déterminer si vous êtes concerné</span><span class="sxs-lookup"><span data-stu-id="bdcb0-133">Determine if you're affected</span></span>

<span data-ttu-id="bdcb0-134">Testez votre application Web à l’aide d’une version du client qui peut s’abonner au nouveau comportement.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="bdcb0-135">Chrome, Firefox et Microsoft Edge chrome ont tous des indicateurs de fonctionnalités d’abonnement qui peuvent être utilisés à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="bdcb0-136">Vérifiez que votre application est compatible avec les versions antérieures du client une fois que vous avez appliqué les correctifs, en particulier Safari.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="bdcb0-137">Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="bdcb0-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="bdcb0-138">Chrome</span></span>

<span data-ttu-id="bdcb0-139">Chrome 78 et versions ultérieures produisent des résultats de test trompeurs.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="bdcb0-140">Ces versions ont une atténuation temporaire en place et autorisent les cookies datant de moins de deux minutes.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="bdcb0-141">Avec les indicateurs de test appropriés activés, chrome 76 et 77 produisent des résultats plus précis.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="bdcb0-142">Pour tester le nouveau comportement, basculez `chrome://flags/#same-site-by-default-cookies` vers activé.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="bdcb0-143">Le chrome 75 et les versions antérieures sont signalés comme `None` ayant échoué avec le nouveau paramètre.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="bdcb0-144">Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="bdcb0-145">Google ne rend pas les versions de chrome plus anciennes disponibles.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="bdcb0-146">Toutefois, vous pouvez télécharger des versions antérieures de chrome, ce qui est suffisant pour les tests.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="bdcb0-147">Suivez les instructions fournies dans [Télécharger chrome](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="bdcb0-148">Chrome 76 Win64</span><span class="sxs-lookup"><span data-stu-id="bdcb0-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="bdcb0-149">Chrome 74 Win64</span><span class="sxs-lookup"><span data-stu-id="bdcb0-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="bdcb0-150">Safari</span><span class="sxs-lookup"><span data-stu-id="bdcb0-150">Safari</span></span>

<span data-ttu-id="bdcb0-151">Safari 12 implémentait strictement le brouillon précédent et échouera s’il voit `None` la nouvelle valeur dans les cookies.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="bdcb0-152">Cela doit être évité par le biais du code de détection du navigateur présenté dans la [prise en charge des navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="bdcb0-153">Veillez à tester Safari 12 et 13 ainsi que les connexions basées sur le type de système d’exploitation WebKit à l’aide de la bibliothèque d’authentification Microsoft (MSAL), de Bibliothèque d’authentification Active Directory (ADAL) ou de la bibliothèque que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="bdcb0-154">Le problème dépend de la version du système d’exploitation sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="bdcb0-155">OSX Mojave 10,14 et iOS 12 sont connus pour présenter des problèmes de compatibilité avec le nouveau comportement.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="bdcb0-156">La mise à niveau vers OSX Catalina 10,15 ou iOS 13 résout le problème.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="bdcb0-157">Safari ne dispose pas actuellement d’un indicateur d’abonnement pour tester le nouveau comportement de la spécification.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="bdcb0-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="bdcb0-158">Firefox</span></span>

<span data-ttu-id="bdcb0-159">La prise en charge de Firefox pour la nouvelle norme peut être testée sur la version 68 et `about:config` versions ultérieures en acceptant sur la page avec l’indicateur `network.cookie.sameSite.laxByDefault`de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="bdcb0-160">Aucun problème de compatibilité n’a été signalé sur les versions antérieures de Firefox.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="bdcb0-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="bdcb0-161">Microsoft Edge</span></span>

<span data-ttu-id="bdcb0-162">Bien que Microsoft Edge prenne `SameSite` en charge l’ancien standard, à compter de la version 44, il n’avait aucun problème de compatibilité avec la nouvelle norme.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="bdcb0-163">Chrome Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="bdcb0-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="bdcb0-164">L’indicateur de fonctionnalité `edge://flags/#same-site-by-default-cookies`est.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="bdcb0-165">Aucun problème de compatibilité n’a été observé lors du test avec Microsoft Edge chrome 78.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="bdcb0-166">Dispositif</span><span class="sxs-lookup"><span data-stu-id="bdcb0-166">Electron</span></span>

<span data-ttu-id="bdcb0-167">Les versions d’électrons incluent des versions plus anciennes de chrome.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="bdcb0-168">Par exemple, la version de l’électron utilisée par Microsoft teams est le chrome 66, qui présente l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="bdcb0-169">Effectuez vos propres tests de compatibilité avec la version d’électrons utilisée par votre produit.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="bdcb0-170">Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="bdcb0-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="bdcb0-171">Prendre en charge les navigateurs plus anciens</span><span class="sxs-lookup"><span data-stu-id="bdcb0-171">Support older browsers</span></span>

<span data-ttu-id="bdcb0-172">La norme `SameSite` 2016 impose que les valeurs inconnues soient `SameSite=Strict` traitées en tant que valeurs.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="bdcb0-173">Par conséquent, tous les anciens navigateurs prenant en charge la norme d’origine peuvent s' `SameSite` arrêter lorsqu’ils voient une `None`propriété avec la valeur.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="bdcb0-174">Les applications Web doivent implémenter la détection de navigateur si elles envisagent de prendre en charge ces anciens navigateurs.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="bdcb0-175">ASP.NET Core n’implémente pas la détection de navigateur `User-Agent` pour vous, car les valeurs d’en-tête de demande sont très instables et changent sur une base hebdomadaire.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="bdcb0-176">Au lieu de cela, un point d’extension dans la stratégie de `User-Agent`cookie vous permet d’ajouter une logique spécifique.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="bdcb0-177">Dans *Startup.cs*, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="bdcb0-177">In *Startup.cs*, add the following code:</span></span>

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

##### <a name="opt-out-switches"></a><span data-ttu-id="bdcb0-178">Commutateurs de refus</span><span class="sxs-lookup"><span data-stu-id="bdcb0-178">Opt-out switches</span></span>

<span data-ttu-id="bdcb0-179">Le `Microsoft.AspNetCore.SuppressSameSiteNone` commutateur de compatibilité vous permet de refuser temporairement le nouveau comportement de cookie ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="bdcb0-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="bdcb0-180">Ajoutez le code JSON suivant à un fichier *runtimeconfig. template. JSON* dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="bdcb0-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="bdcb0-181">Autres versions</span><span class="sxs-lookup"><span data-stu-id="bdcb0-181">Other Versions</span></span>

<span data-ttu-id="bdcb0-182">Les `SameSite` correctifs associés sont à venir pour :</span><span class="sxs-lookup"><span data-stu-id="bdcb0-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="bdcb0-183">ASP.NET Core 2,1, 2,2 et 3,0</span><span class="sxs-lookup"><span data-stu-id="bdcb0-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="bdcb0-184">`Microsoft.Owin`4,1</span><span class="sxs-lookup"><span data-stu-id="bdcb0-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="bdcb0-185">`System.Web`(pour .NET Framework 4.7.2 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="bdcb0-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="bdcb0-186">Category</span><span class="sxs-lookup"><span data-stu-id="bdcb0-186">Category</span></span>

<span data-ttu-id="bdcb0-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bdcb0-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bdcb0-188">API affectées</span><span class="sxs-lookup"><span data-stu-id="bdcb0-188">Affected APIs</span></span>

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
