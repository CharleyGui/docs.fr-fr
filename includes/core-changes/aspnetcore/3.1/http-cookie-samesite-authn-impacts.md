---
ms.openlocfilehash: 02602c70689a6d2729e03d3d7230cda5ae7a4994
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901933"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP : le navigateur SameSite les modifications d’impact sur l’authentification

Certains navigateurs, tels que Chrome et Firefox, ont apporté des modifications importantes à leurs implémentations de `SameSite` pour les cookies. Les modifications ont un impact sur les scénarios d’authentification à distance, tels que OpenID Connect et WS-Federation, qui doivent s’abonner en envoyant `SameSite=None`. Toutefois, `SameSite=None` s’arrête sur iOS 12 et certaines versions antérieures d’autres navigateurs. L’application doit détecter ces versions et omettre `SameSite`.

Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Version introduite

3,1 preview 1

#### <a name="old-behavior"></a>Ancien comportement

`SameSite` est une extension standard de 2016 draft aux cookies HTTP. Elle est destinée à atténuer les falsifications de requête intersites (CSRF). Il a été conçu à l’origine comme une fonctionnalité permettant aux serveurs d’accepter les nouveaux paramètres. ASP.NET Core 2,0 a ajouté la prise en charge initiale de `SameSite`.

#### <a name="new-behavior"></a>Nouveau comportement

Google a proposé un nouveau standard de norme qui n’est pas compatible avec les versions antérieures. La norme modifie le mode par défaut en `Lax` et ajoute une nouvelle entrée `None` à refuser. `Lax` suffit pour la plupart des cookies d’application ; Toutefois, il divise les scénarios inter-sites tels que OpenID Connect et WS-Federation login. La plupart des connexions OAuth ne sont pas affectées en raison de différences de flux de demande. Le nouveau paramètre `None` provoque des problèmes de compatibilité avec les clients qui ont implémenté la norme préliminaire précédente (par exemple, iOS 12). Chrome 80 inclut les modifications. Consultez [mises à jour SameSite](https://www.chromium.org/updates/same-site) pour la chronologie de lancement du produit chrome.

ASP.NET Core 3,1 a été mis à jour pour implémenter le nouveau comportement de `SameSite`. La mise à jour redéfinit le comportement de `SameSiteMode.None` pour émettre `SameSite=None` et ajoute une nouvelle valeur `SameSiteMode.Unspecified` pour omettre l’attribut `SameSite`. Par défaut, toutes les API de cookie sont `Unspecified`, bien que certains composants qui utilisent des cookies définissent des valeurs plus spécifiques à leurs scénarios, tels que la corrélation OpenID Connect et les cookies à usage unique.

Pour les autres modifications récentes de cette zone, consultez [http : certaines valeurs par défaut de SameSite de cookie ont été remplacées par aucune](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none). Dans ASP.NET Core 3,0, la plupart des valeurs par défaut ont été modifiées de <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> à <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (mais en utilisant toujours la norme précédente).

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

Chrome 78 et versions ultérieures produisent des résultats de test trompeurs. Ces versions ont une atténuation temporaire en place et autorisent les cookies datant de moins de deux minutes. Avec les indicateurs de test appropriés activés, chrome 76 et 77 produisent des résultats plus précis. Pour tester le nouveau comportement, basculez `chrome://flags/#same-site-by-default-cookies` sur activé. Le chrome 75 et les versions antérieures sont signalés comme ayant échoué avec le nouveau paramètre de `None`. Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).

Google ne rend pas les versions de chrome plus anciennes disponibles. Toutefois, vous pouvez télécharger des versions antérieures de chrome, ce qui est suffisant pour les tests. Suivez les instructions fournies dans [Télécharger chrome](https://www.chromium.org/getting-involved/download-chromium).

* [Chrome 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chrome 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12 a implémenté strictement le brouillon précédent et échoue s’il voit la nouvelle valeur `None` dans les cookies. Cela doit être évité par le biais du code de détection du navigateur présenté dans la [prise en charge des navigateurs plus anciens](#support-older-browsers). Veillez à tester Safari 12 et 13 ainsi que les connexions basées sur le type de système d’exploitation WebKit à l’aide de la bibliothèque d’authentification Microsoft (MSAL), de Bibliothèque d’authentification Active Directory (ADAL) ou de la bibliothèque que vous utilisez. Le problème dépend de la version du système d’exploitation sous-jacent. OSX Mojave 10,14 et iOS 12 sont connus pour présenter des problèmes de compatibilité avec le nouveau comportement. La mise à niveau vers OSX Catalina 10,15 ou iOS 13 résout le problème. Safari ne dispose pas actuellement d’un indicateur d’abonnement pour tester le nouveau comportement de la spécification.

##### <a name="firefox"></a>Firefox

La prise en charge de Firefox pour la nouvelle version standard peut être testée sur la version 68 et les versions ultérieures en choisissant dans la page `about:config` avec l’indicateur de fonctionnalité `network.cookie.sameSite.laxByDefault`. Aucun problème de compatibilité n’a été signalé sur les versions antérieures de Firefox.

##### <a name="microsoft-edge"></a>Microsoft Edge

Bien que Microsoft Edge prenne en charge l’ancien `SameSite` standard, à partir de la version 44, il n’avait aucun problème de compatibilité avec la nouvelle norme.

##### <a name="microsoft-edge-chromium"></a>Chrome Microsoft Edge

L’indicateur de fonctionnalité est `edge://flags/#same-site-by-default-cookies`. Aucun problème de compatibilité n’a été observé lors du test avec Microsoft Edge chrome 78.

##### <a name="electron"></a>Dispositif

Les versions d’électrons incluent des versions plus anciennes de chrome. Par exemple, la version de l’électron utilisée par Microsoft teams est le chrome 66, qui présente l’ancien comportement. Effectuez vos propres tests de compatibilité avec la version d’électrons utilisée par votre produit. Pour plus d’informations, consultez [prise en charge des navigateurs plus anciens](#support-older-browsers).

##### <a name="support-older-browsers"></a>Prendre en charge les navigateurs plus anciens

La norme 2016 `SameSite` impose que les valeurs inconnues soient traitées comme des valeurs `SameSite=Strict`. Par conséquent, tous les anciens navigateurs prenant en charge la norme d’origine peuvent s’arrêter lorsqu’ils voient une propriété `SameSite` avec la valeur `None`. Les applications Web doivent implémenter la détection de navigateur si elles envisagent de prendre en charge ces anciens navigateurs. ASP.NET Core n’implémente pas la détection de navigateur pour vous, car `User-Agent` valeurs d’en-tête de demande sont très instables et changent sur une base hebdomadaire. Au lieu de cela, un point d’extension dans la stratégie de cookie vous permet d’ajouter `User-Agent`logique spécifique.

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

Le commutateur de compatibilité `Microsoft.AspNetCore.SuppressSameSiteNone` vous permet de refuser temporairement le nouveau comportement de cookie ASP.NET Core. Ajoutez le code JSON suivant à un fichier *runtimeconfig. template. JSON* dans votre projet :

```json
{ 
  "configProperties": { 
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true" 
  } 
}
```

##### <a name="other-versions"></a>Autres versions

Les correctifs `SameSite` associés sont à venir pour :

* ASP.NET Core 2,1, 2,2 et 3,0
* `Microsoft.Owin` 4,1
* `System.Web` (pour .NET Framework 4.7.2 et versions ultérieures)

#### <a name="category"></a>Catégorie

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
