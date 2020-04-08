---
ms.openlocfilehash: 645df8080abd21e4db95903a301a36b79a698858
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888113"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernisation du FolderBrowserDialog

Le <xref:System.Windows.Forms.FolderBrowserDialog> contrôle a changé dans les applications Windows Forms pour .NET Core.

#### <a name="change-description"></a>Description de la modification

Dans le cadre .NET, les formulaires <xref:System.Windows.Forms.FolderBrowserDialog> Windows utilisent le dialogue suivant pour le contrôle :

![The FolderBrowserDialogControl dans le cadre .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

Dans .NET Core 3.0, Windows Forme aux utilisateurs un nouveau contrôle basé sur com qui a été introduit dans Windows Vista:

![The FolderBrowserDialogControl in the .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Le dialogue sera mis à niveau automatiquement.

Si vous désirez conserver le dialogue <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> original, définissez la propriété avant `false` de montrer le dialogue, comme l’illustre le fragment de code suivant :

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

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
