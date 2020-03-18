---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290754"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: DefaultHttpContext extétabilité supprimée

Dans le cadre de ASP.NET’amélioration des performances de Core 3.0, l’extéabilité de `DefaultHttpContext` a été supprimée. La classe `sealed`est maintenant . Pour plus d’informations, voir [dotnet/aspnetcore 6504](https://github.com/dotnet/aspnetcore/pull/6504).

Si vos tests `Mock<DefaultHttpContext>`unitaires utilisent, utilisez `Mock<HttpContext>` ou `new DefaultHttpContext()` à la place.

Pour discussion, voir [dotnet/aspnetcore 6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les classes `DefaultHttpContext`peuvent dériver de .

#### <a name="new-behavior"></a>Nouveau comportement

Les cours ne `DefaultHttpContext`peuvent pas dériver de .

#### <a name="reason-for-change"></a>Raison du changement

L’extéabilité a été initialement fournie `HttpContext`pour permettre la mise en commun de la , mais il a introduit une complexité inutile et entravé d’autres optimisations.

#### <a name="recommended-action"></a>Action recommandée

Si vous utilisez `Mock<DefaultHttpContext>` dans vos tests `Mock<HttpContext>` unitaires, commencez à utiliser à la place.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
