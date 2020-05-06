---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394433"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Framework partagé : suppression de Microsoft. AspNetCore. All

À partir de ASP.NET Core 3,0, `Microsoft.AspNetCore.All` le reconditionnement et l' `Microsoft.AspNetCore.All` infrastructure partagée correspondante ne sont plus produits. Ce package est disponible dans ASP.NET Core 2,2 et continuera à recevoir des mises à jour de maintenance dans ASP.NET Core 2,1.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les applications peuvent utiliser `Microsoft.AspNetCore.All` le package pour cibler le `Microsoft.AspNetCore.All` Framework partagé sur .net core.

#### <a name="new-behavior"></a>Nouveau comportement

.NET Core 3,0 n’inclut pas `Microsoft.AspNetCore.All` de Framework partagé.

#### <a name="reason-for-change"></a>Motif de modification

Le `Microsoft.AspNetCore.All` reconditionnement incluait un grand nombre de dépendances externes.

#### <a name="recommended-action"></a>Action recommandée

Migrez votre projet pour utiliser `Microsoft.AspNetCore.App` le Framework. Les composants qui étaient précédemment disponibles `Microsoft.AspNetCore.All` dans sont toujours disponibles sur NuGet. Ces composants sont maintenant déployés avec votre application au lieu d’être inclus dans le Framework partagé.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
