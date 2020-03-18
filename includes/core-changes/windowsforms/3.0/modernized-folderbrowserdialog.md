---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643962"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="60d8f-101">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="60d8f-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="60d8f-102">Le <xref:System.Windows.Forms.FolderBrowserDialog> contrôle a changé dans les applications Windows Forms pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="60d8f-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="60d8f-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="60d8f-103">Change description</span></span>

<span data-ttu-id="60d8f-104">Dans le cadre .NET, les formulaires <xref:System.Windows.Forms.FolderBrowserDialog> Windows utilisent le dialogue suivant pour le contrôle :</span><span class="sxs-lookup"><span data-stu-id="60d8f-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![The FolderBrowserDialogControl dans le cadre .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="60d8f-106">Dans .NET Core 3.0, Windows Forme aux utilisateurs un nouveau contrôle basé sur com qui a été introduit dans Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="60d8f-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![The FolderBrowserDialogControl in the .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="60d8f-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="60d8f-108">Version introduced</span></span>

<span data-ttu-id="60d8f-109">3.0</span><span class="sxs-lookup"><span data-stu-id="60d8f-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="60d8f-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="60d8f-110">Recommended action</span></span>

<span data-ttu-id="60d8f-111">Le dialogue sera mis à niveau automatiquement.</span><span class="sxs-lookup"><span data-stu-id="60d8f-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="60d8f-112">Si vous désirez conserver le dialogue <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> original, définissez la propriété avant `false` de montrer le dialogue, comme l’illustre le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="60d8f-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="60d8f-113">Category</span><span class="sxs-lookup"><span data-stu-id="60d8f-113">Category</span></span>

<span data-ttu-id="60d8f-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60d8f-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="60d8f-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="60d8f-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
