---
ms.openlocfilehash: 7b5ae84d02b83a10a4b9e002fc2ed4ee0833b84c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198428"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP : extensibilité de DefaultHttpContext supprimée

Dans le cadre de l’amélioration des performances de ASP.NET Core 3,0, l’extensibilité de `DefaultHttpContext` a été supprimée. La classe est maintenant `sealed`. Pour plus d’informations, consultez [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).

Si vos tests unitaires utilisent `Mock<DefaultHttpContext>`, utilisez à la place `Mock<HttpContext>`.

Pour plus d’informations, consultez [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Les classes peuvent dériver de `DefaultHttpContext`.

#### <a name="new-behavior"></a>Nouveau comportement

Les classes ne peuvent pas dériver de `DefaultHttpContext`.

#### <a name="reason-for-change"></a>Motif de modification

L’extensibilité a été fournie initialement pour permettre le regroupement des `HttpContext`, mais elle a introduit une complexité inutile et a entravé d’autres optimisations.

#### <a name="recommended-action"></a>Action recommandée

Si vous utilisez `Mock<DefaultHttpContext>` dans vos tests unitaires, commencez à utiliser `Mock<HttpContext>` à la place.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
