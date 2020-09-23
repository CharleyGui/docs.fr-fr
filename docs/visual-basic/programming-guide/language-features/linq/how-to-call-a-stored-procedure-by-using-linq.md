---
title: 'Guide pratique : appeler une procédure stockée à l’aide de LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 7e5fecf0c4c0d3a561ec7d0c4ac03c9d9ce7f759
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075133"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Comment : appeler une procédure stockée à l'aide de LINQ (Visual Basic)

LINQ (Language-Integrated Query) facilite l’accès aux informations de la base de données, notamment les objets de base de données tels que les procédures stockées.  
  
 L’exemple suivant montre comment créer une application qui appelle une procédure stockée dans une base de données SQL Server. L’exemple montre comment appeler deux procédures stockées différentes dans la base de données. Chaque procédure retourne les résultats d’une requête. Une procédure accepte les paramètres d’entrée, et l’autre procédure n’accepte pas de paramètres.  
  
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
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Pour ajouter des procédures stockées au Concepteur O/R  
  
1. Dans **Explorateur de serveurs** / **Explorateur de base de données**, développez la connexion à la base de données Northwind. Développez le dossier **Procédures stockées** .  
  
     Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier Northwind. dbml que vous avez ajouté précédemment.  
  
2. Cliquez sur la procédure stockée **ventes par année** et faites-la glisser vers le volet droit du concepteur. Cliquez sur la procédure stockée **10 produits les plus chers** , puis faites-la glisser vers le volet droit du concepteur.  
  
3. Enregistrez vos modifications et fermez le concepteur.  
  
4. Enregistrez votre projet.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Pour ajouter du code afin d’afficher les résultats des procédures stockées  
  
1. À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le Windows Form par défaut de votre projet, Form1.  
  
2. Double-cliquez sur Form1 pour ajouter du code à l' `Load` événement.  
  
3. Quand vous avez ajouté des procédures stockées au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet pour votre projet. Cet objet contient le code dont vous devez disposer pour accéder à ces procédures. L' <xref:System.Data.Linq.DataContext> objet pour le projet est nommé en fonction du nom du fichier. dbml. Pour ce projet, l' <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext` .  
  
     Vous pouvez créer une instance de <xref:System.Data.Linq.DataContext> dans votre code et appeler les méthodes de procédure stockée spécifiées par le Concepteur O/R. Pour effectuer une liaison à l' <xref:System.Windows.Forms.DataGridView> objet, vous devrez peut-être forcer la requête à s’exécuter immédiatement en appelant la <xref:System.Linq.Enumerable.ToList%2A> méthode sur les résultats de la procédure stockée.  
  
     Ajoutez le code suivant à l' `Load` événement pour appeler l’une des procédures stockées exposées comme méthodes pour votre contexte de données.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. Appuyez sur F5 pour exécuter votre projet et afficher les résultats.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ](index.md)
- [Requêtes](../../../language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext, méthodes (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
