---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74100937"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorisation : AddAuthorization surcharge déplacée à différents assemblages

Les `AddAuthorization` méthodes de base `Microsoft.AspNetCore.Authorization` qui résidaient `AddAuthorizationCore`dans ont été rebaptisées à . Les `AddAuthorization` anciennes méthodes existent encore, `Microsoft.AspNetCore.Authorization.Policy` mais sont dans l’assemblage à la place. Les applications utilisant les deux méthodes ne devraient pas voir d’impact. Notez `Microsoft.AspNetCore.Authorization.Policy` que maintenant les navires dans le cadre partagé plutôt que d’un paquet autonome comme discuté dans [le cadre partagé: Assemblées supprimées de Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement
`AddAuthorization`méthodes existaient dans `Microsoft.AspNetCore.Authorization`.

#### <a name="new-behavior"></a>Nouveau comportement

`AddAuthorization`méthodes existent `Microsoft.AspNetCore.Authorization.Policy`dans . `AddAuthorizationCore`est le nouveau nom pour les anciennes méthodes.

#### <a name="reason-for-change"></a>Raison du changement

`AddAuthorization`est un meilleur nom de méthode pour ajouter tous les services communs nécessaires à l’autorisation.

#### <a name="recommended-action"></a>Action recommandée

Ajoutez une référence `Microsoft.AspNetCore.Authorization.Policy` ou `AddAuthorizationCore` utilisez plutôt.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
