---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394087"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identité : le constructeur SignInManager accepte le nouveau paramètre

À compter de ASP.NET Core 3,0, un nouveau paramètre `IUserConfirmation<TUser>` a été ajouté au constructeur `SignInManager`. Pour plus d’informations, consultez [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="reason-for-change"></a>Motif de modification

La motivation de la modification consistait à ajouter la prise en charge de nouveaux flux de courrier électronique/confirmation dans l’identité.

#### <a name="recommended-action"></a>Action recommandée

Si vous construisez manuellement un `SignInManager`, fournissez une implémentation de `IUserConfirmation` ou récupérez-en une à partir de l’injection de dépendances à fournir.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
