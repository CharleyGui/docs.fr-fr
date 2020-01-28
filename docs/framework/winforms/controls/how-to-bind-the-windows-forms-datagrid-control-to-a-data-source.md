---
title: Lier le contrôle DataGrid à une source de données
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
ms.openlocfilehash: 2634a6bd8ace36bcf7a49120162474a8c04b2b83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746688"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="da749-102">Comment : lier le contrôle DataGrid Windows Forms à une source de données</span><span class="sxs-lookup"><span data-stu-id="da749-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="da749-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="da749-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="da749-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="da749-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="da749-105">Le contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> est conçu spécifiquement pour afficher des informations à partir d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="da749-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="da749-106">Vous liez le contrôle au moment de l’exécution en appelant la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="da749-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="da749-107">Bien que vous puissiez afficher des données provenant de diverses sources de données, les sources les plus courantes sont les jeux de données et les vues de données.</span><span class="sxs-lookup"><span data-stu-id="da749-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="da749-108">Pour lier des données au contrôle DataGrid par programmation</span><span class="sxs-lookup"><span data-stu-id="da749-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="da749-109">Écrivez du code pour remplir le DataSet.</span><span class="sxs-lookup"><span data-stu-id="da749-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="da749-110">Si la source de données est un DataSet ou une vue de données basée sur une table de DataSet, ajoutez du code au formulaire pour remplir le DataSet.</span><span class="sxs-lookup"><span data-stu-id="da749-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="da749-111">Le code exact que vous utilisez dépend de l’emplacement où le jeu de données obtient des données.</span><span class="sxs-lookup"><span data-stu-id="da749-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="da749-112">Si le DataSet est rempli directement à partir d’une base de données, vous appelez généralement la méthode `Fill` d’un adaptateur de données, comme dans l’exemple suivant, qui remplit un dataset nommé `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="da749-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="da749-113">Si le jeu de données est rempli à partir d’un service Web XML, vous créez généralement une instance du service dans votre code, puis vous appelez l’une de ses méthodes pour retourner un jeu de données.</span><span class="sxs-lookup"><span data-stu-id="da749-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="da749-114">Vous fusionnez ensuite le jeu de données du service Web XML dans votre jeu de données local.</span><span class="sxs-lookup"><span data-stu-id="da749-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="da749-115">L’exemple suivant montre comment vous pouvez créer une instance d’un service Web XML appelé `CategoriesService`, appeler sa méthode `GetCategories` et fusionner le DataSet résultant dans un jeu de données local appelé `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="da749-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2. <span data-ttu-id="da749-116">Appelez la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> du contrôle <xref:System.Windows.Forms.DataGrid>, en lui transmettant la source de données et un membre de données.</span><span class="sxs-lookup"><span data-stu-id="da749-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="da749-117">Si vous n’avez pas besoin de passer explicitement un membre de données, transmettez une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="da749-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="da749-118">Si vous liez la grille pour la première fois, vous pouvez définir les propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> du contrôle.</span><span class="sxs-lookup"><span data-stu-id="da749-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="da749-119">Toutefois, vous ne pouvez pas réinitialiser ces propriétés une fois qu’elles ont été définies.</span><span class="sxs-lookup"><span data-stu-id="da749-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="da749-120">Par conséquent, il est recommandé de toujours utiliser la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="da749-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="da749-121">L’exemple suivant montre comment vous pouvez lier par programmation à la table Customers dans un DataSet appelé `DsCustomers1`:</span><span class="sxs-lookup"><span data-stu-id="da749-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="da749-122">Si la table Customers est la seule table dans le jeu de données, vous pouvez également lier la grille de cette façon :</span><span class="sxs-lookup"><span data-stu-id="da749-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="da749-123">Facultatif Ajoutez les styles de table et de colonne appropriés à la grille.</span><span class="sxs-lookup"><span data-stu-id="da749-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="da749-124">S’il n’existe aucun style de table, vous verrez la table, mais avec une mise en forme minimale et une fois toutes les colonnes visibles.</span><span class="sxs-lookup"><span data-stu-id="da749-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da749-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da749-125">See also</span></span>

- [<span data-ttu-id="da749-126">Vue d’ensemble du contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="da749-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="da749-127">Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da749-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="da749-128">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="da749-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="da749-129">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da749-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
