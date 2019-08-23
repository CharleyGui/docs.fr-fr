---
title: 'Procédure : Créer des listes maître/détail avec le contrôle DataGrid Windows Forms'
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
ms.openlocfilehash: f0fd95cf0cd66e9a5105c0b8ff77d8c536a5822d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914763"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Procédure : créer des listes maître/détails avec le contrôle DataGrid Windows Forms
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Si votre <xref:System.Data.DataSet> contient une série de tables associées, vous pouvez utiliser deux <xref:System.Windows.Forms.DataGrid> contrôles pour afficher les données dans un format maître/détail. L' <xref:System.Windows.Forms.DataGrid> un est désigné comme grille principale et le second est désigné comme grille de détails. Lorsque vous sélectionnez une entrée dans la liste principale, toutes les entrées enfants associées s’affichent dans la liste des détails. Par exemple, si votre <xref:System.Data.DataSet> contient une table Customers et une table Orders associée, vous devez spécifier la table Customers comme grille principale et la table Orders comme grille de détails. Lorsqu’un client est sélectionné dans la grille principale, toutes les commandes associées à ce client dans la table Orders s’affichent dans la grille de détails.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Pour définir une relation maître/détail par programme  
  
1. Créez deux nouveaux <xref:System.Windows.Forms.DataGrid> contrôles et définissez leurs propriétés.  
  
2. Ajoutez des tables au DataSet.  
  
3. Déclarez une variable de <xref:System.Data.DataRelation> type pour représenter la relation que vous souhaitez créer.  
  
4. Instanciez la relation en spécifiant un nom pour la relation et en spécifiant la table, la colonne et l’élément qui vont lier les deux tables.  
  
5. Ajoutez la relation à la <xref:System.Data.DataSet> collection de <xref:System.Data.DataSet.Relations%2A> l’objet.  
  
6. Utilisez la <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode <xref:System.Windows.Forms.DataGrid> de pour lier chacune des grilles à <xref:System.Data.DataSet>.  
  
     L’exemple suivant montre comment définir une relation maître/détail entre les tables Customers et Orders dans un ( <xref:System.Data.DataSet> `ds`) généré précédemment.  
  
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
- [Guide pratique : Lier le contrôle Windows Forms DataGrid à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
