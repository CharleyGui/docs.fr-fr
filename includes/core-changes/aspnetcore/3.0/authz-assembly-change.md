---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74100937"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorisation : surcharge AddAuthorization déplacée vers un assembly différent

Les méthodes `AddAuthorization` principales qui utilisaient pour résider `Microsoft.AspNetCore.Authorization` dans ont été renommées en `AddAuthorizationCore`. Les anciennes `AddAuthorization` méthodes existent toujours, mais elles se trouvent `Microsoft.AspNetCore.Authorization.Policy` dans l’assembly à la place. Les applications qui utilisent les deux méthodes ne doivent pas avoir d’impact. Notez que `Microsoft.AspNetCore.Authorization.Policy` est désormais fourni dans le Framework partagé au lieu d’un package autonome, comme indiqué dans [Framework partagé : assemblys supprimés de Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement
`AddAuthorization`les méthodes existaient `Microsoft.AspNetCore.Authorization`dans.

#### <a name="new-behavior"></a>Nouveau comportement

`AddAuthorization`les méthodes existent `Microsoft.AspNetCore.Authorization.Policy`dans. `AddAuthorizationCore`nouveau nom pour les anciennes méthodes.

#### <a name="reason-for-change"></a>Motif de modification

`AddAuthorization`est un meilleur nom de méthode pour l’ajout de tous les services communs nécessaires à l’autorisation.

#### <a name="recommended-action"></a>Action recommandée

Ajoutez une référence à ou `Microsoft.AspNetCore.Authorization.Policy` utilisez `AddAuthorizationCore` à la place.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
