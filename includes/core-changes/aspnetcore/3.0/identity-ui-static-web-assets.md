---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041657"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Identité : l’interface utilisateur utilise la fonctionnalité de ressources Web statiques

ASP.NET Core 3,0 a introduit une fonctionnalité de ressources Web statiques et l’interface utilisateur de l’identité l’a adoptée.

#### <a name="change-description"></a>Modifier la description

En raison de l’interface utilisateur d’identité adoptant la fonctionnalité de ressources Web statiques :

- La sélection de l’infrastructure s’effectue à l’aide de la propriété `IdentityUIFrameworkVersion` dans votre fichier projet.
- Bootstrap 4 est l’infrastructure d’interface utilisateur par défaut pour l’interface utilisateur d’identité. Le bootstrap 3 a atteint la fin de vie et vous devez envisager une migration vers une version prise en charge.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

L’infrastructure d’interface utilisateur par défaut pour l’interface utilisateur d’identité était **bootstrap 3**. L’infrastructure de l’interface utilisateur peut être configurée à l’aide d’un paramètre de l’appel de méthode `AddDefaultUI` dans `Startup.ConfigureServices`.

#### <a name="new-behavior"></a>Nouveau comportement

L’infrastructure d’interface utilisateur par défaut pour l’interface utilisateur d’identité est **bootstrap 4**. L’infrastructure de l’interface utilisateur doit être configurée dans votre fichier projet, plutôt que dans l’appel de la méthode `AddDefaultUI`.

#### <a name="reason-for-change"></a>Motif de modification

L’adoption de la fonctionnalité de ressources Web statiques nécessitait le déplacement de la configuration de l’infrastructure d’interface utilisateur vers MSBuild. La décision sur l’infrastructure à incorporer est une décision au moment de la génération, et non une décision d’exécution.

#### <a name="recommended-action"></a>Action recommandée

Passez en revue l’interface utilisateur de votre site pour vous assurer que les nouveaux composants bootstrap 4 sont compatibles. Si nécessaire, utilisez la propriété MSBuild `IdentityUIFrameworkVersion` pour revenir à bootstrap 3. Ajoutez la propriété à un élément `<PropertyGroup>` dans votre fichier projet :

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
