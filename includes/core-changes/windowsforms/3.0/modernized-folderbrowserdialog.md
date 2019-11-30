---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643962"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernisation du FolderBrowserDialog

Le contrôle de <xref:System.Windows.Forms.FolderBrowserDialog> a changé dans les applications Windows Forms pour .NET Core.

#### <a name="change-description"></a>Modifier la description

Dans le .NET Framework, Windows Forms utilise la boîte de dialogue suivante pour le contrôle <xref:System.Windows.Forms.FolderBrowserDialog> :

![FolderBrowserDialogControl dans le .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

Dans .NET Core 3,0, Windows Forms utilisateurs un contrôle COM plus récent qui a été introduit dans Windows Vista :

![FolderBrowserDialogControl dans .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

La boîte de dialogue sera automatiquement mise à niveau.

Si vous souhaitez conserver la boîte de dialogue d’origine, affectez à la propriété <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> la valeur `false` avant d’avoir affiché la boîte de dialogue, comme le montre le fragment de code suivant :

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
