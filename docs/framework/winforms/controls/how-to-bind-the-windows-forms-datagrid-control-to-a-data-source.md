---
title: Lier dataGrid Control à une source de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182241"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Comment : lier le contrôle DataGrid Windows Forms à une source de données
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGrid> des formulaires Windows est spécialement conçu pour afficher les informations provenant d’une source de données. Vous liez le contrôle au <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> moment de l’exécution en appelant la méthode. Bien que vous puissiez afficher des données à partir d’une variété de sources de données, les sources les plus typiques sont les ensembles de données et les vues de données.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>Pour lier les données du contrôle DataGrid programmatiquement  
  
1. Écrivez du code pour remplir l’ensemble de données.  
  
     Si la source de données est un jeu de données ou une vue de données basée sur une table de jeu de données, ajoutez du code au formulaire pour remplir le jeu de données.  
  
     Le code exact que vous utilisez dépend de l’endroit où le jeu de données reçoit des données. Si le jeu de données est peuplé directement à `Fill` partir d’une base de données, vous appelez généralement `DsCategories1`la méthode d’un adaptateur de données, comme dans l’exemple suivant, qui remplit un jeu de données appelé :  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Si le jeu de données est rempli à partir d’un service Web XML, vous créez généralement une instance du service dans votre code, puis appelez l’une de ses méthodes pour retourner un jeu de données. Vous fusionnez ensuite le jeu de données du service Web XML dans votre jeu de données local. L’exemple suivant montre comment vous pouvez créer une `CategoriesService`instance `GetCategories` d’un service Web XML appelé , `DsCategories1`appeler sa méthode, et fusionner le jeu de données résultant dans un jeu de données local appelé:  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. Appelez <xref:System.Windows.Forms.DataGrid> la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> du contrôle, en la transmettant la source de données et un membre des données. Si vous n’avez pas besoin de passer explicitement un membre de données, passez une chaîne vide.  
  
    > [!NOTE]
    > Si vous liez la grille pour la première fois, vous pouvez définir les commandes <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> les propriétés. Cependant, vous ne pouvez pas réinitialiser ces propriétés une fois qu’elles ont été définies. Par conséquent, il est recommandé <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> que vous utilisiez toujours la méthode.  
  
     L’exemple suivant montre comment vous pouvez vous lier programmatiquement à la table des clients dans un jeu de données appelé `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Si le tableau des clients est le seul tableau de l’ensemble de données, vous pouvez alternativement lier la grille de cette façon :  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. (Facultatif) Ajoutez les styles de table et les styles de colonne appropriés à la grille. S’il n’y a pas de styles de table, vous verrez la table, mais avec un formatage minimal et avec toutes les colonnes visibles.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du contrôle DataGrid](datagrid-control-overview-windows-forms.md)
- [Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
