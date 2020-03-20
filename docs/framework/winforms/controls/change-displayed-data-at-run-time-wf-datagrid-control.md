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
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="8c8a3-102">Comment : modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="8c8a3-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="8c8a3-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="8c8a3-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8c8a3-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="8c8a3-105">Une fois que vous <xref:System.Windows.Forms.DataGrid> avez créé un formulaire Windows à l’aide des <xref:System.Data.DataSet> fonctionnalités de conception-temps, vous pouvez également modifier dynamiquement des éléments de l’objet de la grille au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="8c8a3-106">Cela peut inclure des modifications aux valeurs individuelles de la <xref:System.Windows.Forms.DataGrid> table ou de changer la source de données qui est liée au contrôle.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="8c8a3-107">Les changements apportés aux <xref:System.Data.DataSet> valeurs individuelles <xref:System.Windows.Forms.DataGrid> se font par l’objet, et non par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="8c8a3-108">Modifier les données programmatiquement</span><span class="sxs-lookup"><span data-stu-id="8c8a3-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="8c8a3-109">Spécifier la <xref:System.Data.DataSet> table désirée à partir de l’objet et la ligne et le champ désirés de la table et définir la cellule égale à la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8c8a3-110">Pour spécifier <xref:System.Data.DataSet> la première table de la table ou la première rangée de la table, utilisez 0.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="8c8a3-111">L’exemple suivant montre comment modifier la deuxième entrée de la première rangée `Button1`de la première table d’un jeu de données en cliquant .</span><span class="sxs-lookup"><span data-stu-id="8c8a3-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="8c8a3-112">Les <xref:System.Data.DataSet> `ds`( )`0` et `1`les tables ( et ) ont été précédemment créés.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="8c8a3-113">(Visual C, Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="8c8a3-114">Au moment de l’exécution, vous pouvez utiliser la <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode pour lier le <xref:System.Windows.Forms.DataGrid> contrôle à une source de données différente.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="8c8a3-115">Par exemple, vous pouvez avoir plusieurs contrôles de données ADO.NET, chacun connecté à une base de données différente.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="8c8a3-116">Pour modifier le programme DataSource</span><span class="sxs-lookup"><span data-stu-id="8c8a3-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="8c8a3-117">Définissez <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> la méthode au nom de la source de données et de la table vers laquelle vous souhaitez vous lier.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="8c8a3-118">L’exemple suivant montre comment modifier <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> la source de date en utilisant la méthode à un contrôle de données ADO.NET (adoPubsAuthors) qui est connecté à la table des auteurs dans la base de données Pubs.</span><span class="sxs-lookup"><span data-stu-id="8c8a3-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c8a3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c8a3-119">See also</span></span>

- [<span data-ttu-id="8c8a3-120">DataSets ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c8a3-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="8c8a3-121">Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c8a3-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="8c8a3-122">Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c8a3-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="8c8a3-123">Comment : lier le contrôle DataGrid Windows Forms à une source de données</span><span class="sxs-lookup"><span data-stu-id="8c8a3-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
