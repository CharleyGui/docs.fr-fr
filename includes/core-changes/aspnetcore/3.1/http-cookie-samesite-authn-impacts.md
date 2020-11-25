---
ms.openlocfilehash: 8b6d334677991382d235fd53cd3c98e3a77d650d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032319"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="b0034-101">HTTP : le navigateur SameSite les modifications d’impact sur l’authentification</span><span class="sxs-lookup"><span data-stu-id="b0034-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="b0034-102">Certains navigateurs, tels que Chrome et Firefox, ont apporté des modifications importantes à leurs implémentations de `SameSite` pour les cookies.</span><span class="sxs-lookup"><span data-stu-id="b0034-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="b0034-103">Les modifications ont un impact sur les scénarios d’authentification à distance, tels que OpenID Connect et WS-Federation, qui doivent refuser par l’envoi `SameSite=None` .</span><span class="sxs-lookup"><span data-stu-id="b0034-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="b0034-104">Toutefois, s' `SameSite=None` arrête sur IOS 12 et certaines versions antérieures d’autres navigateurs.</span><span class="sxs-lookup"><span data-stu-id="b0034-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="b0034-105">L’application doit détecter ces versions et omettre `SameSite` .</span><span class="sxs-lookup"><span data-stu-id="b0034-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="b0034-106">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="b0034-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b0034-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b0034-107">Version introduced</span></span>

<span data-ttu-id="b0034-108">3,1 preview 1</span><span class="sxs-lookup"><span data-stu-id="b0034-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b0034-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="b0034-109">Old behavior</span></span>

<span data-ttu-id="b0034-110">`SameSite` est une extension standard de 2016 pour les cookies HTTP.</span><span class="sxs-lookup"><span data-stu-id="b0034-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="b0034-111">Elle est destinée à atténuer les falsifications de requête intersites (CSRF).</span><span class="sxs-lookup"><span data-stu-id="b0034-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="b0034-112">Il a été conçu à l’origine comme une fonctionnalité permettant aux serveurs d’accepter les nouveaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="b0034-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="b0034-113">ASP.NET Core 2,0 a ajouté la prise en charge initiale de `SameSite` .</span><span class="sxs-lookup"><span data-stu-id="b0034-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b0034-114">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="b0034-114">New behavior</span></span>

<span data-ttu-id="b0034-115">Google a proposé un nouveau standard de norme qui n’est pas compatible avec les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="b0034-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="b0034-116">La norme remplace le mode par défaut par `Lax` et ajoute une nouvelle entrée `None` pour la désactivation. est suffisant `Lax` pour la plupart des cookies d’application ; Toutefois, il arrête les scénarios inter-sites tels que OpenID Connect et WS-Federation connexion.</span><span class="sxs-lookup"><span data-stu-id="b0034-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="b0034-117">La plupart des connexions OAuth ne sont pas affectées en raison de différences de flux de demande.</span><span class="sxs-lookup"><span data-stu-id="b0034-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="b0034-118">Le nouveau `None` paramètre provoque des problèmes de compatibilité avec les clients qui ont implémenté la norme préliminaire précédente (par exemple, IOS 12).</span><span class="sxs-lookup"><span data-stu-id="b0034-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="b0034-119">Chrome 80 inclut les modifications.</span><span class="sxs-lookup"><span data-stu-id="b0034-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="b0034-120">Consultez [mises à jour SameSite](https://www.chromium.org/updates/same-site) pour la chronologie de lancement du produit chrome.</span><span class="sxs-lookup"><span data-stu-id="b0034-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="b0034-121">ASP.NET Core 3,1 a été mis à jour pour implémenter le nouveau `SameSite` comportement.</span><span class="sxs-lookup"><span data-stu-id="b0034-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="b0034-122">La mise à jour redéfinit le comportement de `SameSiteMode.None` pour émettre `SameSite=None` et ajoute une nouvelle valeur `SameSiteMode.Unspecified` pour omettre l' `SameSite` attribut.</span><span class="sxs-lookup"><span data-stu-id="b0034-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="b0034-123">Toutes les API de cookie sont désormais par défaut `Unspecified` , bien que certains composants qui utilisent des cookies définissent des valeurs plus spécifiques à leurs scénarios, tels que la corrélation OpenID Connect et les cookies à usage unique.</span><span class="sxs-lookup"><span data-stu-id="b0034-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="b0034-124">Pour les autres modifications récentes de cette zone, consultez [http : certaines valeurs par défaut de SameSite de cookie ont été remplacées par aucune](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="b0034-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="b0034-125">Dans ASP.NET Core 3,0, la plupart des valeurs par défaut ont été remplacées par <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (mais en utilisant toujours la norme précédente).</span><span class="sxs-lookup"><span data-stu-id="b0034-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b0034-126">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="b0034-126">Reason for change</span></span>

<span data-ttu-id="b0034-127">Modifications des navigateurs et des spécifications comme indiqué dans le texte précédent.</span><span class="sxs-lookup"><span data-stu-id="b0034-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b0034-128">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b0034-128">Recommended action</span></span>

<span data-ttu-id="b0034-129">Les applications qui interagissent avec des sites distants, par exemple par le biais d’une connexion tierce, doivent :</span><span class="sxs-lookup"><span data-stu-id="b0034-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="b0034-130">Testez ces scénarios sur plusieurs navigateurs.</span><span class="sxs-lookup"><span data-stu-id="b0034-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="b0034-131">Appliquez l’atténuation de la détection de l’Explorateur de stratégies de cookies décrite dans [prendre en charge les navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="b0034-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="b0034-132">Pour obtenir des instructions sur le test et la détection de navigateur, consultez la section suivante.</span><span class="sxs-lookup"><span data-stu-id="b0034-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="b0034-133">Déterminer si vous êtes concerné</span><span class="sxs-lookup"><span data-stu-id="b0034-133">Determine if you're affected</span></span>

<span data-ttu-id="b0034-134">Testez votre application Web à l’aide d’une version du client qui peut s’abonner au nouveau comportement.</span><span class="sxs-lookup"><span data-stu-id="b0034-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="b0034-135">Chrome, Firefox et Microsoft Edge chrome ont tous des indicateurs de fonctionnalités d’abonnement qui peuvent être utilisés à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="b0034-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="b0034-136">Vérifiez que votre application est compatible avec les versions antérieures du client une fois que vous avez appliqué les correctifs, en particulier Safari.</span><span class="sxs-lookup"><span data-stu-id="b0034-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="b0034-137">Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="b0034-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="b0034-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="b0034-138">Chrome</span></span>

<span data-ttu-id="b0034-139">Chrome 78 et versions ultérieures produisent des résultats de test trompeurs.</span><span class="sxs-lookup"><span data-stu-id="b0034-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="b0034-140">Ces versions ont une atténuation temporaire en place et autorisent les cookies datant de moins de deux minutes.</span><span class="sxs-lookup"><span data-stu-id="b0034-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="b0034-141">Avec les indicateurs de test appropriés activés, chrome 76 et 77 produisent des résultats plus précis.</span><span class="sxs-lookup"><span data-stu-id="b0034-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="b0034-142">Pour tester le nouveau comportement, basculez `chrome://flags/#same-site-by-default-cookies` vers activé.</span><span class="sxs-lookup"><span data-stu-id="b0034-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="b0034-143">Le chrome 75 et les versions antérieures sont signalés comme ayant échoué avec le nouveau `None` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b0034-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="b0034-144">Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="b0034-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="b0034-145">Google ne rend pas les versions de chrome plus anciennes disponibles.</span><span class="sxs-lookup"><span data-stu-id="b0034-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="b0034-146">Toutefois, vous pouvez télécharger des versions antérieures de chrome, ce qui est suffisant pour les tests.</span><span class="sxs-lookup"><span data-stu-id="b0034-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="b0034-147">Suivez les instructions fournies dans [Télécharger chrome](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="b0034-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="b0034-148">Chrome 76 Win64</span><span class="sxs-lookup"><span data-stu-id="b0034-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="b0034-149">Chrome 74 Win64</span><span class="sxs-lookup"><span data-stu-id="b0034-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="b0034-150">Safari</span><span class="sxs-lookup"><span data-stu-id="b0034-150">Safari</span></span>

<span data-ttu-id="b0034-151">Safari 12 implémentait strictement le brouillon précédent et échouera s’il voit la nouvelle `None` valeur dans les cookies.</span><span class="sxs-lookup"><span data-stu-id="b0034-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="b0034-152">Cela doit être évité par le biais du code de détection du navigateur présenté dans la [prise en charge des navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="b0034-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="b0034-153">Veillez à tester Safari 12 et 13 ainsi que les connexions basées sur le type de système d’exploitation WebKit à l’aide de la bibliothèque d’authentification Microsoft (MSAL), de Bibliothèque d’authentification Active Directory (ADAL) ou de la bibliothèque que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="b0034-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="b0034-154">Le problème dépend de la version du système d’exploitation sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="b0034-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="b0034-155">OSX Mojave 10,14 et iOS 12 sont connus pour présenter des problèmes de compatibilité avec le nouveau comportement.</span><span class="sxs-lookup"><span data-stu-id="b0034-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="b0034-156">La mise à niveau vers OSX Catalina 10,15 ou iOS 13 résout le problème.</span><span class="sxs-lookup"><span data-stu-id="b0034-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="b0034-157">Safari ne dispose pas actuellement d’un indicateur d’abonnement pour tester le nouveau comportement de la spécification.</span><span class="sxs-lookup"><span data-stu-id="b0034-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="b0034-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="b0034-158">Firefox</span></span>

<span data-ttu-id="b0034-159">La prise en charge de Firefox pour la nouvelle norme peut être testée sur la version 68 et versions ultérieures en acceptant sur la `about:config` page avec l’indicateur de fonctionnalité `network.cookie.sameSite.laxByDefault` .</span><span class="sxs-lookup"><span data-stu-id="b0034-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="b0034-160">Aucun problème de compatibilité n’a été signalé sur les versions antérieures de Firefox.</span><span class="sxs-lookup"><span data-stu-id="b0034-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="b0034-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="b0034-161">Microsoft Edge</span></span>

<span data-ttu-id="b0034-162">Bien que Microsoft Edge prenne en charge l’ancien `SameSite` standard, à compter de la version 44, il n’avait aucun problème de compatibilité avec la nouvelle norme.</span><span class="sxs-lookup"><span data-stu-id="b0034-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="b0034-163">Chrome Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="b0034-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="b0034-164">L’indicateur de fonctionnalité est `edge://flags/#same-site-by-default-cookies` .</span><span class="sxs-lookup"><span data-stu-id="b0034-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="b0034-165">Aucun problème de compatibilité n’a été observé lors du test avec Microsoft Edge chrome 78.</span><span class="sxs-lookup"><span data-stu-id="b0034-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="b0034-166">Dispositif</span><span class="sxs-lookup"><span data-stu-id="b0034-166">Electron</span></span>

<span data-ttu-id="b0034-167">Les versions d’électrons incluent des versions plus anciennes de chrome.</span><span class="sxs-lookup"><span data-stu-id="b0034-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="b0034-168">Par exemple, la version de l’électron utilisée par Microsoft teams est le chrome 66, qui présente l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="b0034-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="b0034-169">Effectuez vos propres tests de compatibilité avec la version d’électrons utilisée par votre produit.</span><span class="sxs-lookup"><span data-stu-id="b0034-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="b0034-170">Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="b0034-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="b0034-171">Prendre en charge les navigateurs plus anciens</span><span class="sxs-lookup"><span data-stu-id="b0034-171">Support older browsers</span></span>

<span data-ttu-id="b0034-172">La `SameSite` norme 2016 impose que les valeurs inconnues soient traitées en tant que `SameSite=Strict` valeurs.</span><span class="sxs-lookup"><span data-stu-id="b0034-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="b0034-173">Par conséquent, tous les anciens navigateurs prenant en charge la norme d’origine peuvent s’arrêter lorsqu’ils voient une `SameSite` propriété avec la valeur `None` .</span><span class="sxs-lookup"><span data-stu-id="b0034-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="b0034-174">Les applications Web doivent implémenter la détection de navigateur si elles envisagent de prendre en charge ces anciens navigateurs.</span><span class="sxs-lookup"><span data-stu-id="b0034-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="b0034-175">ASP.NET Core n’implémente pas la détection de navigateur pour vous, car les `User-Agent` valeurs d’en-tête de demande sont très instables et changent sur une base hebdomadaire.</span><span class="sxs-lookup"><span data-stu-id="b0034-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="b0034-176">Au lieu de cela, un point d’extension dans la stratégie de cookie vous permet d’ajouter une `User-Agent` logique spécifique.</span><span class="sxs-lookup"><span data-stu-id="b0034-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="b0034-177">Dans *Startup.cs*, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b0034-177">In *Startup.cs*, add the following code:</span></span>

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

##### <a name="opt-out-switches"></a><span data-ttu-id="b0034-178">Commutateurs de refus</span><span class="sxs-lookup"><span data-stu-id="b0034-178">Opt-out switches</span></span>

<span data-ttu-id="b0034-179">Le `Microsoft.AspNetCore.SuppressSameSiteNone` commutateur de compatibilité vous permet de refuser temporairement le nouveau comportement de cookie ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="b0034-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="b0034-180">Ajoutez le code JSON suivant à un *runtimeconfig.template.js* dans un fichier de votre projet :</span><span class="sxs-lookup"><span data-stu-id="b0034-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="b0034-181">Autres versions</span><span class="sxs-lookup"><span data-stu-id="b0034-181">Other Versions</span></span>

<span data-ttu-id="b0034-182">Les `SameSite` correctifs associés sont à venir pour :</span><span class="sxs-lookup"><span data-stu-id="b0034-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="b0034-183">ASP.NET Core 2,1, 2,2 et 3,0</span><span class="sxs-lookup"><span data-stu-id="b0034-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="b0034-184">`Microsoft.Owin` 4,1</span><span class="sxs-lookup"><span data-stu-id="b0034-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="b0034-185">`System.Web` (pour .NET Framework 4.7.2 et versions ultérieures)</span><span class="sxs-lookup"><span data-stu-id="b0034-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="b0034-186">Category</span><span class="sxs-lookup"><span data-stu-id="b0034-186">Category</span></span>

<span data-ttu-id="b0034-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b0034-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b0034-188">API affectées</span><span class="sxs-lookup"><span data-stu-id="b0034-188">Affected APIs</span></span>

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
