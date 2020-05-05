---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78967934"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP : le navigateur SameSite les modifications d’impact sur l’authentification

Certains navigateurs, tels que Chrome et Firefox, ont apporté des modifications importantes à leurs implémentations de `SameSite` pour les cookies. Les modifications ont un impact sur les scénarios d’authentification à distance, tels que OpenID Connect et WS-Federation, `SameSite=None`qui doivent refuser par l’envoi. Toutefois, `SameSite=None` s’arrête sur IOS 12 et certaines versions antérieures d’autres navigateurs. L’application doit détecter ces versions et omettre `SameSite`.

Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Version introduite

3,1 preview 1

#### <a name="old-behavior"></a>Ancien comportement

`SameSite`est une extension standard de 2016 pour les cookies HTTP. Elle est destinée à atténuer les falsifications de requête intersites (CSRF). Il a été conçu à l’origine comme une fonctionnalité permettant aux serveurs d’accepter les nouveaux paramètres. ASP.NET Core 2,0 a ajouté la prise `SameSite`en charge initiale de.

#### <a name="new-behavior"></a>Nouveau comportement

Google a proposé un nouveau standard de norme qui n’est pas compatible avec les versions antérieures. La norme modifie le mode par défaut `Lax` en et ajoute une nouvelle `None` entrée pour annuler l’abonnement. `Lax` suffit pour la plupart des cookies d’application ; Toutefois, il divise les scénarios inter-sites tels que OpenID Connect et WS-Federation login. La plupart des connexions OAuth ne sont pas affectées en raison de différences de flux de demande. Le nouveau `None` paramètre provoque des problèmes de compatibilité avec les clients qui ont implémenté la norme préliminaire précédente (par exemple, IOS 12). Chrome 80 inclut les modifications. Consultez [mises à jour SameSite](https://www.chromium.org/updates/same-site) pour la chronologie de lancement du produit chrome.

ASP.NET Core 3,1 a été mis à jour pour implémenter le nouveau `SameSite` comportement. La mise à jour redéfinit le `SameSiteMode.None` comportement de `SameSite=None` pour émettre et ajoute une `SameSiteMode.Unspecified` nouvelle valeur pour `SameSite` omettre l’attribut. Toutes les API de `Unspecified`cookie sont désormais par défaut, bien que certains composants qui utilisent des cookies définissent des valeurs plus spécifiques à leurs scénarios, tels que la corrélation OpenID Connect et les cookies à usage unique.

Pour les autres modifications récentes de cette zone, consultez [http : certaines valeurs par défaut de SameSite de cookie ont été remplacées par aucune](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none). Dans ASP.NET Core 3,0, la plupart des valeurs par défaut <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> ont <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> été remplacées par (mais en utilisant toujours la norme précédente).

#### <a name="reason-for-change"></a>Motif de modification

Modifications des navigateurs et des spécifications comme indiqué dans le texte précédent.

#### <a name="recommended-action"></a>Action recommandée

Les applications qui interagissent avec des sites distants, par exemple par le biais d’une connexion tierce, doivent :

* Testez ces scénarios sur plusieurs navigateurs.
* Appliquez l’atténuation de la détection de l’Explorateur de stratégies de cookies décrite dans [prendre en charge les navigateurs plus anciens](#support-older-browsers).

Pour obtenir des instructions sur le test et la détection de navigateur, consultez la section suivante.

##### <a name="determine-if-youre-affected"></a>Déterminer si vous êtes concerné

Testez votre application Web à l’aide d’une version du client qui peut s’abonner au nouveau comportement. Chrome, Firefox et Microsoft Edge chrome ont tous des indicateurs de fonctionnalités d’abonnement qui peuvent être utilisés à des fins de test. Vérifiez que votre application est compatible avec les versions antérieures du client une fois que vous avez appliqué les correctifs, en particulier Safari. Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).

##### <a name="chrome"></a>Chrome

Chrome 78 et versions ultérieures produisent des résultats de test trompeurs. Ces versions ont une atténuation temporaire en place et autorisent les cookies datant de moins de deux minutes. Avec les indicateurs de test appropriés activés, chrome 76 et 77 produisent des résultats plus précis. Pour tester le nouveau comportement, basculez `chrome://flags/#same-site-by-default-cookies` vers activé. Le chrome 75 et les versions antérieures sont signalés comme `None` ayant échoué avec le nouveau paramètre. Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).

Google ne rend pas les versions de chrome plus anciennes disponibles. Toutefois, vous pouvez télécharger des versions antérieures de chrome, ce qui est suffisant pour les tests. Suivez les instructions fournies dans [Télécharger chrome](https://www.chromium.org/getting-involved/download-chromium).

* [Chrome 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chrome 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12 implémentait strictement le brouillon précédent et échouera s’il voit `None` la nouvelle valeur dans les cookies. Cela doit être évité par le biais du code de détection du navigateur présenté dans la [prise en charge des navigateurs plus anciens](#support-older-browsers). Veillez à tester Safari 12 et 13 ainsi que les connexions basées sur le type de système d’exploitation WebKit à l’aide de la bibliothèque d’authentification Microsoft (MSAL), de Bibliothèque d’authentification Active Directory (ADAL) ou de la bibliothèque que vous utilisez. Le problème dépend de la version du système d’exploitation sous-jacent. OSX Mojave 10,14 et iOS 12 sont connus pour présenter des problèmes de compatibilité avec le nouveau comportement. La mise à niveau vers OSX Catalina 10,15 ou iOS 13 résout le problème. Safari ne dispose pas actuellement d’un indicateur d’abonnement pour tester le nouveau comportement de la spécification.

##### <a name="firefox"></a>Firefox

La prise en charge de Firefox pour la nouvelle norme peut être testée sur la version 68 et `about:config` versions ultérieures en acceptant sur la page avec l’indicateur `network.cookie.sameSite.laxByDefault`de fonctionnalité. Aucun problème de compatibilité n’a été signalé sur les versions antérieures de Firefox.

##### <a name="microsoft-edge"></a>Microsoft Edge

Bien que Microsoft Edge prenne `SameSite` en charge l’ancien standard, à compter de la version 44, il n’avait aucun problème de compatibilité avec la nouvelle norme.

##### <a name="microsoft-edge-chromium"></a>Chrome Microsoft Edge

L’indicateur de fonctionnalité `edge://flags/#same-site-by-default-cookies`est. Aucun problème de compatibilité n’a été observé lors du test avec Microsoft Edge chrome 78.

##### <a name="electron"></a>Dispositif

Les versions d’électrons incluent des versions plus anciennes de chrome. Par exemple, la version de l’électron utilisée par Microsoft teams est le chrome 66, qui présente l’ancien comportement. Effectuez vos propres tests de compatibilité avec la version d’électrons utilisée par votre produit. Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).

##### <a name="support-older-browsers"></a>Prendre en charge les navigateurs plus anciens

La norme `SameSite` 2016 impose que les valeurs inconnues soient `SameSite=Strict` traitées en tant que valeurs. Par conséquent, tous les anciens navigateurs prenant en charge la norme d’origine peuvent s' `SameSite` arrêter lorsqu’ils voient une `None`propriété avec la valeur. Les applications Web doivent implémenter la détection de navigateur si elles envisagent de prendre en charge ces anciens navigateurs. ASP.NET Core n’implémente pas la détection de navigateur `User-Agent` pour vous, car les valeurs d’en-tête de demande sont très instables et changent sur une base hebdomadaire. Au lieu de cela, un point d’extension dans la stratégie de `User-Agent`cookie vous permet d’ajouter une logique spécifique.

Dans *Startup.cs*, ajoutez le code suivant :

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

##### <a name="opt-out-switches"></a>Commutateurs de refus

Le `Microsoft.AspNetCore.SuppressSameSiteNone` commutateur de compatibilité vous permet de refuser temporairement le nouveau comportement de cookie ASP.net core. Ajoutez le code JSON suivant à un fichier *runtimeconfig. template. JSON* dans votre projet :

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>Autres versions

Les `SameSite` correctifs associés sont à venir pour :

* ASP.NET Core 2,1, 2,2 et 3,0
* `Microsoft.Owin`4,1
* `System.Web`(pour .NET Framework 4.7.2 et versions ultérieures)

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
