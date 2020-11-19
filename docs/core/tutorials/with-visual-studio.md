---
title: Créer une application console .NET à l’aide de Visual Studio
description: Découvrez comment créer une application console .NET avec C# ou Visual Basic à l’aide de Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: e395122e59f17ed66bbd9d83b01610993f663ce1
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915918"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a><span data-ttu-id="68048-103">Didacticiel : créer une application console .NET à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="68048-103">Tutorial: Create a .NET console application using Visual Studio</span></span>

<span data-ttu-id="68048-104">Ce didacticiel montre comment créer et exécuter une application console .NET dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="68048-104">This tutorial shows how to create and run a .NET console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68048-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="68048-105">Prerequisites</span></span>

- <span data-ttu-id="68048-106">[Visual Studio 2019 version 16,8 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée.</span><span class="sxs-lookup"><span data-stu-id="68048-106">[Visual Studio 2019 version 16.8 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="68048-107">Le kit de développement logiciel (SDK) .NET 5,0 est automatiquement installé lorsque vous sélectionnez cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="68048-107">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="68048-108">Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) .net avec Visual Studio](../install/windows.md#install-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="68048-108">For more information, see [Install the .NET SDK with Visual Studio](../install/windows.md#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="68048-109">Créer l’application</span><span class="sxs-lookup"><span data-stu-id="68048-109">Create the app</span></span>

<span data-ttu-id="68048-110">Créez un projet d’application console .NET nommé « HelloWorld ».</span><span class="sxs-lookup"><span data-stu-id="68048-110">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="68048-111">Démarrez Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="68048-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="68048-112">Sélectionnez **Outils**  >  **options**  >  **environnement**  >  **Aperçu fonctionnalités**, puis sélectionnez **Afficher tous les modèles .net core dans le nouveau projet (nécessite un redémarrage)**.</span><span class="sxs-lookup"><span data-stu-id="68048-112">Select **Tools** > **Options** > **Environment** > **Preview features**, and then select **Show all .NET Core templates in the New project (requires restart)**.</span></span>

   :::image type="content" source="media/with-visual-studio/dotnet-options.png" alt-text="Afficher tous les modèles .NET (option)":::

1. <span data-ttu-id="68048-114">Fermez et rouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="68048-114">Close and reopen Visual Studio.</span></span>

1. <span data-ttu-id="68048-115">Dans la page de démarrage, choisissez **créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="68048-115">On the start page, choose **Create a new project**.</span></span>

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Bouton créer un projet sélectionné dans la page de démarrage de Visual Studio":::

1. <span data-ttu-id="68048-117">Sur la page **créer un nouveau projet** , dans la zone de recherche, entrez **console** .</span><span class="sxs-lookup"><span data-stu-id="68048-117">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="68048-118">Ensuite, choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="68048-118">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="68048-119">Choisissez le modèle **application console** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="68048-119">Choose the **Console Application** template, and then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="Créer une fenêtre de projet avec les filtres sélectionnés":::

   > [!TIP]
   > <span data-ttu-id="68048-121">Si vous ne voyez pas les modèles .NET, vous n’avez probablement pas la charge de travail requise.</span><span class="sxs-lookup"><span data-stu-id="68048-121">If you don't see the .NET templates, you're probably missing the required workload.</span></span> <span data-ttu-id="68048-122">Sous le message **vous ne trouvez pas ce que vous recherchez ?** , choisissez le lien **installer d’autres outils et fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="68048-122">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="68048-123">Le Visual Studio Installer s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="68048-123">The Visual Studio Installer opens.</span></span> <span data-ttu-id="68048-124">Assurez-vous que la charge de travail de **développement multiplateforme .net Core** est installée.</span><span class="sxs-lookup"><span data-stu-id="68048-124">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="68048-125">Dans la boîte de dialogue **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="68048-125">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="68048-126">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="68048-126">Then choose **Create**.</span></span>

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="Configurer votre nouvelle fenêtre de projet avec les champs nom du projet, emplacement et nom de la solution":::

1. <span data-ttu-id="68048-128">Dans la boîte de dialogue **informations supplémentaires** , sélectionnez **.net 5,0 (actuel)**, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="68048-128">In the **Additional information** dialog, select **.NET 5.0 (Current)**, and then select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="Boîte de dialogue d’informations supplémentaires":::

<span data-ttu-id="68048-130">Le modèle crée une application « Hello World » simple.</span><span class="sxs-lookup"><span data-stu-id="68048-130">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="68048-131">Elle appelle la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> méthode pour afficher « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="68048-131">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="68048-132">dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="68048-132">in the console window.</span></span>

<span data-ttu-id="68048-133">Le code du modèle définit une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument :</span><span class="sxs-lookup"><span data-stu-id="68048-133">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine("Hello World!")
    End Sub
End Module
```

<span data-ttu-id="68048-134">`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="68048-134">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="68048-135">Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.</span><span class="sxs-lookup"><span data-stu-id="68048-135">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="68048-136">Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="68048-136">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="68048-137">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="68048-137">Run the app</span></span>

1. <span data-ttu-id="68048-138">Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour exécuter le programme sans débogage.</span><span class="sxs-lookup"><span data-stu-id="68048-138">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="68048-139">Une fenêtre de console s’ouvre avec le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="68048-139">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="68048-140">imprimé à l’écran.</span><span class="sxs-lookup"><span data-stu-id="68048-140">printed on the screen.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Fenêtre de console affichant « Hello World Press any key to continue »":::

1. <span data-ttu-id="68048-142">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="68048-142">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="68048-143">Améliorer l’application</span><span class="sxs-lookup"><span data-stu-id="68048-143">Enhance the app</span></span>

<span data-ttu-id="68048-144">Améliorez l’application pour inviter l’utilisateur à entrer son nom et l’afficher avec la date et l’heure.</span><span class="sxs-lookup"><span data-stu-id="68048-144">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="68048-145">Dans *Program.cs* ou *Program. vb*, remplacez le contenu de la `Main` méthode, qui est la ligne qui appelle `Console.WriteLine` , par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="68048-145">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="68048-146">Ce code affiche une invite dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="68048-146">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="68048-147">Elle stocke cette chaîne dans une variable nommée `name` .</span><span class="sxs-lookup"><span data-stu-id="68048-147">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="68048-148">Elle récupère également la valeur de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété, qui contient l’heure locale actuelle, et l’assigne à une variable nommée `date` ( `currentDate` dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="68048-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="68048-149">Et affiche ces valeurs dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="68048-149">And it displays these values in the console window.</span></span> <span data-ttu-id="68048-150">Enfin, il affiche une invite dans la fenêtre de console et appelle la <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> méthode pour attendre l’entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="68048-150">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="68048-151">`\n`( `vbCrLf` En Visual Basic) représente un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="68048-151">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="68048-152">Le signe dollar ( `$` ) devant une chaîne vous permet de placer des expressions telles que des noms de variable entre accolades dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="68048-152">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="68048-153">La valeur de l’expression est insérée dans la chaîne à la place de l’expression.</span><span class="sxs-lookup"><span data-stu-id="68048-153">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="68048-154">Cette syntaxe est appelée « [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md)».</span><span class="sxs-lookup"><span data-stu-id="68048-154">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="68048-155">Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour exécuter le programme sans débogage.</span><span class="sxs-lookup"><span data-stu-id="68048-155">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="68048-156">Répondez à l’invite en entrant un nom et en appuyant sur la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="68048-156">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="Fenêtre de console avec la sortie du programme modifié":::

1. <span data-ttu-id="68048-158">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="68048-158">Press any key to close the console window.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="68048-159">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="68048-159">Additional resources</span></span>

- [<span data-ttu-id="68048-160">Versions actuelles et versions de support à long terme</span><span class="sxs-lookup"><span data-stu-id="68048-160">Current releases and long-term support releases</span></span>](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a><span data-ttu-id="68048-161">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="68048-161">Next steps</span></span>

<span data-ttu-id="68048-162">Dans ce didacticiel, vous avez créé une application console .NET.</span><span class="sxs-lookup"><span data-stu-id="68048-162">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="68048-163">Dans le didacticiel suivant, vous allez déboguer l’application.</span><span class="sxs-lookup"><span data-stu-id="68048-163">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="68048-164">Débogage d’une application console .NET à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="68048-164">Debug a .NET console application using Visual Studio</span></span>](debugging-with-visual-studio.md)
