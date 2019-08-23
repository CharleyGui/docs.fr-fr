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
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="98682-102">Procédure : créer des listes maître/détails avec le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98682-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="98682-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="98682-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="98682-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="98682-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="98682-105">Si votre <xref:System.Data.DataSet> contient une série de tables associées, vous pouvez utiliser deux <xref:System.Windows.Forms.DataGrid> contrôles pour afficher les données dans un format maître/détail.</span><span class="sxs-lookup"><span data-stu-id="98682-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="98682-106">L' <xref:System.Windows.Forms.DataGrid> un est désigné comme grille principale et le second est désigné comme grille de détails.</span><span class="sxs-lookup"><span data-stu-id="98682-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="98682-107">Lorsque vous sélectionnez une entrée dans la liste principale, toutes les entrées enfants associées s’affichent dans la liste des détails.</span><span class="sxs-lookup"><span data-stu-id="98682-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="98682-108">Par exemple, si votre <xref:System.Data.DataSet> contient une table Customers et une table Orders associée, vous devez spécifier la table Customers comme grille principale et la table Orders comme grille de détails.</span><span class="sxs-lookup"><span data-stu-id="98682-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="98682-109">Lorsqu’un client est sélectionné dans la grille principale, toutes les commandes associées à ce client dans la table Orders s’affichent dans la grille de détails.</span><span class="sxs-lookup"><span data-stu-id="98682-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="98682-110">Pour définir une relation maître/détail par programme</span><span class="sxs-lookup"><span data-stu-id="98682-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="98682-111">Créez deux nouveaux <xref:System.Windows.Forms.DataGrid> contrôles et définissez leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="98682-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="98682-112">Ajoutez des tables au DataSet.</span><span class="sxs-lookup"><span data-stu-id="98682-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="98682-113">Déclarez une variable de <xref:System.Data.DataRelation> type pour représenter la relation que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="98682-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="98682-114">Instanciez la relation en spécifiant un nom pour la relation et en spécifiant la table, la colonne et l’élément qui vont lier les deux tables.</span><span class="sxs-lookup"><span data-stu-id="98682-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="98682-115">Ajoutez la relation à la <xref:System.Data.DataSet> collection de <xref:System.Data.DataSet.Relations%2A> l’objet.</span><span class="sxs-lookup"><span data-stu-id="98682-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="98682-116">Utilisez la <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode <xref:System.Windows.Forms.DataGrid> de pour lier chacune des grilles à <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="98682-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="98682-117">L’exemple suivant montre comment définir une relation maître/détail entre les tables Customers et Orders dans un ( <xref:System.Data.DataSet> `ds`) généré précédemment.</span><span class="sxs-lookup"><span data-stu-id="98682-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98682-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98682-118">See also</span></span>

- [<span data-ttu-id="98682-119">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="98682-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="98682-120">Vue d’ensemble du contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="98682-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="98682-121">Guide pratique : Lier le contrôle Windows Forms DataGrid à une source de données</span><span class="sxs-lookup"><span data-stu-id="98682-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
