---
title: Prise en main de C# et Visual Studio Code
description: Découvrez comment créer et déboguer votre première application .NET Core en C# à l’aide de Visual Studio Code.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506884"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="153f0-103">Prise en main de C# et Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="153f0-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="153f0-104">.NET Core vous offre une plateforme rapide et évolutive pour la création d’applications qui s’exécutent sur Windows, Linux et Mac OS.</span><span class="sxs-lookup"><span data-stu-id="153f0-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="153f0-105">Utilisez Visual Studio Code avec l’extension de langage C# pour une expérience d’édition puissante avec prise en charge complète de C# IntelliSense (saisie semi-automatique intelligente de code).</span><span class="sxs-lookup"><span data-stu-id="153f0-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="153f0-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="153f0-106">Prerequisites</span></span>

1. <span data-ttu-id="153f0-107">Installez [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="153f0-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="153f0-108">Installez le [kit de développement logiciel (SDK) .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="153f0-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="153f0-109">Installez l’[extension C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) pour Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="153f0-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="153f0-110">Pour plus d’informations sur l’installation d’extensions pour Visual Studio Code, consultez [Place de marché des extensions VS Code](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="153f0-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="153f0-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="153f0-111">Hello World</span></span>

<span data-ttu-id="153f0-112">Prise en main d’un simple programme « Hello World » sur .NET Core :</span><span class="sxs-lookup"><span data-stu-id="153f0-112">Get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="153f0-113">Ouvrez un projet :</span><span class="sxs-lookup"><span data-stu-id="153f0-113">Open a project:</span></span>

    - <span data-ttu-id="153f0-114">Ouvrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="153f0-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="153f0-115">Sélectionnez **fichier** > **ouvrir le dossier** dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="153f0-115">Select **File** > **Open Folder** from the main menu.</span></span>
    - <span data-ttu-id="153f0-116">Créez un dossier nommé *HelloWorld*, puis cliquez sur **Sélectionner un dossier**.</span><span class="sxs-lookup"><span data-stu-id="153f0-116">Create a folder named *HelloWorld*, and click **Select Folder**.</span></span> <span data-ttu-id="153f0-117">Le nom du dossier devient le nom du projet et le nom de l’espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="153f0-117">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="153f0-118">Vous ajouterez du code ultérieurement dans le didacticiel qui suppose que l’espace de `HelloWorld`noms du projet est.</span><span class="sxs-lookup"><span data-stu-id="153f0-118">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="153f0-119">Initialiser un projet C# :</span><span class="sxs-lookup"><span data-stu-id="153f0-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="153f0-120">Ouvrez le terminal à partir de Visual Studio code en sélectionnant **Afficher** > le**Terminal** dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="153f0-120">Open the Terminal from Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>
    - <span data-ttu-id="153f0-121">Dans la fenêtre de terminal, `dotnet new console`entrez.</span><span class="sxs-lookup"><span data-stu-id="153f0-121">In the terminal window, enter `dotnet new console`.</span></span>

      <span data-ttu-id="153f0-122">Cette commande crée un fichier *Program.cs* dans votre dossier avec un simple programme « Hello World » déjà écrit, ainsi qu’un fichier projet C# nommé *HelloWorld. csproj*.</span><span class="sxs-lookup"><span data-stu-id="153f0-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![La nouvelle commande dotnet](media/with-visual-studio-code/dotnet-new-command.png)

1. <span data-ttu-id="153f0-124">Exécutez le programme Hello World :</span><span class="sxs-lookup"><span data-stu-id="153f0-124">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="153f0-125">Dans la fenêtre de terminal, `dotnet run`entrez.</span><span class="sxs-lookup"><span data-stu-id="153f0-125">In the terminal window, enter `dotnet run`.</span></span>

      ![La commande dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a><span data-ttu-id="153f0-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="153f0-127">Debug</span></span>

1. <span data-ttu-id="153f0-128">Ouvrez *Program.cs* en cliquant dessus.</span><span class="sxs-lookup"><span data-stu-id="153f0-128">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="153f0-129">La première fois que vous ouvrez un fichier C# dans Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) se charge dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="153f0-129">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Ouvrez le fichier Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="153f0-131">Visual Studio Code vous invite à ajouter les ressources manquantes pour générer et déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="153f0-131">Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="153f0-132">Sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="153f0-132">Select **Yes**.</span></span>

    ![Invite pour les fichiers manquants](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="153f0-134">Pour ouvrir la vue de débogage, cliquez sur l’icône de débogage dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="153f0-134">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Ouvrir l’onglet Débogage dans Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

1. <span data-ttu-id="153f0-136">Cherchez la flèche verte en haut du volet.</span><span class="sxs-lookup"><span data-stu-id="153f0-136">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="153f0-137">Assurez-vous que la liste déroulante en regard du menu de **lancement de .net Core (console)** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="153f0-137">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Sélection de .NET Core dans Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

1. <span data-ttu-id="153f0-139">Ajoutez un point d’arrêt à votre projet en cliquant sur la **marge de l’éditeur**, qui est l’espace à gauche des numéros de ligne dans l’éditeur, à côté de la ligne 9, ou déplacez le curseur texte vers la ligne 9 dans l’éditeur et appuyez sur <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="153f0-139">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Définition d'un point d'arrêt](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. <span data-ttu-id="153f0-141">Pour démarrer le débogage, appuyez sur <kbd>F5</kbd> ou sélectionnez la flèche verte.</span><span class="sxs-lookup"><span data-stu-id="153f0-141">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="153f0-142">Le débogueur arrête l’exécution de votre programme lorsqu’il atteint le point d’arrêt que vous avez défini à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="153f0-142">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="153f0-143">Lors du débogage, vous pouvez afficher vos variables locales dans le volet supérieur gauche ou utiliser la console de débogage.</span><span class="sxs-lookup"><span data-stu-id="153f0-143">While debugging, you can view your local variables in the top-left pane or use the debug console.</span></span>

1. <span data-ttu-id="153f0-144">Sélectionnez la flèche bleue en haut pour continuer le débogage, ou le carré rouge en haut pour l’arrêter.</span><span class="sxs-lookup"><span data-stu-id="153f0-144">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Exécution et débogage dans Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="153f0-146">Pour obtenir plus d’informations et de conseils de dépannage sur le débogage de .NET Core avec OmniSharp dans Visual Studio Code, consultez [Instructions de configuration du débogueur .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="153f0-146">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="153f0-147">Ajouter une classe</span><span class="sxs-lookup"><span data-stu-id="153f0-147">Add a class</span></span>

1. <span data-ttu-id="153f0-148">Pour ajouter une nouvelle classe, cliquez avec le bouton droit dans l’Explorateur VSCode sous *Program.cs* et sélectionnez **nouveau fichier**.</span><span class="sxs-lookup"><span data-stu-id="153f0-148">To add a new class, right-click in the VSCode Explorer below *Program.cs* and select **New File**.</span></span> <span data-ttu-id="153f0-149">Un nouveau fichier est ajouté au dossier ouvert dans VS Code.</span><span class="sxs-lookup"><span data-stu-id="153f0-149">This adds a new file to the folder you have open in VSCode.</span></span>
1. <span data-ttu-id="153f0-150">Nommez votre fichier *MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="153f0-150">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="153f0-151">Vous devez l’enregistrer avec l’extension `.cs` à la fin pour qu’il soit reconnu comme fichier C#.</span><span class="sxs-lookup"><span data-stu-id="153f0-151">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
1. <span data-ttu-id="153f0-152">Ajoutez le code suivant pour créer votre première classe.</span><span class="sxs-lookup"><span data-stu-id="153f0-152">Add the following code to create your first class.</span></span>

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

1. <span data-ttu-id="153f0-153">Appelez votre nouvelle classe à partir `Main` de votre méthode en remplaçant le code dans *Program.cs* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="153f0-153">Call your new class from your `Main` method by replacing the code in *Program.cs* with the following code:</span></span>

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

1. <span data-ttu-id="153f0-154">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="153f0-154">Save your changes.</span></span>

1. <span data-ttu-id="153f0-155">Réexécutez le programme.</span><span class="sxs-lookup"><span data-stu-id="153f0-155">Run the program again.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="153f0-156">Le nouveau message s’affiche avec la chaîne ajoutée.</span><span class="sxs-lookup"><span data-stu-id="153f0-156">The new message appears with the appended string.</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="153f0-157">Questions fréquentes (FAQ)</span><span class="sxs-lookup"><span data-stu-id="153f0-157">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="153f0-158">Je n’ai pas les ressources nécessaires pour générer et déboguer du code C# dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="153f0-158">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="153f0-159">Mon débogueur indique « Aucune configuration ».</span><span class="sxs-lookup"><span data-stu-id="153f0-159">My debugger says "No Configuration."</span></span>

<span data-ttu-id="153f0-160">L’extension Visual Studio Code C# peut générer automatiquement les ressources dont vous avez besoin pour les builds et le débogage.</span><span class="sxs-lookup"><span data-stu-id="153f0-160">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="153f0-161">Visual Studio Code vous invite à générer ces ressources à la première ouverture d’un projet C#.</span><span class="sxs-lookup"><span data-stu-id="153f0-161">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="153f0-162">Si vous n’avez pas généré ces ressources au départ, vous pouvez le faire à tout moment en exécutant cette commande : ouvrez la palette de commandes (**Affichage > Palette de commandes**) et tapez « >.NET: Generate Assets for Build and Debug ».</span><span class="sxs-lookup"><span data-stu-id="153f0-162">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="153f0-163">La sélection de cette option génère les fichiers de configuration *. vscode*, *Launch. JSON*et *Tasks. JSON* dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="153f0-163">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="153f0-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="153f0-164">See also</span></span>

- [<span data-ttu-id="153f0-165">Configurer Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="153f0-165">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="153f0-166">Débogage dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="153f0-166">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
