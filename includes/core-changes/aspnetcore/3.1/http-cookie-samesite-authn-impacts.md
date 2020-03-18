---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78967934"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP: Navigateur SameSite changements d’impact authentification

Certains navigateurs, tels que Chrome et Firefox, ont `SameSite` apporté des modifications de rupture à leurs implémentations de cookies. Les changements ont un impact sur les scénarios d’authentification à distance, tels que OpenID Connect et WS-Federation, qui doivent se retirer en envoyant `SameSite=None`. Cependant, `SameSite=None` les pauses sur iOS 12 et quelques anciennes versions d’autres navigateurs. L’application doit renifler ces `SameSite`versions et omettre .

Pour discussion sur cette question, voir [dotnet/aspnetcore-14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Version introduite

3.1 Aperçu 1

#### <a name="old-behavior"></a>Ancien comportement

`SameSite`est un projet d’extension standard 2016 aux cookies HTTP. Il vise à atténuer la contrefaçon de demandes inter-sites (CSRF). Ceci a été conçu à l’origine comme une fonctionnalité que les serveurs opteraient en ajoutant les nouveaux paramètres. ASP.NET Core 2.0 a ajouté `SameSite`un soutien initial pour .

#### <a name="new-behavior"></a>Nouveau comportement

Google a proposé un nouveau projet de norme qui n’est pas compatible à l’envers. La norme modifie le `Lax` mode par `None` défaut et ajoute une nouvelle entrée pour se désinscrier. `Lax` suffit pour la plupart des cookies d’application ; cependant, il brise des scénarios inter-sites comme OpenID Connect et WS-Federation login. La plupart des connexions OAuth ne sont pas affectées en raison des différences dans la façon dont la demande circule. Le `None` nouveau paramètre cause des problèmes de compatibilité avec les clients qui ont mis en œuvre la norme de projet préalable (par exemple, iOS 12). Chrome 80 inclura les modifications. Voir [les mises à jour SameSite](https://www.chromium.org/updates/same-site) pour la chronologie de lancement du produit Chrome.

ASP.NET Core 3.1 a été mis à `SameSite` jour pour mettre en œuvre le nouveau comportement. La mise à jour `SameSiteMode.None` redéfinit le comportement de l’émission `SameSite=None` et ajoute une nouvelle valeur `SameSiteMode.Unspecified` pour omettre l’attribut. `SameSite` Toutes les API `Unspecified`cookie sont maintenant par défaut, bien que certains composants qui utilisent des cookies définis des valeurs plus spécifiques à leurs scénarios tels que la corrélation OpenID Connect et les cookies non-avantages.

Pour d’autres changements récents dans ce domaine, voir [HTTP: Certains cookies SameSite défauts changé à Aucun](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none). Dans ASP.NET Core 3.0, la plupart des <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> défauts ont été changés de (mais toujours en utilisant la norme antérieure).

#### <a name="reason-for-change"></a>Raison du changement

Navigateur et modifications de spécifications telles qu’indiquées dans le texte précédent.

#### <a name="recommended-action"></a>Action recommandée

Les applications qui interagissent avec des sites distants, par exemple par l’intermédiaire de connexion tierces, doivent :

* Testez ces scénarios sur plusieurs navigateurs.
* Appliquer la stratégie de cookie navigateur renifler l’atténuation discutée dans [Support navigateurs plus anciens](#support-older-browsers).

Pour les instructions de test et de reniflement du navigateur, voir la section suivante.

##### <a name="determine-if-youre-affected"></a>Déterminez si vous êtes affecté

Testez votre application web à l’aide d’une version client qui peut opter pour le nouveau comportement. Chrome, Firefox et Microsoft Edge Chromium ont tous de nouveaux drapeaux de fonctionnalité opt-in qui peuvent être utilisés pour les tests. Vérifiez que votre application est compatible avec les anciennes versions client après avoir appliqué les correctifs, en particulier Safari. Pour plus d’informations, voir [Support anciens navigateurs](#support-older-browsers).

##### <a name="chrome"></a>Chrome

Chrome 78 et plus tard donnent des résultats de test trompeurs. Ces versions ont une atténuation temporaire en place et permettent aux cookies de moins de deux minutes. Avec les indicateurs de test appropriés activés, Chrome 76 et 77 donnent des résultats plus précis. Pour tester le nouveau `chrome://flags/#same-site-by-default-cookies` comportement, basculer vers activé. Chrome 75 et plus tôt sont `None` signalés à l’échec avec le nouveau paramètre. Pour plus d’informations, voir [Support anciens navigateurs](#support-older-browsers).

Google ne rend pas les anciennes versions Chrome disponibles. Vous pouvez, cependant, télécharger des versions plus anciennes de Chrome, qui suffira pour les tests. Suivez les instructions à [Télécharger Chromium](https://www.chromium.org/getting-involved/download-chromium).

* [Chrome 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chrome 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12 a strictement mis en œuvre `None` le projet précédent et échoue s’il voit la nouvelle valeur dans les cookies. Cela doit être évité via le code de reniflement du navigateur indiqué dans [Support navigateurs anciens](#support-older-browsers). Assurez-vous de tester Safari 12 et 13 ainsi que des connexions de style OS basées sur WebKit à l’aide de Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL) ou quelle que soit la bibliothèque que vous utilisez. Le problème dépend de la version OS sous-jacente. OSX Mojave 10.14 et iOS 12 sont connus pour avoir des problèmes de compatibilité avec le nouveau comportement. La mise à niveau vers OSX Catalina 10.15 ou iOS 13 résout le problème. Safari n’a pas actuellement de drapeau d’opt-in pour tester le nouveau comportement de spécification.

##### <a name="firefox"></a>Firefox

Le support Firefox pour la nouvelle norme peut être testé sur `about:config` la version 68 et plus tard en optant sur la page avec le drapeau `network.cookie.sameSite.laxByDefault`de fonctionnalité . Aucun problème de compatibilité n’a été signalé sur les anciennes versions de Firefox.

##### <a name="microsoft-edge"></a>Microsoft Edge

Alors que Microsoft `SameSite` Edge prend en charge l’ancienne norme, à partir de la version 44, il n’a pas eu de problèmes de compatibilité avec la nouvelle norme.

##### <a name="microsoft-edge-chromium"></a>Chrome Microsoft Edge

Le drapeau `edge://flags/#same-site-by-default-cookies`caractéristique est . Aucun problème de compatibilité n’a été observé lors des tests avec Microsoft Edge Chromium 78.

##### <a name="electron"></a>Électron

Les versions d’Electron incluent des versions plus anciennes de Chrome. Par exemple, la version d’Electron utilisée par Microsoft Teams est le chrome 66, qui montre le comportement plus ancien. Effectuez vos propres tests de compatibilité avec la version d’Electron votre produit utilise. Pour plus d’informations, voir [Support anciens navigateurs](#support-older-browsers).

##### <a name="support-older-browsers"></a>Prendre en charge les anciens navigateurs

La norme de `SameSite` 2016 exigeait que `SameSite=Strict` les valeurs inconnues soient traitées comme des valeurs. Par conséquent, tous les navigateurs plus anciens qui `SameSite` prennent en charge `None`la norme d’origine peuvent se briser quand ils voient une propriété avec une valeur de . Les applications Web doivent implémenter le navigateur si elles ont l’intention de prendre en charge ces anciens navigateurs. ASP.NET Core ne met pas en œuvre `User-Agent` le reniflement du navigateur pour vous parce que les valeurs d’en-tête de demande sont très instables et changent sur une base hebdomadaire. Au lieu de cela, un point `User-Agent`d’extension dans la stratégie de cookie vous permet d’ajouter une logique spécifique.

Dans *Startup.cs*, ajouter le code suivant:

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

##### <a name="opt-out-switches"></a>Commutateurs d’opt-out

Le `Microsoft.AspNetCore.SuppressSameSiteNone` commutateur de compatibilité vous permet de vous retirer temporairement du nouveau comportement de cookie ASP.NET Core. Ajoutez le JSON suivant à un fichier *runtimeconfig.template.json* dans votre projet :

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>Autres versions

Des `SameSite` correctifs connexes sont à venir pour:

* ASP.NET Core 2.1, 2.2 et 3.0
* `Microsoft.Owin`4.1
* `System.Web`(pour .NET Framework 4.7.2 et plus tard)

#### <a name="category"></a>Category

ASP.NET

#### <a name="affected-apis"></a>API affectées

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
