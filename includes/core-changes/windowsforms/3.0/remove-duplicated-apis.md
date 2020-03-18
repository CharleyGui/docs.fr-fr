---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937007"
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

- Non détectable par l’analyse de l’API.

<!--

### Affected APIs

- Not detectable via API analysis.

-->
