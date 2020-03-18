---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901914"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identité: SignInManager constructeur accepte un nouveau paramètre

En commençant par ASP.NET Core 3.0, un `IUserConfirmation<TUser>` nouveau `SignInManager` paramètre a été ajouté au constructeur. Pour plus d’informations, voir [dotnet/aspnetcore 8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Raison du changement

La motivation pour le changement était d’ajouter un soutien pour les nouveaux flux de messagerie / confirmation dans l’identité.

#### <a name="recommended-action"></a>Action recommandée

Si la construction `SignInManager`manuelle d’un, fournir une mise en œuvre ou `IUserConfirmation` saisir un de l’injection de dépendance à fournir.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
