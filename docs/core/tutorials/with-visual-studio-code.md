---
title: Prise en main de C# et Visual Studio Code
description: Découvrez comment créer et déboguer votre première application .NET Core en C# à l’aide de Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: 03a2edcbb3414cfd63006603424a3ca1eade528f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849453"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="349f7-103">Prise en main de C# et Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="349f7-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="349f7-104">.NET Core vous offre une plateforme rapide et évolutive pour la création d’applications qui s’exécutent sur Windows, Linux et Mac OS.</span><span class="sxs-lookup"><span data-stu-id="349f7-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="349f7-105">Utilisez Visual Studio Code avec l’extension de langage C# pour une expérience d’édition puissante avec prise en charge complète de C# IntelliSense (saisie semi-automatique intelligente de code).</span><span class="sxs-lookup"><span data-stu-id="349f7-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="349f7-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="349f7-106">Prerequisites</span></span>

1. <span data-ttu-id="349f7-107">Installez [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="349f7-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="349f7-108">Installez le [SDK .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="349f7-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="349f7-109">Installez l’[extension C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) pour Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="349f7-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="349f7-110">Pour plus d’informations sur l’installation d’extensions pour Visual Studio Code, consultez [Place de marché des extensions VS Code](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="349f7-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="349f7-111">Hello World</span><span class="sxs-lookup"><span data-stu-id="349f7-111">Hello World</span></span>

<span data-ttu-id="349f7-112">Commençons par un programme « Hello World » simple sur .NET Core :</span><span class="sxs-lookup"><span data-stu-id="349f7-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="349f7-113">Ouvrez un projet :</span><span class="sxs-lookup"><span data-stu-id="349f7-113">Open a project:</span></span>

    - <span data-ttu-id="349f7-114">Ouvrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="349f7-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="349f7-115">Cliquez sur l’icône Explorer dans le menu de gauche, puis sur **Ouvrir le dossier**.</span><span class="sxs-lookup"><span data-stu-id="349f7-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="349f7-116">Sélectionnez **Fichier** > **Ouvrir le dossier** dans le menu principal pour ouvrir le dossier dans lequel vous souhaitez que votre projet C# se trouve et cliquez sur **Sélectionner le dossier**.</span><span class="sxs-lookup"><span data-stu-id="349f7-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="349f7-117">Dans notre exemple, nous créons un dossier pour notre projet nommé *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="349f7-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Ouvrir un dossier Visual Studio Code](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="349f7-119">Initialiser un projet C# :</span><span class="sxs-lookup"><span data-stu-id="349f7-119">Initialize a C# project:</span></span>
    - <span data-ttu-id="349f7-120">Ouvrez le terminal intégré à partir de Visual Studio Code en sélectionnant **Vue** > **Terminal intégré** dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="349f7-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    - <span data-ttu-id="349f7-121">Dans la fenêtre de Terminal, tapez `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="349f7-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="349f7-122">Cette commande crée un fichier `Program.cs` dans votre dossier avec un simple programme « Hello World » déjà écrit, ainsi qu’un fichier projet C# nommé `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="349f7-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![La nouvelle commande dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="349f7-124">Résolution des ressources de génération :</span><span class="sxs-lookup"><span data-stu-id="349f7-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="349f7-125">Pour **.NET Core 1.x**, tapez `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="349f7-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="349f7-126">Exécuter `dotnet restore` vous donne accès aux packages .NET Core qui sont nécessaires pour générer votre projet.</span><span class="sxs-lookup"><span data-stu-id="349f7-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![La commande dotnet restore](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="349f7-128">Exécutez le programme Hello World :</span><span class="sxs-lookup"><span data-stu-id="349f7-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="349f7-129">Tapez `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="349f7-129">Type `dotnet run`.</span></span>

      ![La commande dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="349f7-131">Vous pouvez également regarder un court didacticiel vidéo pour plus d’informations sur la configuration sur [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="349f7-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="349f7-132">Débogage</span><span class="sxs-lookup"><span data-stu-id="349f7-132">Debug</span></span>

1. <span data-ttu-id="349f7-133">Ouvrez *Program.cs* en cliquant dessus.</span><span class="sxs-lookup"><span data-stu-id="349f7-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="349f7-134">La première fois que vous ouvrez un fichier C# dans Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) se charge dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="349f7-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Ouvrez le fichier Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="349f7-136">Visual Studio Code doit vous inviter à ajouter les ressources manquantes pour générer et déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="349f7-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="349f7-137">Sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="349f7-137">Select **Yes**.</span></span>

    ![Invite pour les fichiers manquants](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="349f7-139">Pour ouvrir la vue de débogage, cliquez sur l’icône de débogage dans le menu de gauche.</span><span class="sxs-lookup"><span data-stu-id="349f7-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Ouvrir l’onglet Débogage dans Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="349f7-141">Cherchez la flèche verte en haut du volet.</span><span class="sxs-lookup"><span data-stu-id="349f7-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="349f7-142">Assurez-vous que `.NET Core Launch (console)` est sélectionné dans la liste déroulante à côté du volet.</span><span class="sxs-lookup"><span data-stu-id="349f7-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![Sélection de .NET Core dans Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="349f7-144">Ajoutez un point d’arrêt à votre projet en cliquant sur la **marge de l’éditeur**, qui est l’espace à gauche des numéros de ligne dans l’éditeur, à côté de la ligne 9, ou déplacez le curseur texte vers la ligne 9 dans l’éditeur et appuyez sur <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="349f7-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Définition d'un point d'arrêt](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="349f7-146">Pour démarrer le débogage, sélectionnez <kbd>F5</kbd> ou la flèche verte.</span><span class="sxs-lookup"><span data-stu-id="349f7-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="349f7-147">Le débogueur arrête l’exécution de votre programme lorsqu’il atteint le point d’arrêt que vous avez défini à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="349f7-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="349f7-148">Pendant le débogage, vous pouvez afficher vos variables locales dans le volet supérieur gauche ou utiliser la console de débogage.</span><span class="sxs-lookup"><span data-stu-id="349f7-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

7. <span data-ttu-id="349f7-149">Sélectionnez la flèche bleue en haut pour continuer le débogage, ou le carré rouge en haut pour l’arrêter.</span><span class="sxs-lookup"><span data-stu-id="349f7-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Exécution et débogage dans Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="349f7-151">Pour obtenir plus d’informations et de conseils de dépannage sur le débogage de .NET Core avec OmniSharp dans Visual Studio Code, consultez [Instructions de configuration du débogueur .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="349f7-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="349f7-152">Ajouter une classe</span><span class="sxs-lookup"><span data-stu-id="349f7-152">Add a class</span></span>

1. <span data-ttu-id="349f7-153">Pour ajouter une nouvelle classe, cliquez avec le bouton droit dans l’Explorateur VS Code et sélectionnez **Nouveau fichier**.</span><span class="sxs-lookup"><span data-stu-id="349f7-153">To add a new class right-click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="349f7-154">Un nouveau fichier est ajouté au dossier ouvert dans VS Code.</span><span class="sxs-lookup"><span data-stu-id="349f7-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="349f7-155">Nommez votre fichier `MyClass.cs`.</span><span class="sxs-lookup"><span data-stu-id="349f7-155">Name your file `MyClass.cs`.</span></span> <span data-ttu-id="349f7-156">Vous devez l’enregistrer avec l’extension `.cs` à la fin pour qu’il soit reconnu comme fichier C#.</span><span class="sxs-lookup"><span data-stu-id="349f7-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="349f7-157">Ajoutez le code ci-dessous pour créer votre première classe.</span><span class="sxs-lookup"><span data-stu-id="349f7-157">Add the code below to create your first class.</span></span> <span data-ttu-id="349f7-158">Veillez à inclure le bon espace de noms pour pouvoir y faire référence dans votre fichier `Program.cs`.</span><span class="sxs-lookup"><span data-stu-id="349f7-158">Make sure to include the correct namespace so you can reference it from your `Program.cs` file.</span></span>

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

4. <span data-ttu-id="349f7-159">Appelez votre nouvelle classe dans votre méthode principale, dans `Program.cs`, en ajoutant le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="349f7-159">Call your new class from your main method in `Program.cs` by adding the code below.</span></span>

    ```csharp
    using System;
    
    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                MyClass c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. <span data-ttu-id="349f7-160">Enregistrez vos modifications et exécutez à nouveau votre programme.</span><span class="sxs-lookup"><span data-stu-id="349f7-160">Save your changes and run your program again.</span></span> <span data-ttu-id="349f7-161">Le nouveau message devrait apparaître avec la chaîne ajoutée.</span><span class="sxs-lookup"><span data-stu-id="349f7-161">The new message should appear with the appended string.</span></span>

    ```console
    > dotnet run
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="349f7-162">Questions fréquentes (FAQ)</span><span class="sxs-lookup"><span data-stu-id="349f7-162">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="349f7-163">Je n’ai pas les ressources nécessaires pour générer et déboguer du code C# dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="349f7-163">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="349f7-164">Mon débogueur indique « Aucune configuration ».</span><span class="sxs-lookup"><span data-stu-id="349f7-164">My debugger says "No Configuration."</span></span>

<span data-ttu-id="349f7-165">L’extension Visual Studio Code C# peut générer automatiquement les ressources dont vous avez besoin pour les builds et le débogage.</span><span class="sxs-lookup"><span data-stu-id="349f7-165">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="349f7-166">Visual Studio Code vous invite à générer ces ressources à la première ouverture d’un projet C#.</span><span class="sxs-lookup"><span data-stu-id="349f7-166">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="349f7-167">Si vous n’avez pas généré ces ressources au départ, vous pouvez le faire à tout moment en exécutant cette commande : ouvrez la palette de commandes (**Affichage > Palette de commandes**) et tapez « >.NET: Generate Assets for Build and Debug ».</span><span class="sxs-lookup"><span data-stu-id="349f7-167">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="349f7-168">Cette commande génère les fichiers de configuration .vscode, launch.json et tasks.json dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="349f7-168">Selecting this generates the .vscode, launch.json, and tasks.json configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="349f7-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="349f7-169">See also</span></span>

- [<span data-ttu-id="349f7-170">Configuration de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="349f7-170">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="349f7-171">Débogage dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="349f7-171">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
