---
title: Lier le contrôle DataGrid à une source de données à l’aide du concepteur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: cc0a74eca40e34f06b065980d25d922b919b0c3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744089"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="fd3b0-102">Comment : lier le contrôle DataGrid Windows Forms à une source de données à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="fd3b0-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="fd3b0-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="fd3b0-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="fd3b0-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

 <span data-ttu-id="fd3b0-105">Le contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> est conçu spécifiquement pour afficher des informations à partir d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="fd3b0-106">Vous liez le contrôle au moment du design en définissant les propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A>, ou au moment de l’exécution en appelant la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="fd3b0-107">Bien que vous puissiez afficher des données provenant de diverses sources de données, les sources les plus courantes sont les jeux de données et les vues de données.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>

 <span data-ttu-id="fd3b0-108">Si la source de données est disponible au moment de la conception, par exemple, si le formulaire contient une instance d’un DataSet ou d’une vue de données, vous pouvez lier la grille à la source de données au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="fd3b0-109">Vous pouvez ensuite afficher un aperçu de ce à quoi ressemblera les données dans la grille.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-109">You can then preview what the data will look like in the grid.</span></span>

 <span data-ttu-id="fd3b0-110">Vous pouvez également lier la grille par programmation, au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="fd3b0-111">Cela est utile lorsque vous souhaitez définir une source de données en fonction des informations que vous recevez au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="fd3b0-112">Par exemple, l’application peut permettre à l’utilisateur de spécifier le nom d’une table à afficher.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="fd3b0-113">Elle est également nécessaire dans les situations où la source de données n’existe pas au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="fd3b0-114">Cela comprend les sources de données telles que les tableaux, les collections, les datasets non typés et les lecteurs de données.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>

 <span data-ttu-id="fd3b0-115">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="fd3b0-116">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fd3b0-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="fd3b0-117">Dans Visual Studio 2005, le contrôle <xref:System.Windows.Forms.DataGrid> ne se trouve pas dans la **boîte à outils** par défaut.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="fd3b0-118">Pour plus d’informations sur l’ajout de ce dernier, consultez [Comment : ajouter des éléments à la boîte à outils](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fd3b0-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="fd3b0-119">En outre, dans Visual Studio 2005, vous pouvez utiliser la fenêtre **sources de données** pour la liaison de données au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="fd3b0-120">Pour plus d’informations [, consultez lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="fd3b0-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="fd3b0-121">Pour lier des données au contrôle DataGrid à une seule table dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="fd3b0-121">To data-bind the DataGrid control to a single table in the designer</span></span>

1. <span data-ttu-id="fd3b0-122">Affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> du contrôle l’objet contenant les éléments de données avec lesquels vous souhaitez effectuer la liaison.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-122">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="fd3b0-123">Si la source de données est un DataSet, affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A> le nom de la table à lier.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-123">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>

3. <span data-ttu-id="fd3b0-124">Si la source de données est un DataSet ou une vue de données basée sur une table de DataSet, ajoutez du code au formulaire pour remplir le DataSet.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-124">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>

     <span data-ttu-id="fd3b0-125">Le code exact que vous utilisez dépend de l’emplacement où le jeu de données obtient des données.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-125">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="fd3b0-126">Si le DataSet est rempli directement à partir d’une base de données, vous appelez généralement la méthode `Fill` d’un adaptateur de données, comme dans l’exemple de code suivant, qui remplit un dataset nommé `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="fd3b0-126">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. <span data-ttu-id="fd3b0-127">Facultatif Ajoutez les styles de table et de colonne appropriés à la grille.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-127">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>

     <span data-ttu-id="fd3b0-128">S’il n’existe aucun style de table, vous verrez la table, mais avec une mise en forme minimale et une fois toutes les colonnes visibles.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-128">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="fd3b0-129">Pour lier des données le contrôle DataGrid à plusieurs tables dans un DataSet dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="fd3b0-129">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>

1. <span data-ttu-id="fd3b0-130">Affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> du contrôle l’objet contenant les éléments de données avec lesquels vous souhaitez effectuer la liaison.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-130">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="fd3b0-131">Si le DataSet contient des tables associées (autrement dit, s’il contient un objet relation), affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A> le nom de la table parente.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-131">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>

3. <span data-ttu-id="fd3b0-132">Écrivez du code pour remplir le DataSet.</span><span class="sxs-lookup"><span data-stu-id="fd3b0-132">Write code to fill the dataset.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd3b0-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd3b0-133">See also</span></span>

- [<span data-ttu-id="fd3b0-134">Vue d’ensemble du contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="fd3b0-134">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="fd3b0-135">Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd3b0-135">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="fd3b0-136">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="fd3b0-136">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="fd3b0-137">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd3b0-137">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="fd3b0-138">Accès aux données dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd3b0-138">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
