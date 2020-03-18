---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394281"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Authentification : La signature OAuthHandler ExchangeCodeAsync modifiée

Dans ASP.NET Core 3.0, la `OAuthHandler.ExchangeCodeAsync` signature de a été changée de:

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

Les `code` `redirectUri` et les ficelles ont été adoptées comme des arguments distincts.

#### <a name="new-behavior"></a>Nouveau comportement

`Code`et `RedirectUri` sont `OAuthCodeExchangeContext` des propriétés sur `OAuthCodeExchangeContext` qui peuvent être définis via le constructeur. Le `OAuthCodeExchangeContext` nouveau type est le `OAuthHandler.ExchangeCodeAsync`seul argument passé à .

#### <a name="reason-for-change"></a>Raison du changement

Cette modification permet de fournir des paramètres supplémentaires d’une manière non-rupture. Il n’est pas `ExchangeCodeAsync` nécessaire de créer de nouvelles surcharges.

#### <a name="recommended-action"></a>Action recommandée

Construire `OAuthCodeExchangeContext` un avec `code` `redirectUri` le approprié et les valeurs. Une <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance doit être fournie. Cette `OAuthCodeExchangeContext` seule instance peut `OAuthHandler.ExchangeCodeAsync` être adoptée au lieu de multiples arguments.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
