---
ms.openlocfilehash: 7a6b0b15de4295506ff03b8566c06010b918566c
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158391"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="f1f17-101">Les méthodes WinForms lèvent désormais ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="f1f17-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="f1f17-102">Certaines méthodes Windows Forms lèvent désormais <xref:System.ArgumentNullException> un pour les arguments null, où ils ont <xref:System.NullReferenceException>précédemment levé un.</span><span class="sxs-lookup"><span data-stu-id="f1f17-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f1f17-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="f1f17-103">Change description</span></span>

<span data-ttu-id="f1f17-104">Jusqu’à présent, certaines méthodes Windows Forms <xref:System.NullReferenceException> ont levé une si passé un argument qui avait la valeur null.</span><span class="sxs-lookup"><span data-stu-id="f1f17-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="f1f17-105">À compter de .NET 5,0, ces méthodes lèvent <xref:System.ArgumentNullException> désormais une exception pour les arguments null.</span><span class="sxs-lookup"><span data-stu-id="f1f17-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments instead.</span></span>

<span data-ttu-id="f1f17-106">La levée <xref:System.ArgumentNullException> d’une conforme au comportement du Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="f1f17-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="f1f17-107">Il améliore également l’expérience de débogage en communiquant clairement qu’un argument est null et son argument.</span><span class="sxs-lookup"><span data-stu-id="f1f17-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f1f17-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f1f17-108">Version introduced</span></span>

<span data-ttu-id="f1f17-109">.NET 5,0 Preview 1 </span><span class="sxs-lookup"><span data-stu-id="f1f17-109">.NET 5.0 Preview 1</span></span>\
<span data-ttu-id="f1f17-110">.NET 5,0 Preview 2</span><span class="sxs-lookup"><span data-stu-id="f1f17-110">.NET 5.0 Preview 2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f1f17-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f1f17-111">Recommended action</span></span>

<span data-ttu-id="f1f17-112">Si vous appelez l’une de ces méthodes et que votre code intercepte actuellement un <xref:System.NullReferenceException> pour les arguments <xref:System.ArgumentNullException> null, interceptez à la place.</span><span class="sxs-lookup"><span data-stu-id="f1f17-112">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="f1f17-113">En outre, envisagez de mettre à jour le code afin d’éviter de passer des arguments null aux méthodes listées.</span><span class="sxs-lookup"><span data-stu-id="f1f17-113">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="f1f17-114">Category</span><span class="sxs-lookup"><span data-stu-id="f1f17-114">Category</span></span>

<span data-ttu-id="f1f17-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f1f17-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f1f17-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="f1f17-116">Affected APIs</span></span>

<span data-ttu-id="f1f17-117">À compter de .NET 5,0 Preview 1 :</span><span class="sxs-lookup"><span data-stu-id="f1f17-117">Starting in .NET 5.0 Preview 1:</span></span>

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

<span data-ttu-id="f1f17-118">À compter de .NET 5,0 Preview 2 :</span><span class="sxs-lookup"><span data-stu-id="f1f17-118">Starting in .NET 5.0 Preview 2:</span></span>

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <span data-ttu-id="f1f17-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>(pour le <xref:System.IO.Stream> paramètre uniquement)</span><span class="sxs-lookup"><span data-stu-id="f1f17-119"><xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> (for the <xref:System.IO.Stream> parameter only)</span></span>

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
