---
title: Créer des listes maîtres/détails avec le contrôle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: e8ab63d52d97a8a6e6f60da741186e3937350e1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730984"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Comment : créer des listes maîtres/détails avec le contrôle DataGrid Windows Forms
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Si votre <xref:System.Data.DataSet> contient une série de tables associées, vous pouvez utiliser deux contrôles <xref:System.Windows.Forms.DataGrid> pour afficher les données dans un format maître/détail. Un <xref:System.Windows.Forms.DataGrid> est désigné comme grille principale et le second est désigné comme grille de détails. Lorsque vous sélectionnez une entrée dans la liste principale, toutes les entrées enfants associées s’affichent dans la liste des détails. Par exemple, si votre <xref:System.Data.DataSet> contient une table Customers et une table Orders associée, vous devez spécifier la table Customers comme grille principale et la table Orders comme grille de détails. Lorsqu’un client est sélectionné dans la grille principale, toutes les commandes associées à ce client dans la table Orders s’affichent dans la grille de détails.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Pour définir une relation maître/détail par programme  
  
1. Créez deux contrôles de <xref:System.Windows.Forms.DataGrid> et définissez leurs propriétés.  
  
2. Ajoutez des tables au DataSet.  
  
3. Déclarez une variable de type <xref:System.Data.DataRelation> pour représenter la relation que vous souhaitez créer.  
  
4. Instanciez la relation en spécifiant un nom pour la relation et en spécifiant la table, la colonne et l’élément qui vont lier les deux tables.  
  
5. Ajoutez la relation à la collection de <xref:System.Data.DataSet.Relations%2A> de l’objet <xref:System.Data.DataSet>.  
  
6. Utilisez la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> de la <xref:System.Windows.Forms.DataGrid> pour lier chacune des grilles à la <xref:System.Data.DataSet>.  
  
     L’exemple suivant montre comment définir une relation maître/détail entre les tables Customers et Orders dans un <xref:System.Data.DataSet> (`ds`) généré précédemment.  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Vue d’ensemble du contrôle DataGrid](datagrid-control-overview-windows-forms.md)
- [Guide pratique pour lier le contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
