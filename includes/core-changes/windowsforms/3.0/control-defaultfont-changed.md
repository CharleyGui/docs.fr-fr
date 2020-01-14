---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936995"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="2a94b-101">La police de contrôle par défaut a été remplacée par Segoe UI 9 PT</span><span class="sxs-lookup"><span data-stu-id="2a94b-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="2a94b-102">Description des modifications</span><span class="sxs-lookup"><span data-stu-id="2a94b-102">Change description</span></span>

<span data-ttu-id="2a94b-103">Dans .NET Framework, la propriété <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> a été définie sur `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="2a94b-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="2a94b-104">L’illustration suivante montre une fenêtre qui utilise la police par défaut.</span><span class="sxs-lookup"><span data-stu-id="2a94b-104">The following image shows a window that uses the default font.</span></span>

![Police de contrôle par défaut dans .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="2a94b-106">À compter de .NET Core 3,0, la police par défaut est définie sur `Segoe UI 9 pt` (la même police que <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="2a94b-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="2a94b-107">Suite à cette modification, les formulaires et les contrôles sont dimensionnés à une taille supérieure à 27% pour tenir compte de la taille de la nouvelle police par défaut.</span><span class="sxs-lookup"><span data-stu-id="2a94b-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="2a94b-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2a94b-108">For example:</span></span>

![Police de contrôle par défaut dans .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="2a94b-110">Cette modification a été apportée pour s’aligner sur [les instructions de l’expérience utilisateur Windows (UX)](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="2a94b-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2a94b-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2a94b-111">Version introduced</span></span>

<span data-ttu-id="2a94b-112">3.0</span><span class="sxs-lookup"><span data-stu-id="2a94b-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2a94b-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2a94b-113">Recommended action</span></span>

<span data-ttu-id="2a94b-114">En raison de la modification de la taille des formulaires et des contrôles, assurez-vous que votre application s’affiche correctement.</span><span class="sxs-lookup"><span data-stu-id="2a94b-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="2a94b-115">Pour conserver la police d’origine, définissez la police par défaut de votre formulaire sur `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="2a94b-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="2a94b-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2a94b-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="2a94b-117">Catégorie</span><span class="sxs-lookup"><span data-stu-id="2a94b-117">Category</span></span>

- <span data-ttu-id="2a94b-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a94b-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a94b-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="2a94b-119">Affected APIs</span></span>

<span data-ttu-id="2a94b-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2a94b-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
