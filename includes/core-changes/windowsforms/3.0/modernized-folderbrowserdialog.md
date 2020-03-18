---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643962"
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

- `System.Windows.Forms.FolderBrowserDialog`

-->
