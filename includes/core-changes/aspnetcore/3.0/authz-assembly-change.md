---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393978"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorisation : surcharge AddAuthorization déplacée vers un assembly différent

Les méthodes principales `AddAuthorization` qui se trouvent dans `Microsoft.AspNetCore.Authorization` ont été renommées en `AddAuthorizationCore`. Les anciennes méthodes `AddAuthorization` existent toujours, mais elles se trouvent dans le package `Microsoft.AspNetCore.Authorization.Policy` à la place. Les applications qui utilisent les deux méthodes ne doivent pas avoir d’impact. Les applications qui n’utilisent pas le package de stratégie doivent passer à l’utilisation de `AddAuthorizationCore`.

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
