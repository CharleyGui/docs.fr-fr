---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643948"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a>`Control.DefaultFont` changé en `Segoe UI 9pt`

#### <a name="change-description"></a>Modifier la description

Dans le .NET Framework, la propriété <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> a été définie sur `Microsoft Sans Serif 8pt`. L’illustration suivante montre une fenêtre qui utilise la police par défaut.

![police de contrôle par défaut dans .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

Dans .NET Core à compter de .NET Core 3,0, il est défini sur `Segoe UI 9pt` (la même police que <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>). Suite à cette modification, les formulaires et les contrôles seront dimensionnés à une taille supérieure à 27% pour prendre en compte la plus grande taille de la nouvelle police par défaut. Par exemple :

![police de contrôle par défaut-dans .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Cette modification a été apportée pour s’aligner sur [les directives Windows UX](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

En raison de la modification de la taille des formulaires et des contrôles, assurez-vous que votre application s’affiche correctement.

Pour conserver la police d’origine, définissez la police par défaut de votre formulaire sur `Microsoft Sans Serif 8pt`. Par exemple :

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
