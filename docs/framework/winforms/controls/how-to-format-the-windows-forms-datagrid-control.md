---
title: Mettre en forme le contrôle DataGrid
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
ms.openlocfilehash: 30342a89f3176255fa7217ccbbbd91c166ff7f35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732960"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a><span data-ttu-id="a7e53-102">Comment : mettre en forme le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7e53-102">How to: Format the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="a7e53-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="a7e53-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="a7e53-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a7e53-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="a7e53-105">L’application de couleurs différentes à différentes parties d’un contrôle de <xref:System.Windows.Forms.DataGrid> peut aider à faciliter la lecture et l’interprétation des informations.</span><span class="sxs-lookup"><span data-stu-id="a7e53-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="a7e53-106">La couleur peut être appliquée aux lignes et aux colonnes.</span><span class="sxs-lookup"><span data-stu-id="a7e53-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="a7e53-107">Les lignes et les colonnes peuvent également être masquées ou affichées à votre convenance.</span><span class="sxs-lookup"><span data-stu-id="a7e53-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="a7e53-108">Il existe trois aspects fondamentaux de la mise en forme du contrôle <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="a7e53-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="a7e53-109">Vous pouvez définir des propriétés pour établir un style par défaut dans lequel les données sont affichées.</span><span class="sxs-lookup"><span data-stu-id="a7e53-109">You can set properties to establish a default style in which data is displayed.</span></span> <span data-ttu-id="a7e53-110">À partir de cette base, vous pouvez personnaliser la façon dont certaines tables s’affichent au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a7e53-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span> <span data-ttu-id="a7e53-111">Enfin, vous pouvez modifier les colonnes qui sont affichées dans la grille de données ainsi que les couleurs et autres mises en forme affichées.</span><span class="sxs-lookup"><span data-stu-id="a7e53-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="a7e53-112">En guise de première étape de mise en forme d’une grille de données, vous pouvez définir les propriétés du <xref:System.Windows.Forms.DataGrid> lui-même.</span><span class="sxs-lookup"><span data-stu-id="a7e53-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="a7e53-113">Ces options de couleur et de format forment une base à partir de laquelle vous pouvez apporter des modifications en fonction des tables de données et des colonnes affichées.</span><span class="sxs-lookup"><span data-stu-id="a7e53-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="a7e53-114">Pour établir un style par défaut pour le contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="a7e53-114">To establish a default style for the DataGrid control</span></span>  
  
1. <span data-ttu-id="a7e53-115">Définissez les propriétés suivantes comme il convient :</span><span class="sxs-lookup"><span data-stu-id="a7e53-115">Set the following properties as appropriate:</span></span>  
  
    |<span data-ttu-id="a7e53-116">Propriété</span><span class="sxs-lookup"><span data-stu-id="a7e53-116">Property</span></span>|<span data-ttu-id="a7e53-117">Description</span><span class="sxs-lookup"><span data-stu-id="a7e53-117">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="a7e53-118">La propriété <xref:System.Windows.Forms.DataGrid.BackColor%2A> définit la couleur des lignes paires de la grille.</span><span class="sxs-lookup"><span data-stu-id="a7e53-118">The <xref:System.Windows.Forms.DataGrid.BackColor%2A> property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="a7e53-119">Lorsque vous définissez la propriété <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> sur une couleur différente, chaque autre ligne est définie sur cette nouvelle couleur (lignes 1, 3, 5, etc.).</span><span class="sxs-lookup"><span data-stu-id="a7e53-119">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="a7e53-120">Couleur d’arrière-plan des lignes numérotées de la grille (lignes 0, 2, 4, 6, etc.).</span><span class="sxs-lookup"><span data-stu-id="a7e53-120">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="a7e53-121">Tandis que les propriétés <xref:System.Windows.Forms.DataGrid.BackColor%2A> et <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> déterminent la couleur des lignes dans la grille, la propriété <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> détermine la couleur de la zone nonrow, qui est visible uniquement lorsque la grille fait défiler vers le bas, ou si seules quelques lignes sont contenues dans la grille.</span><span class="sxs-lookup"><span data-stu-id="a7e53-121">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the nonrow area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="a7e53-122">Le style de bordure de la grille, l’une des <xref:System.Windows.Forms.BorderStyle> valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="a7e53-122">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="a7e53-123">Couleur d’arrière-plan du titre de fenêtre de la grille qui s’affiche immédiatement au-dessus de la grille.</span><span class="sxs-lookup"><span data-stu-id="a7e53-123">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="a7e53-124">Police de la légende en haut de la grille.</span><span class="sxs-lookup"><span data-stu-id="a7e53-124">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="a7e53-125">Couleur d’arrière-plan du titre de fenêtre de la grille.</span><span class="sxs-lookup"><span data-stu-id="a7e53-125">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="a7e53-126">Police utilisée pour afficher le texte dans la grille.</span><span class="sxs-lookup"><span data-stu-id="a7e53-126">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="a7e53-127">Couleur de la police affichée par les données dans les lignes de la grille de données.</span><span class="sxs-lookup"><span data-stu-id="a7e53-127">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="a7e53-128">Couleur des lignes de la grille de données.</span><span class="sxs-lookup"><span data-stu-id="a7e53-128">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="a7e53-129">Style des lignes séparant les cellules de la grille, l’une des <xref:System.Windows.Forms.DataGridLineStyle> valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="a7e53-129">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="a7e53-130">Couleur d’arrière-plan des en-têtes de ligne et de colonne.</span><span class="sxs-lookup"><span data-stu-id="a7e53-130">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="a7e53-131">Police utilisée pour les en-têtes de colonnes.</span><span class="sxs-lookup"><span data-stu-id="a7e53-131">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="a7e53-132">Couleur de premier plan des en-têtes de colonnes de la grille, y compris le texte d’en-tête de colonne et les glyphes plus/moins (pour développer les lignes quand plusieurs tables associées sont affichées).</span><span class="sxs-lookup"><span data-stu-id="a7e53-132">The foreground color of the grid's column headers, including the column header text and the plus/minus glyphs (to expand rows when multiple related tables are displayed).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="a7e53-133">Couleur du texte de tous les liens de la grille de données, y compris les liens vers les tables enfants, le nom de la relation, etc.</span><span class="sxs-lookup"><span data-stu-id="a7e53-133">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="a7e53-134">Dans une table enfant, il s’agit de la couleur d’arrière-plan des lignes parentes.</span><span class="sxs-lookup"><span data-stu-id="a7e53-134">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="a7e53-135">Dans une table enfant, il s’agit de la couleur de premier plan des lignes parentes.</span><span class="sxs-lookup"><span data-stu-id="a7e53-135">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="a7e53-136">Détermine si les noms de table et de colonne sont affichés dans la ligne parente, au moyen de l’énumération <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>.</span><span class="sxs-lookup"><span data-stu-id="a7e53-136">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="a7e53-137">Largeur par défaut (en pixels) des colonnes de la grille.</span><span class="sxs-lookup"><span data-stu-id="a7e53-137">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="a7e53-138">Définissez cette propriété avant de réinitialiser les propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> (séparément ou à l’aide de la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>), sinon la propriété n’aura aucun effet.</span><span class="sxs-lookup"><span data-stu-id="a7e53-138">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="a7e53-139">La propriété ne peut pas être définie sur une valeur inférieure à 0.</span><span class="sxs-lookup"><span data-stu-id="a7e53-139">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="a7e53-140">Hauteur de ligne (en pixels) des lignes de la grille.</span><span class="sxs-lookup"><span data-stu-id="a7e53-140">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="a7e53-141">Définissez cette propriété avant de réinitialiser les propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> (séparément ou à l’aide de la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>), sinon la propriété n’aura aucun effet.</span><span class="sxs-lookup"><span data-stu-id="a7e53-141">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="a7e53-142">La propriété ne peut pas être définie sur une valeur inférieure à 0.</span><span class="sxs-lookup"><span data-stu-id="a7e53-142">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="a7e53-143">Largeur des en-têtes de lignes de la grille.</span><span class="sxs-lookup"><span data-stu-id="a7e53-143">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="a7e53-144">Quand une ligne ou une cellule est sélectionnée, il s’agit de la couleur d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="a7e53-144">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="a7e53-145">Quand une ligne ou une cellule est sélectionnée, il s’agit de la couleur de premier plan.</span><span class="sxs-lookup"><span data-stu-id="a7e53-145">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="a7e53-146">N’oubliez pas, lors de la personnalisation des couleurs des contrôles, qu’il est possible de rendre le contrôle inaccessible, en raison d’un choix de couleurs médiocres (par exemple, Red et Green).</span><span class="sxs-lookup"><span data-stu-id="a7e53-146">Keep in mind, when customizing the colors of controls, that it is possible to make the control inaccessible, due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="a7e53-147">Utilisez les couleurs disponibles dans la palette **couleurs système** pour éviter ce problème.</span><span class="sxs-lookup"><span data-stu-id="a7e53-147">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="a7e53-148">Les procédures suivantes supposent que votre formulaire possède un contrôle de <xref:System.Windows.Forms.DataGrid> lié à une table de données.</span><span class="sxs-lookup"><span data-stu-id="a7e53-148">The following procedures assume your form has a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="a7e53-149">Pour plus d’informations, consultez [liaison du contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="a7e53-149">For more information, see [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a><span data-ttu-id="a7e53-150">Pour définir par programmation le style de table et de colonne d’une table de données</span><span class="sxs-lookup"><span data-stu-id="a7e53-150">To set the table and column style of a data table programmatically</span></span>  
  
1. <span data-ttu-id="a7e53-151">Créez un nouveau style de table et définissez ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="a7e53-151">Create a new table style and set its properties.</span></span>  
  
2. <span data-ttu-id="a7e53-152">Créez un style de colonne et définissez ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="a7e53-152">Create a column style and set its properties.</span></span>  
  
3. <span data-ttu-id="a7e53-153">Ajoutez le style de colonne à la collection de styles de colonne du style de tableau.</span><span class="sxs-lookup"><span data-stu-id="a7e53-153">Add the column style to the table style's column styles collection.</span></span>  
  
4. <span data-ttu-id="a7e53-154">Ajoutez le style de tableau à la collection de styles de table de la grille de données.</span><span class="sxs-lookup"><span data-stu-id="a7e53-154">Add the table style to the data grid's table styles collection.</span></span>  
  
5. <span data-ttu-id="a7e53-155">Dans l’exemple ci-dessous, créez une instance d’une nouvelle <xref:System.Windows.Forms.DataGridTableStyle> et définissez sa propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7e53-155">In the example below, create an instance of a new <xref:System.Windows.Forms.DataGridTableStyle> and set its <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property.</span></span>  
  
6. <span data-ttu-id="a7e53-156">Créez une nouvelle instance d’un **GridColumnStyle** et définissez son **MappingName** (ainsi que d’autres propriétés de disposition et d’affichage).</span><span class="sxs-lookup"><span data-stu-id="a7e53-156">Create a new instance of a **GridColumnStyle** and set its **MappingName** (and some other layout and display properties).</span></span>  
  
7. <span data-ttu-id="a7e53-157">Répétez les étapes 2 à 6 pour chaque style de colonne que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="a7e53-157">Repeat steps 2 through 6 for each column style you want to create.</span></span>  
  
     <span data-ttu-id="a7e53-158">L’exemple suivant illustre la façon dont un <xref:System.Windows.Forms.DataGridTextBoxColumn> est créé, car un nom doit être affiché dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="a7e53-158">The following example illustrates how a <xref:System.Windows.Forms.DataGridTextBoxColumn> is created, because a name is to be displayed in the column.</span></span> <span data-ttu-id="a7e53-159">En outre, vous ajoutez le style de colonne à la <xref:System.Windows.Forms.GridColumnStylesCollection> du style de table, et vous ajoutez le style de tableau à la <xref:System.Windows.Forms.GridTableStylesCollection> de la grille de données.</span><span class="sxs-lookup"><span data-stu-id="a7e53-159">Additionally, you add the column style to the <xref:System.Windows.Forms.GridColumnStylesCollection> of the table style, and you add the table style to the <xref:System.Windows.Forms.GridTableStylesCollection> of the data grid.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7e53-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7e53-160">See also</span></span>

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [<span data-ttu-id="a7e53-161">Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7e53-161">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="a7e53-162">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="a7e53-162">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
