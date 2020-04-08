---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888114"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>API dupliquée supprimée des formulaires Windows

Un certain nombre d’API <xref:System.Windows.Forms?displayProperty=fullName> accidentellement dupliqué dans l’espace de nom à partir de .NET Core 3.0 Aperçu 4 ont été supprimés dans .NET Core 3.0 RC1.

#### <a name="change-description"></a>Description de la modification

.NET Core 3.0 Aperçu 4 par inadvertance <xref:System.Windows.Forms?displayProperty=fullName> dupliqué un certain <xref:System.ComponentModel.Design?displayProperty=fullName> nombre de types dans l’espace nom qui existait déjà dans l’espace nom. À partir de .NET Core 3.0 RC1, ces types dupliqués ne sont plus disponibles. Le tableau suivant affiche les listes du type d’origine et de son type dupliqué :

> [!div class="mx-tdCol2BreakAll"]
> |Type original|Type dupliqué|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>Version introduite

3.0 RC1

#### <a name="recommended-action"></a>Action recommandée

Mettre à jour le code pour référencer le type d’origine, tel qu’indiqué dans la colonne de **type Original** de la table.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucun.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
