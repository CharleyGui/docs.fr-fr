---
title: 'Procédure : mettre en forme le contrôle DataGrid Windows Forms'
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
ms.openlocfilehash: 99acef0a7b29228ddf0406352ff5a88b77294b00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966670"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Procédure : mettre en forme le contrôle DataGrid Windows Forms
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 L’application de différentes couleurs à différentes parties <xref:System.Windows.Forms.DataGrid> d’un contrôle peut aider à rendre les informations plus faciles à lire et à interpréter. La couleur peut être appliquée aux lignes et aux colonnes. Les lignes et les colonnes peuvent également être masquées ou affichées à votre convenance.  
  
 Il existe trois aspects de base de la mise <xref:System.Windows.Forms.DataGrid> en forme du contrôle. Vous pouvez définir des propriétés pour établir un style par défaut dans lequel les données sont affichées. À partir de cette base, vous pouvez personnaliser la façon dont certaines tables s’affichent au moment de l’exécution. Enfin, vous pouvez modifier les colonnes qui sont affichées dans la grille de données ainsi que les couleurs et autres mises en forme affichées.  
  
 En guise d’étape initiale dans la mise en forme d’une grille de données, vous <xref:System.Windows.Forms.DataGrid> pouvez définir les propriétés du lui-même. Ces options de couleur et de format forment une base à partir de laquelle vous pouvez apporter des modifications en fonction des tables de données et des colonnes affichées.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Pour établir un style par défaut pour le contrôle DataGrid  
  
1. Définissez les propriétés suivantes comme il convient:  
  
    |Propriété|Description|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|La <xref:System.Windows.Forms.DataGrid.BackColor%2A> propriété définit la couleur des lignes paires de la grille. Lorsque vous définissez la <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> propriété sur une couleur différente, chaque autre ligne est définie sur cette nouvelle couleur (lignes 1, 3, 5, etc.).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Couleur d’arrière-plan des lignes numérotées de la grille (lignes 0, 2, 4, 6, etc.).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Tandis <xref:System.Windows.Forms.DataGrid.BackColor%2A> que <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> les propriétés et déterminent la couleur des lignes dans la <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> grille, la propriété détermine la couleur de la zone nonrow, qui est visible uniquement lorsque la grille défile vers le bas, ou si seules quelques lignes sont contenues dans grille.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Style de bordure de la grille, l’une <xref:System.Windows.Forms.BorderStyle> des valeurs d’énumération.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Couleur d’arrière-plan du titre de fenêtre de la grille qui s’affiche immédiatement au-dessus de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Police de la légende en haut de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Couleur d’arrière-plan du titre de fenêtre de la grille.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Police utilisée pour afficher le texte dans la grille.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Couleur de la police affichée par les données dans les lignes de la grille de données.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Couleur des lignes de la grille de données.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Style des lignes qui séparent les cellules de la grille, l’une des valeurs <xref:System.Windows.Forms.DataGridLineStyle> d’énumération.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Couleur d’arrière-plan des en-têtes de ligne et de colonne.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Police utilisée pour les en-têtes de colonnes.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Couleur de premier plan des en-têtes de colonnes de la grille, y compris le texte d’en-tête de colonne et les glyphes plus/moins (pour développer les lignes quand plusieurs tables associées sont affichées).|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Couleur du texte de tous les liens de la grille de données, y compris les liens vers les tables enfants, le nom de la relation, etc.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Dans une table enfant, il s’agit de la couleur d’arrière-plan des lignes parentes.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Dans une table enfant, il s’agit de la couleur de premier plan des lignes parentes.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Détermine si les noms de table et de colonne sont affichés dans la ligne parente, au <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> moyen de l’énumération.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Largeur par défaut (en pixels) des colonnes de la grille. Définissez cette propriété avant de réinitialiser les <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriétés <xref:System.Windows.Forms.DataGrid.DataMember%2A> et (séparément ou à l’aide de <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> la méthode), sinon la propriété n’aura aucun effet.<br /><br /> La propriété ne peut pas être définie sur une valeur inférieure à 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Hauteur de ligne (en pixels) des lignes de la grille. Définissez cette propriété avant de réinitialiser les <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriétés <xref:System.Windows.Forms.DataGrid.DataMember%2A> et (séparément ou à l’aide de <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> la méthode), sinon la propriété n’aura aucun effet.<br /><br /> La propriété ne peut pas être définie sur une valeur inférieure à 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Largeur des en-têtes de lignes de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Quand une ligne ou une cellule est sélectionnée, il s’agit de la couleur d’arrière-plan.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Quand une ligne ou une cellule est sélectionnée, il s’agit de la couleur de premier plan.|  
  
    > [!NOTE]
    > N’oubliez pas, lors de la personnalisation des couleurs des contrôles, qu’il est possible de rendre le contrôle inaccessible, en raison d’un choix de couleurs médiocres (par exemple, Red et Green). Utilisez les couleurs disponibles dans la palette **couleurs système** pour éviter ce problème.  
  
     Les procédures suivantes supposent que votre formulaire <xref:System.Windows.Forms.DataGrid> possède un contrôle lié à une table de données. Pour plus d’informations, consultez [liaison du contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Pour définir par programmation le style de table et de colonne d’une table de données  
  
1. Créez un nouveau style de table et définissez ses propriétés.  
  
2. Créez un style de colonne et définissez ses propriétés.  
  
3. Ajoutez le style de colonne à la collection de styles de colonne du style de tableau.  
  
4. Ajoutez le style de tableau à la collection de styles de table de la grille de données.  
  
5. Dans l’exemple ci-dessous, créez une instance d' <xref:System.Windows.Forms.DataGridTableStyle> un nouveau et <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> définissez sa propriété.  
  
6. Créez une nouvelle instance d’un **GridColumnStyle** et définissez son **MappingName** (ainsi que d’autres propriétés de disposition et d’affichage).  
  
7. Répétez les étapes 2 à 6 pour chaque style de colonne que vous souhaitez créer.  
  
     L’exemple suivant illustre la façon dont <xref:System.Windows.Forms.DataGridTextBoxColumn> un est créé, car un nom doit être affiché dans la colonne. En outre, vous ajoutez le style de colonne au <xref:System.Windows.Forms.GridColumnStylesCollection> du style de table, et vous ajoutez le style de tableau à <xref:System.Windows.Forms.GridTableStylesCollection> la de la grille de données.  
  
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
- [Guide pratique pour Supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
