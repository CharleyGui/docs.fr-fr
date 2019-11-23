---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394433"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Framework partagé : suppression de Microsoft. AspNetCore. All

À partir de ASP.NET Core 3,0, le sous-package `Microsoft.AspNetCore.All` et l’infrastructure partagée `Microsoft.AspNetCore.All` correspondante ne sont plus produits. Ce package est disponible dans ASP.NET Core 2,2 et continuera à recevoir des mises à jour de maintenance dans ASP.NET Core 2,1.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Les applications peuvent utiliser le sous-package `Microsoft.AspNetCore.All` pour cibler le `Microsoft.AspNetCore.All` Framework partagé sur .NET Core.

#### <a name="new-behavior"></a>Nouveau comportement

.NET Core 3,0 n’inclut pas de `Microsoft.AspNetCore.All` Framework partagé.

#### <a name="reason-for-change"></a>Motif de modification

Le sous-package `Microsoft.AspNetCore.All` incluait un grand nombre de dépendances externes.

#### <a name="recommended-action"></a>Action recommandée

Migrez votre projet pour utiliser l’infrastructure `Microsoft.AspNetCore.App`. Les composants qui étaient précédemment disponibles dans `Microsoft.AspNetCore.All` sont toujours disponibles sur NuGet. Ces composants sont maintenant déployés avec votre application au lieu d’être inclus dans le Framework partagé.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
