---
title: 'Procédure pas à pas : Requête et modèle objet simples (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: 9bf97263bf8ae0ac3ece187e81a51edfaef48a54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742582"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a>Procédure pas à pas : Requête et modèle objet simples (Visual Basic)
Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel de complexité minimale. Vous allez créer une classe d'entité qui modélise la table Customers dans l'exemple de base de données Northwind. Vous créerez ensuite une requête simple pour répertorier les clients localisés à Londres.  
  
 Cette procédure pas à pas est orientée code en termes de conception pour permettre l'affichage des concepts [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Normal, vous utiliseriez le concepteur objet/relationnel pour créer votre modèle objet.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.  
  
## <a name="prerequisites"></a>Prérequis  
  
- Les fichiers sont stockés dans un dossier dédié, c:\linqtest. Vous devez créer ce dossier avant de commencer la procédure pas à pas.  
  
- Cette procédure pas à pas requiert l'exemple de base de données Northwind. Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Après avoir téléchargé la base de données, copiez le fichier dans le dossier c:\linqtest.  
  
## <a name="overview"></a>Présentation  
 Cette procédure pas à pas se compose de six tâches principales :  
  
- Création d’un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution dans Visual Studio.  
  
- Mappage d'une classe à une table de base de données.  
  
- Désignation de propriétés sur la classe pour représenter des colonnes de base de données.  
  
- Spécification de la connexion à la base de données Northwind.  
  
- Création d'une requête simple à exécuter sur la base de données.  
  
- Exécution de la requête et observation des résultats.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Création d'une solution LINQ to SQL  
 Dans cette première tâche, vous créez une solution Visual Studio qui contient les références nécessaires pour générer et exécuter un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projet.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Pour créer une solution LINQ to SQL  
  
1. Dans le menu **Fichier**, cliquez sur **Nouveau projet**.  
  
2. Dans le **types de projets** volet de la **nouveau projet** boîte de dialogue, cliquez sur **Visual Basic**.  
  
3. Dans le volet **Modèles**, cliquez sur **Application console**.  
  
4. Dans le **nom** , tapez **LinqConsoleApp**.  
  
5. Cliquez sur **OK**.  
  
## <a name="adding-linq-references-and-directives"></a>Ajout de références et de directives LINQ  
 Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet. Si `System.Data.Linq` n’est pas répertorié en tant que référence dans votre projet (cliquez sur **afficher tous les fichiers** dans **l’Explorateur de solutions** et développez le **références** nœud), ajoutez-le comme expliqué dans les étapes suivantes.  
  
#### <a name="to-add-systemdatalinq"></a>Pour ajouter System.Data.Linq  
  
1. Dans **l’Explorateur de solutions**, avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.  
  
2. Dans le **ajouter une référence** boîte de dialogue, cliquez sur **.NET**et cliquez sur l’assembly System.Data.Linq, puis cliquez sur **OK**.  
  
     L'assembly est ajouté au projet.  
  
3. Également dans le **ajouter une référence** boîte de dialogue, cliquez sur **.NET**, faites défiler vers et cliquez sur System.Windows.Forms, puis cliquez sur **OK**.  
  
     Cet assembly qui prend en charge le message dans la procédure pas à pas est ajouté au projet.  
  
4. Ajoutez les directives suivantes au-dessus de `Module1` :  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a>Mappage d'une classe à une table de base de données  
 Au cours de cette étape, vous allez créer une classe et la mapper à une table de base de données. Une telle classe est appelée un *classe d’entité*. Notez que le mappage s'effectue simplement en ajoutant l'attribut <xref:System.Data.Linq.Mapping.TableAttribute>. La propriété <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> spécifie le nom de la table dans la base de données.  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Pour créer une classe d'entité et la mapper à une table de base de données  
  
- Tapez ou collez immédiatement le code suivant dans Module1.vb au-dessus de `Sub Main` :  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Désignation de propriétés sur la classe pour représenter des colonnes de base de données  
 Au cours de cette étape, vous allez effectuer plusieurs tâches.  
  
- Utilisez l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> pour désigner les propriétés `CustomerID` et `City` sur la classe d'entité comme représentant des colonnes de la table de base de données.  
  
- Désignez la propriété `CustomerID` comme représentant une colonne de clé primaire dans la base de données.  
  
- Désignez les champs `_CustomerID` et `_City` pour le stockage privé. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] peut ensuite stocker et récupérer directement des valeurs, au lieu d'utiliser des accesseurs publics qui peuvent inclure la logique métier.  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a>Pour représenter les caractéristiques de deux colonnes de base de données  
  
- Tapez ou collez le code suivant dans Module1.vb juste avant `End Class` :  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a>Spécification de la connexion à la base de données Northwind  
 Au cours de cette étape, vous allez utiliser un objet <xref:System.Data.Linq.DataContext> pour établir une connexion entre vos structures de données basées sur du code et la base de données elle-même. Le <xref:System.Data.Linq.DataContext> est le canal principal par le biais duquel vous récupérez des objets de la base de données et soumettez des modifications.  
  
 Déclarez également un `Table(Of Customer)` comme jouant le rôle de table typée logique pour vos requêtes sur la table Customers dans la base de données. La création et l'exécution de ces requêtes s'effectueront dans des étapes ultérieures.  
  
#### <a name="to-specify-the-database-connection"></a>Pour spécifier la connexion de base de données  
  
- Tapez ou collez le code suivant dans la méthode `Sub Main` :  
  
     Notez que le fichier `northwnd.mdf` est censé se trouver dans le dossier linqtest. Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a>Création d'une requête simple  
 Au cours de cette étape, vous allez créer une requête pour rechercher les clients localisés à Londres dans la table Customers de la base de données. Le code de requête de cette étape décrit simplement la requête. Il ne l'exécute pas. Cette approche est appelée *exécution différée*. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Vous produirez également une sortie de journal pour afficher les commandes SQL générées par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Cette fonctionnalité d’enregistrement (qui utilise <xref:System.Data.Linq.DataContext.Log%2A>) est utile pour le débogage et pour déterminer que les commandes envoyées à la base de données représentent précisément votre requête.  
  
#### <a name="to-create-a-simple-query"></a>Pour créer une requête simple  
  
- Tapez ou collez le code suivant dans la méthode `Sub Main` après la déclaration `Table(Of Customer)` :  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a>Exécution de la requête  
 Dans cette étape, vous allez exécuter la requête. Les expressions de requête créées au cours des étapes précédentes ne sont pas évaluées tant que les résultats ne sont pas nécessaires. Lorsque vous commencez l'itération `For Each`, une commande SQL est exécutée sur la base de données et les objets sont matérialisés.  
  
#### <a name="to-execute-the-query"></a>Pour exécuter la requête  
  
1. Tapez ou collez le code suivant à la fin de la méthode `Sub Main` (après la description de la requête) :  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2. Appuyez sur F5 pour déboguer l'application.  
  
    > [!NOTE]
    >  Si votre application génère une erreur d’exécution, consultez la section de résolution des problèmes de [apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     Le message affiche une liste de six clients. La fenêtre de console affiche le code SQL généré.  
  
3. Cliquez sur **OK** pour fermer la boîte de message.  
  
     L'application se ferme.  
  
4. Dans le menu **Fichier**, cliquez sur **Enregistrer tout**.  
  
     Vous aurez besoin de cette application si vous passez à la procédure pas à pas suivante.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Le [procédure pas à pas : Interrogation de relations (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) rubrique continue où cette procédure pas à pas se termine. La procédure pas à pas interrogation de relations montre comment [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] peut interroger des tables, similaire à *jointures* dans une base de données relationnelle.  
  
 Si vous souhaitez suivre la procédure pas à pas Interrogation de relations, pensez à enregistrer la solution de la procédure que vous venez d'exécuter, car elle est indispensable.  
  
## <a name="see-also"></a>Voir aussi

- [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
