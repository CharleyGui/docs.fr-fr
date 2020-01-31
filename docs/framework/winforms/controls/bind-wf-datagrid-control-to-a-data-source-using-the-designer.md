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
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Comment : lier le contrôle DataGrid Windows Forms à une source de données à l'aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Le contrôle Windows Forms <xref:System.Windows.Forms.DataGrid> est conçu spécifiquement pour afficher des informations à partir d’une source de données. Vous liez le contrôle au moment du design en définissant les propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A>, ou au moment de l’exécution en appelant la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>. Bien que vous puissiez afficher des données provenant de diverses sources de données, les sources les plus courantes sont les jeux de données et les vues de données.

 Si la source de données est disponible au moment de la conception, par exemple, si le formulaire contient une instance d’un DataSet ou d’une vue de données, vous pouvez lier la grille à la source de données au moment de la conception. Vous pouvez ensuite afficher un aperçu de ce à quoi ressemblera les données dans la grille.

 Vous pouvez également lier la grille par programmation, au moment de l’exécution. Cela est utile lorsque vous souhaitez définir une source de données en fonction des informations que vous recevez au moment de l’exécution. Par exemple, l’application peut permettre à l’utilisateur de spécifier le nom d’une table à afficher. Elle est également nécessaire dans les situations où la source de données n’existe pas au moment de la conception. Cela comprend les sources de données telles que les tableaux, les collections, les datasets non typés et les lecteurs de données.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGrid>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md). Dans Visual Studio 2005, le contrôle <xref:System.Windows.Forms.DataGrid> ne se trouve pas dans la **boîte à outils** par défaut. Pour plus d’informations sur l’ajout de ce dernier, consultez [Comment : ajouter des éléments à la boîte à outils](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)). En outre, dans Visual Studio 2005, vous pouvez utiliser la fenêtre **sources de données** pour la liaison de données au moment du Design. Pour plus d’informations [, consultez lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Pour lier des données au contrôle DataGrid à une seule table dans le concepteur

1. Affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> du contrôle l’objet contenant les éléments de données avec lesquels vous souhaitez effectuer la liaison.

2. Si la source de données est un DataSet, affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A> le nom de la table à lier.

3. Si la source de données est un DataSet ou une vue de données basée sur une table de DataSet, ajoutez du code au formulaire pour remplir le DataSet.

     Le code exact que vous utilisez dépend de l’emplacement où le jeu de données obtient des données. Si le DataSet est rempli directement à partir d’une base de données, vous appelez généralement la méthode `Fill` d’un adaptateur de données, comme dans l’exemple de code suivant, qui remplit un dataset nommé `DsCategories1`:

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. Facultatif Ajoutez les styles de table et de colonne appropriés à la grille.

     S’il n’existe aucun style de table, vous verrez la table, mais avec une mise en forme minimale et une fois toutes les colonnes visibles.

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Pour lier des données le contrôle DataGrid à plusieurs tables dans un DataSet dans le concepteur

1. Affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A> du contrôle l’objet contenant les éléments de données avec lesquels vous souhaitez effectuer la liaison.

2. Si le DataSet contient des tables associées (autrement dit, s’il contient un objet relation), affectez à la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A> le nom de la table parente.

3. Écrivez du code pour remplir le DataSet.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle DataGrid](datagrid-control-overview-windows-forms.md)
- [Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
- [Accès aux données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
