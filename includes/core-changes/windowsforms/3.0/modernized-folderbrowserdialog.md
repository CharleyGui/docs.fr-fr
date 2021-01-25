---
ms.openlocfilehash: 27c6353f8f71254a505b434921f4b1e61e64cdda
ms.sourcegitcommit: 2b878d7011306b215dbf3d5dc9c1e78355a6dcd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98758162"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernisation du FolderBrowserDialog

Le <xref:System.Windows.Forms.FolderBrowserDialog> contrôle a été modifié dans Windows Forms applications pour .net core.

#### <a name="change-description"></a>Description de la modification

Dans le .NET Framework, Windows Forms utilise la boîte de dialogue suivante pour le <xref:System.Windows.Forms.FolderBrowserDialog> contrôle :

![FolderBrowserDialogControl dans le .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

Dans .NET Core 3,0, Windows Forms utilise un contrôle COM plus récent qui a été introduit dans Windows Vista :

![FolderBrowserDialogControl dans .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

La boîte de dialogue sera automatiquement mise à niveau.

Si vous souhaitez conserver la boîte de dialogue d’origine, affectez à la propriété la valeur <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> `false` avant d’illustrer la boîte de dialogue, comme illustré par le fragment de code suivant :

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>Catégorie

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
