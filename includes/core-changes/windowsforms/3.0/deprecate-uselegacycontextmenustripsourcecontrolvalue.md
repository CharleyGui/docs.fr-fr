---
ms.openlocfilehash: 3ada05a13ec7acde1d8374ed733d0d51cdfb408c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720911"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge

Le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.2, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Description de la modification

À partir de la .NET Framework 4.7.2, le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur de compatibilité permet au développeur de refuser le nouveau comportement de la <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriété, qui retourne à présent une référence au contrôle de code source. Le comportement précédent de la propriété consistait à retourner `null` . Pour plus d’informations, consultez [ \< AppContextSwitchOverrides>, élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

Dans .NET Core, le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
