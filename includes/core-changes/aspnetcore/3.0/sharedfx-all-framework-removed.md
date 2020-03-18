---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394433"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>Cadre partagé: Supprimé Microsoft.AspNetCore.All

À partir de ASP.NET Core 3.0, le `Microsoft.AspNetCore.All` métapackage et le cadre partagé correspondant `Microsoft.AspNetCore.All` ne sont plus produits. Ce forfait est disponible en ASP.NET Core 2.2 et continuera de recevoir des mises à jour d’entretien dans ASP.NET Core 2.1.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les applications `Microsoft.AspNetCore.All` pourraient utiliser le `Microsoft.AspNetCore.All` métapackage pour cibler le cadre partagé sur .NET Core.

#### <a name="new-behavior"></a>Nouveau comportement

.NET Core 3.0 n’inclut pas de `Microsoft.AspNetCore.All` cadre commun.

#### <a name="reason-for-change"></a>Raison du changement

Le `Microsoft.AspNetCore.All` métapackage comprenait un grand nombre de dépendances externes.

#### <a name="recommended-action"></a>Action recommandée

Migrez votre `Microsoft.AspNetCore.App` projet pour utiliser le cadre. Les composants qui étaient `Microsoft.AspNetCore.All` auparavant disponibles sont toujours disponibles sur NuGet. Ces composants sont maintenant déployés avec votre application au lieu d’être inclus dans le cadre partagé.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
