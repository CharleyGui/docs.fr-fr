---
title: Application console
description: Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: dbe64fe0a01ddab9e7a3ad0a9118b3fe59fba8aa
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656981"
---
# <a name="console-app"></a><span data-ttu-id="9c524-103">Application console</span><span class="sxs-lookup"><span data-stu-id="9c524-103">Console app</span></span>

<span data-ttu-id="9c524-104">Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#.</span><span class="sxs-lookup"><span data-stu-id="9c524-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="9c524-105">Vous apprendrez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="9c524-105">You'll learn:</span></span>

- <span data-ttu-id="9c524-106">Les principes de base du CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c524-106">The basics of the .NET Core CLI</span></span>
- <span data-ttu-id="9c524-107">La structure d’une application de console C#</span><span class="sxs-lookup"><span data-stu-id="9c524-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="9c524-108">E/S console</span><span class="sxs-lookup"><span data-stu-id="9c524-108">Console I/O</span></span>
- <span data-ttu-id="9c524-109">Les principes fondamentaux des API d’E/S de fichier dans .NET</span><span class="sxs-lookup"><span data-stu-id="9c524-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="9c524-110">Les principes fondamentaux de la programmation asynchrone basée sur des tâches dans .NET</span><span class="sxs-lookup"><span data-stu-id="9c524-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="9c524-111">Vous allez générer une application qui lit un fichier texte et renvoie le contenu de ce fichier texte sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c524-111">You'll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="9c524-112">La sortie sur la console se fait à un rythme permettant de la lire à haute voix.</span><span class="sxs-lookup"><span data-stu-id="9c524-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="9c524-113">Vous pouvez accélérer ou ralentir le rythme en appuyant sur les clés « < » (inférieure à) ou « > » (supérieur à).</span><span class="sxs-lookup"><span data-stu-id="9c524-113">You can speed up or slow down the pace by pressing the '<' (less than) or '>' (greater than) keys.</span></span>

<span data-ttu-id="9c524-114">Il existe un grand nombre de fonctionnalités dans ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="9c524-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="9c524-115">Créons-les un par un.</span><span class="sxs-lookup"><span data-stu-id="9c524-115">Let's build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9c524-116">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="9c524-116">Prerequisites</span></span>

- <span data-ttu-id="9c524-117">Configurez votre ordinateur pour exécuter .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c524-117">Set up your machine to run .NET Core.</span></span> <span data-ttu-id="9c524-118">Vous trouverez les instructions d’installation dans la page [téléchargements .net Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="9c524-118">You can find the installation instructions on the [.NET Core downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="9c524-119">Vous pouvez exécuter cette application sur Windows, Linux, macOS ou dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="9c524-119">You can run this application on Windows, Linux, macOS, or in a Docker container.</span></span>

- <span data-ttu-id="9c524-120">Installez votre éditeur de code favori.</span><span class="sxs-lookup"><span data-stu-id="9c524-120">Install your favorite code editor.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="9c524-121">Créer l’application</span><span class="sxs-lookup"><span data-stu-id="9c524-121">Create the app</span></span>

<span data-ttu-id="9c524-122">La première étape consiste à créer une nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="9c524-122">The first step is to create a new application.</span></span> <span data-ttu-id="9c524-123">Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="9c524-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="9c524-124">Réglez-le comme répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="9c524-124">Make that the current directory.</span></span> <span data-ttu-id="9c524-125">Saisissez la commande `dotnet new console` à l’invite.</span><span class="sxs-lookup"><span data-stu-id="9c524-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="9c524-126">Elle crée les fichiers de démarrage d’une application « Hello World » de base.</span><span class="sxs-lookup"><span data-stu-id="9c524-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="9c524-127">Avant de commencer à apporter des modifications, suivez les étapes pour exécuter l’application simple Hello World.</span><span class="sxs-lookup"><span data-stu-id="9c524-127">Before you start making modifications, let's go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="9c524-128">Après avoir créé l’application, saisissez `dotnet restore` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="9c524-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="9c524-129">Cette commande exécute le processus de restauration de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="9c524-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="9c524-130">NuGet est un gestionnaire de packages .NET.</span><span class="sxs-lookup"><span data-stu-id="9c524-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="9c524-131">Cette commande télécharge les dépendances manquantes pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="9c524-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="9c524-132">Comme il s’agit d’un nouveau projet, aucune des dépendances n’est en place, donc la première exécution téléchargera le framework .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c524-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="9c524-133">Après cette étape initiale, vous devrez exécuter `dotnet restore` lorsque vous ajoutez de nouveaux packages dépendants ou mettez à jour les versions de vos dépendances.</span><span class="sxs-lookup"><span data-stu-id="9c524-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="9c524-134">Après la restauration des packages, vous exécutez `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="9c524-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="9c524-135">Cela exécute le moteur de génération et crée l’exécutable de votre application.</span><span class="sxs-lookup"><span data-stu-id="9c524-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="9c524-136">Enfin, vous exécutez `dotnet run` pour lancer votre application.</span><span class="sxs-lookup"><span data-stu-id="9c524-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="9c524-137">Le code d’application Hello World simple se trouve intégralement dans le fichier Program.cs.</span><span class="sxs-lookup"><span data-stu-id="9c524-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="9c524-138">Ouvrez ce fichier avec votre éditeur de texte préféré.</span><span class="sxs-lookup"><span data-stu-id="9c524-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="9c524-139">Nous allons apporter nos premières modifications.</span><span class="sxs-lookup"><span data-stu-id="9c524-139">We're about to make our first changes.</span></span> <span data-ttu-id="9c524-140">En haut du fichier, remarquez l’instruction using :</span><span class="sxs-lookup"><span data-stu-id="9c524-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="9c524-141">Cette instruction indique au compilateur que tous les types de l’espace de noms `System` sont dans la portée.</span><span class="sxs-lookup"><span data-stu-id="9c524-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="9c524-142">Comme d’autres langages orientés objet que vous avez peut-être utilisés, C# utilise des espaces de noms pour organiser les types.</span><span class="sxs-lookup"><span data-stu-id="9c524-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="9c524-143">Ce programme Hello World ne fait pas exception.</span><span class="sxs-lookup"><span data-stu-id="9c524-143">This Hello World program is no different.</span></span> <span data-ttu-id="9c524-144">Vous pouvez voir que le programme est placé dans l’espace de noms nommé d’après le nom du répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="9c524-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="9c524-145">Pour ce tutoriel, nous changeons le nom de l’espace de noms en `TeleprompterConsole` :</span><span class="sxs-lookup"><span data-stu-id="9c524-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="9c524-146">Lecture et affichage du fichier</span><span class="sxs-lookup"><span data-stu-id="9c524-146">Reading and Echoing the File</span></span>

<span data-ttu-id="9c524-147">La première fonctionnalité à ajouter est la capacité à lire un fichier texte et à afficher tout le texte dans la console.</span><span class="sxs-lookup"><span data-stu-id="9c524-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="9c524-148">Tout d’abord, nous allons ajouter un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="9c524-148">First, let's add a text file.</span></span> <span data-ttu-id="9c524-149">Copiez le fichier [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) à partir du dépôt GitHub pour cet [exemple](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) dans votre répertoire de projet.</span><span class="sxs-lookup"><span data-stu-id="9c524-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="9c524-150">Il servira de script pour votre application.</span><span class="sxs-lookup"><span data-stu-id="9c524-150">This will serve as the script for your application.</span></span> <span data-ttu-id="9c524-151">Si vous voulez des informations sur la façon de télécharger l’exemple d’application de cette rubrique, consultez les instructions de la rubrique [Exemples et didacticiels](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="9c524-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples) topic.</span></span>

<span data-ttu-id="9c524-152">Ensuite, ajoutez la méthode suivante dans votre classe `Program` (juste en dessous de la méthode `Main`) :</span><span class="sxs-lookup"><span data-stu-id="9c524-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="9c524-153">Cette méthode utilise les types de deux nouveaux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9c524-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="9c524-154">Pour compiler, vous devez ajouter les deux lignes suivantes au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="9c524-154">For this to compile you'll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="9c524-155">L'interface <xref:System.Collections.Generic.IEnumerable%601> est définie dans l’espace de noms <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="9c524-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="9c524-156">La classe <xref:System.IO.File> est définie dans l’espace de noms <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="9c524-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="9c524-157">Cette méthode est un type spécial de méthode C# appelé *méthode d’itérateur*.</span><span class="sxs-lookup"><span data-stu-id="9c524-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="9c524-158">Les méthodes d’énumérateur retournent des séquences qui sont évaluées de manière tardive.</span><span class="sxs-lookup"><span data-stu-id="9c524-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="9c524-159">Cela signifie que chaque élément de la séquence est généré lorsque cela est demandé par le code utilisant la séquence.</span><span class="sxs-lookup"><span data-stu-id="9c524-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="9c524-160">Les méthodes d’énumérateur sont des méthodes qui contiennent une ou plusieurs [`yield return`](../language-reference/keywords/yield.md) instructions.</span><span class="sxs-lookup"><span data-stu-id="9c524-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="9c524-161">L’objet retourné par la méthode `ReadFrom` contient le code pour générer chaque élément dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="9c524-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="9c524-162">Dans cet exemple, cela implique la lecture de la ligne de texte suivante à partir du fichier source et le renvoi de cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c524-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="9c524-163">Chaque fois que le code appelant demande l’élément suivant de la séquence, le code lit la ligne suivante du texte à partir du fichier et la renvoie.</span><span class="sxs-lookup"><span data-stu-id="9c524-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="9c524-164">Quand le fichier est entièrement lu, la séquence indique qu’il n’y a pas d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="9c524-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="9c524-165">Il existe deux autres éléments de syntaxe de C# qui peuvent être nouveaux pour vous.</span><span class="sxs-lookup"><span data-stu-id="9c524-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="9c524-166">L' [`using`](../language-reference/keywords/using-statement.md) instruction dans cette méthode gère le nettoyage des ressources.</span><span class="sxs-lookup"><span data-stu-id="9c524-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="9c524-167">La variable initialisée dans l’instruction `using` (`reader`, dans cet exemple) doit implémenter l’interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="9c524-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="9c524-168">Cette interface définit une méthode unique, `Dispose`, qui doit être appelée lorsque les ressources doivent être libérées.</span><span class="sxs-lookup"><span data-stu-id="9c524-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="9c524-169">Le compilateur génère l’appel lorsque l’exécution atteint l’accolade fermante de l’instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="9c524-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="9c524-170">Le code généré par le compilateur garantit que la ressource est libérée même si une exception est levée à partir du code dans le bloc défini par l’instruction using.</span><span class="sxs-lookup"><span data-stu-id="9c524-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="9c524-171">La variable `reader` est définie à l’aide du mot-clé `var`.</span><span class="sxs-lookup"><span data-stu-id="9c524-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="9c524-172">[`var`](../language-reference/keywords/var.md) définit une *variable locale implicitement typée*.</span><span class="sxs-lookup"><span data-stu-id="9c524-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="9c524-173">Cela signifie que le type de la variable est déterminé par le type au moment de la compilation de l’objet assigné à la variable.</span><span class="sxs-lookup"><span data-stu-id="9c524-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="9c524-174">Ici, c’est la valeur retournée par la méthode <xref:System.IO.File.OpenText(System.String)>, qui est un objet <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="9c524-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="9c524-175">À présent, nous allons renseigner le code pour lire le fichier dans la `Main` méthode :</span><span class="sxs-lookup"><span data-stu-id="9c524-175">Now, let's fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="9c524-176">Exécutez le programme (à l’aide de `dotnet run`). Chaque ligne est envoyée sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c524-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="9c524-177">Ajout de délais et de mise en forme à la sortie</span><span class="sxs-lookup"><span data-stu-id="9c524-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="9c524-178">Ce que vous avez s’affiche beaucoup trop rapidement pour le lire à haute voix.</span><span class="sxs-lookup"><span data-stu-id="9c524-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="9c524-179">Vous devez maintenant ajouter des délais à la sortie.</span><span class="sxs-lookup"><span data-stu-id="9c524-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="9c524-180">Au démarrage, vous allez générer un code de base qui permet un traitement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9c524-180">As you start, you'll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="9c524-181">Toutefois, ces premières étapes suivront quelques anti-modèles.</span><span class="sxs-lookup"><span data-stu-id="9c524-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="9c524-182">Les anti-modèles sont signalés dans les commentaires lorsque vous ajoutez le code, et le code sera actualisé ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="9c524-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="9c524-183">Il existe deux étapes dans cette section.</span><span class="sxs-lookup"><span data-stu-id="9c524-183">There are two steps to this section.</span></span> <span data-ttu-id="9c524-184">Tout d’abord, vous allez mettre à jour la méthode Iterator pour retourner des mots uniques au lieu de lignes entières.</span><span class="sxs-lookup"><span data-stu-id="9c524-184">First, you'll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="9c524-185">Cela se fait avec ces modifications.</span><span class="sxs-lookup"><span data-stu-id="9c524-185">That's done with these modifications.</span></span> <span data-ttu-id="9c524-186">Remplacez l’instruction `yield return line;` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="9c524-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="9c524-187">Ensuite, vous devez modifier la façon dont vous consommez les lignes du fichier, et ajoutez un délai après chaque mot.</span><span class="sxs-lookup"><span data-stu-id="9c524-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="9c524-188">Remplacez l’instruction `Console.WriteLine(line)` dans la méthode `Main` avec le bloc suivant :</span><span class="sxs-lookup"><span data-stu-id="9c524-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="9c524-189">La classe <xref:System.Threading.Tasks.Task> se trouve dans l’espace de noms <xref:System.Threading.Tasks>, vous devez donc ajouter cette instruction `using` au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="9c524-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="9c524-190">Exécutez l’exemple et vérifiez le résultat.</span><span class="sxs-lookup"><span data-stu-id="9c524-190">Run the sample, and check the output.</span></span> <span data-ttu-id="9c524-191">À présent, chaque mot unique est affiché séparément, suivi d’un délai de 200 ms.</span><span class="sxs-lookup"><span data-stu-id="9c524-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="9c524-192">Toutefois, la sortie affichée présente certains problèmes, car le fichier texte source possède plusieurs lignes qui ont plus de 80 caractères sans saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="9c524-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="9c524-193">Ce qui peut être difficile à lire lors du défilement.</span><span class="sxs-lookup"><span data-stu-id="9c524-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="9c524-194">C’est facile à corriger.</span><span class="sxs-lookup"><span data-stu-id="9c524-194">That's easy to fix.</span></span> <span data-ttu-id="9c524-195">Il vous suffit d’effectuer le suivi de la longueur de chaque ligne et de générer une nouvelle ligne chaque fois que la longueur de la ligne atteint un certain seuil.</span><span class="sxs-lookup"><span data-stu-id="9c524-195">You'll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="9c524-196">Déclarez une variable locale après la déclaration de `words` dans la méthode `ReadFrom` qui contient la longueur de ligne :</span><span class="sxs-lookup"><span data-stu-id="9c524-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="9c524-197">Ensuite, ajoutez le code suivant après l’instruction `yield return word + " ";` (avant l’accolade fermante) :</span><span class="sxs-lookup"><span data-stu-id="9c524-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="9c524-198">Exécutez l’exemple et vous serez en mesure de lire à haute voix à son rythme préconfiguré.</span><span class="sxs-lookup"><span data-stu-id="9c524-198">Run the sample, and you'll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="9c524-199">Tâches asynchrones</span><span class="sxs-lookup"><span data-stu-id="9c524-199">Async Tasks</span></span>

<span data-ttu-id="9c524-200">Dans cette étape finale, vous allez ajouter le code pour écrire la sortie de façon asynchrone dans une tâche, tout en exécutant également une autre tâche pour lire l’entrée de l’utilisateur s’il souhaite accélérer ou ralentir l’affichage du texte, ou arrêter complètement l’affichage du texte.</span><span class="sxs-lookup"><span data-stu-id="9c524-200">In this final step, you'll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="9c524-201">Il y a quelques étapes dans l’informatique et, à la fin, vous disposerez de toutes les mises à jour dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="9c524-201">This has a few steps in it and by the end, you'll have all the updates that you need.</span></span> <span data-ttu-id="9c524-202">La première étape consiste à créer une <xref:System.Threading.Tasks.Task> méthode de retour asynchrone qui représente le code que vous avez créé jusqu’à présent pour lire et afficher le fichier.</span><span class="sxs-lookup"><span data-stu-id="9c524-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you've created so far to read and display the file.</span></span>

<span data-ttu-id="9c524-203">Ajoutez cette méthode à votre `Program` classe (elle est extraite du corps de votre `Main` méthode) :</span><span class="sxs-lookup"><span data-stu-id="9c524-203">Add this method to your `Program` class (it's taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="9c524-204">Vous remarquerez deux modifications.</span><span class="sxs-lookup"><span data-stu-id="9c524-204">You'll notice two changes.</span></span> <span data-ttu-id="9c524-205">Tout d’abord, dans le corps de la méthode, au lieu d’appeler <xref:System.Threading.Tasks.Task.Wait> pour attendre de manière synchrone qu’une tâche se termine, cette version utilise le mot-clé `await`.</span><span class="sxs-lookup"><span data-stu-id="9c524-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="9c524-206">Pour ce faire, vous devez ajouter le modificateur `async` pour la signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="9c524-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="9c524-207">Cette méthode renvoie une `Task`.</span><span class="sxs-lookup"><span data-stu-id="9c524-207">This method returns a `Task`.</span></span> <span data-ttu-id="9c524-208">Notez qu’il n’y a aucune instruction de retour renvoyant un objet `Task`.</span><span class="sxs-lookup"><span data-stu-id="9c524-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="9c524-209">Au lieu de cela, cet objet `Task` est créé par le code que le compilateur génère lorsque vous utilisez l’opérateur `await`.</span><span class="sxs-lookup"><span data-stu-id="9c524-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="9c524-210">Vous pouvez imaginer que cette méthode renvoie une valeur lorsqu’elle atteint un `await`.</span><span class="sxs-lookup"><span data-stu-id="9c524-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="9c524-211">La `Task` renvoyée indique que la tâche n’a pas été effectuée.</span><span class="sxs-lookup"><span data-stu-id="9c524-211">The returned `Task` indicates that the work has not completed.</span></span> <span data-ttu-id="9c524-212">La méthode reprend lorsque la tâche attendue se termine.</span><span class="sxs-lookup"><span data-stu-id="9c524-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="9c524-213">Lorsqu’elle a terminé son exécution, la `Task` renvoyée indique qu’elle est terminée.</span><span class="sxs-lookup"><span data-stu-id="9c524-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="9c524-214">Le code appelant peut surveiller cette `Task` renvoyée pour déterminer si elle est terminée.</span><span class="sxs-lookup"><span data-stu-id="9c524-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="9c524-215">Vous pouvez appeler cette nouvelle méthode dans votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="9c524-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="9c524-216">Ici, dans `Main`, le code attend de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="9c524-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="9c524-217">Vous devez utiliser l’opérateur `await` au lieu d’attendre de manière synchrone lorsque cela est possible.</span><span class="sxs-lookup"><span data-stu-id="9c524-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="9c524-218">Toutefois, dans la méthode d’une application console `Main` , vous ne pouvez pas utiliser l' `await` opérateur.</span><span class="sxs-lookup"><span data-stu-id="9c524-218">But, in a console application's `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="9c524-219">Cela entraînerait la fermeture de l’application avant la fin de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="9c524-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="9c524-220">Si vous utilisez C# 7.1 ou une version ultérieure, vous pouvez créer des applications de console à l’aide de la méthode [`async` `Main`](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="9c524-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="9c524-221">Ensuite, vous devez écrire la deuxième méthode asynchrone pour lire à partir de la console et surveiller les clés « < » (inférieur à), « > » (supérieur à) et « X » ou « x ».</span><span class="sxs-lookup"><span data-stu-id="9c524-221">Next, you need to write the second asynchronous method to read from the Console and watch for the '<' (less than), '>' (greater than) and 'X' or 'x' keys.</span></span> <span data-ttu-id="9c524-222">Voici la méthode que vous ajoutez pour cette tâche :</span><span class="sxs-lookup"><span data-stu-id="9c524-222">Here's the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="9c524-223">Cela crée une expression lambda pour représenter un <xref:System.Action> délégué qui lit une clé à partir de la console et modifie une variable locale représentant le délai quand l’utilisateur appuie sur les clés « < » (inférieur à) ou « > » (supérieur à).</span><span class="sxs-lookup"><span data-stu-id="9c524-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the '<' (less than) or '>' (greater than) keys.</span></span> <span data-ttu-id="9c524-224">La méthode déléguée se termine lorsque l’utilisateur appuie sur les touches « X » ou « x », ce qui permet à l’utilisateur d’arrêter l’affichage du texte à tout moment.</span><span class="sxs-lookup"><span data-stu-id="9c524-224">The delegate method finishes when user presses the 'X' or 'x'  keys, which allow the user to stop the text display at any time.</span></span> <span data-ttu-id="9c524-225">Cette méthode utilise <xref:System.Console.ReadKey> pour bloquer et attendre que l’utilisateur appuie sur une touche.</span><span class="sxs-lookup"><span data-stu-id="9c524-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="9c524-226">Pour terminer cette fonctionnalité, vous devez créer une nouvelle méthode de retour `async Task` qui démarre ces deux tâches (`GetInput` et `ShowTeleprompter`) et gère également les données partagées entre ces deux tâches.</span><span class="sxs-lookup"><span data-stu-id="9c524-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="9c524-227">Il est temps de créer une classe capable de gérer les données partagées entre ces deux tâches.</span><span class="sxs-lookup"><span data-stu-id="9c524-227">It's time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="9c524-228">Cette classe contient deux propriétés publiques : le délai et un indicateur `Done` pour indiquer que le fichier a été entièrement lu :</span><span class="sxs-lookup"><span data-stu-id="9c524-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="9c524-229">Placez cette classe dans un nouveau fichier et ajoutez-la à l’espace de noms `TeleprompterConsole`, comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="9c524-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="9c524-230">Vous devez également ajouter une `using static` instruction pour pouvoir référencer les `Min` `Max` méthodes et sans les noms de classe ou d’espace de noms englobants.</span><span class="sxs-lookup"><span data-stu-id="9c524-230">You'll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="9c524-231">Une [`using static`](../language-reference/keywords/using-static.md) instruction importe les méthodes d’une classe.</span><span class="sxs-lookup"><span data-stu-id="9c524-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="9c524-232">Cela est en opposition avec les instructions `using` utilisées jusqu'à présent, et qui avaient importé toutes les classes à partir d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9c524-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="9c524-233">Ensuite, vous devez mettre à jour les méthodes `ShowTeleprompter` et `GetInput` pour utiliser le nouvel objet `config`.</span><span class="sxs-lookup"><span data-stu-id="9c524-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="9c524-234">Écrivez une dernière `Task` renvoyant une méthode `async` pour démarrer les deux tâches et quitter lorsque la première tâche est terminée :</span><span class="sxs-lookup"><span data-stu-id="9c524-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="9c524-235">Ici, la nouvelle méthode est l’appel <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])>.</span><span class="sxs-lookup"><span data-stu-id="9c524-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="9c524-236">Elle crée une `Task` qui se termine dès que les tâches de sa liste d’arguments se terminent.</span><span class="sxs-lookup"><span data-stu-id="9c524-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="9c524-237">Ensuite, vous devez mettre à jour les méthodes `ShowTeleprompter` et `GetInput` pour utiliser l’objet `config` pour le délai :</span><span class="sxs-lookup"><span data-stu-id="9c524-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="9c524-238">Cette nouvelle version de `ShowTeleprompter` appelle une nouvelle méthode dans la classe `TeleprompterConfig`.</span><span class="sxs-lookup"><span data-stu-id="9c524-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="9c524-239">À présent, vous devez mettre à jour `Main` pour appeler `RunTeleprompter` au lieu de `ShowTeleprompter` :</span><span class="sxs-lookup"><span data-stu-id="9c524-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="9c524-240">Conclusion</span><span class="sxs-lookup"><span data-stu-id="9c524-240">Conclusion</span></span>

<span data-ttu-id="9c524-241">Ce didacticiel vous a montré certaines des fonctionnalités du langage C# et les bibliothèques .NET Core liées au travail dans les applications console.</span><span class="sxs-lookup"><span data-stu-id="9c524-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span> <span data-ttu-id="9c524-242">Vous pouvez utiliser ces connaissances pour explorer davantage le langage ainsi que les classes présentées ici.</span><span class="sxs-lookup"><span data-stu-id="9c524-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="9c524-243">Vous avez vu les principes de base des e/s de fichier et de console, l’utilisation de blocage et de non-blocage de la programmation asynchrone basée sur des tâches, une visite guidée du langage C# et de la façon dont les programmes C# sont organisés, et les CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c524-243">You've seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized, and the .NET Core CLI.</span></span>

<span data-ttu-id="9c524-244">Pour plus d’informations sur les E/S de fichier, consultez la rubrique [E/S de fichier et de flux](../../standard/io/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c524-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="9c524-245">Pour plus d’informations sur le modèle de programmation asynchrone utilisé dans ce tutoriel, consultez la rubrique [Programmation asynchrone basée sur les tâches](../../standard/parallel-programming/task-based-asynchronous-programming.md) et la rubrique [Programmation asynchrone](../async.md).</span><span class="sxs-lookup"><span data-stu-id="9c524-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../../standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
