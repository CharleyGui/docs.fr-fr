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
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="e5e1e-102">Procédure pas à pas : Utiliser BatchBlock et BatchedJoinBlock pour améliorer l’efficacité</span><span class="sxs-lookup"><span data-stu-id="e5e1e-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="e5e1e-103">La bibliothèque de flux de données TPL comporte les classes <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType>, qui permettent de recevoir et de mettre en mémoire tampon des données provenant d’une ou plusieurs sources, puis de les propager sous la forme d’une seule et même collection.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="e5e1e-104">Ce mécanisme de traitement par lot est utile pour collecter des données provenant d’une ou plusieurs sources, puis pour traiter par lot plusieurs éléments de données.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="e5e1e-105">Prenons par exemple une application qui utilise un flux de données pour insérer des enregistrements dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="e5e1e-106">Cette opération est plus efficace si plusieurs éléments sont insérés en même temps, plutôt qu’un à la fois successivement.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="e5e1e-107">Ce document explique comment utiliser la classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> afin d’améliorer l’efficacité de ces opérations d’insertion en base de données.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="e5e1e-108">Il montre également comment se servir de la classe <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> pour capturer les résultats et toutes les exceptions qui se produisent quand le programme lit des données à partir d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="e5e1e-109">Prérequis</span><span class="sxs-lookup"><span data-stu-id="e5e1e-109">Prerequisites</span></span>

1. <span data-ttu-id="e5e1e-110">Lisez la section Blocs de jointure du document [Flux de données](dataflow-task-parallel-library.md) avant de commencer cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-110">Read the Join Blocks section in the [Dataflow](dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="e5e1e-111">Vérifiez que vous disposez d’une copie de la base de données Northwind, Northwind.sdf, sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="e5e1e-112">Ce fichier se trouve généralement dans le dossier %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e5e1e-113">Dans certaines versions de Windows, il n’est pas possible de se connecter à Northwind.sdf si Visual Studio est en mode non administrateur.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="e5e1e-114">Pour vous connecter à Northwind.sdf, démarrez Visual Studio ou une invite de commandes développeur pour Visual Studio en mode **Exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="e5e1e-115">Cette procédure pas à pas contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="e5e1e-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="e5e1e-116">Créer l'application console</span><span class="sxs-lookup"><span data-stu-id="e5e1e-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="e5e1e-117">Définir la classe Employee</span><span class="sxs-lookup"><span data-stu-id="e5e1e-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="e5e1e-118">Définir des opérations de base de données Employee</span><span class="sxs-lookup"><span data-stu-id="e5e1e-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="e5e1e-119">Ajout de données d’employés à la base de données sans utilisation de la mise en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="e5e1e-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="e5e1e-120">Utiliser la mise en mémoire tampon pour ajouter des données sur les employés à la base de données</span><span class="sxs-lookup"><span data-stu-id="e5e1e-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="e5e1e-121">Utiliser la jointure en mémoire tampon pour lire des données sur les employés à partir de la base de données</span><span class="sxs-lookup"><span data-stu-id="e5e1e-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="e5e1e-122">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="e5e1e-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="e5e1e-123">Créer l'application console</span><span class="sxs-lookup"><span data-stu-id="e5e1e-123">Creating the Console Application</span></span>

1. <span data-ttu-id="e5e1e-124">Dans Visual Studio, créez un projet d' **application console** Visual C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="e5e1e-125">Dans ce document, le projet est nommé `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="e5e1e-126">Dans votre projet, ajoutez une référence à System.Data.SqlServerCe.dll et une autre à System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="e5e1e-127">Vérifiez que Form1.cs (Form1.vb pour Visual Basic) contient les instructions `using` suivantes (`Imports`en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e5e1e-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="e5e1e-128">Ajoutez les membres de données suivants à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="e5e1e-129">Définir la classe Employee</span><span class="sxs-lookup"><span data-stu-id="e5e1e-129">Defining the Employee Class</span></span>

<span data-ttu-id="e5e1e-130">Ajoutez la classe `Employee` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="e5e1e-131">La classe `Employee` contient trois propriétés : `EmployeeID`, `LastName` et `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="e5e1e-132">Elles correspondent aux colonnes `Employee ID`, `Last Name` et `First Name` de la table `Employees` dans la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="e5e1e-133">Pour cette démonstration, la classe `Employee` définit également la méthode `Random`, ce qui crée un objet `Employee` ayant des valeurs aléatoires pour propriétés.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="e5e1e-134">Définir des opérations de base de données Employee</span><span class="sxs-lookup"><span data-stu-id="e5e1e-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="e5e1e-135">Ajoutez les méthodes `InsertEmployees`, `GetEmployeeCount` et `GetEmployeeID` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="e5e1e-136">La méthode `InsertEmployees` ajoute de nouveaux enregistrements d’employés à la base de données.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="e5e1e-137">La méthode `GetEmployeeCount` récupère le nombre d’entrées de la table `Employees`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="e5e1e-138">La méthode `GetEmployeeID` extrait l’identificateur du premier employé possédant le nom indiqué.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="e5e1e-139">Chacune de ces méthodes prend une chaîne de connexion à la base de données Northwind et utilise des fonctionnalités de l’espace de noms `System.Data.SqlServerCe` pour communiquer avec la base de données.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="e5e1e-140">Ajouter des données sur les employés à la base de données sans utiliser la mise en mémoire tampon</span><span class="sxs-lookup"><span data-stu-id="e5e1e-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="e5e1e-141">Ajoutez les méthodes `AddEmployees` et `PostRandomEmployees` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="e5e1e-142">La méthode `AddEmployees` ajoute des données aléatoires sur les employés à la base de données à l’aide d’un flux de données.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="e5e1e-143">Elle crée un objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> qui appelle la méthode `InsertEmployees` pour ajouter une entrée d’employé à la base de données.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="e5e1e-144">La méthode `AddEmployees` appelle ensuite la méthode `PostRandomEmployees` pour publier plusieurs objets `Employee` sur l’objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="e5e1e-145">La méthode `AddEmployees` attend alors la fin de toutes les opérations d’insertion.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="e5e1e-146">Utiliser la mise en mémoire tampon pour ajouter des données sur les employés à la base de données</span><span class="sxs-lookup"><span data-stu-id="e5e1e-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="e5e1e-147">Ajoutez la méthode `AddEmployeesBatched` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="e5e1e-148">Cette méthode s’apparente à `AddEmployees`, sauf qu’elle utilise également la classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> pour mettre en mémoire tampon plusieurs objets `Employee` avant de les envoyer vers l’objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="e5e1e-149">Dans la mesure où la classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> propage plusieurs éléments sous forme de collection, l’objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> est modifié pour fonctionner sur un tableau d’objets `Employee`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="e5e1e-150">Comme la méthode `AddEmployees`, `AddEmployeesBatched` appelle la méthode `PostRandomEmployees` pour publier plusieurs objets `Employee`,`AddEmployeesBatched` mais cette fois sur l’objet <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="e5e1e-151">Elle `AddEmployeesBatched` attend également la fin de toutes les opérations d’insertion.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="e5e1e-152">Utiliser la jointure en mémoire tampon pour lire des données sur les employés à partir de la base de données</span><span class="sxs-lookup"><span data-stu-id="e5e1e-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="e5e1e-153">Ajoutez la méthode `GetRandomEmployees` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="e5e1e-154">Cette méthode imprime des informations sur des employés pris au hasard dans la console.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="e5e1e-155">Elle crée plusieurs objets `Employee` aléatoires et appelle la méthode `GetEmployeeID` pour récupérer l’identificateur unique de chacun d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="e5e1e-156">Étant donné que la méthode `GetEmployeeID` lève une exception si aucun employé ne correspond au prénom et au nom donnés, la méthode `GetRandomEmployees` utilise la classe <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> pour stocker des objets `Employee` pour les appels à `GetEmployeeID` qui ont abouti et des objets <xref:System.Exception?displayProperty=nameWithType> pour ceux qui ont échoué.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="e5e1e-157">L’objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> de cet exemple fonctionne sur un objet <xref:System.Tuple%602> contenant une liste d’objets `Employee` et une liste d’objets <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="e5e1e-158">L’objet <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> propage ces données lorsque le nombre total d’objets <xref:System.Exception> et `Employee` reçus est égal à la taille du lot.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="e5e1e-159">Exemple complet</span><span class="sxs-lookup"><span data-stu-id="e5e1e-159">The Complete Example</span></span>

<span data-ttu-id="e5e1e-160">L'exemple suivant montre le code complet.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-160">The following example shows the complete code.</span></span> <span data-ttu-id="e5e1e-161">La méthode `Main` compare le temps nécessaire pour effectuer des insertions en base de données par lot et sans mise en lots.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="e5e1e-162">Elle montre également l’utilisation d’une jointure en mémoire tampon pour lire des données sur les employés à partir de la base de données, et signaler les erreurs.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="e5e1e-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5e1e-163">See also</span></span>

- [<span data-ttu-id="e5e1e-164">Dataflow</span><span class="sxs-lookup"><span data-stu-id="e5e1e-164">Dataflow</span></span>](dataflow-task-parallel-library.md)
