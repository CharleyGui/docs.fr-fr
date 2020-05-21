---
ms.openlocfilehash: 3dfacadb5127319d4ce27f367803637cfb1ed00f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721427"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>API dupliquées supprimées de Windows Forms

Un certain nombre d’API dupliquées accidentellement dans l' <xref:System.Windows.Forms?displayProperty=fullName> espace de noms à compter de .net core 3,0 Preview 4 ont été supprimées dans .net core 3,0 RC1.

#### <a name="change-description"></a>Description de la modification

.NET Core 3,0 Preview 4 a, par inadvertance, dupliqué un certain nombre de types dans l' <xref:System.Windows.Forms?displayProperty=fullName> espace de noms qui existaient déjà dans l' <xref:System.ComponentModel.Design?displayProperty=fullName> espace de noms. À compter de .NET Core 3,0 RC1, ces types dupliqués ne sont plus disponibles. Le tableau suivant répertorie le type d’origine et son type dupliqué :

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

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucun.

<!--

#### Affected APIs

- Not detectable via API analysis.

-->
