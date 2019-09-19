---
ms.openlocfilehash: 02dbf5ccca97f5e7d2e1fada39bdf601cf37906f
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119358"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a>`Control.DefaultFont`remplacé par`Segoe UI 9pt` 

#### <a name="change-description"></a>Modifier la description

Dans le .NET Framework, la <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> propriété a la `Microsoft Sans Serif 8pt`valeur. L’illustration suivante montre une fenêtre qui utilise la police par défaut.

![police de contrôle par défaut dans .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

Dans .net core à compter de .net Core 3,0, il est défini `Segoe UI 9pt` sur (la même police <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>que). Suite à cette modification, les formulaires et les contrôles seront dimensionnés à une taille supérieure à 27% pour prendre en compte la plus grande taille de la nouvelle police par défaut. Par exemple :

![police de contrôle par défaut-dans .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Cette modification a été apportée pour s’aligner sur [les directives Windows UX](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

En raison de la modification de la taille des formulaires et des contrôles, assurez-vous que votre application s’affiche correctement.

Pour conserver la police d’origine, définissez la police par défaut de `Microsoft Sans Serif 8pt`votre formulaire sur. Par exemple :

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