---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937030"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>DoNotLoadLatestRichEditControl commutateur de compatibilité non pris en charge

Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans windows Forms sur .NET Core 3.0.

#### <a name="change-description"></a>Description de la modification

Dans le cadre .NET 4.6.2 et <xref:System.Windows.Forms.RichTextBox> les versions précédentes, le contrôle instantanémentait le contrôle Win32 RichEdit v3.0, et <xref:System.Windows.Forms.RichTextBox> pour les applications qui ciblent .NET Framework 4.7.1, le contrôle serait instantanée RichEdit v4.1 (en *msftedit.dll*). Le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur de compatibilité a été introduit pour permettre aux applications qui ciblent .NET Framework 4.7.1 et les versions ultérieures de se retirer du nouveau contrôle RichEdit v4.1 et d’utiliser l’ancien contrôle RichEdit v3 à la place.

Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` pas pris en charge. Seules les nouvelles <xref:System.Windows.Forms.RichTextBox> versions du contrôle sont prises en charge.

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 9

#### <a name="recommended-action"></a>Action recommandée

Retirez l’interrupteur. Le commutateur n’est pas pris en charge, et aucune fonctionnalité alternative n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
