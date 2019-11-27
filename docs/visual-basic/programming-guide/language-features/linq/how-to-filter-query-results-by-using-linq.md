---
title: 'Comment : filtrer les résultats d’une requête à l’aide de LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 2ea8a852a2f012ddb25ec1198c66e09df880ff47
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344986"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>Comment : filtrer les résultats d'une requête à l'aide de LINQ (Visual Basic)

LINQ (Language-Integrated Query) facilite l’accès aux informations de la base de données et à l’exécution des requêtes.

L’exemple suivant montre comment créer une application qui effectue des requêtes sur une base de données SQL Server et filtre les résultats en fonction d’une valeur particulière à l’aide de la clause `Where`. Pour plus d’informations, consultez [Where, clause](../../../../visual-basic/language-reference/queries/where-clause.md).

Les exemples de cette rubrique utilisent l’exemple de base de données Northwind. Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du centre de téléchargement Microsoft. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a>Pour créer une connexion à une base de données

1. Dans Visual Studio, ouvrez **Explorateur de serveurs**/**Explorateur de base de données** en cliquant sur Explorateur de serveurs **/Explorateur de base de données dans le** menu **affichage** .

2. Cliquez avec le bouton droit sur **connexions de données** dans **Explorateur de serveurs**/**Explorateur de base de données** puis cliquez sur **Ajouter une connexion**.

3. Spécifiez une connexion valide à l’exemple de base de données Northwind.

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Pour ajouter un projet qui contient un fichier LINQ to SQL

1. Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**. Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.

2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**. Sélectionnez le modèle d’élément **Classes LINQ to SQL** .

3. Nommez le fichier `northwind.dbml`. Cliquez sur **Ajouter**. Le Concepteur Objet Relationnel (Concepteur O/R) s’ouvre pour le fichier Northwind. dbml.

## <a name="to-add-tables-to-query-to-the-or-designer"></a>Pour ajouter des tables à interroger dans le Concepteur O/R

1. Dans **Explorateur de serveurs**/**Explorateur de base de données**, développez la connexion à la base de données Northwind. Développez le dossier **tables** .

     Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier Northwind. dbml que vous avez ajouté précédemment.

2. Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur. Cliquez sur la table Orders et faites-la glisser vers le volet gauche du concepteur.

     Le concepteur crée de nouveaux `Customer` et `Order` objets pour votre projet. Notez que le concepteur détecte automatiquement les relations entre les tables et crée des propriétés enfants pour les objets connexes. Par exemple, IntelliSense indique que l’objet `Customer` a une propriété `Orders` pour toutes les commandes associées à ce client.

3. Enregistrez vos modifications et fermez le concepteur.

4. Enregistrez votre projet.

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Pour ajouter du code pour interroger la base de données et afficher les résultats

1. À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.DataGridView> sur le Windows Form par défaut de votre projet, Form1.

2. Double-cliquez sur Form1 pour ajouter du code à l’événement `Load` du formulaire.

3. Quand vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un objet <xref:System.Data.Linq.DataContext> pour votre projet. Cet objet contient le code dont vous devez disposer pour accéder à ces tables, en plus des objets et des collections individuels pour chaque table. L’objet <xref:System.Data.Linq.DataContext> de votre projet est nommé en fonction du nom de votre fichier. dbml. Pour ce projet, l’objet <xref:System.Data.Linq.DataContext> est nommé `northwindDataContext`.

    Vous pouvez créer une instance du <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.

    Ajoutez le code suivant à l’événement `Load` pour interroger les tables qui sont exposées en tant que propriétés de votre contexte de données. La requête filtre les résultats et retourne uniquement les clients qui se trouvent dans `London`.

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. Appuyez sur F5 pour exécuter votre projet et afficher les résultats.

5. Voici d’autres filtres que vous pouvez essayer.

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a>Voir aussi

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Requêtes](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext, méthodes (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
