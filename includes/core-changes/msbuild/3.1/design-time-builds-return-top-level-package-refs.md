---
ms.openlocfilehash: 53840ddd59ae3463bae2930fd0151ab2cd2d65cb
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593321"
---
### <a name="design-time-builds-only-return-top-level-package-references"></a>Les builds au moment du design ne retournent que les références de package de niveau supérieur

À partir de kit SDK .NET Core 3.1.400, seules les références de package de niveau supérieur sont retournées par la `RunResolvePackageDependencies` cible.

#### <a name="version-introduced"></a>Version introduite

Kit SDK .NET Core 3.1.400

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes du kit SDK .NET Core, la `RunResolvePackageDependencies` cible créait les éléments MSBuild suivants qui contenaient des informations à partir du fichier de ressources NuGet :

- `PackageDefinitions`
- `PackageDependencies`
- `TargetDefinitions`
- `FileDefinitions`
- `FileDependencies`

Ces données sont utilisées par Visual Studio pour remplir le nœud dépendances dans Explorateur de solutions. Toutefois, il peut s’agir d’une grande quantité de données, et les données ne sont pas nécessaires, sauf si le nœud dépendances est développé.

À partir de la version kit SDK .NET Core 3.1.400, la plupart de ces éléments ne sont pas générés par défaut. Seuls les éléments de type `Package` sont retournés. Si Visual Studio a besoin que les éléments remplissent le nœud Dependencies, il lit les informations directement à partir du fichier de ressources.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification a été introduite pour améliorer les performances de chargement de la solution dans Visual Studio. Auparavant, toutes les références de package seraient chargées, ce qui impliquait le chargement de nombreuses références que la plupart des utilisateurs n’afficheraient jamais.

#### <a name="recommended-action"></a>Action recommandée

Si vous avez une logique MSBuild qui dépend de la création de ces éléments, affectez à la propriété la valeur `EmitLegacyAssetsFileItems` `true` dans votre fichier projet. Ce paramètre active le comportement précédent dans lequel tous les éléments sont créés.

#### <a name="category"></a>Category

MSBuild

#### <a name="affected-apis"></a>API affectées

N/A
