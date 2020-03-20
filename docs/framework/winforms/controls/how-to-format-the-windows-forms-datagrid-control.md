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
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Comment : mettre en forme le contrôle DataGrid Windows Forms
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 L’application de différentes <xref:System.Windows.Forms.DataGrid> couleurs à différentes parties d’un contrôle peut aider à rendre l’information en elle plus facile à lire et à interpréter. La couleur peut être appliquée sur les rangées et les colonnes. Les lignes et les colonnes peuvent également être cachées ou affichées à votre discrétion.  
  
 Il y a trois aspects <xref:System.Windows.Forms.DataGrid> de base de la mise en forme du contrôle. Vous pouvez définir des propriétés pour établir un style par défaut dans lequel les données sont affichées. À partir de cette base, vous pouvez ensuite personnaliser la façon dont certaines tables sont affichées au moment de l’exécution. Enfin, vous pouvez modifier les colonnes affichées dans la grille de données ainsi que les couleurs et autres formatages qui sont affichés.  
  
 Comme première étape dans la mise en forme d’une grille de données, vous pouvez définir les propriétés de la <xref:System.Windows.Forms.DataGrid> lui-même. Ces choix de couleur et de format forment une base à partir de laquelle vous pouvez ensuite apporter des modifications en fonction des tableaux de données et des colonnes affichées.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Établir un style par défaut pour le contrôle DataGrid  
  
1. Définissez les propriétés suivantes au besoin :  
  
    |Propriété|Description|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|La <xref:System.Windows.Forms.DataGrid.BackColor%2A> propriété définit la couleur des rangées à numéros pair de la grille. Lorsque vous <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> définissez la propriété à une couleur différente, chaque autre rangée est réglée à cette nouvelle couleur (lignes 1, 3, 5, et ainsi de suite).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|La couleur de fond des rangées à numéros pair de la grille (lignes 0, 2, 4, 6, et ainsi de suite).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Alors <xref:System.Windows.Forms.DataGrid.BackColor%2A> que <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> les propriétés et les propriétés <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> déterminent la couleur des rangées dans la grille, la propriété détermine la couleur de la zone nonrow, qui n’est visible que lorsque la grille est défilée vers le bas, ou si seulement quelques lignes sont contenues dans la grille.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Le style frontière de la <xref:System.Windows.Forms.BorderStyle> grille, l’une des valeurs d’énumération.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|La couleur de fond de la légende de fenêtre de la grille qui apparaît immédiatement au-dessus de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|La police de la légende en haut de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|La couleur de fond de la légende de fenêtre de la grille.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|La police utilisée pour afficher le texte dans la grille.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|La couleur de la police affichée par les données dans les lignes de la grille de données.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|La couleur des lignes de grille de la grille de données.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Le style des lignes séparant les cellules <xref:System.Windows.Forms.DataGridLineStyle> de la grille, l’une des valeurs d’énumération.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|La couleur de fond des en-têtes de ligne et de colonne.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|La police utilisée pour les en-têtes de colonne.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|La couleur de premier plan des en-têtes de colonne de la grille, y compris le texte d’en-tête de colonne et les glyphes plus/moins (pour étendre les rangées lorsque plusieurs tables connexes sont affichées).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|La couleur du texte de tous les liens dans la grille de données, y compris les liens vers les tables pour enfants, le nom de relation, et ainsi de suite.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Dans une table pour enfants, c’est la couleur de fond des rangées de parents.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Dans une table pour enfants, c’est la couleur de premier plan des rangées parent.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Détermine si les noms de la table et de la <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> colonne sont affichés dans la rangée parente, au moyen de l’énumération.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Largeur par défaut (en pixels) des colonnes de la grille. Définissez cette propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> avant <xref:System.Windows.Forms.DataGrid.DataMember%2A> de réinitialiser <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> les propriétés et les propriétés (séparément, ou par la méthode), ou la propriété n’aura aucun effet.<br /><br /> La propriété ne peut pas être réglée à une valeur inférieure à 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|La hauteur de la ligne (en pixels) des rangées dans la grille. Définissez cette propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> avant <xref:System.Windows.Forms.DataGrid.DataMember%2A> de réinitialiser <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> les propriétés et les propriétés (séparément, ou par la méthode), ou la propriété n’aura aucun effet.<br /><br /> La propriété ne peut pas être réglée à une valeur inférieure à 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|La largeur des en-têtes de la ligne de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Lorsqu’une ligne ou une cellule est sélectionnée, c’est la couleur de fond.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Lorsqu’une ligne ou une cellule est sélectionnée, c’est la couleur du premier plan.|  
  
    > [!NOTE]
    > Gardez à l’esprit, lors de la personnalisation des couleurs des commandes, qu’il est possible de rendre le contrôle inaccessible, en raison d’un mauvais choix de couleur (par exemple, rouge et vert). Utilisez les couleurs disponibles sur la palette **De couleurs système** pour éviter ce problème.  
  
     Les procédures suivantes supposent <xref:System.Windows.Forms.DataGrid> que votre formulaire a un contrôle lié à une table de données. Pour plus d’informations, voir [Binding the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Définir le style de table et de colonne d’une table de données programmatiquement  
  
1. Créez un nouveau style de table et définissez ses propriétés.  
  
2. Créez un style de colonne et définissez ses propriétés.  
  
3. Ajoutez le style colonne à la collection de styles de colonne du style de table.  
  
4. Ajoutez le style de table à la collection de styles de table de la grille de données.  
  
5. Dans l’exemple ci-dessous, <xref:System.Windows.Forms.DataGridTableStyle> créez un <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> exemple de nouveau et définissez sa propriété.  
  
6. Créez une nouvelle instance d’un **GridColumnStyle** et définissez son **MappingName** (et d’autres propriétés de mise en page et d’affichage).  
  
7. Répétez les étapes 2 à 6 pour chaque style de colonne que vous souhaitez créer.  
  
     L’exemple suivant illustre <xref:System.Windows.Forms.DataGridTextBoxColumn> comment un est créé, parce qu’un nom doit être affiché dans la colonne. En outre, vous ajoutez <xref:System.Windows.Forms.GridColumnStylesCollection> le style de colonne au style de <xref:System.Windows.Forms.GridTableStylesCollection> table, et vous ajoutez le style de table à la grille de données.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
