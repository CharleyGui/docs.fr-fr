---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643962"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="82565-101">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="82565-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="82565-102">Le contrôle de <xref:System.Windows.Forms.FolderBrowserDialog> a changé dans les applications Windows Forms pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="82565-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="82565-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="82565-103">Change description</span></span>

<span data-ttu-id="82565-104">Dans le .NET Framework, Windows Forms utilise la boîte de dialogue suivante pour le contrôle <xref:System.Windows.Forms.FolderBrowserDialog> :</span><span class="sxs-lookup"><span data-stu-id="82565-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![FolderBrowserDialogControl dans le .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="82565-106">Dans .NET Core 3,0, Windows Forms utilisateurs un contrôle COM plus récent qui a été introduit dans Windows Vista :</span><span class="sxs-lookup"><span data-stu-id="82565-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![FolderBrowserDialogControl dans .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="82565-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="82565-108">Version introduced</span></span>

<span data-ttu-id="82565-109">3.0</span><span class="sxs-lookup"><span data-stu-id="82565-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="82565-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="82565-110">Recommended action</span></span>

<span data-ttu-id="82565-111">La boîte de dialogue sera automatiquement mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="82565-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="82565-112">Si vous souhaitez conserver la boîte de dialogue d’origine, affectez à la propriété <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> la valeur `false` avant d’avoir affiché la boîte de dialogue, comme le montre le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="82565-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="82565-113">Category</span><span class="sxs-lookup"><span data-stu-id="82565-113">Category</span></span>

<span data-ttu-id="82565-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82565-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82565-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="82565-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
