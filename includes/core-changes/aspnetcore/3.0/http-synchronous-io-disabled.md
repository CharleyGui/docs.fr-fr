---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901871"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: Synchronous IO désactivé dans tous les serveurs

En commençant par ASP.NET Core 3.0, les opérations de serveur synchrone sont désactivées par défaut.

#### <a name="change-description"></a>Description de la modification

`AllowSynchronousIO`est une option dans chaque serveur qui permet ou désactive synchrone IO API comme `HttpRequest.Body.Read`, `HttpResponse.Body.Write`et `Stream.Flush`. Ces API ont longtemps été une source de famine de fil et d’application se bloque. À partir de ASP.NET Core 3.0 Preview 3, ces opérations synchrones sont désactivées par défaut.

Serveurs concernés :

- Kestrel
- HttpSys (en)
- IIS en cours de traitement
- TestServer

Attendez-vous à des erreurs similaires à :

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Chaque serveur `AllowSynchronousIO` a une option qui contrôle ce comportement `false`et la valeur par défaut pour chacun d’eux est maintenant .

Le comportement peut également être remplacé sur une base par demande comme une atténuation temporaire. Par exemple :

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Si vous avez `TextWriter` des problèmes avec un ou un `Dispose`autre flux `DisposeAsync` appelant une API synchrone, appelez la nouvelle API à la place.

Pour discussion, voir [dotnet/aspnetcore 7644](https://github.com/dotnet/aspnetcore/issues/7644).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`HttpRequest.Body.Read`, `HttpResponse.Body.Write`et `Stream.Flush` ont été autorisés par défaut.

#### <a name="new-behavior"></a>Nouveau comportement

Ces API synchrones sont refusées par défaut :

Attendez-vous à des erreurs similaires à :

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Raison du changement

Ces API synchrones ont longtemps été une source de famine de fil et d’app hangs. À partir de ASP.NET Core 3.0 Preview 3, les opérations synchrones sont désactivées par défaut.

#### <a name="recommended-action"></a>Action recommandée

Utilisez les versions asynchrones des méthodes. Le comportement peut également être remplacé sur une base par demande comme une atténuation temporaire.

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
