---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721724"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Commutateur de compatibilité DoNotLoadLatestRichEditControl non pris en charge

Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Description de la modification

Dans le .NET Framework 4.6.2 et les versions antérieures, le <xref:System.Windows.Forms.RichTextBox> contrôle instancierait le contrôle Win32 RichEdit v 3.0 et, pour les applications qui ciblent .NET Framework 4.7.1, le <xref:System.Windows.Forms.RichTextBox> contrôle instancierait RichEdit v 4.1 (dans *que dans msftedit. dll*). Le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur de compatibilité a été introduit pour permettre aux applications qui ciblent .NET Framework 4.7.1 et versions ultérieures de refuser le nouveau contrôle RichEdit v 4.1 et d’utiliser à la place l’ancien contrôle RichEdit v3.

Dans .NET Core, le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur n’est pas pris en charge. Seules les nouvelles versions du <xref:System.Windows.Forms.RichTextBox> contrôle sont prises en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
