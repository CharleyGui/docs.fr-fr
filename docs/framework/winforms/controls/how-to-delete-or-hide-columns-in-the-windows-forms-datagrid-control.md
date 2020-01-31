---
title: Supprimer ou masquer des colonnes dans le contrôle DataGrid
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
ms.openlocfilehash: c730be934e9b978bdaf09bc7e668b4318077fba5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743298"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Vous pouvez supprimer ou masquer par programmation les colonnes du contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> à l’aide des propriétés et des méthodes des objets <xref:System.Windows.Forms.GridColumnStylesCollection> et <xref:System.Windows.Forms.DataGridColumnStyle> (qui sont membres de la classe <xref:System.Windows.Forms.DataGridTableStyle>).  
  
 Les colonnes supprimées ou masquées existent toujours dans la source de données à laquelle la grille est liée, et sont toujours accessibles par programme. Ils ne sont plus visibles dans le DataGrid.  
  
> [!NOTE]
> Si votre application n’accède pas à certaines colonnes de données et que vous ne souhaitez pas qu’elles s’affichent dans la grille de données, il n’est probablement pas nécessaire de les inclure dans la source de données en premier lieu.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Pour supprimer une colonne de la grille de contrôle DataGrid par programmation  
  
1. Dans la zone déclarations de votre formulaire, déclarez une nouvelle instance de la classe <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2. Affectez à la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> la table de votre source de données à laquelle vous souhaitez appliquer le style. L’exemple suivant utilise la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, qu’elle suppose comme étant déjà définie.  
  
3. Ajoutez le nouvel objet <xref:System.Windows.Forms.DataGridTableStyle> à la collection de styles de table de DataGrid.  
  
4. Appelez la méthode <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> de la collection de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> du <xref:System.Windows.Forms.DataGrid>, en spécifiant l’index de colonne de la colonne à supprimer.  
  
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
  
1. Dans la zone déclarations de votre formulaire, déclarez une nouvelle instance de la classe <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2. Définissez la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> du <xref:System.Windows.Forms.DataGridTableStyle> sur la table de votre source de données à laquelle vous souhaitez appliquer le style. L’exemple de code suivant utilise la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>, qu’il suppose comme étant déjà définie.  
  
3. Ajoutez le nouvel objet <xref:System.Windows.Forms.DataGridTableStyle> à la collection de styles de table de DataGrid.  
  
4. Masquez la colonne en affectant à sa propriété `Width` la valeur 0, en spécifiant l’index de colonne de la colonne à masquer.  
  
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

- [Guide pratique pour modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l’exécution](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
