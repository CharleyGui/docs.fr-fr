---
title: 'Procédure : lier le contrôle DataGrid Windows Forms à une source de données à l’aide du concepteur'
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
ms.openlocfilehash: 665a1af990aaf615c763c1c2eae508024d9de5c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917830"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Procédure : lier le contrôle DataGrid Windows Forms à une source de données à l’aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Le contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms est spécifiquement conçu pour afficher des informations à partir d’une source de données. Vous liez le contrôle au moment du design en définissant <xref:System.Windows.Forms.DataGrid.DataMember%2A> les <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriétés et, ou au moment de l' <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> exécution en appelant la méthode. Bien que vous puissiez afficher des données provenant de diverses sources de données, les sources les plus courantes sont les jeux de données et les vues de données.

 Si la source de données est disponible au moment de la conception, par exemple, si le formulaire contient une instance d’un DataSet ou d’une vue de données, vous pouvez lier la grille à la source de données au moment de la conception. Vous pouvez ensuite afficher un aperçu de ce à quoi ressemblera les données dans la grille.

 Vous pouvez également lier la grille par programmation, au moment de l’exécution. Cela est utile lorsque vous souhaitez définir une source de données en fonction des informations que vous recevez au moment de l’exécution. Par exemple, l’application peut permettre à l’utilisateur de spécifier le nom d’une table à afficher. Elle est également nécessaire dans les situations où la source de données n’existe pas au moment de la conception. Cela comprend les sources de données telles que les tableaux, les collections, les datasets non typés et les lecteurs de données.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGrid> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms. Dans Visual Studio 2005, le <xref:System.Windows.Forms.DataGrid> contrôle ne se trouve pas dans la **boîte à outils** par défaut. Pour plus d’informations sur l’ajout [de ce dernier, consultez Procédure: Ajoutez des éléments à la](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))boîte à outils. En outre, dans Visual Studio 2005, vous pouvez utiliser la fenêtre **sources de données** pour la liaison de données au moment du Design. Pour plus d’informations [, consultez lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Pour lier des données au contrôle DataGrid à une seule table dans le concepteur

1. Affectez à la <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété du contrôle l’objet contenant les éléments de données avec lesquels vous souhaitez effectuer la liaison.

2. Si la source de données est un DataSet, affectez à la <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété le nom de la table à lier.

3. Si la source de données est un DataSet ou une vue de données basée sur une table de DataSet, ajoutez du code au formulaire pour remplir le DataSet.

     Le code exact que vous utilisez dépend de l’emplacement où le jeu de données obtient des données. Si le DataSet est rempli directement à partir d’une base de données, vous `Fill` appelez généralement la méthode d’un adaptateur de données, comme dans l’exemple de code suivant, qui `DsCategories1`remplit un DataSet appelé:

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

1. Affectez à la <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété du contrôle l’objet contenant les éléments de données avec lesquels vous souhaitez effectuer la liaison.

2. Si le DataSet contient des tables associées (autrement dit, s’il contient un objet relation), affectez à la <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété le nom de la table parente.

3. Écrivez du code pour remplir le DataSet.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle DataGrid](datagrid-control-overview-windows-forms.md)
- [Guide pratique : Ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
- [Accès aux données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
