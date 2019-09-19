---
ms.openlocfilehash: 02dbf5ccca97f5e7d2e1fada39bdf601cf37906f
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119358"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a><span data-ttu-id="88c49-101">`Control.DefaultFont`remplacé par`Segoe UI 9pt`</span><span class="sxs-lookup"><span data-stu-id="88c49-101">`Control.DefaultFont` changed to `Segoe UI 9pt`</span></span> 

#### <a name="change-description"></a><span data-ttu-id="88c49-102">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="88c49-102">Change description</span></span>

<span data-ttu-id="88c49-103">Dans le .NET Framework, la <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> propriété a la `Microsoft Sans Serif 8pt`valeur.</span><span class="sxs-lookup"><span data-stu-id="88c49-103">In the .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="88c49-104">L’illustration suivante montre une fenêtre qui utilise la police par défaut.</span><span class="sxs-lookup"><span data-stu-id="88c49-104">The following figure shows a window that uses the default font.</span></span>

![police de contrôle par défaut dans .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="88c49-106">Dans .net core à compter de .net Core 3,0, il est défini `Segoe UI 9pt` sur (la même police <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>que).</span><span class="sxs-lookup"><span data-stu-id="88c49-106">In .NET Core starting with .NET Core 3.0, it is set to `Segoe UI 9pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="88c49-107">Suite à cette modification, les formulaires et les contrôles seront dimensionnés à une taille supérieure à 27% pour prendre en compte la plus grande taille de la nouvelle police par défaut.</span><span class="sxs-lookup"><span data-stu-id="88c49-107">As a result of this change, forms and controls will be sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="88c49-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="88c49-108">For example:</span></span>

![police de contrôle par défaut-dans .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="88c49-110">Cette modification a été apportée pour s’aligner sur [les directives Windows UX](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="88c49-110">This change was made to align with [Windows UX guidelines](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="88c49-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="88c49-111">Version introduced</span></span>

<span data-ttu-id="88c49-112">3.0</span><span class="sxs-lookup"><span data-stu-id="88c49-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="88c49-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="88c49-113">Recommended action</span></span>

<span data-ttu-id="88c49-114">En raison de la modification de la taille des formulaires et des contrôles, assurez-vous que votre application s’affiche correctement.</span><span class="sxs-lookup"><span data-stu-id="88c49-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="88c49-115">Pour conserver la police d’origine, définissez la police par défaut de `Microsoft Sans Serif 8pt`votre formulaire sur.</span><span class="sxs-lookup"><span data-stu-id="88c49-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="88c49-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="88c49-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="88c49-117">Category</span><span class="sxs-lookup"><span data-stu-id="88c49-117">Category</span></span>

- <span data-ttu-id="88c49-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88c49-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="88c49-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="88c49-119">Affected APIs</span></span>

<span data-ttu-id="88c49-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="88c49-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->