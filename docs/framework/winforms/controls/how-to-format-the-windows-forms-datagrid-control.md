---
title: Format DataGrid Control
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
ms.openlocfilehash: 180f837c7d60f49af880faefc05da262be061d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182146"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="b9ec1-102">Comment : mettre en forme le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9ec1-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="b9ec1-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b9ec1-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b9ec1-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="b9ec1-105">L’application de différentes <xref:System.Windows.Forms.DataGrid> couleurs à différentes parties d’un contrôle peut aider à rendre l’information en elle plus facile à lire et à interpréter.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="b9ec1-106">La couleur peut être appliquée sur les rangées et les colonnes.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="b9ec1-107">Les lignes et les colonnes peuvent également être cachées ou affichées à votre discrétion.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="b9ec1-108">Il y a trois aspects <xref:System.Windows.Forms.DataGrid> de base de la mise en forme du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="b9ec1-109">Vous pouvez définir des propriétés pour établir un style par défaut dans lequel les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="b9ec1-110">À partir de cette base, vous pouvez ensuite personnaliser la façon dont certaines tables sont affichées au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="b9ec1-111">Enfin, vous pouvez modifier les colonnes affichées dans la grille de données ainsi que les couleurs et autres formatages qui sont affichés.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="b9ec1-112">Comme première étape dans la mise en forme d’une grille de données, vous pouvez définir les propriétés de la <xref:System.Windows.Forms.DataGrid> lui-même.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="b9ec1-113">Ces choix de couleur et de format forment une base à partir de laquelle vous pouvez ensuite apporter des modifications en fonction des tableaux de données et des colonnes affichées.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="b9ec1-114">Établir un style par défaut pour le contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="b9ec1-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="b9ec1-115">Définissez les propriétés suivantes au besoin :</span><span class="sxs-lookup"><span data-stu-id="b9ec1-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="b9ec1-116">Propriété</span><span class="sxs-lookup"><span data-stu-id="b9ec1-116">Property</span></span>|<span data-ttu-id="b9ec1-117">Description</span><span class="sxs-lookup"><span data-stu-id="b9ec1-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="b9ec1-118">La <xref:System.Windows.Forms.DataGrid.BackColor%2A> propriété définit la couleur des rangées à numéros pair de la grille.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="b9ec1-119">Lorsque vous <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> définissez la propriété à une couleur différente, chaque autre rangée est réglée à cette nouvelle couleur (lignes 1, 3, 5, et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="b9ec1-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="b9ec1-120">La couleur de fond des rangées à numéros pair de la grille (lignes 0, 2, 4, 6, et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="b9ec1-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="b9ec1-121">Alors <xref:System.Windows.Forms.DataGrid.BackColor%2A> que <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> les propriétés et les propriétés <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> déterminent la couleur des rangées dans la grille, la propriété détermine la couleur de la zone nonrow, qui n’est visible que lorsque la grille est défilée vers le bas, ou si seulement quelques lignes sont contenues dans la grille.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="b9ec1-122">Le style frontière de la <xref:System.Windows.Forms.BorderStyle> grille, l’une des valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="b9ec1-123">La couleur de fond de la légende de fenêtre de la grille qui apparaît immédiatement au-dessus de la grille.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="b9ec1-124">La police de la légende en haut de la grille.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="b9ec1-125">La couleur de fond de la légende de fenêtre de la grille.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="b9ec1-126">La police utilisée pour afficher le texte dans la grille.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="b9ec1-127">La couleur de la police affichée par les données dans les lignes de la grille de données.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="b9ec1-128">La couleur des lignes de grille de la grille de données.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="b9ec1-129">Le style des lignes séparant les cellules <xref:System.Windows.Forms.DataGridLineStyle> de la grille, l’une des valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="b9ec1-130">La couleur de fond des en-têtes de ligne et de colonne.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="b9ec1-131">La police utilisée pour les en-têtes de colonne.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="b9ec1-132">La couleur de premier plan des en-têtes de colonne de la grille, y compris le texte d’en-tête de colonne et les glyphes plus/moins (pour étendre les rangées lorsque plusieurs tables connexes sont affichées).</span><span class="sxs-lookup"><span data-stu-id="b9ec1-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="b9ec1-133">La couleur du texte de tous les liens dans la grille de données, y compris les liens vers les tables pour enfants, le nom de relation, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="b9ec1-134">Dans une table pour enfants, c’est la couleur de fond des rangées de parents.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="b9ec1-135">Dans une table pour enfants, c’est la couleur de premier plan des rangées parent.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="b9ec1-136">Détermine si les noms de la table et de la <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> colonne sont affichés dans la rangée parente, au moyen de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="b9ec1-137">Largeur par défaut (en pixels) des colonnes de la grille.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="b9ec1-138">Définissez cette propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> avant <xref:System.Windows.Forms.DataGrid.DataMember%2A> de réinitialiser <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> les propriétés et les propriétés (séparément, ou par la méthode), ou la propriété n’aura aucun effet.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="b9ec1-139">La propriété ne peut pas être réglée à une valeur inférieure à 0.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="b9ec1-140">La hauteur de la ligne (en pixels) des rangées dans la grille.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="b9ec1-141">Définissez cette propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> avant <xref:System.Windows.Forms.DataGrid.DataMember%2A> de réinitialiser <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> les propriétés et les propriétés (séparément, ou par la méthode), ou la propriété n’aura aucun effet.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="b9ec1-142">La propriété ne peut pas être réglée à une valeur inférieure à 0.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="b9ec1-143">La largeur des en-têtes de la ligne de la grille.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="b9ec1-144">Lorsqu’une ligne ou une cellule est sélectionnée, c’est la couleur de fond.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="b9ec1-145">Lorsqu’une ligne ou une cellule est sélectionnée, c’est la couleur du premier plan.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="b9ec1-146">Gardez à l’esprit, lors de la personnalisation des couleurs des commandes, qu’il est possible de rendre le contrôle inaccessible, en raison d’un mauvais choix de couleur (par exemple, rouge et vert).</span><span class="sxs-lookup"><span data-stu-id="b9ec1-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="b9ec1-147">Utilisez les couleurs disponibles sur la palette **De couleurs système** pour éviter ce problème.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="b9ec1-148">Les procédures suivantes supposent <xref:System.Windows.Forms.DataGrid> que votre formulaire a un contrôle lié à une table de données.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="b9ec1-149">Pour plus d’informations, voir [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="b9ec1-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="b9ec1-150">Définir le style de table et de colonne d’une table de données programmatiquement</span><span class="sxs-lookup"><span data-stu-id="b9ec1-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="b9ec1-151">Créez un nouveau style de table et définissez ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="b9ec1-152">Créez un style de colonne et définissez ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="b9ec1-153">Ajoutez le style colonne à la collection de styles de colonne du style de table.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="b9ec1-154">Ajoutez le style de table à la collection de styles de table de la grille de données.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="b9ec1-155">Dans l’exemple ci-dessous, <xref:System.Windows.Forms.DataGridTableStyle> créez un <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> exemple de nouveau et définissez sa propriété.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="b9ec1-156">Créez une nouvelle instance d’un **GridColumnStyle** et définissez son **MappingName** (et d’autres propriétés de mise en page et d’affichage).</span><span class="sxs-lookup"><span data-stu-id="b9ec1-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="b9ec1-157">Répétez les étapes 2 à 6 pour chaque style de colonne que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="b9ec1-158">L’exemple suivant illustre <xref:System.Windows.Forms.DataGridTextBoxColumn> comment un est créé, parce qu’un nom doit être affiché dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="b9ec1-159">En outre, vous ajoutez <xref:System.Windows.Forms.GridColumnStylesCollection> le style de colonne au style de <xref:System.Windows.Forms.GridTableStylesCollection> table, et vous ajoutez le style de table à la grille de données.</span><span class="sxs-lookup"><span data-stu-id="b9ec1-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName
       ' to the name of a DataColumn in the DataTable.
       ' Set the HeaderText and Width properties.
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to
       ' the GridTableStylesCollection.
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName
       // to the name of a DataColumn in the DataTable.
       // Set the HeaderText and Width properties.
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to
       // the GridTableStylesCollection.
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName
          // to the name of a DataColumn in the DataTable.
          // Set the HeaderText and Width properties.
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to
          // the GridTableStylesCollection.
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b9ec1-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9ec1-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="b9ec1-161">Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9ec1-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="b9ec1-162">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="b9ec1-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
