---
ms.openlocfilehash: 474f039cf00cb48761bfe7b7c4a0a9c6300cd820
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637195"
---
### <a name="identity-adddefaultui-method-overload-removed"></a>Identité : Surcharge de la méthode AddDefaultUI supprimée

À partir de ASP.NET Core 3.0, la surcharge de la méthode [IdentityBuilderUIExtensions.AddDefaultUI (IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) n’existe plus.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Raison du changement

Ce changement est le résultat de l’adoption de la fonction d’actifs Web statiques.

#### <a name="recommended-action"></a>Action recommandée

Appelez <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> au lieu de la surcharge qui prend deux arguments. Si vous utilisez Bootstrap 3, ajoutez également `<PropertyGroup>` la ligne suivante à un élément de votre fichier de projet :

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

[IdentityBuilderUIExtensions.AddDefaultUI (IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
