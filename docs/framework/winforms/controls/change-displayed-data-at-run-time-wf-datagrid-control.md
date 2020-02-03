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
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="b6aea-102">Comment : modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="b6aea-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="b6aea-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="b6aea-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b6aea-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b6aea-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="b6aea-105">Une fois que vous avez créé un Windows Forms <xref:System.Windows.Forms.DataGrid> à l’aide des fonctionnalités au moment du design, vous pouvez également modifier dynamiquement les éléments de l’objet <xref:System.Data.DataSet> de la grille au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b6aea-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="b6aea-106">Il peut s’agir de modifications apportées à des valeurs individuelles de la table ou de la modification de la source de données liée au contrôle <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="b6aea-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="b6aea-107">Les modifications apportées aux valeurs individuelles sont effectuées par le biais de l’objet <xref:System.Data.DataSet>, et non du contrôle <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="b6aea-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="b6aea-108">Pour modifier des données par programmation</span><span class="sxs-lookup"><span data-stu-id="b6aea-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="b6aea-109">Spécifiez la table souhaitée à partir de l’objet <xref:System.Data.DataSet>, ainsi que la ligne et le champ souhaités de la table et définissez la cellule comme égale à la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="b6aea-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b6aea-110">Pour spécifier la première table de la <xref:System.Data.DataSet> ou la première ligne de la table, utilisez 0.</span><span class="sxs-lookup"><span data-stu-id="b6aea-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="b6aea-111">L’exemple suivant montre comment modifier la deuxième entrée de la première ligne de la première table d’un jeu de données en cliquant sur `Button1`.</span><span class="sxs-lookup"><span data-stu-id="b6aea-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="b6aea-112">Les tables <xref:System.Data.DataSet> (`ds`) et (`0` et `1`) ont été créées précédemment.</span><span class="sxs-lookup"><span data-stu-id="b6aea-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="b6aea-113">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="b6aea-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="b6aea-114">Au moment de l’exécution, vous pouvez utiliser la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> pour lier le contrôle <xref:System.Windows.Forms.DataGrid> à une source de données différente.</span><span class="sxs-lookup"><span data-stu-id="b6aea-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="b6aea-115">Par exemple, vous pouvez avoir plusieurs contrôles de données ADO.NET, chacun connectés à une base de données différente.</span><span class="sxs-lookup"><span data-stu-id="b6aea-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="b6aea-116">Pour modifier la source de source par programmation</span><span class="sxs-lookup"><span data-stu-id="b6aea-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="b6aea-117">Définissez la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> sur le nom de la source de données et de la table avec laquelle vous souhaitez effectuer la liaison.</span><span class="sxs-lookup"><span data-stu-id="b6aea-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="b6aea-118">L’exemple suivant montre comment modifier la source de date à l’aide de la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> pour un contrôle de données ADO.NET (adoPubsAuthors) connecté à la table authors de la base de données pubs.</span><span class="sxs-lookup"><span data-stu-id="b6aea-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6aea-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6aea-119">See also</span></span>

- [<span data-ttu-id="b6aea-120">DataSets ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6aea-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="b6aea-121">Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b6aea-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="b6aea-122">Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b6aea-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="b6aea-123">Guide pratique pour lier le contrôle DataGrid Windows Forms à une source de données</span><span class="sxs-lookup"><span data-stu-id="b6aea-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
