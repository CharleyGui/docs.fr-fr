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
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Vous pouvez afficher les données dans le contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> dans les tables et les colonnes en créant des objets **DataGridTableStyle** et en les ajoutant à l’objet **GridTableStylesCollection** , accessible via la propriété **TableStyles** du contrôle <xref:System.Windows.Forms.DataGrid>. Chaque style de table affiche le contenu de la table de données spécifiée dans la propriété **MappingName** de l’objet **DataGridTableStyle** . Par défaut, un style de table sans style de colonne spécifié affiche toutes les colonnes de cette table de données. Vous pouvez limiter les colonnes de la table en ajoutant des objets **DataGridColumnStyle** à l’objet **GridColumnStylesCollection** , accessible via la propriété **GridColumnStyles** de chaque objet **DataGridTableStyle** .

### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Pour ajouter une table et une colonne à un DataGrid par programmation

1. Pour afficher des données dans la table, vous devez d’abord lier le contrôle <xref:System.Windows.Forms.DataGrid> à un DataSet. Pour plus d’informations, consultez [Comment : lier le contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

    > [!CAUTION]
    > Lorsque vous spécifiez des styles de colonne par programmation, créez toujours des objets **DataGridColumnStyle** et ajoutez-les à l’objet **GridColumnStylesCollection** avant d’ajouter des objets **DataGridTableStyle** à l’objet **GridTableStylesCollection** . Lorsque vous ajoutez un objet **DataGridTableStyle** vide à la collection, les objets **DataGridColumnStyle** sont automatiquement générés pour vous. Par conséquent, une exception est levée si vous essayez d’ajouter de nouveaux objets **DataGridColumnStyle** avec des valeurs **MappingName** dupliquées à l’objet **GridColumnStylesCollection** .

2. Déclarez un nouveau style de table et définissez son nom de mappage.

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

3. Déclarez un nouveau style de colonne et définissez son nom de mappage et d’autres propriétés.

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

4. Appelez la méthode **Add** de l’objet **GridColumnStylesCollection** pour ajouter la colonne au style de table

    ```vb
    ts1.GridColumnStyles.Add(myDataCol)
    ```

    ```csharp
    ts1.GridColumnStyles.Add(myDataCol);
    ```

    ```cpp
    ts1->GridColumnStyles->Add(myDataCol);
    ```

5. Appelez la méthode **Add** de l’objet **GridTableStylesCollection** pour ajouter le style de table à la grille de données.

    ```vb
    DataGrid1.TableStyles.Add(ts1)
    ```

    ```csharp
    dataGrid1.TableStyles.Add(ts1);
    ```

    ```cpp
    dataGrid1->TableStyles->Add(ts1);
    ```

## <a name="see-also"></a>Voir aussi

- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
