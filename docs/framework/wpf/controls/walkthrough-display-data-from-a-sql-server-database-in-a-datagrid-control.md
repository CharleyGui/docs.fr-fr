---
title: 'Procédure pas à pas : afficher des données à partir d’une base de données SQL Server dans un contrôle DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 1398d8408a0b85d6603d638312e92ba35c5e77d3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591031"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Procédure pas à pas : affichage de données d’une base de données SQL Server dans un contrôle DataGrid

Dans cette procédure pas à pas, vous extrayez des données d’une base de données SQL Server et affichez ces données dans un <xref:System.Windows.Controls.DataGrid> contrôle. Vous utilisez la Entity Framework ADO.NET pour créer les classes d’entité qui représentent les données, et utilisez LINQ pour écrire une requête qui récupère les données spécifiées à partir d’une classe d’entité.

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Visual Studio.

- Accès à une instance en cours d’exécution de SQL Server ou SQL Server Express à laquelle l’exemple de base de données AdventureWorks est attaché. Vous pouvez télécharger la base de données AdventureWorks à partir du [GitHub](https://github.com/Microsoft/sql-server-samples/releases).

## <a name="create-entity-classes"></a>Créer des classes d’entité

1. Créez un projet d’application WPF dans Visual Basic ou C#, puis nommez-le `DataGridSQLExample` .

2. Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet, pointez sur **Ajouter**, puis sélectionnez **nouvel élément**.

     La boîte de dialogue Ajouter un nouvel élément s'affiche.

3. Dans le volet Modèles installés, sélectionnez **données** et dans la liste des modèles, sélectionnez **ADO.NET Entity Data Model**.

     ![Modèle d’élément de Entity Data Model ADO.NET](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4. Nommez le fichier `AdventureWorksModel.edmx` , puis cliquez sur **Ajouter**.

     L'Assistant Entity Data Model s'affiche.

5. Dans l’écran choisir le contenu du modèle, sélectionnez le **Concepteur EF à partir de la base de données** , puis cliquez sur **suivant**.

6. Dans l’écran choisir votre connexion de données, fournissez la connexion à votre base de données AdventureWorksLT2008. Pour plus d’informations, consultez [boîte de dialogue choisir votre connexion de données](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).

    Assurez-vous que le nom est `AdventureWorksLT2008Entities` et que la case à cocher **enregistrer les paramètres de connexion de l’entité dans App. config en tant que** est activée, puis cliquez sur **suivant**.

7. Dans l’écran choisir vos objets de base de données, développez le nœud tables, puis sélectionnez les tables **Product** et **ProductCategory** .

     Vous pouvez générer des classes d’entité pour toutes les tables ; Toutefois, dans cet exemple, vous récupérez uniquement les données de ces deux tables.

     ![Sélectionner Product et ProductCategory dans les tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")

8. Cliquez sur **Terminer**.

     Les entités Product et ProductCategory sont affichées dans la Entity Designer.

     ![Modèles d'entité Product et ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")

## <a name="retrieve-and-present-the-data"></a>Récupérer et présenter les données

1. Ouvrez le fichier MainWindow. Xaml.

2. Affectez <xref:System.Windows.FrameworkElement.Width%2A> à la propriété de la valeur <xref:System.Windows.Window> 450.

3. Dans l’éditeur XAML, ajoutez la <xref:System.Windows.Controls.DataGrid> balise suivante entre `<Grid>` les `</Grid>` balises et pour ajouter un <xref:System.Windows.Controls.DataGrid> nommé `dataGrid1` .

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     ![Fenêtre avec DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")

4. Sélectionnez <xref:System.Windows.Window>.

5. À l’aide de l’Fenêtre Propriétés ou de l’éditeur XAML, créez un gestionnaire d’événements pour le <xref:System.Windows.Window> nommé `Window_Loaded` pour l' <xref:System.Windows.FrameworkElement.Loaded> événement. Pour plus d’informations, consultez [Comment : créer un gestionnaire d’événements simple](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

     L’exemple suivant montre le code XAML pour MainWindow. Xaml.

    > [!NOTE]
    > Si vous utilisez Visual Basic, dans la première ligne de MainWindow. xaml, remplacez `x:Class="DataGridSQLExample.MainWindow"` par `x:Class="MainWindow"` .

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. Ouvrez le fichier code-behind (MainWindow. Xaml. vb ou MainWindow.xaml.cs) pour le <xref:System.Windows.Window> .

7. Ajoutez le code suivant pour récupérer uniquement des valeurs spécifiques des tables jointes et définissez la <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété de <xref:System.Windows.Controls.DataGrid> sur les résultats de la requête.

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. Exécutez l'exemple.

     Vous devez voir un <xref:System.Windows.Controls.DataGrid> qui affiche des données.

     ![DataGrid avec des données de la base de données SQL](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataGrid>
