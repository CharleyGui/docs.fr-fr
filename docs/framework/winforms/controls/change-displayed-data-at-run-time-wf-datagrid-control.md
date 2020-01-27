---
title: Modifier les données affichées au moment de l’exécution dans le contrôle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: f91e2ea01ef4a52dd649efed70319017efb8368a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740588"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Comment : modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l'exécution
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Une fois que vous avez créé un Windows Forms <xref:System.Windows.Forms.DataGrid> à l’aide des fonctionnalités au moment du design, vous pouvez également modifier dynamiquement les éléments de l’objet <xref:System.Data.DataSet> de la grille au moment de l’exécution. Il peut s’agir de modifications apportées à des valeurs individuelles de la table ou de la modification de la source de données liée au contrôle <xref:System.Windows.Forms.DataGrid>. Les modifications apportées aux valeurs individuelles sont effectuées par le biais de l’objet <xref:System.Data.DataSet>, et non du contrôle <xref:System.Windows.Forms.DataGrid>.  
  
### <a name="to-change-data-programmatically"></a>Pour modifier des données par programmation  
  
1. Spécifiez la table souhaitée à partir de l’objet <xref:System.Data.DataSet>, ainsi que la ligne et le champ souhaités de la table et définissez la cellule comme égale à la nouvelle valeur.  
  
    > [!NOTE]
    > Pour spécifier la première table de la <xref:System.Data.DataSet> ou la première ligne de la table, utilisez 0.  
  
     L’exemple suivant montre comment modifier la deuxième entrée de la première ligne de la première table d’un jeu de données en cliquant sur `Button1`. Les tables <xref:System.Data.DataSet> (`ds`) et (`0` et `1`) ont été créées précédemment.  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     (Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     Au moment de l’exécution, vous pouvez utiliser la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> pour lier le contrôle <xref:System.Windows.Forms.DataGrid> à une source de données différente. Par exemple, vous pouvez avoir plusieurs contrôles de données ADO.NET, chacun connectés à une base de données différente.  
  
### <a name="to-change-the-datasource-programmatically"></a>Pour modifier la source de source par programmation  
  
1. Définissez la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> sur le nom de la source de données et de la table avec laquelle vous souhaitez effectuer la liaison.  
  
     L’exemple suivant montre comment modifier la source de date à l’aide de la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> pour un contrôle de données ADO.NET (adoPubsAuthors) connecté à la table authors de la base de données pubs.  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [DataSets ADO.NET](../../data/adonet/ado-net-datasets.md)
- [Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Guide pratique pour lier le contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
