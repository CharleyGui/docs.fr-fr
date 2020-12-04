---
title: Créer une application console .NET à l’aide de Visual Studio pour Mac
description: Découvrez comment créer une application console .NET à l’aide de Visual Studio pour Mac.
ms.date: 11/30/2020
ms.openlocfilehash: 1351b06eec32cd8d3d9d44926655405fe2246f58
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599484"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="038c9-103">Didacticiel : créer une application console .NET à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="038c9-103">Tutorial: Create a .NET console application using Visual Studio for Mac</span></span>

<span data-ttu-id="038c9-104">Ce didacticiel montre comment créer et exécuter une application console .NET à l’aide de Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="038c9-104">This tutorial shows how to create and run a .NET console application using Visual Studio for Mac.</span></span>

> [!NOTE]
> <span data-ttu-id="038c9-105">Vos commentaires sont extrêmement précieux.</span><span class="sxs-lookup"><span data-stu-id="038c9-105">Your feedback is highly valued.</span></span> <span data-ttu-id="038c9-106">Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :</span><span class="sxs-lookup"><span data-stu-id="038c9-106">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="038c9-107">Dans Visual Studio pour Mac, sélectionnez **aide**  >  **signaler un problème** dans le menu ou **signaler un problème** dans l’écran d’accueil, qui ouvre une fenêtre pour l’enregistrement d’un rapport de bogue.</span><span class="sxs-lookup"><span data-stu-id="038c9-107">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="038c9-108">Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://aka.ms/feedback/report?space=41).</span><span class="sxs-lookup"><span data-stu-id="038c9-108">You can track your feedback in the [Developer Community](https://aka.ms/feedback/report?space=41) portal.</span></span>
> * <span data-ttu-id="038c9-109">Pour faire une suggestion, sélectionnez **aide**  >  **fournir une suggestion** dans le menu ou **fournissez une suggestion** à partir de l’écran d’accueil, qui vous permet de vous rendre sur la [page Web de la communauté des développeurs Visual Studio pour Mac](https://aka.ms/feedback/suggest?space=41).</span><span class="sxs-lookup"><span data-stu-id="038c9-109">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://aka.ms/feedback/suggest?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="038c9-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="038c9-110">Prerequisites</span></span>

* <span data-ttu-id="038c9-111">[Visual Studio pour Mac version 8,8 ou ultérieure](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="038c9-111">[Visual Studio for Mac version 8.8 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="038c9-112">Sélectionnez l’option d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="038c9-112">Select the option to install .NET Core.</span></span> <span data-ttu-id="038c9-113">L’installation de Xamarin est facultative pour le développement .NET.</span><span class="sxs-lookup"><span data-stu-id="038c9-113">Installing Xamarin is optional for .NET development.</span></span> <span data-ttu-id="038c9-114">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="038c9-114">For more information, see the following resources:</span></span>

  * <span data-ttu-id="038c9-115">[Didacticiel : installer Visual Studio pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="038c9-115">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="038c9-116">[Versions MacOS prises en charge](../install/windows.md).</span><span class="sxs-lookup"><span data-stu-id="038c9-116">[Supported macOS versions](../install/windows.md).</span></span>
  * <span data-ttu-id="038c9-117">[Versions .net prises en charge par Visual Studio pour Mac](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="038c9-117">[.NET versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="038c9-118">Créer l’application</span><span class="sxs-lookup"><span data-stu-id="038c9-118">Create the app</span></span>

1. <span data-ttu-id="038c9-119">Démarrez Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="038c9-119">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="038c9-120">Sélectionnez **nouveau** dans la fenêtre démarrer.</span><span class="sxs-lookup"><span data-stu-id="038c9-120">Select **New** in the start window.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Bouton Nouveau sur l’écran Démarrer de Visual Studio pour Mac":::

1. <span data-ttu-id="038c9-122">Dans la boîte de dialogue **nouveau projet** , sélectionnez **application** sous le nœud **Web et console** .</span><span class="sxs-lookup"><span data-stu-id="038c9-122">In the **New Project** dialog, select **App** under the **Web and Console** node.</span></span> <span data-ttu-id="038c9-123">Sélectionnez le modèle **application console** , puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="038c9-123">Select the **Console Application** template, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Liste des modèles Nouveau projet":::

1. <span data-ttu-id="038c9-125">Dans la liste déroulante **Framework cible** de la boîte de dialogue **configurer votre nouvelle application console** , sélectionnez **.net 5,0**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="038c9-125">In the **Target Framework** drop-down of the **Configure your new Console Application** dialog, select **.NET 5.0**, and select **Next**.</span></span>

1. <span data-ttu-id="038c9-126">Tapez « HelloWorld » comme **nom de projet**, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="038c9-126">Type "HelloWorld" for the **Project Name**, and select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Boîte de dialogue de configuration de votre nouvelle application console":::

<span data-ttu-id="038c9-128">Le modèle crée une application « Hello World » simple.</span><span class="sxs-lookup"><span data-stu-id="038c9-128">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="038c9-129">Elle appelle la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> méthode pour afficher « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="038c9-129">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="038c9-130">dans la fenêtre de terminal.</span><span class="sxs-lookup"><span data-stu-id="038c9-130">in the terminal window.</span></span>

<span data-ttu-id="038c9-131">Le code du modèle définit une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument :</span><span class="sxs-lookup"><span data-stu-id="038c9-131">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="038c9-132">`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="038c9-132">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="038c9-133">Les arguments de ligne de commande fournis lorsque l’application est lancée sont disponibles dans le `args` tableau.</span><span class="sxs-lookup"><span data-stu-id="038c9-133">Any command-line arguments supplied when the application is launched are available in the `args` array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="038c9-134">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="038c9-134">Run the app</span></span>

1. <span data-ttu-id="038c9-135">Appuyez sur <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>commande</kbd> + <kbd>entrée</kbd>) pour exécuter l’application sans débogage.</span><span class="sxs-lookup"><span data-stu-id="038c9-135">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app without debugging.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="Le terminal affiche Hello World !":::

1. <span data-ttu-id="038c9-137">Fermez la fenêtre de **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="038c9-137">Close the **Terminal** window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="038c9-138">Améliorer l’application</span><span class="sxs-lookup"><span data-stu-id="038c9-138">Enhance the app</span></span>

<span data-ttu-id="038c9-139">Améliorez l’application pour inviter l’utilisateur à entrer son nom et l’afficher avec la date et l’heure.</span><span class="sxs-lookup"><span data-stu-id="038c9-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="038c9-140">Dans *Program.cs*, remplacez le contenu de la `Main` méthode, qui est la ligne qui appelle `Console.WriteLine` , par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="038c9-140">In *Program.cs*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="038c9-141">Ce code affiche une invite dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="038c9-141">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>enter</kbd> key.</span></span> <span data-ttu-id="038c9-142">Elle stocke cette chaîne dans une variable nommée `name` .</span><span class="sxs-lookup"><span data-stu-id="038c9-142">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="038c9-143">Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`.</span><span class="sxs-lookup"><span data-stu-id="038c9-143">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="038c9-144">Et affiche ces valeurs dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="038c9-144">And it displays these values in the console window.</span></span> <span data-ttu-id="038c9-145">Enfin, il affiche une invite dans la fenêtre de console et appelle la <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> méthode pour attendre l’entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="038c9-145">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="038c9-146">`\n`Représente un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="038c9-146">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="038c9-147">Le signe dollar ( `$` ) devant une chaîne vous permet de placer des expressions telles que des noms de variable entre accolades dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="038c9-147">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="038c9-148">La valeur de l’expression est insérée dans la chaîne à la place de l’expression.</span><span class="sxs-lookup"><span data-stu-id="038c9-148">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="038c9-149">Cette syntaxe est appelée « [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md)».</span><span class="sxs-lookup"><span data-stu-id="038c9-149">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="038c9-150">Appuyez sur <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>commande</kbd> + <kbd>entrée</kbd>) pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="038c9-150">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app.</span></span>

1. <span data-ttu-id="038c9-151">Répondez à l’invite en entrant un nom et en appuyant sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="038c9-151">Respond to the prompt by entering a name and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Le terminal affiche la sortie du programme modifié":::

1. <span data-ttu-id="038c9-153">Fermez le terminal.</span><span class="sxs-lookup"><span data-stu-id="038c9-153">Close the terminal.</span></span>

## <a name="next-steps"></a><span data-ttu-id="038c9-154">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="038c9-154">Next steps</span></span>

<span data-ttu-id="038c9-155">Dans ce didacticiel, vous avez créé une application console .NET.</span><span class="sxs-lookup"><span data-stu-id="038c9-155">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="038c9-156">Dans le didacticiel suivant, vous allez déboguer l’application.</span><span class="sxs-lookup"><span data-stu-id="038c9-156">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="038c9-157">Déboguer une application console .NET à l’aide d’Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="038c9-157">Debug a .NET console application using Visual Studio for Mac</span></span>](debugging-with-visual-studio-mac.md)
