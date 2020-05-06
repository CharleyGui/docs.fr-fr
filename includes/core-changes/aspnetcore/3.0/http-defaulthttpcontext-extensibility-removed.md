---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290754"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP : extensibilité de DefaultHttpContext supprimée

Dans le cadre de l’amélioration des performances de ASP.NET Core 3,0 `DefaultHttpContext` , l’extensibilité de a été supprimée. La classe est maintenant `sealed`. Pour plus d’informations, consultez [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).

Si vos tests unitaires `Mock<DefaultHttpContext>`utilisent, `Mock<HttpContext>` utilisez `new DefaultHttpContext()` ou à la place.

Pour plus d’informations, consultez [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les classes peuvent dériver de `DefaultHttpContext`.

#### <a name="new-behavior"></a>Nouveau comportement

Les classes ne peuvent `DefaultHttpContext`pas dériver de.

#### <a name="reason-for-change"></a>Motif de modification

L’extensibilité a été fournie initialement pour permettre le `HttpContext`regroupement du, mais elle a introduit une complexité inutile et empêchait d’autres optimisations.

#### <a name="recommended-action"></a>Action recommandée

Si vous utilisez `Mock<DefaultHttpContext>` dans vos tests unitaires, commencez à `Mock<HttpContext>` utiliser à la place.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
