---
ms.openlocfilehash: fc0eec26073c299887b4748d0ad37e21c7294e84
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274827"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a><span data-ttu-id="9a4e8-101">WinForms API maintenant jeter ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="9a4e8-101">WinForms APIs now throw ArgumentNullException</span></span>

<span data-ttu-id="9a4e8-102">Certaines méthodes de formulaires Windows maintenant jeter <xref:System.ArgumentNullException> un <xref:System.NullReferenceException>pour les arguments nuls, où auparavant ils ont jeté un .</span><span class="sxs-lookup"><span data-stu-id="9a4e8-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9a4e8-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="9a4e8-103">Change description</span></span>

<span data-ttu-id="9a4e8-104">Auparavant, certaines méthodes de <xref:System.NullReferenceException> Formulaires Windows ont lancé un argument qui était nul.</span><span class="sxs-lookup"><span data-stu-id="9a4e8-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="9a4e8-105">À partir de .NET 5.0, <xref:System.ArgumentNullException> ces méthodes jettent maintenant un pour les arguments nuls à la place.</span><span class="sxs-lookup"><span data-stu-id="9a4e8-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="9a4e8-106">Jeter <xref:System.ArgumentNullException> une conformité au comportement de l’exécution .NET.</span><span class="sxs-lookup"><span data-stu-id="9a4e8-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="9a4e8-107">Il améliore également l’expérience de débogage en communiquant clairement qu’un argument est nul et quel argument il est.</span><span class="sxs-lookup"><span data-stu-id="9a4e8-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9a4e8-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9a4e8-108">Version introduced</span></span>

<span data-ttu-id="9a4e8-109">.NET 5.0 Aperçu 1</span><span class="sxs-lookup"><span data-stu-id="9a4e8-109">.NET 5.0 Preview 1\</span></span>
<span data-ttu-id="9a4e8-110">.NET 5.0 Aperçu 2</span><span class="sxs-lookup"><span data-stu-id="9a4e8-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9a4e8-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9a4e8-111">Recommended action</span></span>

<span data-ttu-id="9a4e8-112">Si vous appelez l’une de ces <xref:System.NullReferenceException> méthodes et que <xref:System.ArgumentNullException> votre code attrape actuellement un pour les arguments nuls, attrapez plutôt un.</span><span class="sxs-lookup"><span data-stu-id="9a4e8-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="9a4e8-113">En outre, envisagez de mettre à jour le code pour éviter de transmettre des arguments nuls aux méthodes énumérées.</span><span class="sxs-lookup"><span data-stu-id="9a4e8-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="9a4e8-114">Category</span><span class="sxs-lookup"><span data-stu-id="9a4e8-114">Category</span></span>

<span data-ttu-id="9a4e8-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a4e8-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9a4e8-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="9a4e8-116">Affected APIs</span></span>

<span data-ttu-id="9a4e8-117">À partir de .NET 5.0 Aperçu 1:</span><span class="sxs-lookup"><span data-stu-id="9a4e8-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="9a4e8-118">À partir de .NET 5.0 Aperçu 2:</span><span class="sxs-lookup"><span data-stu-id="9a4e8-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="9a4e8-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(pour <xref:System.IO.Stream> le paramètre seulement)</span><span class="sxs-lookup"><span data-stu-id="9a4e8-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`

-->
