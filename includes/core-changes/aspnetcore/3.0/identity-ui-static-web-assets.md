---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041657"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Identité : L’interface utilisateur utilise la fonction d’actifs Web statiques

ASP.NET Core 3.0 a introduit une fonction d’actifs Web statiques, et Identity UI l’a adoptée.

#### <a name="change-description"></a>Description de la modification

À la suite de l’interface utilisateur Identity adoptant la fonction d’actifs Web statiques :

- La sélection des cadres `IdentityUIFrameworkVersion` est effectuée en utilisant la propriété dans votre dossier de projet.
- Bootstrap 4 est le cadre d’interface utilisateur par défaut pour l’interface utilisateur d’identité. Bootstrap 3 a atteint la fin de la vie, et vous devriez envisager de migrer vers une version prise en charge.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le cadre d’interface utilisateur par défaut pour l’interface utilisateur d’identité était **Bootstrap 3**. Le cadre d’interface utilisateur pourrait être `AddDefaultUI` configuré à l’aide d’un paramètre à la méthode appelez `Startup.ConfigureServices`.

#### <a name="new-behavior"></a>Nouveau comportement

Le cadre d’interface utilisateur par défaut pour l’interface utilisateur d’identité est **Bootstrap 4**. Le cadre d’interface utilisateur doit être configuré `AddDefaultUI` dans votre fichier de projet, au lieu de l’appel de méthode.

#### <a name="reason-for-change"></a>Raison du changement

L’adoption de la fonction d’actifs Web statiques exigeait que la configuration du cadre d’interface utilisateur passe à MSBuild. La décision sur le cadre à intégrer est une décision de prise de fonction, et non une décision en temps d’exécution.

#### <a name="recommended-action"></a>Action recommandée

Examinez votre interface utilisateur de site pour vous assurer que les nouveaux composants Bootstrap 4 sont compatibles. Si nécessaire, `IdentityUIFrameworkVersion` utilisez la propriété MSBuild pour revenir à Bootstrap 3. Ajoutez la propriété `<PropertyGroup>` à un élément de votre dossier de projet :

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
