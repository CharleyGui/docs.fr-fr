---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394281"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Authentification : OAuthHandler ExchangeCodeAsync signature a changé

Dans ASP.NET Core 3,0, la signature de `OAuthHandler.ExchangeCodeAsync` a été remplacée par :

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

Par :

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les `code` chaînes `redirectUri` et ont été passées en tant qu’arguments distincts.

#### <a name="new-behavior"></a>Nouveau comportement

`Code`et `RedirectUri` sont des `OAuthCodeExchangeContext` propriétés qui peuvent être définies via le `OAuthCodeExchangeContext` constructeur. Le nouveau `OAuthCodeExchangeContext` type est le seul argument passé à `OAuthHandler.ExchangeCodeAsync`.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification permet de fournir des paramètres supplémentaires de manière sans rupture. Il n’est pas nécessaire de créer `ExchangeCodeAsync` de nouvelles surcharges.

#### <a name="recommended-action"></a>Action recommandée

Construisez `OAuthCodeExchangeContext` un avec les `code` valeurs `redirectUri` et appropriées. Une <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance doit être fournie. Cette instance `OAuthCodeExchangeContext` unique peut être passée au `OAuthHandler.ExchangeCodeAsync` au lieu de plusieurs arguments.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
