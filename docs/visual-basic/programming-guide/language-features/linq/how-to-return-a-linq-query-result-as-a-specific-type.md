---
title: 'Comment : retourner un résultat de requête LINQ en tant que type spécifique'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 249c3eebaeec3d09a297fead07ab056caff1b618
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071805"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>Comment : retourner un résultat de requête LINQ en tant que type spécifique (Visual Basic)

LINQ (Language-Integrated Query) facilite l’accès aux informations de la base de données et à l’exécution des requêtes. Par défaut, les requêtes LINQ retournent une liste d’objets en tant que type anonyme. Vous pouvez également spécifier qu’une requête retourne une liste d’un type spécifique à l’aide de la `Select` clause.  
  
 L’exemple suivant montre comment créer une application qui exécute des requêtes sur une base de données SQL Server et projette les résultats sous la forme d’un type nommé spécifique. Pour plus d’informations, consultez [types anonymes](../objects-and-classes/anonymous-types.md) et [clause SELECT](../../../language-reference/queries/select-clause.md).  
  
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
  
2. Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.  
  
     Le concepteur crée un nouvel `Customer` objet pour votre projet. Vous pouvez projeter un résultat de requête en tant que `Customer` type ou en tant que type que vous créez. Cet exemple crée un nouveau type dans une procédure ultérieure et projette un résultat de requête comme ce type.  
  
3. Enregistrez vos modifications et fermez le concepteur.  
  
4. Enregistrez votre projet.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Pour ajouter du code pour interroger la base de données et afficher les résultats  
  
1. À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le Windows Form par défaut de votre projet, Form1.  
  
2. Double-cliquez sur Form1 pour modifier la classe Form1.  
  
3. Après l' `End Class` instruction de la classe Form1, ajoutez le code suivant pour créer un `CustomerInfo` type destiné à contenir les résultats de la requête pour cet exemple.  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. Quand vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet à votre projet. Cet objet contient le code dont vous devez disposer pour accéder à ces tables et pour accéder à des objets et des collections individuels pour chaque table. L' <xref:System.Data.Linq.DataContext> objet de votre projet est nommé en fonction du nom de votre fichier. dbml. Pour ce projet, l' <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext` .  
  
     Vous pouvez créer une instance de <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.  
  
     Dans l' `Load` événement de la classe Form1, ajoutez le code suivant pour interroger les tables qui sont exposées en tant que propriétés de votre contexte de données. La `Select` clause de la requête créera un nouveau `CustomerInfo` type au lieu d’un type anonyme pour chaque élément du résultat de la requête.  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. Appuyez sur F5 pour exécuter votre projet et afficher les résultats.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ](index.md)
- [Requêtes](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext, méthodes (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
