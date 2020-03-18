---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936995"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Police de contrôle par défaut changée en Segoe UI 9 pt

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, la <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> `Microsoft Sans Serif 8 pt`propriété a été fixée à . L’image suivante montre une fenêtre qui utilise la police par défaut.

![Police de contrôle par défaut dans .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

À partir de .NET Core 3.0, `Segoe UI 9 pt` la police <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>par défaut est définie (la même police que ). À la suite de ce changement, les formulaires et les contrôles sont classés environ 27 % plus grands pour tenir compte de la plus grande taille de la nouvelle police par défaut. Par exemple :

![Police de contrôle par défaut dans .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Cette modification a été apportée pour s’aligner sur les directives de [l’expérience utilisateur de Windows (UX).](/windows/win32/uxguide/vis-fonts#fonts-and-colors)

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

En raison de la modification de la taille des formulaires et des contrôles, assurez-vous que votre application se rend correctement.

Pour conserver la police d’origine, définissez la `Microsoft Sans Serif 8 pt`police par défaut de votre formulaire à . Par exemple :

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>Category

- Windows Forms

#### <a name="affected-apis"></a>API affectées

Aucun.

<!--

### Affected APIs

- Not detectable via API analysis

-->
