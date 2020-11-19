---
title: Créer une application console .NET à l’aide de Visual Studio Code
description: Découvrez comment créer une application console .NET à l’aide de Visual Studio Code et de l’interface CLI .NET.
ms.date: 11/17/2020
ms.openlocfilehash: dbbdf88b0c84089249eb7e446c25eddc11543c1a
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915867"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-code"></a><span data-ttu-id="7c549-103">Didacticiel : créer une application console .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7c549-103">Tutorial: Create a .NET console application using Visual Studio Code</span></span>

<span data-ttu-id="7c549-104">Ce didacticiel montre comment créer et exécuter une application console .NET à l’aide de Visual Studio Code et de l’interface CLI .NET.</span><span class="sxs-lookup"><span data-stu-id="7c549-104">This tutorial shows how to create and run a .NET console application by using Visual Studio Code and the .NET CLI.</span></span> <span data-ttu-id="7c549-105">Les tâches de projet, telles que la création, la compilation et l’exécution d’un projet, sont effectuées à l’aide de l’interface CLI .NET.</span><span class="sxs-lookup"><span data-stu-id="7c549-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET CLI.</span></span> <span data-ttu-id="7c549-106">Vous pouvez suivre ce didacticiel avec un autre éditeur de code et exécuter des commandes dans un terminal, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="7c549-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c549-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="7c549-107">Prerequisites</span></span>

1. <span data-ttu-id="7c549-108">[Visual Studio code](https://code.visualstudio.com/) avec l' [extension C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installée.</span><span class="sxs-lookup"><span data-stu-id="7c549-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="7c549-109">Pour plus d’informations sur la façon d’installer des extensions sur Visual Studio Code, consultez [vs code d’extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="7c549-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="7c549-110">Le [Kit de développement logiciel (SDK) .net 5,0 ou version ultérieure](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="7c549-110">The [.NET 5.0 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="7c549-111">Créer l’application</span><span class="sxs-lookup"><span data-stu-id="7c549-111">Create the app</span></span>

<span data-ttu-id="7c549-112">Créez un projet d’application console .NET nommé « HelloWorld ».</span><span class="sxs-lookup"><span data-stu-id="7c549-112">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="7c549-113">Démarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="7c549-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="7c549-114">**File**  >  Dans le menu principal, sélectionnez fichier **ouvrir le dossier** (**fichier**  >  **Ouvrir..** . sur MacOS).</span><span class="sxs-lookup"><span data-stu-id="7c549-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="7c549-115">Dans la boîte de dialogue **ouvrir un dossier** , créez un dossier *HelloWorld* , puis cliquez sur **Sélectionner un dossier** (**ouvrir** sur MacOS).</span><span class="sxs-lookup"><span data-stu-id="7c549-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="7c549-116">Le nom du dossier devient le nom du projet et le nom de l’espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="7c549-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="7c549-117">Vous ajouterez du code ultérieurement dans le didacticiel qui suppose que l’espace de noms du projet est `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="7c549-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="7c549-118">Ouvrez le **Terminal** dans Visual Studio code en sélectionnant **Afficher** le  >  **Terminal** dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="7c549-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="7c549-119">Le **Terminal** s’ouvre avec l’invite de commandes dans le dossier *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="7c549-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="7c549-120">Dans le **Terminal**, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7c549-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="7c549-121">Le modèle crée une application « Hello World » simple.</span><span class="sxs-lookup"><span data-stu-id="7c549-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="7c549-122">Elle appelle la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> méthode pour afficher « :::no-loc text="Hello World!"::: » dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="7c549-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display ":::no-loc text="Hello World!":::" in the console window.</span></span>

<span data-ttu-id="7c549-123">Le code du modèle définit une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument :</span><span class="sxs-lookup"><span data-stu-id="7c549-123">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="7c549-124">`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="7c549-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="7c549-125">Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.</span><span class="sxs-lookup"><span data-stu-id="7c549-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="7c549-126">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="7c549-126">Run the app</span></span>

<span data-ttu-id="7c549-127">Exécutez la commande suivante dans le **Terminal**:</span><span class="sxs-lookup"><span data-stu-id="7c549-127">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="7c549-128">Le programme affiche « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="7c549-128">The program displays "Hello World!"</span></span> <span data-ttu-id="7c549-129">et se termine.</span><span class="sxs-lookup"><span data-stu-id="7c549-129">and ends.</span></span>

![La commande dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="7c549-131">Améliorer l’application</span><span class="sxs-lookup"><span data-stu-id="7c549-131">Enhance the app</span></span>

<span data-ttu-id="7c549-132">Améliorez l’application pour inviter l’utilisateur à entrer son nom et l’afficher avec la date et l’heure.</span><span class="sxs-lookup"><span data-stu-id="7c549-132">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="7c549-133">Ouvrez *Program.cs* en cliquant dessus.</span><span class="sxs-lookup"><span data-stu-id="7c549-133">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="7c549-134">La première fois que vous ouvrez un fichier C# dans Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) se charge dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="7c549-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Ouvrez le fichier Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="7c549-136">Sélectionnez **Oui** lorsque Visual Studio code vous invite à ajouter les ressources manquantes pour générer et déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="7c549-136">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Invite pour les fichiers manquants](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="7c549-138">Remplacez le contenu de la `Main` méthode dans *Program.cs*, qui est la ligne qui appelle `Console.WriteLine` , avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7c549-138">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="7c549-139">Ce code affiche une invite dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="7c549-139">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="7c549-140">Elle stocke cette chaîne dans une variable nommée `name` .</span><span class="sxs-lookup"><span data-stu-id="7c549-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="7c549-141">Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`.</span><span class="sxs-lookup"><span data-stu-id="7c549-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="7c549-142">Et affiche ces valeurs dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="7c549-142">And it displays these values in the console window.</span></span> <span data-ttu-id="7c549-143">Enfin, il affiche une invite dans la fenêtre de console et appelle la <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> méthode pour attendre l’entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7c549-143">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="7c549-144">`\n`Représente un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="7c549-144">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="7c549-145">Le signe dollar ( `$` ) devant une chaîne vous permet de placer des expressions telles que des noms de variable entre accolades dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="7c549-145">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="7c549-146">La valeur de l’expression est insérée dans la chaîne à la place de l’expression.</span><span class="sxs-lookup"><span data-stu-id="7c549-146">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="7c549-147">Cette syntaxe est appelée « [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md)».</span><span class="sxs-lookup"><span data-stu-id="7c549-147">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="7c549-148">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="7c549-148">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="7c549-149">Dans Visual Studio Code, vous devez enregistrer explicitement les modifications.</span><span class="sxs-lookup"><span data-stu-id="7c549-149">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="7c549-150">Contrairement à Visual Studio, les modifications de fichiers ne sont pas enregistrées automatiquement quand vous générez et exécutez une application.</span><span class="sxs-lookup"><span data-stu-id="7c549-150">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="7c549-151">Réexécutez le programme :</span><span class="sxs-lookup"><span data-stu-id="7c549-151">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="7c549-152">Répondez à l’invite en entrant un nom et en appuyant sur la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="7c549-152">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Fenêtre de terminal avec sortie du programme modifiée":::

1. <span data-ttu-id="7c549-154">Appuyez sur n’importe quelle touche pour quitter le programme.</span><span class="sxs-lookup"><span data-stu-id="7c549-154">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7c549-155">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="7c549-155">Additional resources</span></span>

- [<span data-ttu-id="7c549-156">Configurer Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7c549-156">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="7c549-157">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7c549-157">Next steps</span></span>

<span data-ttu-id="7c549-158">Dans ce didacticiel, vous avez créé une application console .NET.</span><span class="sxs-lookup"><span data-stu-id="7c549-158">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="7c549-159">Dans le didacticiel suivant, vous allez déboguer l’application.</span><span class="sxs-lookup"><span data-stu-id="7c549-159">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c549-160">Déboguer une application console .NET à l’aide d’Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7c549-160">Debug a .NET console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
