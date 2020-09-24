---
title: 'Procédure pas à pas : Manipulation de données (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: dbf18273e69ff0977f5d16ff179b8659865ef696
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164049"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>Procédure pas à pas : Manipulation de données (Visual Basic)

Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel pour l'ajout, la modification et la suppression de données dans une base de données. Vous utiliserez une copie de l'exemple de base de données Northwind pour ajouter un client, modifier le nom d'un client et supprimer une commande.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.  
  
## <a name="prerequisites"></a>Prérequis  

 Elle requiert les éléments suivants :  
  
- Les fichiers sont stockés dans un dossier dédié, c:\linqtest2. Vous devez créer ce dossier avant de commencer la procédure pas à pas.  
  
- Exemple de base de données Northwind.  
  
     Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md). Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\linqtest2.  
  
- Fichier de code Visual Basic généré à partir de la base de données Northwind.  
  
     Vous pouvez générer ce fichier à l’aide de l’Concepteur Objet Relationnel ou de l’outil SQLMetal. Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :  
  
     **sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**  
  
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
  
1. Dans le menu **Fichier** de Visual Studio, cliquez sur **Nouveau projet**.  
  
2. Dans le volet **types de projets** de la boîte de dialogue **nouveau projet** , cliquez sur **Visual Basic**.  
  
3. Dans le volet **Modèles**, cliquez sur **Application console**.  
  
4. Dans la zone **nom** , tapez **LinqDataManipulationApp**.  
  
5. Cliquez sur **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Ajout de références et de directives LINQ  

 Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet. Si `System.Data.Linq` n’est pas listé comme une référence dans votre projet (cliquez sur **Afficher tous les fichiers** dans **Explorateur de solutions** et développez le nœud **références** ), ajoutez-le, comme expliqué dans les étapes suivantes.  
  
#### <a name="to-add-systemdatalinq"></a>Pour ajouter System.Data.Linq  
  
1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références**, puis cliquez sur **Ajouter une référence**.  
  
2. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, sur l’assembly System. Data. Linq, puis sur **OK**.  
  
     L'assembly est ajouté au projet.  
  
3. Dans l’éditeur de code, ajoutez les directives suivantes au-dessus de **Module1**:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Ajout du fichier de code Northwind au projet  

 Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind. Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Pour ajouter le fichier de code Northwind au projet  
  
1. Dans le menu **Projet** , cliquez sur **Ajouter un élément existant**.  
  
2. Dans la boîte de dialogue **Ajouter un élément existant** , accédez à c:\linqtest2\northwind.vb, puis cliquez sur **Ajouter**.  
  
     Le fichier northwind.vb est ajouté au projet.  
  
## <a name="setting-up-the-database-connection"></a>Paramétrage de la connexion de base de données  

 Commencez par tester votre connexion à la base de données. Notez en particulier que le nom de la base de données (Northwnd) ne comporte pas de caractère i. Si vous générez des erreurs au cours des étapes suivantes, examinez le fichier northwind.vb pour déterminer comment la classe partielle Northwind est orthographiée.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Pour paramétrer et tester la connexion de base de données  
  
1. Tapez ou collez le code suivant dans `Sub Main` :  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. Appuyez sur F5 pour tester l'application à ce stade.  
  
     Une fenêtre de **console** s’ouvre.  
  
     Fermez l’application en appuyant sur entrée dans la fenêtre de la **console** , ou en cliquant sur **arrêter le débogage** dans le menu **Déboguer** de Visual Studio.  
  
## <a name="creating-a-new-entity"></a>Création d'une entité  

 La création d'une entité est une opération simple. Vous pouvez créer des objets (`Customer`, par exemple) à l'aide du mot clé `New`.  
  
 Dans cette section et les suivantes, vous apporterez des modifications uniquement au cache local. Aucune modification n'est envoyée à la base de données tant que vous n'avez pas appelé <xref:System.Data.Linq.DataContext.SubmitChanges%2A> vers la fin de cette procédure pas à pas.  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Pour ajouter un nouvel objet d'entité Customer  
  
1. Créez un `Customer` en ajoutant le code suivant avant `Console.ReadLine` dans `Sub Main` :  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. Appuyez sur F5 pour déboguer la solution.  
  
     Les résultats suivants s'affichent dans la fenêtre de console :  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Notez que la nouvelle ligne n'apparaît pas dans les résultats. Les nouvelles données n'ont pas encore été soumises à la base de données.  
  
3. Appuyez sur entrée dans la fenêtre de **console** pour arrêter le débogage.  
  
## <a name="updating-an-entity"></a>Mise à jour d'une entité  

 Au cours des étapes suivantes, vous allez récupérer un objet `Customer` et modifier l'une de ses propriétés.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Pour modifier le nom d'un client  
  
- Ajoutez le code suivant au-dessus de `Console.ReadLine()` :  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Suppression d’une entité  

 Vous pouvez supprimer la première commande à l'aide du même objet Customer.  
  
 Le code suivant montre comment couper les relations entre les lignes et supprimer une ligne de la base de données.  
  
#### <a name="to-delete-a-row"></a>Pour supprimer une ligne  
  
- Ajoutez le code suivant juste au-dessus de `Console.ReadLine()` :  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Soumission des modifications à la base de données  

 La dernière étape requise pour la création, la mise à jour et la suppression d'objets consiste à soumettre les modifications à la base de données. Sans cette étape, vos modifications restent locales et n'apparaissent pas dans les résultats de requêtes.  
  
#### <a name="to-submit-changes-to-the-database"></a>Pour soumettre les modifications à la base de données  
  
1. Insérez le code suivant juste au-dessus de `Console.ReadLine` :  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. Insérez le code suivant (après `SubmitChanges`) pour afficher les effets avant/après de la soumission des modifications :  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. Appuyez sur F5 pour déboguer la solution.  
  
     La fenêtre de console se présente comme suit :  
  
    ```console
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. Appuyez sur entrée dans la fenêtre de **console** pour arrêter le débogage.  
  
> [!NOTE]
> Une fois que vous avez soumis les modifications (ajouté le nouveau client), vous ne pouvez plus exécuter cette solution telle quelle car vous ne pouvez plus ajouter le même client tel quel. Pour exécuter à nouveau la solution, modifiez la valeur de l'ID client à ajouter.  
  
## <a name="see-also"></a>Voir aussi

- [Apprentissage par les procédures pas à pas](learning-by-walkthroughs.md)
