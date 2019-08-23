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
ms.openlocfilehash: c7bf70a67729744f4cf96318f6b270a5ea81b812
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917727"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="068b1-102">Procédure : modifier les données affichées au moment de l’exécution dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="068b1-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="068b1-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="068b1-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="068b1-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="068b1-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="068b1-105">Une fois que vous avez créé <xref:System.Windows.Forms.DataGrid> un Windows Forms à l’aide des fonctionnalités au moment du design, vous pouvez également modifier dynamiquement <xref:System.Data.DataSet> les éléments de l’objet de la grille au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="068b1-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="068b1-106">Il peut s’agir de modifications apportées à des valeurs individuelles de la table ou de la modification <xref:System.Windows.Forms.DataGrid> de la source de données liée au contrôle.</span><span class="sxs-lookup"><span data-stu-id="068b1-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="068b1-107">Les modifications apportées aux valeurs individuelles <xref:System.Data.DataSet> sont effectuées par le <xref:System.Windows.Forms.DataGrid> biais de l’objet, et non du contrôle.</span><span class="sxs-lookup"><span data-stu-id="068b1-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="068b1-108">Pour modifier des données par programmation</span><span class="sxs-lookup"><span data-stu-id="068b1-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="068b1-109">Spécifiez la table souhaitée à <xref:System.Data.DataSet> partir de l’objet et la ligne et le champ souhaités de la table et définissez la cellule comme égale à la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="068b1-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="068b1-110">Pour spécifier la première table du <xref:System.Data.DataSet> ou de la première ligne de la table, utilisez 0.</span><span class="sxs-lookup"><span data-stu-id="068b1-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="068b1-111">L’exemple suivant montre comment modifier la deuxième entrée de la première ligne de la première table d’un jeu de données en `Button1`cliquant sur.</span><span class="sxs-lookup"><span data-stu-id="068b1-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="068b1-112">Les <xref:System.Data.DataSet> tables`ds`() et (`0` et `1`) ont été créées précédemment.</span><span class="sxs-lookup"><span data-stu-id="068b1-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="068b1-113">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="068b1-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="068b1-114">Au moment de l’exécution, vous <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> pouvez utiliser la méthode <xref:System.Windows.Forms.DataGrid> pour lier le contrôle à une source de données différente.</span><span class="sxs-lookup"><span data-stu-id="068b1-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="068b1-115">Par exemple, vous pouvez avoir plusieurs contrôles de données ADO.NET, chacun connectés à une base de données différente.</span><span class="sxs-lookup"><span data-stu-id="068b1-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="068b1-116">Pour modifier la source de source par programmation</span><span class="sxs-lookup"><span data-stu-id="068b1-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="068b1-117">Définissez la <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode sur le nom de la source de données et de la table avec laquelle vous souhaitez effectuer la liaison.</span><span class="sxs-lookup"><span data-stu-id="068b1-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="068b1-118">L’exemple suivant montre comment modifier la source de date à l' <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> aide de la méthode pour un contrôle de données ADO.net (adoPubsAuthors) qui est connecté à la table authors dans la base de données pubs.</span><span class="sxs-lookup"><span data-stu-id="068b1-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="068b1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="068b1-119">See also</span></span>

- [<span data-ttu-id="068b1-120">DataSets ADO.NET</span><span class="sxs-lookup"><span data-stu-id="068b1-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="068b1-121">Guide pratique pour Supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="068b1-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="068b1-122">Guide pratique pour Ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="068b1-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="068b1-123">Guide pratique pour Lier le contrôle Windows Forms DataGrid à une source de données</span><span class="sxs-lookup"><span data-stu-id="068b1-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
