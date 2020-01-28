---
title: Ajouter des tables et des colonnes au contrôle DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: 2db2e38c326cbcd78c58ee4fe00cd9ed20ae0e8a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747208"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="b4995-102">Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4995-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>

> [!NOTE]
> <span data-ttu-id="b4995-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="b4995-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b4995-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b4995-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

<span data-ttu-id="b4995-105">Vous pouvez afficher les données dans le contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> dans les tables et les colonnes en créant des objets **DataGridTableStyle** et en les ajoutant à l’objet **GridTableStylesCollection** , accessible via la propriété **TableStyles** du contrôle <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="b4995-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="b4995-106">Chaque style de table affiche le contenu de la table de données spécifiée dans la propriété **MappingName** de l’objet **DataGridTableStyle** .</span><span class="sxs-lookup"><span data-stu-id="b4995-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="b4995-107">Par défaut, un style de table sans style de colonne spécifié affiche toutes les colonnes de cette table de données.</span><span class="sxs-lookup"><span data-stu-id="b4995-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="b4995-108">Vous pouvez limiter les colonnes de la table en ajoutant des objets **DataGridColumnStyle** à l’objet **GridColumnStylesCollection** , accessible via la propriété **GridColumnStyles** de chaque objet **DataGridTableStyle** .</span><span class="sxs-lookup"><span data-stu-id="b4995-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="b4995-109">Pour ajouter une table et une colonne à un DataGrid par programmation</span><span class="sxs-lookup"><span data-stu-id="b4995-109">To add a table and column to a DataGrid programmatically</span></span>

1. <span data-ttu-id="b4995-110">Pour afficher des données dans la table, vous devez d’abord lier le contrôle <xref:System.Windows.Forms.DataGrid> à un DataSet.</span><span class="sxs-lookup"><span data-stu-id="b4995-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="b4995-111">Pour plus d’informations, consultez [Comment : lier le contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="b4995-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>

    > [!CAUTION]
    > <span data-ttu-id="b4995-112">Lorsque vous spécifiez des styles de colonne par programmation, créez toujours des objets **DataGridColumnStyle** et ajoutez-les à l’objet **GridColumnStylesCollection** avant d’ajouter des objets **DataGridTableStyle** à l’objet **GridTableStylesCollection** .</span><span class="sxs-lookup"><span data-stu-id="b4995-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="b4995-113">Lorsque vous ajoutez un objet **DataGridTableStyle** vide à la collection, les objets **DataGridColumnStyle** sont automatiquement générés pour vous.</span><span class="sxs-lookup"><span data-stu-id="b4995-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="b4995-114">Par conséquent, une exception est levée si vous essayez d’ajouter de nouveaux objets **DataGridColumnStyle** avec des valeurs **MappingName** dupliquées à l’objet **GridColumnStylesCollection** .</span><span class="sxs-lookup"><span data-stu-id="b4995-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>

2. <span data-ttu-id="b4995-115">Déclarez un nouveau style de table et définissez son nom de mappage.</span><span class="sxs-lookup"><span data-stu-id="b4995-115">Declare a new table style and set its mapping name.</span></span>

    ```vb
    Dim ts1 As New DataGridTableStyle()
    ts1.MappingName = "Customers"
    ```

    ```csharp
    DataGridTableStyle ts1 = new DataGridTableStyle();
    ts1.MappingName = "Customers";
    ```

    ```cpp
    DataGridTableStyle* ts1 = new DataGridTableStyle();
    ts1->MappingName = S"Customers";
    ```

3. <span data-ttu-id="b4995-116">Déclarez un nouveau style de colonne et définissez son nom de mappage et d’autres propriétés.</span><span class="sxs-lookup"><span data-stu-id="b4995-116">Declare a new column style and set its mapping name and other properties.</span></span>

    ```vb
    Dim myDataCol As New DataGridBoolColumn()
    myDataCol.HeaderText = "My New Column"
    myDataCol.MappingName = "Current"
    ```

    ```csharp
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();
    myDataCol.HeaderText = "My New Column";
    myDataCol.MappingName = "Current";
    ```

    ```cpp
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();
    myDataCol->HeaderText = "My New Column";
    myDataCol->MappingName = "Current";
    ```

4. <span data-ttu-id="b4995-117">Appelez la méthode **Add** de l’objet **GridColumnStylesCollection** pour ajouter la colonne au style de table</span><span class="sxs-lookup"><span data-stu-id="b4995-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>

    ```vb
    ts1.GridColumnStyles.Add(myDataCol)
    ```

    ```csharp
    ts1.GridColumnStyles.Add(myDataCol);
    ```

    ```cpp
    ts1->GridColumnStyles->Add(myDataCol);
    ```

5. <span data-ttu-id="b4995-118">Appelez la méthode **Add** de l’objet **GridTableStylesCollection** pour ajouter le style de table à la grille de données.</span><span class="sxs-lookup"><span data-stu-id="b4995-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>

    ```vb
    DataGrid1.TableStyles.Add(ts1)
    ```

    ```csharp
    dataGrid1.TableStyles.Add(ts1);
    ```

    ```cpp
    dataGrid1->TableStyles->Add(ts1);
    ```

## <a name="see-also"></a><span data-ttu-id="b4995-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4995-119">See also</span></span>

- [<span data-ttu-id="b4995-120">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="b4995-120">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="b4995-121">Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4995-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
