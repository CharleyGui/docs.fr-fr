---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74100937"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorisation : surcharge AddAuthorization déplacée vers un assembly différent

Les méthodes principales `AddAuthorization` qui se trouvent dans `Microsoft.AspNetCore.Authorization` ont été renommées en `AddAuthorizationCore`. Les anciennes méthodes `AddAuthorization` existent toujours, mais elles se trouvent dans l’assembly `Microsoft.AspNetCore.Authorization.Policy` à la place. Les applications qui utilisent les deux méthodes ne doivent pas avoir d’impact. Notez que `Microsoft.AspNetCore.Authorization.Policy` est désormais fourni dans le Framework partagé au lieu d’un package autonome, comme indiqué dans [Framework partagé : assemblys supprimés de Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement
les méthodes `AddAuthorization` existaient dans `Microsoft.AspNetCore.Authorization`.

#### <a name="new-behavior"></a>Nouveau comportement

les méthodes `AddAuthorization` existent dans `Microsoft.AspNetCore.Authorization.Policy`. `AddAuthorizationCore` est le nouveau nom des anciennes méthodes.

#### <a name="reason-for-change"></a>Motif de modification

`AddAuthorization` est un meilleur nom de méthode pour l’ajout de tous les services communs nécessaires à l’autorisation.

#### <a name="recommended-action"></a>Action recommandée

Ajoutez une référence à `Microsoft.AspNetCore.Authorization.Policy` ou utilisez `AddAuthorizationCore` à la place.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
