---
title: Modifier les données affichées à l’heure d’exécution dans le contrôle DataGrid
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
ms.openlocfilehash: 6b788c10784082a0c74ee09f8cd85d540c670b84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142379"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Comment : modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l'exécution
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Une fois que vous <xref:System.Windows.Forms.DataGrid> avez créé un formulaire Windows à l’aide des <xref:System.Data.DataSet> fonctionnalités de conception-temps, vous pouvez également modifier dynamiquement des éléments de l’objet de la grille au moment de l’exécution. Cela peut inclure des modifications aux valeurs individuelles de la <xref:System.Windows.Forms.DataGrid> table ou de changer la source de données qui est liée au contrôle. Les changements apportés aux <xref:System.Data.DataSet> valeurs individuelles <xref:System.Windows.Forms.DataGrid> se font par l’objet, et non par le contrôle.  
  
### <a name="to-change-data-programmatically"></a>Modifier les données programmatiquement  
  
1. Spécifier la <xref:System.Data.DataSet> table désirée à partir de l’objet et la ligne et le champ désirés de la table et définir la cellule égale à la nouvelle valeur.  
  
    > [!NOTE]
    > Pour spécifier <xref:System.Data.DataSet> la première table de la table ou la première rangée de la table, utilisez 0.  
  
     L’exemple suivant montre comment modifier la deuxième entrée de la première rangée `Button1`de la première table d’un jeu de données en cliquant . Les <xref:System.Data.DataSet> `ds`( )`0` et `1`les tables ( et ) ont été précédemment créés.  
  
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
  
     (Visual C, Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     Au moment de l’exécution, vous pouvez utiliser la <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode pour lier le <xref:System.Windows.Forms.DataGrid> contrôle à une source de données différente. Par exemple, vous pouvez avoir plusieurs contrôles de données ADO.NET, chacun connecté à une base de données différente.  
  
### <a name="to-change-the-datasource-programmatically"></a>Pour modifier le programme DataSource  
  
1. Définissez <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> la méthode au nom de la source de données et de la table vers laquelle vous souhaitez vous lier.  
  
     L’exemple suivant montre comment modifier <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> la source de date en utilisant la méthode à un contrôle de données ADO.NET (adoPubsAuthors) qui est connecté à la table des auteurs dans la base de données Pubs.  
  
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
- [Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Comment : lier le contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
