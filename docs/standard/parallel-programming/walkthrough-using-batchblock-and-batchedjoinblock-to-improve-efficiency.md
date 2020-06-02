---
title: 'Procédure pas à pas : Utiliser BatchBlock et BatchedJoinBlock pour améliorer l’efficacité'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
ms.openlocfilehash: e572c5a14958ccc069ae7649af8c8ed4eb967dc1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284583"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Procédure pas à pas : Utiliser BatchBlock et BatchedJoinBlock pour améliorer l’efficacité

La bibliothèque de flux de données TPL comporte les classes <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType>, qui permettent de recevoir et de mettre en mémoire tampon des données provenant d’une ou plusieurs sources, puis de les propager sous la forme d’une seule et même collection. Ce mécanisme de traitement par lot est utile pour collecter des données provenant d’une ou plusieurs sources, puis pour traiter par lot plusieurs éléments de données. Prenons par exemple une application qui utilise un flux de données pour insérer des enregistrements dans une base de données. Cette opération est plus efficace si plusieurs éléments sont insérés en même temps, plutôt qu’un à la fois successivement. Ce document explique comment utiliser la classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> afin d’améliorer l’efficacité de ces opérations d’insertion en base de données. Il montre également comment se servir de la classe <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> pour capturer les résultats et toutes les exceptions qui se produisent quand le programme lit des données à partir d’une base de données.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>Prérequis

1. Lisez la section Blocs de jointure du document [Flux de données](dataflow-task-parallel-library.md) avant de commencer cette procédure pas à pas.

2. Vérifiez que vous disposez d’une copie de la base de données Northwind, Northwind.sdf, sur votre ordinateur. Ce fichier se trouve généralement dans le dossier %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.

    > [!IMPORTANT]
    > Dans certaines versions de Windows, il n’est pas possible de se connecter à Northwind.sdf si Visual Studio est en mode non administrateur. Pour vous connecter à Northwind.sdf, démarrez Visual Studio ou une invite de commandes développeur pour Visual Studio en mode **Exécuter en tant qu’administrateur**.

Cette procédure pas à pas contient les sections suivantes :

- [Créer l'application console](#creating)

- [Définir la classe Employee](#employeeClass)

- [Définir des opérations de base de données Employee](#operations)

- [Ajout de données d’employés à la base de données sans utilisation de la mise en mémoire tampon](#nonBuffering)

- [Utiliser la mise en mémoire tampon pour ajouter des données sur les employés à la base de données](#buffering)

- [Utiliser la jointure en mémoire tampon pour lire des données sur les employés à partir de la base de données](#bufferedJoin)

- [Exemple complet](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a>Créer l'application console

1. Dans Visual Studio, créez un projet d' **application console** Visual C# ou Visual Basic. Dans ce document, le projet est nommé `DataflowBatchDatabase`.

2. Dans votre projet, ajoutez une référence à System.Data.SqlServerCe.dll et une autre à System.Threading.Tasks.Dataflow.dll.

3. Vérifiez que Form1.cs (Form1.vb pour Visual Basic) contient les instructions `using` suivantes (`Imports`en Visual Basic).

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. Ajoutez les membres de données suivants à la classe `Program`.

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a>Définir la classe Employee

Ajoutez la classe `Employee` à la classe `Program`.

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

La classe `Employee` contient trois propriétés : `EmployeeID`, `LastName` et `FirstName`. Elles correspondent aux colonnes `Employee ID`, `Last Name` et `First Name` de la table `Employees` dans la base de données Northwind. Pour cette démonstration, la classe `Employee` définit également la méthode `Random`, ce qui crée un objet `Employee` ayant des valeurs aléatoires pour propriétés.

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a>Définir des opérations de base de données Employee

Ajoutez les méthodes `InsertEmployees`, `GetEmployeeCount` et `GetEmployeeID` à la classe `Program`.

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

La méthode `InsertEmployees` ajoute de nouveaux enregistrements d’employés à la base de données. La méthode `GetEmployeeCount` récupère le nombre d’entrées de la table `Employees`. La méthode `GetEmployeeID` extrait l’identificateur du premier employé possédant le nom indiqué. Chacune de ces méthodes prend une chaîne de connexion à la base de données Northwind et utilise des fonctionnalités de l’espace de noms `System.Data.SqlServerCe` pour communiquer avec la base de données.

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Ajouter des données sur les employés à la base de données sans utiliser la mise en mémoire tampon

Ajoutez les méthodes `AddEmployees` et `PostRandomEmployees` à la classe `Program`.

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

La méthode `AddEmployees` ajoute des données aléatoires sur les employés à la base de données à l’aide d’un flux de données. Elle crée un objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> qui appelle la méthode `InsertEmployees` pour ajouter une entrée d’employé à la base de données. La méthode `AddEmployees` appelle ensuite la méthode `PostRandomEmployees` pour publier plusieurs objets `Employee` sur l’objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. La méthode `AddEmployees` attend alors la fin de toutes les opérations d’insertion.

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Utiliser la mise en mémoire tampon pour ajouter des données sur les employés à la base de données

Ajoutez la méthode `AddEmployeesBatched` à la classe `Program`.

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

Cette méthode s’apparente à `AddEmployees`, sauf qu’elle utilise également la classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> pour mettre en mémoire tampon plusieurs objets `Employee` avant de les envoyer vers l’objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Dans la mesure où la classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> propage plusieurs éléments sous forme de collection, l’objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> est modifié pour fonctionner sur un tableau d’objets `Employee`. Comme la méthode `AddEmployees`, `AddEmployeesBatched` appelle la méthode `PostRandomEmployees` pour publier plusieurs objets `Employee`,`AddEmployeesBatched` mais cette fois sur l’objet <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>. Elle `AddEmployeesBatched` attend également la fin de toutes les opérations d’insertion.

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Utiliser la jointure en mémoire tampon pour lire des données sur les employés à partir de la base de données

Ajoutez la méthode `GetRandomEmployees` à la classe `Program`.

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

Cette méthode imprime des informations sur des employés pris au hasard dans la console. Elle crée plusieurs objets `Employee` aléatoires et appelle la méthode `GetEmployeeID` pour récupérer l’identificateur unique de chacun d’entre eux. Étant donné que la méthode `GetEmployeeID` lève une exception si aucun employé ne correspond au prénom et au nom donnés, la méthode `GetRandomEmployees` utilise la classe <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> pour stocker des objets `Employee` pour les appels à `GetEmployeeID` qui ont abouti et des objets <xref:System.Exception?displayProperty=nameWithType> pour ceux qui ont échoué. L’objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> de cet exemple fonctionne sur un objet <xref:System.Tuple%602> contenant une liste d’objets `Employee` et une liste d’objets <xref:System.Exception>. L’objet <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> propage ces données lorsque le nombre total d’objets <xref:System.Exception> et `Employee` reçus est égal à la taille du lot.

<a name="complete"></a>

## <a name="the-complete-example"></a>Exemple complet

L'exemple suivant montre le code complet. La méthode `Main` compare le temps nécessaire pour effectuer des insertions en base de données par lot et sans mise en lots. Elle montre également l’utilisation d’une jointure en mémoire tampon pour lire des données sur les employés à partir de la base de données, et signaler les erreurs.

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a>Voir aussi

- [Dataflow](dataflow-task-parallel-library.md)
