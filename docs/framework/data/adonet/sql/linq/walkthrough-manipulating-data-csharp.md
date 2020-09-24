---
title: 'Procédure pas à pas : Manipulation de données (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: fefbee533634ee42785c65e0265ce1e0567561b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164062"
---
# <a name="walkthrough-manipulating-data-c"></a>Procédure pas à pas : Manipulation de données (C#)

Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel pour l'ajout, la modification et la suppression de données dans une base de données. Vous utiliserez une copie de l'exemple de base de données Northwind pour ajouter un client, modifier le nom d'un client et supprimer une commande.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C#.  
  
## <a name="prerequisites"></a>Prérequis  

 Elle requiert les éléments suivants :  
  
- Les fichiers sont stockés dans un dossier dédié, c:\linqtest6. Vous devez créer ce dossier avant de commencer la procédure pas à pas.  
  
- Exemple de base de données Northwind.  
  
     Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md). Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest6.  
  
- Fichier de code C# généré à partir de la base de données Northwind.  
  
     Vous pouvez générer ce fichier à l’aide de l’Concepteur Objet Relationnel ou de l’outil SQLMetal. Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :  
  
     **sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**  
  
     Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Vue d’ensemble  

 Cette procédure pas à pas se compose de six tâches principales :  
  
- Création [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de la solution dans Visual Studio.  
  
- Ajout du fichier de code de base de données au projet.  
  
- Création d'un objet représentant un client.  
  
- Modification du nom de contact d'un client.  
  
- Suppression d'une commande.  
  
- Soumission de ces modifications à la base de données Northwind.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Création d'une solution LINQ to SQL  

 Dans cette première tâche, vous allez créer une solution Visual Studio qui contient les références nécessaires pour générer et exécuter un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projet.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Pour créer une solution LINQ to SQL  
  
1. Dans le menu **fichier** de Visual Studio, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2. Dans le volet **types de projets** de la boîte de dialogue **nouveau projet** , cliquez sur **Visual C#**.  
  
3. Dans le volet **Modèles**, cliquez sur **Application console**.  
  
4. Dans la zone **nom** , tapez **LinqDataManipulationApp**.  
  
5. Dans la zone **emplacement** , vérifiez l’emplacement où vous souhaitez stocker vos fichiers projet.  
  
6. Cliquez sur **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Ajout de références et de directives LINQ  

 Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet. Si System.Data.Linq n'est pas répertorié comme une référence dans votre projet, ajoutez-le comme indiqué dans les étapes suivantes :  
  
#### <a name="to-add-systemdatalinq"></a>Pour ajouter System.Data.Linq  
  
1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références**, puis cliquez sur **Ajouter une référence**.  
  
2. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, sur l’assembly System. Data. Linq, puis sur **OK**.  
  
     L'assembly est ajouté au projet.  
  
3. Ajoutez les directives suivantes au haut de Program.cs :  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Ajout du fichier de code Northwind au projet  

 Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind. Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Pour ajouter le fichier de code Northwind au projet  
  
1. Dans le menu **Projet** , cliquez sur **Ajouter un élément existant**.  
  
2. Dans la boîte de dialogue **Ajouter un élément existant** , accédez à c:\linqtest6\northwind.cs, puis cliquez sur **Ajouter**.  
  
     Le fichier northwind.cs est ajouté au projet.  
  
## <a name="setting-up-the-database-connection"></a>Paramétrage de la connexion de base de données  

 Commencez par tester votre connexion à la base de données. Notez en particulier que le nom de la base de données (Northwnd) ne comporte pas de caractère i. Si vous générez des erreurs au cours des étapes suivantes, examinez le fichier northwind.cs pour déterminer comment la classe partielle Northwind est orthographiée.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Pour paramétrer et tester la connexion de base de données  
  
1. Tapez ou collez le code suivant dans la méthode `Main` de la classe Program :  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. Appuyez sur F5 pour tester l'application à ce stade.  
  
     Une fenêtre de **console** s’ouvre.  
  
     Vous pouvez fermer l’application en appuyant sur entrée dans la fenêtre de **console** , ou en cliquant sur **arrêter le débogage** dans le menu **Déboguer** de Visual Studio.  
  
## <a name="creating-a-new-entity"></a>Création d'une entité  

 La création d'une entité est une opération simple. Vous pouvez créer des objets (`Customer`, par exemple) à l'aide du mot clé `new`.  
  
 Dans cette section et les suivantes, vous apporterez des modifications uniquement au cache local. Aucune modification n'est envoyée à la base de données tant que vous n'avez pas appelé <xref:System.Data.Linq.DataContext.SubmitChanges%2A> vers la fin de cette procédure pas à pas.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Pour ajouter un nouvel objet d'entité Customer  
  
1. Créez un `Customer` en ajoutant le code suivant avant `Console.ReadLine();` dans la méthode `Main` :  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. Appuyez sur F5 pour déboguer la solution.  
  
3. Appuyez sur entrée dans la fenêtre de **console** pour arrêter le débogage et poursuivez la procédure pas à pas.  
  
## <a name="updating-an-entity"></a>Mise à jour d'une entité  

 Au cours des étapes suivantes, vous allez récupérer un objet `Customer` et modifier l'une de ses propriétés.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Pour modifier le nom d'un client  
  
- Ajoutez le code suivant au-dessus de `Console.ReadLine();` :  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a>Suppression d’une entité  

 Vous pouvez supprimer la première commande à l'aide du même objet Customer.  
  
 Le code suivant montre comment couper les relations entre les lignes et supprimer une ligne de la base de données. Ajoutez le code suivant avant `Console.ReadLine` pour voir comment les objets peuvent être supprimés :  
  
#### <a name="to-delete-a-row"></a>Pour supprimer une ligne  
  
- Ajoutez le code suivant juste au-dessus de `Console.ReadLine();` :  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Soumission des modifications à la base de données  

 La dernière étape requise pour la création, la mise à jour et la suppression d'objets consiste à soumettre les modifications à la base de données. Sans cette étape, vos modifications restent locales et n'apparaissent pas dans les résultats de requêtes.  
  
#### <a name="to-submit-changes-to-the-database"></a>Pour soumettre les modifications à la base de données  
  
1. Insérez le code suivant juste au-dessus de `Console.ReadLine` :  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. Insérez le code suivant (après `SubmitChanges`) pour afficher les effets avant/après de la soumission des modifications :  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. Appuyez sur F5 pour déboguer la solution.  
  
4. Appuyez sur entrée dans la fenêtre de **console** pour fermer l’application.  
  
> [!NOTE]
> Une fois que vous avez soumis les modifications (ajouté le nouveau client), vous ne pouvez plus exécuter cette solution telle quelle. Pour l'exécuter à nouveau, modifiez le nom du client et l'ID client à ajouter.  
  
## <a name="see-also"></a>Voir aussi

- [Apprentissage par les procédures pas à pas](learning-by-walkthroughs.md)
