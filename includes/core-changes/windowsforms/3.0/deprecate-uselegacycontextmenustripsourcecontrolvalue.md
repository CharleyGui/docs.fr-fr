---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937043"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>UtiliserLegacyContextMenuStripSourceControlValue commutateur de compatibilité non pris en charge

Le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.2, n’est pas pris en charge dans windows Forms sur .NET Core 3.0.

#### <a name="change-description"></a>Description de la modification

En commençant par le cadre .NET 4.7.2, le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur de compatibilité <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> permet au développeur de se retirer du nouveau comportement de la propriété, qui renvoie maintenant une référence au contrôle source. Le comportement précédent de la `null`propriété était de revenir . Pour plus d’informations, voir [ \<AppContextSwitchOverrides> élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 9

#### <a name="recommended-action"></a>Action recommandée

Retirez l’interrupteur. Le commutateur n’est pas pris en charge, et aucune fonctionnalité alternative n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
