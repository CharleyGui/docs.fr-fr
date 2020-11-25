---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032475"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorisation : surcharge AddAuthorization déplacée vers un assembly différent

Les `AddAuthorization` méthodes principales qui utilisaient pour résider dans `Microsoft.AspNetCore.Authorization` ont été renommées en `AddAuthorizationCore` . Les anciennes `AddAuthorization` méthodes existent toujours, mais elles se trouvent dans l' `Microsoft.AspNetCore.Authorization.Policy` assembly à la place. Les applications qui utilisent les deux méthodes ne doivent pas avoir d’impact. Notez que est `Microsoft.AspNetCore.Authorization.Policy` désormais fourni dans le Framework partagé au lieu d’un package autonome, comme indiqué dans [Framework partagé : assemblys supprimés de Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement
`AddAuthorization` les méthodes existaient dans `Microsoft.AspNetCore.Authorization` .

#### <a name="new-behavior"></a>Nouveau comportement

`AddAuthorization` les méthodes existent dans `Microsoft.AspNetCore.Authorization.Policy` . `AddAuthorizationCore` nouveau nom pour les anciennes méthodes.

#### <a name="reason-for-change"></a>Motif de modification

`AddAuthorization` est un meilleur nom de méthode pour l’ajout de tous les services communs nécessaires à l’autorisation.

#### <a name="recommended-action"></a>Action recommandée

Ajoutez une référence à `Microsoft.AspNetCore.Authorization.Policy` ou utilisez à la `AddAuthorizationCore` place.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
