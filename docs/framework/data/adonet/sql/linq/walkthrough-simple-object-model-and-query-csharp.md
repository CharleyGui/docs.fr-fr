---
title: 'Procédure pas à pas : requête et modèle objet simples (C#)'
description: Suivez cette procédure pas à pas pour créer une classe d’entité qui modélise une table dans un exemple de base de données. Créez ensuite une requête simple pour répertorier les clients dans un emplacement donné.
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 4637fabecc1726d8fec12857a667073912cfbed5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286299"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a>Procédure pas à pas : requête et modèle objet simples (C#)

Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel de complexité minimale. Vous allez créer une classe d'entité qui modélise la table Customers dans l'exemple de base de données Northwind. Vous créerez ensuite une requête simple pour répertorier les clients localisés à Londres.

Cette procédure pas à pas est orientée code en termes de conception pour permettre l'affichage des concepts [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. En règle générale, vous utilisez la Concepteur Objet Relationnel pour créer votre modèle objet.

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C#.

## <a name="prerequisites"></a>Prérequis

- Les fichiers sont stockés dans un dossier dédié, c:\linqtest5. Vous devez créer ce dossier avant de commencer la procédure pas à pas.

- Cette procédure pas à pas requiert l'exemple de base de données Northwind. Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft. Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md). Après avoir téléchargé la base de données, copiez le fichier dans le dossier c:\linqtest5.

## <a name="overview"></a>Vue d’ensemble

Cette procédure pas à pas se compose de six tâches principales :

- Création d’une [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution dans Visual Studio.

- Mappage d'une classe à une table de base de données.

- Désignation de propriétés sur la classe pour représenter des colonnes de base de données.

- Spécification de la connexion à la base de données Northwind.

- Création d'une requête simple à exécuter sur la base de données.

- Exécution de la requête et observation des résultats.

## <a name="creating-a-linq-to-sql-solution"></a>Création d'une solution LINQ to SQL

Dans cette première tâche, vous allez créer une solution Visual Studio qui contient les références nécessaires pour générer et exécuter un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projet.

### <a name="to-create-a-linq-to-sql-solution"></a>Pour créer une solution LINQ to SQL

1. Dans le menu **fichier** de Visual Studio, pointez sur **nouveau**, puis cliquez sur **projet**.

2. Dans le volet **types de projets** de la boîte de dialogue **nouveau projet** , cliquez sur **Visual C#**.

3. Dans le volet **Modèles**, cliquez sur **Application console**.

4. Dans la zone **nom** , tapez **LinqConsoleApp**.

5. Dans la zone **emplacement** , vérifiez l’emplacement où vous souhaitez stocker vos fichiers projet.

6. Cliquez sur **OK**.

## <a name="adding-linq-references-and-directives"></a>Ajout de références et de directives LINQ

Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet. Si System. Data. Linq n’est pas listé comme une référence dans votre projet (développez le nœud **références** dans **Explorateur de solutions**), ajoutez-le, comme expliqué dans les étapes suivantes.

### <a name="to-add-systemdatalinq"></a>Pour ajouter System.Data.Linq

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **références**, puis cliquez sur **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur **.net**, sur l’assembly System. Data. Linq, puis sur **OK**.

     L'assembly est ajouté au projet.

3. Ajoutez les directives suivantes en haut de **Program.cs**:

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a>Mappage d'une classe à une table de base de données

Au cours de cette étape, vous allez créer une classe et la mapper à une table de base de données. Une telle classe est appelée classe d' *entité*. Notez que le mappage s'effectue simplement en ajoutant l'attribut <xref:System.Data.Linq.Mapping.TableAttribute>. La propriété <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> spécifie le nom de la table dans la base de données.

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a>Pour créer une classe d'entité et la mapper à une table de base de données

- Tapez ou collez le code suivant dans Program.cs juste au-dessus de la déclaration de classe `Program` :

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a>Désignation de propriétés sur la classe pour représenter des colonnes de base de données

Au cours de cette étape, vous allez effectuer plusieurs tâches.

- Utilisez l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> pour désigner les propriétés `CustomerID` et `City` sur la classe d'entité comme représentant des colonnes de la table de base de données.

- Désignez la propriété `CustomerID` comme représentant une colonne de clé primaire dans la base de données.

- Désignez les champs `_CustomerID` et `_City` pour le stockage privé. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] peut ensuite stocker et récupérer directement des valeurs, au lieu d'utiliser des accesseurs publics qui peuvent inclure la logique métier.

### <a name="to-represent-characteristics-of-two-database-columns"></a>Pour représenter les caractéristiques de deux colonnes de base de données

- Tapez ou collez le code suivant dans Program.cs à l'intérieur des accolades pour la classe `Customer`.

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a>Spécification de la connexion à la base de données Northwind

Au cours de cette étape, vous allez utiliser un objet <xref:System.Data.Linq.DataContext> pour établir une connexion entre vos structures de données basées sur du code et la base de données elle-même. Le <xref:System.Data.Linq.DataContext> est le canal principal par le biais duquel vous récupérez des objets de la base de données et soumettez des modifications.

Déclarez également un `Table<Customer>` comme jouant le rôle de table typée logique pour vos requêtes sur la table Customers dans la base de données. La création et l'exécution de ces requêtes s'effectueront dans des étapes ultérieures.

### <a name="to-specify-the-database-connection"></a>Pour spécifier la connexion de base de données

- Tapez ou collez le code suivant dans la méthode `Main` :

     Notez que le fichier `northwnd.mdf` est censé se trouver dans le dossier linqtest5. Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a>Création d'une requête simple

Au cours de cette étape, vous allez créer une requête pour rechercher les clients localisés à Londres dans la table Customers de la base de données. Le code de requête de cette étape décrit simplement la requête. Il ne l'exécute pas. Cette approche est appelée *exécution différée*. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

Vous produirez également une sortie de journal pour afficher les commandes SQL générées par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Cette fonctionnalité d’enregistrement (qui utilise <xref:System.Data.Linq.DataContext.Log%2A>) est utile pour le débogage et pour déterminer que les commandes envoyées à la base de données représentent précisément votre requête.

### <a name="to-create-a-simple-query"></a>Pour créer une requête simple

- Tapez ou collez le code suivant dans la méthode `Main` après la déclaration `Table<Customer>` :

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a>Exécution de la requête

Dans cette étape, vous allez exécuter la requête. Les expressions de requête créées au cours des étapes précédentes ne sont pas évaluées tant que les résultats ne sont pas nécessaires. Lorsque vous commencez l'itération `foreach`, une commande SQL est exécutée sur la base de données et les objets sont matérialisés.

### <a name="to-execute-the-query"></a>Pour exécuter la requête

1. Tapez ou collez le code suivant à la fin de la méthode `Main` (après la description de la requête).

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. Appuyez sur F5 pour déboguer l'application.

    > [!NOTE]
    > Si votre application génère une erreur d’exécution, consultez la section résolution des problèmes d' [apprentissage par les procédures pas à pas](learning-by-walkthroughs.md).

     Les résultats de la requête dans la fenêtre de console doivent apparaître comme suit :

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. Appuyez sur Entrée dans la fenêtre de console pour fermer l'application.

## <a name="next-steps"></a>Étapes suivantes

La rubrique [procédure pas à pas : interrogation de relations (C#)](walkthrough-querying-across-relationships-csharp.md) continue là où cette procédure pas à pas se termine. La procédure pas à pas interroger les relations montre comment [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] peut interroger des tables, comme les *jointures* dans une base de données relationnelle.

Si vous souhaitez suivre la procédure pas à pas Interrogation de relations, pensez à enregistrer la solution de la procédure que vous venez d'exécuter car elle est indispensable.

## <a name="see-also"></a>Voir aussi

- [Apprentissage par les procédures pas à pas](learning-by-walkthroughs.md)
