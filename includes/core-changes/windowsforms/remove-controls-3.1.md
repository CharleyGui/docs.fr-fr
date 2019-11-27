---
ms.openlocfilehash: 7ff8345fd0a3ca30375cf93d22625f89d5d9a053
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429237"
---
### <a name="removed-controls"></a><span data-ttu-id="b8d34-101">Contrôles supprimés</span><span class="sxs-lookup"><span data-stu-id="b8d34-101">Removed controls</span></span>

<span data-ttu-id="b8d34-102">À compter de .NET Core 3,1, certains contrôles de Windows Forms ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="b8d34-102">Starting in .NET Core 3.1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b8d34-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="b8d34-103">Change description</span></span>

<span data-ttu-id="b8d34-104">À compter de .NET Core 3,1, les différents contrôles de Windows Forms ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="b8d34-104">Starting with .NET Core 3.1, various Windows Forms controls are no longer available.</span></span> <span data-ttu-id="b8d34-105">Les contrôles de remplacement qui offrent une meilleure conception et une meilleure prise en charge ont été introduits dans .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b8d34-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="b8d34-106">Les contrôles déconseillés ont été précédemment supprimés des boîtes à outils du concepteur, mais ils étaient toujours disponibles pour être utilisés.</span><span class="sxs-lookup"><span data-stu-id="b8d34-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span>

<span data-ttu-id="b8d34-107">Les types suivants ne sont plus disponibles :</span><span class="sxs-lookup"><span data-stu-id="b8d34-107">The following types are no longer available:</span></span>

- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.Menu.MenuItemCollection>
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.ToolBar>
- <xref:System.Windows.Forms.ToolBarAppearance>
- <xref:System.Windows.Forms.ToolBarButton>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>
- <xref:System.Windows.Forms.ToolBarButtonStyle>
- <xref:System.Windows.Forms.ToolBarTextAlign>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.DataGridBoolColumn>
- <xref:System.Windows.Forms.DataGridCell>
- <xref:System.Windows.Forms.DataGridColumnStyle>
- <xref:System.Windows.Forms.DataGridLineStyle>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter>
- <xref:System.Windows.Forms.DataGridTableStyle>
- <xref:System.Windows.Forms.DataGridTextBox>
- <xref:System.Windows.Forms.DataGridTextBoxColumn>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.GridTablesFactory>
- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.IDataGridEditingService>
- <xref:System.Windows.Forms.DataGrid.HitTestType>
- <xref:System.Windows.Forms.Design.IMenuEditorService>

#### <a name="version-introduced"></a><span data-ttu-id="b8d34-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b8d34-108">Version introduced</span></span>

<span data-ttu-id="b8d34-109">3,1</span><span class="sxs-lookup"><span data-stu-id="b8d34-109">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b8d34-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b8d34-110">Recommended action</span></span>

<span data-ttu-id="b8d34-111">Chaque contrôle supprimé a un contrôle de remplacement recommandé.</span><span class="sxs-lookup"><span data-stu-id="b8d34-111">Each removed control has a recommended replacement control.</span></span> <span data-ttu-id="b8d34-112">Reportez-vous au tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="b8d34-112">Refer to the following table:</span></span>

| <span data-ttu-id="b8d34-113">Contrôle supprimé (API)</span><span class="sxs-lookup"><span data-stu-id="b8d34-113">Removed control (API)</span></span> | <span data-ttu-id="b8d34-114">Remplacement recommandé</span><span class="sxs-lookup"><span data-stu-id="b8d34-114">Recommended replacement</span></span> | <span data-ttu-id="b8d34-115">API associées supprimées</span><span class="sxs-lookup"><span data-stu-id="b8d34-115">Associated APIs that are removed</span></span> |
|-|-|-|
| <span data-ttu-id="b8d34-116">DataGrid</span><span class="sxs-lookup"><span data-stu-id="b8d34-116">DataGrid</span></span> | <span data-ttu-id="b8d34-117">DataGridView</span><span class="sxs-lookup"><span data-stu-id="b8d34-117">DataGridView</span></span> | <span data-ttu-id="b8d34-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span><span class="sxs-lookup"><span data-stu-id="b8d34-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span></span> |
| <span data-ttu-id="b8d34-119">ToolBar</span><span class="sxs-lookup"><span data-stu-id="b8d34-119">ToolBar</span></span> | <span data-ttu-id="b8d34-120">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b8d34-120">ToolStrip</span></span> | <span data-ttu-id="b8d34-121">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="b8d34-121">ToolBarAppearance</span></span> |
| <span data-ttu-id="b8d34-122">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="b8d34-122">ToolBarButton</span></span> | <span data-ttu-id="b8d34-123">ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="b8d34-123">ToolStripButton</span></span> | <span data-ttu-id="b8d34-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="b8d34-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span></span>|
| <span data-ttu-id="b8d34-125">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="b8d34-125">ContextMenu</span></span> | <span data-ttu-id="b8d34-126">ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="b8d34-126">ContextMenuStrip</span></span> | |
| <span data-ttu-id="b8d34-127">Menu</span><span class="sxs-lookup"><span data-stu-id="b8d34-127">Menu</span></span> | <span data-ttu-id="b8d34-128">ToolStripDropDown, ToolstripDropDownMenu</span><span class="sxs-lookup"><span data-stu-id="b8d34-128">ToolStripDropDown, ToolstripDropDownMenu</span></span> | <span data-ttu-id="b8d34-129">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="b8d34-129">MenuItemCollection</span></span> |
| <span data-ttu-id="b8d34-130">MainMenu</span><span class="sxs-lookup"><span data-stu-id="b8d34-130">MainMenu</span></span> | <span data-ttu-id="b8d34-131">MenuStrip</span><span class="sxs-lookup"><span data-stu-id="b8d34-131">MenuStrip</span></span> | |
| <span data-ttu-id="b8d34-132">MenuItem</span><span class="sxs-lookup"><span data-stu-id="b8d34-132">MenuItem</span></span> | <span data-ttu-id="b8d34-133">ToolstripMenuItem</span><span class="sxs-lookup"><span data-stu-id="b8d34-133">ToolstripMenuItem</span></span> | |

#### <a name="category"></a><span data-ttu-id="b8d34-134">Catégorie</span><span class="sxs-lookup"><span data-stu-id="b8d34-134">Category</span></span>

<span data-ttu-id="b8d34-135">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8d34-135">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b8d34-136">API affectées</span><span class="sxs-lookup"><span data-stu-id="b8d34-136">Affected APIs</span></span>

- <xref:System.Windows.Forms.Menu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Menu.MenuItemCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MainMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ContextMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MenuItem?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarAppearance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarTextAlign?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridBoolColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridCell?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridColumnStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridLineStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTableStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBox?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBoxColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridColumnStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTablesFactory?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTableStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.IDataGridEditingService?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid.HitTestType?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Design.IMenuEditorService?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `T:System.Windows.Forms.Menu`
- `T:System.Windows.Forms.Menu.MenuItemCollection`
- `T:System.Windows.Forms.MainMenu`
- `T:System.Windows.Forms.ContextMenu`
- `T:System.Windows.Forms.MenuItem`
- `T:System.Windows.Forms.ToolBar`
- `T:System.Windows.Forms.ToolBarAppearance`
- `T:System.Windows.Forms.ToolBarButton`
- `T:System.Windows.Forms.ToolBar.ToolBarButtonCollection`
- `T:System.Windows.Forms.ToolBarButtonClickEventArgs`
- `T:System.Windows.Forms.ToolBarButtonStyle`
- `T:System.Windows.Forms.ToolBarTextAlign`
- `T:System.Windows.Forms.DataGrid`
- `T:System.Windows.Forms.DataGridBoolColumn`
- `T:System.Windows.Forms.DataGridCell`
- `T:System.Windows.Forms.DataGridColumnStyle`
- `T:System.Windows.Forms.DataGridLineStyle`
- `T:System.Windows.Forms.DataGridParentRowsLabelStyle`
- `T:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter`
- `T:System.Windows.Forms.DataGridTableStyle`
- `T:System.Windows.Forms.DataGridTextBox`
- `T:System.Windows.Forms.DataGridTextBoxColumn`
- `T:System.Windows.Forms.GridColumnStylesCollection`
- `T:System.Windows.Forms.GridTablesFactory`
- `T:System.Windows.Forms.GridTableStylesCollection`
- `T:System.Windows.Forms.IDataGridEditingService`
- `T:System.Windows.Forms.DataGrid.HitTestType`
- `T:System.Windows.Forms.Design.IMenuEditorService`

-->
