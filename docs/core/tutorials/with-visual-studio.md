---
title: Créer une application console .NET Core à l’aide de Visual Studio
description: Découvrez comment créer une application console .NET Core avec C# ou Visual Basic à l’aide de Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7ef8e17b8a42defc0858123332976d30c83f20c8
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84700430"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="f6f90-103">Didacticiel : créer une application console .NET Core à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6f90-103">Tutorial: Create a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="f6f90-104">Ce didacticiel montre comment créer et exécuter une application console .NET Core dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="f6f90-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6f90-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f6f90-105">Prerequisites</span></span>

- <span data-ttu-id="f6f90-106">[Visual Studio 2019 version 16,6 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée.</span><span class="sxs-lookup"><span data-stu-id="f6f90-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="f6f90-107">Le kit de développement logiciel (SDK) .NET Core 3,1 est automatiquement installé lorsque vous sélectionnez cette charge de travail.</span><span class="sxs-lookup"><span data-stu-id="f6f90-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="f6f90-108">Pour plus d’informations, consultez [installer le kit SDK .net core avec Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f6f90-108">For more information, see [Install the .NET Core SDK with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="f6f90-109">Créer l’application</span><span class="sxs-lookup"><span data-stu-id="f6f90-109">Create the app</span></span>

<span data-ttu-id="f6f90-110">Créez un projet d’application console .NET Core nommé « HelloWorld ».</span><span class="sxs-lookup"><span data-stu-id="f6f90-110">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="f6f90-111">Démarrez Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="f6f90-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="f6f90-112">Dans la page de démarrage, choisissez **créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="f6f90-112">On the start page, choose **Create a new project**.</span></span>

   ![Bouton créer un projet sélectionné dans la page de démarrage de Visual Studio](./media/with-visual-studio/start-window.png)

1. <span data-ttu-id="f6f90-114">Sur la page **créer un nouveau projet** , dans la zone de recherche, entrez **console** .</span><span class="sxs-lookup"><span data-stu-id="f6f90-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="f6f90-115">Ensuite, choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="f6f90-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="f6f90-116">Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="f6f90-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   ![Créer une fenêtre de projet avec les filtres sélectionnés](./media/with-visual-studio/create-new-project.png)

   > [!TIP]
   > <span data-ttu-id="f6f90-118">Si vous ne voyez pas les modèles .NET Core, vous n’avez probablement pas la charge de travail requise.</span><span class="sxs-lookup"><span data-stu-id="f6f90-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="f6f90-119">Sous le message **vous ne trouvez pas ce que vous recherchez ?** , choisissez le lien **installer d’autres outils et fonctionnalités** .</span><span class="sxs-lookup"><span data-stu-id="f6f90-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="f6f90-120">Le Visual Studio Installer s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="f6f90-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="f6f90-121">Assurez-vous que la charge de travail de **développement multiplateforme .net Core** est installée.</span><span class="sxs-lookup"><span data-stu-id="f6f90-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="f6f90-122">Dans la boîte de dialogue **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="f6f90-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="f6f90-123">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="f6f90-123">Then choose **Create**.</span></span>

   ![Configurer votre nouvelle fenêtre de projet avec les champs nom du projet, emplacement et nom de la solution](./media/with-visual-studio/configure-new-project.png)

<span data-ttu-id="f6f90-125">Le modèle crée une application « Hello World » simple.</span><span class="sxs-lookup"><span data-stu-id="f6f90-125">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="f6f90-126">Elle appelle la <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> méthode pour afficher « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="f6f90-126">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="f6f90-127">dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="f6f90-127">in the console window.</span></span>

<span data-ttu-id="f6f90-128">Le code du modèle définit une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument :</span><span class="sxs-lookup"><span data-stu-id="f6f90-128">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="f6f90-129">`Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="f6f90-129">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="f6f90-130">Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.</span><span class="sxs-lookup"><span data-stu-id="f6f90-130">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="f6f90-131">Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="f6f90-131">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="f6f90-132">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="f6f90-132">Run the app</span></span>

1. <span data-ttu-id="f6f90-133">Appuyez sur <kbd>MAJ</kbd> + <kbd>F5</kbd> pour exécuter le programme sans débogage.</span><span class="sxs-lookup"><span data-stu-id="f6f90-133">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="f6f90-134">Une fenêtre de console s’ouvre avec le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="f6f90-134">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="f6f90-135">imprimé à l’écran et certaines informations de débogage de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f6f90-135">printed on the screen and some Visual Studio debug information.</span></span>

   ![Fenêtre de console affichant « Hello World Press any key to continue »](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="f6f90-137">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="f6f90-137">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="f6f90-138">Améliorer l’application</span><span class="sxs-lookup"><span data-stu-id="f6f90-138">Enhance the app</span></span>

<span data-ttu-id="f6f90-139">Améliorez l’application pour inviter l’utilisateur à entrer son nom et l’afficher avec la date et l’heure.</span><span class="sxs-lookup"><span data-stu-id="f6f90-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="f6f90-140">Dans *Program.cs* ou *Program. vb*, remplacez le contenu de la `Main` méthode, qui est la ligne qui appelle `Console.WriteLine` , par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f6f90-140">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](./snippets/with-visual-studio/csharp/Program.cs#1)]
   [!code-vb[GettingStarted#1](./snippets/with-visual-studio/vb/Program.vb#1)]

   <span data-ttu-id="f6f90-141">Ce code affiche « What is your name? ».</span><span class="sxs-lookup"><span data-stu-id="f6f90-141">This code displays "What is your name?"</span></span> <span data-ttu-id="f6f90-142">dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="f6f90-142">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="f6f90-143">Elle stocke cette chaîne dans une variable nommée `name` .</span><span class="sxs-lookup"><span data-stu-id="f6f90-143">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="f6f90-144">Elle récupère également la valeur de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété, qui contient l’heure locale actuelle, et l’assigne à une variable nommée `date` ( `currentDate` dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f6f90-144">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="f6f90-145">Enfin, il affiche ces valeurs dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="f6f90-145">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="f6f90-146">`\n`( `vbCrLf` En Visual Basic) représente un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="f6f90-146">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="f6f90-147">Le signe dollar ( `$` ) devant une chaîne vous permet de placer des expressions telles que des noms de variable entre accolades dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="f6f90-147">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="f6f90-148">La valeur de l’expression est insérée dans la chaîne à la place de l’expression.</span><span class="sxs-lookup"><span data-stu-id="f6f90-148">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="f6f90-149">Cette syntaxe est appelée « [chaînes interpolées](../../csharp/language-reference/tokens/interpolated.md)».</span><span class="sxs-lookup"><span data-stu-id="f6f90-149">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="f6f90-150">Appuyez sur <kbd>MAJ</kbd> + <kbd>F5</kbd> pour exécuter le programme sans débogage.</span><span class="sxs-lookup"><span data-stu-id="f6f90-150">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="f6f90-151">Répondez à l’invite en entrant un nom et en appuyant sur la touche <kbd>entrée</kbd> .</span><span class="sxs-lookup"><span data-stu-id="f6f90-151">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="f6f90-153">Appuyez sur une touche pour fermer la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="f6f90-153">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f6f90-154">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f6f90-154">Next steps</span></span>

<span data-ttu-id="f6f90-155">Dans ce didacticiel, vous avez créé une application console .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6f90-155">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="f6f90-156">Dans le didacticiel suivant, vous allez déboguer l’application.</span><span class="sxs-lookup"><span data-stu-id="f6f90-156">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f6f90-157">Déboguer une application console .NET Core dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6f90-157">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
