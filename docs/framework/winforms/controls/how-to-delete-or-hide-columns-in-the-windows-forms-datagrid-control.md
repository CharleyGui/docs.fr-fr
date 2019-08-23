---
title: 'Procédure : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: 70229abddb831788f521f85747db1093c941ba8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967374"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Procédure : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Vous pouvez supprimer ou masquer par programmation les colonnes du contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> à l’aide des propriétés et <xref:System.Windows.Forms.GridColumnStylesCollection> des méthodes des objets <xref:System.Windows.Forms.DataGridColumnStyle> et (qui sont membres de la <xref:System.Windows.Forms.DataGridTableStyle> classe).  
  
 Les colonnes supprimées ou masquées existent toujours dans la source de données à laquelle la grille est liée, et sont toujours accessibles par programme. Ils ne sont plus visibles dans le DataGrid.  
  
> [!NOTE]
> Si votre application n’accède pas à certaines colonnes de données et que vous ne souhaitez pas qu’elles s’affichent dans la grille de données, il n’est probablement pas nécessaire de les inclure dans la source de données en premier lieu.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Pour supprimer une colonne de la grille de contrôle DataGrid par programmation  
  
1. Dans la zone déclarations de votre formulaire, déclarez une nouvelle instance de <xref:System.Windows.Forms.DataGridTableStyle> la classe.  
  
2. Affectez <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> à la propriété la table de votre source de données à laquelle vous souhaitez appliquer le style. L’exemple suivant utilise la <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> propriété, qui est supposée être déjà définie.  
  
3. Ajoutez le nouvel <xref:System.Windows.Forms.DataGridTableStyle> objet à la collection de styles de table de DataGrid.  
  
4. Appelez la <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> méthode <xref:System.Windows.Forms.DataGrid> de<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> la collection de, en spécifiant l’index de colonne de la colonne à supprimer.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Pour masquer une colonne dans la grille de contrôle DataGrid par programmation  
  
1. Dans la zone déclarations de votre formulaire, déclarez une nouvelle instance de <xref:System.Windows.Forms.DataGridTableStyle> la classe.  
  
2. Affectez à la <xref:System.Windows.Forms.DataGridTableStyle> propriétédelavaleurdelatabledanslasourcededonnéesàlaquellevoussouhaitezappliquerlestyle.<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> L’exemple de code suivant utilise <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> la propriété, qui est supposée être déjà définie.  
  
3. Ajoutez le nouvel <xref:System.Windows.Forms.DataGridTableStyle> objet à la collection de styles de table de DataGrid.  
  
4. Masquez la colonne en affectant à sa `Width` propriété la valeur 0, en spécifiant l’index de colonne de la colonne à masquer.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Modifier les données affichées au moment de l’exécution dans le contrôle DataGrid Windows Forms](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Guide pratique : Ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
