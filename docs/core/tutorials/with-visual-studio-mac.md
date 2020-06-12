---
title: Créer une application console .NET Core à l’aide de Visual Studio pour Mac
description: Découvrez comment créer une application console .NET Core à l’aide de Visual Studio pour Mac.
ms.date: 06/02/2020
ms.openlocfilehash: 57f16e510270b7256b285493b1f978101fc11804
ms.sourcegitcommit: f6350c2c542e6edd52d7e9d6667b96d85d810e67
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84717521"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="a7115-103">Didacticiel : créer une application console .NET Core à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="a7115-103">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="a7115-104">Ce didacticiel montre comment créer et exécuter une application console .NET Core à l’aide de Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="a7115-104">This tutorial shows how to create and run a .NET Core console application using Visual Studio for Mac.</span></span>

> [!NOTE]
> <span data-ttu-id="a7115-105">Vos commentaires sont extrêmement précieux.</span><span class="sxs-lookup"><span data-stu-id="a7115-105">Your feedback is highly valued.</span></span> <span data-ttu-id="a7115-106">Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :</span><span class="sxs-lookup"><span data-stu-id="a7115-106">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="a7115-107">Dans Visual Studio pour Mac, sélectionnez **aide**  >  **signaler un problème** dans le menu ou **signaler un problème** dans l’écran d’accueil, qui ouvre une fenêtre pour l’enregistrement d’un rapport de bogue.</span><span class="sxs-lookup"><span data-stu-id="a7115-107">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="a7115-108">Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="a7115-108">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="a7115-109">Pour faire une suggestion, sélectionnez **aide**  >  **fournir une suggestion** dans le menu ou **fournissez une suggestion** à partir de l’écran d’accueil, qui vous permet de vous rendre sur la [page Web de la communauté des développeurs Visual Studio pour Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="a7115-109">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a7115-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="a7115-110">Prerequisites</span></span>

* <span data-ttu-id="a7115-111">[Visual Studio pour Mac version 8,6 ou ultérieure](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="a7115-111">[Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="a7115-112">Sélectionnez l’option d’installation de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7115-112">Select the option to install .NET Core.</span></span> <span data-ttu-id="a7115-113">L’installation de Xamarin est facultative pour le développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7115-113">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="a7115-114">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="a7115-114">For more information, see the following resources:</span></span>

  * <span data-ttu-id="a7115-115">[Didacticiel : installer Visual Studio pour Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="a7115-115">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="a7115-116">[Versions MacOS prises en charge](../install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="a7115-116">[Supported macOS versions](../install/dependencies.md?pivots=os-macos).</span></span>
  * <span data-ttu-id="a7115-117">[Versions de .net Core prises en charge par Visual Studio pour Mac](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="a7115-117">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="a7115-118">Créer l’application</span><span class="sxs-lookup"><span data-stu-id="a7115-118">Create the app</span></span>

<span data-ttu-id="a7115-119">Créez un projet d’application console .NET Core nommé « HelloWorld ».</span><span class="sxs-lookup"><span data-stu-id="a7115-119">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="a7115-120">Démarrez Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="a7115-120">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="a7115-121">Sélectionnez **nouveau** dans la fenêtre démarrer.</span><span class="sxs-lookup"><span data-stu-id="a7115-121">Select **New** in the start window.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Bouton Nouveau sur l’écran Démarrer de Visual Studio pour Mac":::

1. <span data-ttu-id="a7115-123">Dans la boîte de dialogue **nouveau projet** , sélectionnez **application** sous le nœud **Web et console** .</span><span class="sxs-lookup"><span data-stu-id="a7115-123">In the **New Project** dialog, select **App** under the **Web and Console** node.</span></span> <span data-ttu-id="a7115-124">Sélectionnez le modèle **application console** , puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="a7115-124">Select the **Console Application** template, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Liste des modèles Nouveau projet":::

1. <span data-ttu-id="a7115-126">Dans la liste déroulante **Framework cible** de la boîte de dialogue **configurer votre nouvelle application console** , sélectionnez **.net Core 3,1**, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="a7115-126">In the **Target Framework** drop-down of the **Configure your new Console Application** dialog, select **.NET Core 3.1**, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="Sélectionner la version cible de .NET Framework":::

1. <span data-ttu-id="a7115-128">Tapez « HelloWorld » comme **nom de projet**, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="a7115-128">Type "HelloWorld" for the **Project Name**, and select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Boîte de dialogue de configuration de votre nouvelle application console":::

<span data-ttu-id="a7115-130">Le modèle crée une application « Hello World » simple.</span><span class="sxs-lookup"><span data-stu-id="a7115-130">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="a7115-131">Elle appelle la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> méthode pour afficher « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="a7115-131">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="a7115-132">dans la fenêtre de terminal.</span><span class="sxs-lookup"><span data-stu-id="a7115-132">in the terminal window.</span></span>

<span data-ttu-id="a7115-133">Le code du modèle définit une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument :</span><span class="sxs-lookup"><span data-stu-id="a7115-133">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="a7115-134">`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="a7115-134">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="a7115-135">Les arguments de ligne de commande fournis lorsque l’application est lancée sont disponibles dans le `args` tableau.</span><span class="sxs-lookup"><span data-stu-id="a7115-135">Any command-line arguments supplied when the application is launched are available in the `args` array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="a7115-136">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="a7115-136">Run the app</span></span>

1. <span data-ttu-id="a7115-137">Appuyez sur <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>commande</kbd> + <kbd>entrée</kbd>) pour exécuter l’application sans débogage.</span><span class="sxs-lookup"><span data-stu-id="a7115-137">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app without debugging.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="Le terminal affiche Hello World !":::

1. <span data-ttu-id="a7115-139">Fermez la fenêtre de **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="a7115-139">Close the **Terminal** window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="a7115-140">Améliorer l’application</span><span class="sxs-lookup"><span data-stu-id="a7115-140">Enhance the app</span></span>

<span data-ttu-id="a7115-141">Améliorez l’application pour inviter l’utilisateur à entrer son nom et l’afficher avec la date et l’heure.</span><span class="sxs-lookup"><span data-stu-id="a7115-141">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="a7115-142">Dans *Program.cs*, remplacez le contenu de la `Main` méthode, qui est la ligne qui appelle `Console.WriteLine` , par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a7115-142">In *Program.cs*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="1":::

   <span data-ttu-id="a7115-143">Ce code affiche « What is your name? ».</span><span class="sxs-lookup"><span data-stu-id="a7115-143">This code displays "What is your name?"</span></span> <span data-ttu-id="a7115-144">dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="a7115-144">in the console window and waits until the user enters a string followed by the <kbd>enter</kbd> key.</span></span> <span data-ttu-id="a7115-145">Elle stocke cette chaîne dans une variable nommée `name` .</span><span class="sxs-lookup"><span data-stu-id="a7115-145">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="a7115-146">Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`.</span><span class="sxs-lookup"><span data-stu-id="a7115-146">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="a7115-147">Enfin, il affiche ces valeurs dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="a7115-147">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="a7115-148">`\n`Représente un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="a7115-148">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="a7115-149">Le signe dollar ( `$` ) devant une chaîne vous permet de placer des expressions telles que des noms de variable entre accolades dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="a7115-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="a7115-150">La valeur de l’expression est insérée dans la chaîne à la place de l’expression.</span><span class="sxs-lookup"><span data-stu-id="a7115-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="a7115-151">Cette syntaxe est appelée « [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md)».</span><span class="sxs-lookup"><span data-stu-id="a7115-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="a7115-152">Appuyez sur <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>commande</kbd> + <kbd>entrée</kbd>) pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="a7115-152">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app.</span></span>

1. <span data-ttu-id="a7115-153">Répondez à l’invite en entrant un nom et en appuyant sur <kbd>entrée</kbd>.</span><span class="sxs-lookup"><span data-stu-id="a7115-153">Respond to the prompt by entering a name and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Le terminal affiche la sortie du programme modifié":::

1. <span data-ttu-id="a7115-155">Fermez le terminal.</span><span class="sxs-lookup"><span data-stu-id="a7115-155">Close the terminal.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a7115-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a7115-156">Next steps</span></span>

<span data-ttu-id="a7115-157">Dans ce didacticiel, vous avez créé une application console .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7115-157">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="a7115-158">Dans le didacticiel suivant, vous allez déboguer l’application.</span><span class="sxs-lookup"><span data-stu-id="a7115-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a7115-159">Déboguer une application console .NET Core dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a7115-159">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio-mac.md)
