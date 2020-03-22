---
title: 'Guide pratique : rechercher la valeur minimale ou maximale dans un résultat de requête à l’aide de LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112360"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>Comment : rechercher la valeur minimale ou maximale dans un résultat de requête à l'aide de LINQ (Visual Basic)
La requête intégrée en langue (LINQ) facilite l’accès aux informations de base de données et exécute des requêtes.  
  
 L’exemple suivant montre comment créer une nouvelle application qui effectue des requêtes contre une base de données SQL Server. L’échantillon détermine les valeurs minimales et `Aggregate` maximales pour les résultats en utilisant les et `Group By` les clauses. Pour plus d’informations, voir [Clause globale](../../../../visual-basic/language-reference/queries/aggregate-clause.md) et [Groupe par clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Les exemples dans ce sujet utilisent la base de données de l’échantillon Northwind. Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du Centre de téléchargement Microsoft. Pour obtenir des instructions, voir [Télécharger des bases de données d’échantillons](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a>Créer une connexion à une base de données  
  
1. Dans Visual Studio, ouvrez **Server Explorer**/**Database Explorer** en cliquant sur Server **Explorer**/**Database Explorer** sur le menu **View.**  
  
2. Cliquez à droite **Data Connections** dans **Server Explorer**/**Database Explorer,** puis cliquez sur **Add Connection**.  
  
3. Spécifier une connexion valide à la base de données de l’échantillon Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Pour ajouter un projet qui contient un LINQ au fichier SQL  
  
1. Dans Visual Studio, sur le menu **Du fichier,** pointez vers **New** puis cliquez sur **Project**. Sélectionnez Visual Basic **Windows Forms Application** comme type de projet.  
  
2. Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**. Sélectionnez le modèle **d’article LINQ à SQL Classes.**  
  
3. Nommez le fichier `northwind.dbml`. Cliquez sur **Ajouter**. L’Object Relational Designer (O/R Designer) est ouvert pour le fichier northwind.dbml.  
  
## <a name="add-tables-to-query-to-the-or-designer"></a>Ajouter des tables à la requête au concepteur O/R  
  
1. Dans **Server Explorer**/**Database Explorer**, étendre la connexion à la base de données Northwind. Développez le dossier **Tables** .  
  
     Si vous avez fermé le concepteur O/R, vous pouvez le rouvrir en cliquant à deux fois sur le fichier northwind.dbml que vous avez ajouté plus tôt.  
  
2. Cliquez sur la table des clients et faites-la glisser sur la vitre gauche du concepteur. Cliquez sur la table des commandes et faites-la glisser sur la vitre gauche du concepteur.  
  
     Le designer `Customer` crée `Order` de nouveaux objets pour votre projet. Notez que le concepteur détecte automatiquement les relations entre les tables et crée des propriétés pour enfants pour les objets connexes. Par exemple, IntelliSense montrera que l’objet `Customer` a une `Orders` propriété pour toutes les commandes liées à ce client.  
  
3. Enregistrez vos modifications et fermez le concepteur.  
  
4. Enregistrez votre projet.  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a>Ajouter du code pour interroger la base de données et afficher les résultats  
  
1. Depuis la boîte à <xref:System.Windows.Forms.DataGridView> **outils,** faites glisser un contrôle sur le formulaire Windows par défaut pour votre projet, Form1.  
  
2. Double clic Form1 pour ajouter `Load` du code à l’événement du formulaire.  
  
3. Lorsque vous avez ajouté des tables au concepteur <xref:System.Data.Linq.DataContext> O/R, le concepteur a ajouté un objet pour votre projet. Cet objet contient le code que vous devez avoir pour accéder à ces tables, en plus des objets individuels et des collections pour chaque table. L’objet <xref:System.Data.Linq.DataContext> de votre projet est nommé en fonction du nom de votre fichier .dbml. Pour ce projet, l’objet <xref:System.Data.Linq.DataContext> est nommé `northwindDataContext`.  
  
     Vous pouvez créer une <xref:System.Data.Linq.DataContext> instance de l’in votre code et interroger les tables spécifiées par le concepteur O/R.  
  
     Ajoutez le code `Load` suivant à l’événement. Ce code interroge les tableaux qui sont exposés comme propriétés de votre contexte de données et détermine les valeurs minimales et maximales pour les résultats. L’échantillon `Aggregate` utilise la clause pour demander un `Group By` seul résultat, et la clause pour afficher une moyenne pour les résultats groupés.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Appuyez sur **F5** pour exécuter votre projet et voir les résultats.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Requêtes](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Méthodes DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
