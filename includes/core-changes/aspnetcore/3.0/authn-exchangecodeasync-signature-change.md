---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394281"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Authentification : OAuthHandler ExchangeCodeAsync signature a changé

Dans ASP.NET Core 3,0, la signature de `OAuthHandler.ExchangeCodeAsync` a été remplacée par :

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

À :

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Les chaînes `code` et `redirectUri` ont été passées en tant qu’arguments distincts.

#### <a name="new-behavior"></a>Nouveau comportement

`Code` et `RedirectUri` sont des propriétés sur `OAuthCodeExchangeContext` qui peuvent être définies via le constructeur `OAuthCodeExchangeContext`. Le nouveau type `OAuthCodeExchangeContext` est le seul argument passé à `OAuthHandler.ExchangeCodeAsync`.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification permet de fournir des paramètres supplémentaires de manière sans rupture. Il n’est pas nécessaire de créer de nouvelles surcharges `ExchangeCodeAsync`.

#### <a name="recommended-action"></a>Action recommandée

Construisez un `OAuthCodeExchangeContext` avec les valeurs `code` et `redirectUri` appropriées. Une instance <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> doit être fournie. Cette seule instance `OAuthCodeExchangeContext` peut être passée à `OAuthHandler.ExchangeCodeAsync` au lieu de plusieurs arguments.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
