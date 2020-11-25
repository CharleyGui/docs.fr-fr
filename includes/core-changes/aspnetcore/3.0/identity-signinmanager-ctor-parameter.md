---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032564"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identité : le constructeur SignInManager accepte le nouveau paramètre

À compter de ASP.NET Core 3,0, un nouveau `IUserConfirmation<TUser>` paramètre a été ajouté au `SignInManager` constructeur. Pour plus d’informations, consultez [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Motif de modification

La motivation de la modification consistait à ajouter la prise en charge de nouveaux flux de courrier électronique/confirmation dans l’identité.

#### <a name="recommended-action"></a>Action recommandée

Si vous construisez manuellement un `SignInManager` , fournissez une implémentation de `IUserConfirmation` ou récupérez-en un à partir de l’injection de dépendances pour fournir.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
