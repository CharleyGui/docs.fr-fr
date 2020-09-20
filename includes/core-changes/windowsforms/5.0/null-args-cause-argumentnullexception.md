---
ms.openlocfilehash: 59e7b55516d79aa5c574a8869698e1a18576ef41
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770816"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="ebdb0-101">Les méthodes WinForms lèvent désormais ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="ebdb0-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="ebdb0-102">Certaines méthodes Windows Forms lèvent désormais un <xref:System.ArgumentNullException> pour les arguments null, où ils ont précédemment levé un <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="ebdb0-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ebdb0-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ebdb0-103">Change description</span></span>

<span data-ttu-id="ebdb0-104">Jusqu’à présent, certaines méthodes Windows Forms <xref:System.NullReferenceException> ont levé une si passé un argument qui avait la valeur null.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="ebdb0-105">À compter de .NET 5,0, ces méthodes lèvent désormais une exception <xref:System.ArgumentNullException> pour les arguments null, à la place.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="ebdb0-106">La levée d’une <xref:System.ArgumentNullException> conforme au comportement du Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="ebdb0-107">Il améliore également l’expérience de débogage en communiquant clairement qu’un argument est null et son argument.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ebdb0-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ebdb0-108">Version introduced</span></span>

<span data-ttu-id="ebdb0-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="ebdb0-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ebdb0-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ebdb0-110">Recommended action</span></span>

<span data-ttu-id="ebdb0-111">Si vous appelez l’une de ces méthodes et que votre code intercepte actuellement un <xref:System.NullReferenceException> pour les arguments null, interceptez à la <xref:System.ArgumentNullException> place.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-111">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="ebdb0-112">En outre, envisagez de mettre à jour le code afin d’éviter de passer des arguments null aux méthodes listées.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-112">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="ebdb0-113">Category</span><span class="sxs-lookup"><span data-stu-id="ebdb0-113">Category</span></span>

<span data-ttu-id="ebdb0-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ebdb0-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ebdb0-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="ebdb0-115">Affected APIs</span></span>

<span data-ttu-id="ebdb0-116">Le tableau suivant répertorie les méthodes et les paramètres affectés :</span><span class="sxs-lookup"><span data-stu-id="ebdb0-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="ebdb0-117">Méthode</span><span class="sxs-lookup"><span data-stu-id="ebdb0-117">Method</span></span> | <span data-ttu-id="ebdb0-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="ebdb0-118">Parameter name</span></span> | <span data-ttu-id="ebdb0-119">Version ajoutée</span><span class="sxs-lookup"><span data-stu-id="ebdb0-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="ebdb0-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-120">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="ebdb0-121">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-121">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="ebdb0-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-122">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ebdb0-123">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-123">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ebdb0-124">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-124">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ebdb0-125">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-125">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ebdb0-126">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-126">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="ebdb0-127">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-127">Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="ebdb0-128">Préversion 2</span><span class="sxs-lookup"><span data-stu-id="ebdb0-128">Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="ebdb0-129">Préversion 2</span><span class="sxs-lookup"><span data-stu-id="ebdb0-129">Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="ebdb0-130">Préversion 5</span><span class="sxs-lookup"><span data-stu-id="ebdb0-130">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="ebdb0-131">Préversion 5</span><span class="sxs-lookup"><span data-stu-id="ebdb0-131">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="ebdb0-132">Préversion 5</span><span class="sxs-lookup"><span data-stu-id="ebdb0-132">Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="ebdb0-133">Préversion 5</span><span class="sxs-lookup"><span data-stu-id="ebdb0-133">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="ebdb0-134">Préversion 6</span><span class="sxs-lookup"><span data-stu-id="ebdb0-134">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="ebdb0-135">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="ebdb0-135">`owner`, `value`</span></span> | <span data-ttu-id="ebdb0-136">Préversion 6</span><span class="sxs-lookup"><span data-stu-id="ebdb0-136">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="ebdb0-137">`owner`, `value`</span><span class="sxs-lookup"><span data-stu-id="ebdb0-137">`owner`, `value`</span></span> | <span data-ttu-id="ebdb0-138">Préversion 6</span><span class="sxs-lookup"><span data-stu-id="ebdb0-138">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="ebdb0-139">Préversion 6</span><span class="sxs-lookup"><span data-stu-id="ebdb0-139">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="ebdb0-140">Préversion 6</span><span class="sxs-lookup"><span data-stu-id="ebdb0-140">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="ebdb0-141">Préversion 6</span><span class="sxs-lookup"><span data-stu-id="ebdb0-141">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="ebdb0-142">Préversion 6</span><span class="sxs-lookup"><span data-stu-id="ebdb0-142">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListView.SelectedIndexCollection.%23ctor(System.Windows.Forms.ListView)> | `owner` | <span data-ttu-id="ebdb0-143">Version préliminaire 7</span><span class="sxs-lookup"><span data-stu-id="ebdb0-143">Preview 7</span></span> |
> | <xref:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="ebdb0-144">`key` est `null` ou vide</span><span class="sxs-lookup"><span data-stu-id="ebdb0-144">`key` is `null` or empty</span></span> | <span data-ttu-id="ebdb0-145">Version préliminaire 8</span><span class="sxs-lookup"><span data-stu-id="ebdb0-145">Preview 8</span></span> |
> | <xref:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="ebdb0-146">`key` est `null` ou vide</span><span class="sxs-lookup"><span data-stu-id="ebdb0-146">`key` is `null` or empty</span></span> | <span data-ttu-id="ebdb0-147">RC1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-147">RC1</span></span> |
> | <xref:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="ebdb0-148">RC1</span><span class="sxs-lookup"><span data-stu-id="ebdb0-148">RC1</span></span> |

<!-- 

#### Affected APIs

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
- `M:System.Windows.Forms.ListViewGroup.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.#ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System#Collections#ICollection#CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListView.SelectedIndexCollection.#ctor(System.Windows.Forms.ListView)`
- `M:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)`

-->
