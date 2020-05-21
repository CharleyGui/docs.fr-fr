---
ms.openlocfilehash: 11c04441dcec260f0bfb90f6ed2b919b1545b382
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720933"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="27e76-101">Modernisation du FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="27e76-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="27e76-102">Le <xref:System.Windows.Forms.FolderBrowserDialog> contrôle a été modifié dans Windows Forms applications pour .net core.</span><span class="sxs-lookup"><span data-stu-id="27e76-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="27e76-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="27e76-103">Change description</span></span>

<span data-ttu-id="27e76-104">Dans le .NET Framework, Windows Forms utilise la boîte de dialogue suivante pour le <xref:System.Windows.Forms.FolderBrowserDialog> contrôle :</span><span class="sxs-lookup"><span data-stu-id="27e76-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![FolderBrowserDialogControl dans le .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="27e76-106">Dans .NET Core 3,0, Windows Forms utilisateurs un contrôle COM plus récent qui a été introduit dans Windows Vista :</span><span class="sxs-lookup"><span data-stu-id="27e76-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![FolderBrowserDialogControl dans .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="27e76-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="27e76-108">Version introduced</span></span>

<span data-ttu-id="27e76-109">3.0</span><span class="sxs-lookup"><span data-stu-id="27e76-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="27e76-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="27e76-110">Recommended action</span></span>

<span data-ttu-id="27e76-111">La boîte de dialogue sera automatiquement mise à niveau.</span><span class="sxs-lookup"><span data-stu-id="27e76-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="27e76-112">Si vous souhaitez conserver la boîte de dialogue d’origine, affectez à la propriété la valeur <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> `false` avant d’illustrer la boîte de dialogue, comme illustré par le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="27e76-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="27e76-113">Category</span><span class="sxs-lookup"><span data-stu-id="27e76-113">Category</span></span>

<span data-ttu-id="27e76-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27e76-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="27e76-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="27e76-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
