---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901914"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identité : le constructeur SignInManager accepte le nouveau paramètre

À compter de ASP.NET Core 3,0, un nouveau paramètre de `IUserConfirmation<TUser>` a été ajouté au constructeur `SignInManager`. Pour plus d’informations, consultez [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Motif de modification

La motivation de la modification consistait à ajouter la prise en charge de nouveaux flux de courrier électronique/confirmation dans l’identité.

#### <a name="recommended-action"></a>Action recommandée

Si vous créez manuellement un `SignInManager`, fournissez une implémentation de `IUserConfirmation` ou récupérez-en un à partir de l’injection de dépendances pour fournir.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
