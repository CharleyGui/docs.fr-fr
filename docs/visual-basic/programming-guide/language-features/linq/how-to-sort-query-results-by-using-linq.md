---
title: 'Guide pratique : trier les résultats d’une requête à l’aide de LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
ms.openlocfilehash: c1bc6ab863f9de118d59e102d3d5d251d326f497
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404937"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a>Comment : trier les résultats d'une requête à l'aide de LINQ (Visual Basic)
LINQ (Language-Integrated Query) facilite l’accès aux informations de la base de données et à l’exécution des requêtes.  
  
 L’exemple suivant montre comment créer une application qui exécute des requêtes sur une base de données SQL Server et trie les résultats en fonction de plusieurs champs à l’aide de la `Order By` clause. L’ordre de tri de chaque champ peut être ordre croissant ou décroissant. Pour plus d’informations, consultez [clause ORDER BY](../../../language-reference/queries/order-by-clause.md).  
  
 Les exemples de cette rubrique utilisent l’exemple de base de données Northwind. Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du Centre de téléchargement Microsoft. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Pour créer une connexion à une base de données  
  
1. Dans Visual Studio, ouvrez **Explorateur de serveurs** / **Explorateur de base de données** en cliquant sur **Explorateur de serveurs** / **Explorateur de base de données** dans le menu **affichage** .  
  
2. Cliquez avec le bouton droit sur **connexions de données** dans **Explorateur de serveurs** / **Explorateur de base de données** puis cliquez sur **Ajouter une connexion**.  
  
3. Spécifiez une connexion valide à l’exemple de base de données Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Pour ajouter un projet qui contient un fichier LINQ to SQL  
  
1. Dans Visual Studio, dans le menu **fichier** , pointez sur **nouveau** , puis cliquez sur **projet**. Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.  
  
2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**. Sélectionnez le modèle d’élément **Classes LINQ to SQL** .  
  
3. Nommez le fichier `northwind.dbml`. Cliquez sur **Add**. Le Concepteur Objet Relationnel (Concepteur O/R) est ouvert pour le fichier Northwind. dbml.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Pour ajouter des tables à interroger dans le Concepteur O/R  
  
1. Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez la connexion à la base de données Northwind. Développez le dossier **Tables** .  
  
     Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier Northwind. dbml que vous avez ajouté précédemment.  
  
2. Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur. Cliquez sur la table Orders et faites-la glisser vers le volet gauche du concepteur.  
  
     Le concepteur crée `Customer` de nouveaux `Order` objets et pour votre projet. Notez que le concepteur détecte automatiquement les relations entre les tables et crée des propriétés enfants pour les objets connexes. Par exemple, IntelliSense indique que l' `Customer` objet a une `Orders` propriété pour toutes les commandes associées à ce client.  
  
3. Enregistrez vos modifications et fermez le concepteur.  
  
4. Enregistrez votre projet.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Pour ajouter du code pour interroger la base de données et afficher les résultats  
  
1. À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le Windows Form par défaut de votre projet, Form1.  
  
2. Double-cliquez sur Form1 pour ajouter du code à l' `Load` événement du formulaire.  
  
3. Quand vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet à votre projet. Cet objet contient le code dont vous devez disposer pour accéder à ces tables et pour accéder à des objets et des collections individuels pour chaque table. L' <xref:System.Data.Linq.DataContext> objet de votre projet est nommé en fonction du nom de votre fichier. dbml. Pour ce projet, l' <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext` .  
  
     Vous pouvez créer une instance de <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.  
  
     Ajoutez le code suivant à l' `Load` événement pour interroger les tables qui sont exposées en tant que propriétés de votre contexte de données et trier les résultats. La requête trie les résultats selon le nombre de commandes client, dans l’ordre décroissant. Les clients qui ont le même nombre de commandes sont classés par nom de société dans l’ordre croissant (valeur par défaut).  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4. Appuyez sur F5 pour exécuter votre projet et afficher les résultats.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ](index.md)
- [Requêtes](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Méthode DataContext (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
