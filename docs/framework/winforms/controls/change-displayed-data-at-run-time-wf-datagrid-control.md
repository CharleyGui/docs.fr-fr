---
title: 'Procédure : modifier les données affichées au moment de l’exécution dans le contrôle DataGrid Windows Forms'
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
ms.openlocfilehash: ccc36d51201e63584c0345d7afaab558649adf53
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053434"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Procédure : modifier les données affichées au moment de l’exécution dans le contrôle DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Une fois que vous avez créé un formulaire Windows <xref:System.Windows.Forms.DataGrid> à l’aide des fonctionnalités au moment du design, vous pouvez également souhaiter modifier dynamiquement les éléments de la <xref:System.Data.DataSet> objet de la grille en cours d’exécution. Cela peut inclure des modifications apportées à certaines valeurs de la table ou de changer la source de données est lié à la <xref:System.Windows.Forms.DataGrid> contrôle. Les modifications apportées aux valeurs individuelles sont effectuées via le <xref:System.Data.DataSet> de l’objet, pas le <xref:System.Windows.Forms.DataGrid> contrôle.  
  
### <a name="to-change-data-programmatically"></a>Pour modifier des données par programmation  
  
1. Spécifiez la table souhaitée à partir de la <xref:System.Data.DataSet> objet et la ligne et le champ dans la table et la cellule égale à la nouvelle valeur souhaitée.  
  
    > [!NOTE]
    >  Pour spécifier la première table de la <xref:System.Data.DataSet> ou la première ligne de la table, utilisez la valeur 0.  
  
     L’exemple suivant montre comment modifier la seconde entrée de la première ligne de la première table d’un jeu de données en cliquant sur `Button1`. Le <xref:System.Data.DataSet> (`ds`) et les Tables (`0` et `1`) ont été créés précédemment.  
  
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
  
     (Visual C#, Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     À l’exécution que vous pouvez utiliser la <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode à laquelle lier le <xref:System.Windows.Forms.DataGrid> contrôle à une autre source de données. Par exemple, vous pouvez avoir plusieurs contrôles de données ADO.NET, chacune connectée à une autre base de données.  
  
### <a name="to-change-the-datasource-programmatically"></a>Pour modifier la source de données par programmation  
  
1. Définir le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (méthode) sur le nom de la source de données et la table que vous souhaitez lier à.  
  
     L’exemple suivant montre comment modifier la source de la date en utilisant le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode à un contrôle de données ADO.NET (adoPubsAuthors) qui est connecté à la table Authors dans la base de données Pubs.  
  
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
- [Guide pratique pour Supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [Guide pratique pour Ajouter des Tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [Guide pratique pour Lier le contrôle DataGrid Windows Forms à une Source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
