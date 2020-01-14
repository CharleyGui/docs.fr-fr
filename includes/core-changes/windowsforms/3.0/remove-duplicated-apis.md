---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937007"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>API dupliquées supprimées de Windows Forms

Un certain nombre d’API dupliquées accidentellement dans l’espace de noms <xref:System.Windows.Forms?displayProperty=fullName> à partir de .NET Core 3,0 Preview 4 ont été supprimées dans .NET Core 3,0 RC1.

#### <a name="change-description"></a>Description des modifications

.NET Core 3,0 Preview 4 a, par inadvertance, dupliqué un certain nombre de types dans l’espace de noms <xref:System.Windows.Forms?displayProperty=fullName> qui existaient déjà dans l’espace de noms <xref:System.ComponentModel.Design?displayProperty=fullName>. À compter de .NET Core 3,0 RC1, ces types dupliqués ne sont plus disponibles. Le tableau suivant répertorie le type d’origine et son type dupliqué :

> [!div class="mx-tdCol2BreakAll"]
> |Type d’origine|Type dupliqué|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Version introduite

3,0 RC1

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour le code pour référencer le type d’origine, comme indiqué dans la colonne **type d’origine** de la table.

#### <a name="category"></a>Catégorie

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Non détectable via l’analyse des API.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
