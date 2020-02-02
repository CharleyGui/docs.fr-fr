---
title: Consommer une bibliothèque .NET Standard dans Visual Studio
description: Générez une application .NET Core qui appelle les membres d’une autre bibliothèque de classes avec Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920457"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="229ad-103">Consommer une bibliothèque .NET Standard dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="229ad-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="229ad-104">Une fois que vous avez créé une bibliothèque de classes .NET Standard, que vous l’avez testée et créé une version Release de la bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants.</span><span class="sxs-lookup"><span data-stu-id="229ad-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="229ad-105">Vous pouvez procéder de deux manières :</span><span class="sxs-lookup"><span data-stu-id="229ad-105">You can do this in two ways:</span></span>

- <span data-ttu-id="229ad-106">Si la bibliothèque doit être utilisée par une seule solution (par exemple s’il s’agit d’un composant dans une seule application de grande taille), vous pouvez l’inclure en tant que projet dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="229ad-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="229ad-107">Si la bibliothèque est publiquement disponible, vous pouvez la distribuer en tant que package NuGet.</span><span class="sxs-lookup"><span data-stu-id="229ad-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="229ad-108">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="229ad-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="229ad-109">Ajoutez une application console à votre solution qui fait référence à un projet de bibliothèque .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="229ad-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="229ad-110">Créez un package NuGet qui contient un projet de bibliothèque .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="229ad-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="229ad-111">Ajouter une application console à votre solution</span><span class="sxs-lookup"><span data-stu-id="229ad-111">Add a console app to your solution</span></span>

<span data-ttu-id="229ad-112">Tout comme vous avez inclus des tests unitaires dans la même solution que votre bibliothèque de classes dans [test d’une bibliothèque de .NET standard dans Visual Studio](testing-library-with-visual-studio.md), vous pouvez inclure votre application dans le cadre de cette solution.</span><span class="sxs-lookup"><span data-stu-id="229ad-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="229ad-113">Par exemple, vous pouvez utiliser votre bibliothèque de classes dans une application console qui invite l’utilisateur à entrer une chaîne et indique si son premier caractère est une majuscule :</span><span class="sxs-lookup"><span data-stu-id="229ad-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="229ad-114">Ouvrez la solution `ClassLibraryProjects` que vous avez créée dans l’article [créer une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md) .</span><span class="sxs-lookup"><span data-stu-id="229ad-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="229ad-115">Ajoutez une nouvelle application console .NET Core nommée « ShowCase » à la solution.</span><span class="sxs-lookup"><span data-stu-id="229ad-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="229ad-116">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter** > **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="229ad-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="229ad-117">Dans la page **Ajouter un nouveau projet** , dans la zone de recherche, entrez **console** .</span><span class="sxs-lookup"><span data-stu-id="229ad-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="229ad-118">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="229ad-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="229ad-119">Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="229ad-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="229ad-120">Dans la page **configurer votre nouveau projet** , entrez **Showcase** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="229ad-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="229ad-121">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="229ad-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="229ad-122">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="229ad-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu contextuel du projet Visual Studio pour définir le projet de démarrage](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="229ad-124">Initialement, votre projet n’a pas accès à votre bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="229ad-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="229ad-125">Pour lui permettre d’appeler des méthodes dans votre bibliothèque de classes, vous créez une référence à la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="229ad-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="229ad-126">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet `ShowCase` et sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="229ad-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Menu contextuel ajouter une référence dans Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="229ad-128">Dans la boîte de dialogue **Gestionnaire de références**, sélectionnez **StringLibrary**, votre projet de bibliothèque de classe, puis sélectionnez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="229ad-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Boîte de dialogue Gestionnaire de références avec StringLibrary sélectionné](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="229ad-130">Dans la fenêtre de code du fichier *Program.cs* ou *Program. vb* , remplacez tout le code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="229ad-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="229ad-131">Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="229ad-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="229ad-132">Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="229ad-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="229ad-133">Le programme invite l’utilisateur à entrer une chaîne.</span><span class="sxs-lookup"><span data-stu-id="229ad-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="229ad-134">Il indique si la chaîne commence par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="229ad-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="229ad-135">Si l’utilisateur appuie sur la touche entrée sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.</span><span class="sxs-lookup"><span data-stu-id="229ad-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="229ad-136">Si nécessaire, changez la barre d’outils pour compiler la version **Debug** du projet `ShowCase`.</span><span class="sxs-lookup"><span data-stu-id="229ad-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="229ad-137">Compilez et exécutez le programme en sélectionnant la flèche verte sur le bouton **ShowCase**.</span><span class="sxs-lookup"><span data-stu-id="229ad-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Barre d’outils de projet Visual Studio avec le bouton déboguer](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="229ad-139">Vous pouvez déboguer et publier l’application qui utilise cette bibliothèque en suivant les étapes décrites dans [déboguer votre C# ou Visual Basic application Hello World .net core à l’aide de Visual Studio](debugging-with-visual-studio.md) et [publier votre application .net Core Hello World avec Visual Studio](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="229ad-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="229ad-140">Créer un package NuGet</span><span class="sxs-lookup"><span data-stu-id="229ad-140">Create a NuGet package</span></span>

<span data-ttu-id="229ad-141">Vous pouvez rendre votre bibliothèque de classes disponible à grande échelle en la publiant sous forme de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="229ad-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="229ad-142">Visual Studio ne prend pas en charge la création de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="229ad-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="229ad-143">Pour en créer un, vous devez utiliser les commandes CLI .NET Core :</span><span class="sxs-lookup"><span data-stu-id="229ad-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="229ad-144">Ouvrez une fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="229ad-144">Open a console window.</span></span>

   <span data-ttu-id="229ad-145">Par exemple, entrez l' **invite de commandes** dans la zone de recherche de la barre des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="229ad-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="229ad-146">Sélectionnez l’application de bureau **invite de commandes** ou appuyez sur **entrée** si elle est déjà sélectionnée dans les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="229ad-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="229ad-147">Accédez au répertoire de votre projet de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="229ad-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="229ad-148">Le répertoire contient votre code source et un fichier projet, *StringLibrary. csproj* ou *StringLibrary. vbproj*.</span><span class="sxs-lookup"><span data-stu-id="229ad-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="229ad-149">Exécutez la commande [dotnet Pack](../tools/dotnet-pack.md) pour générer un package avec l’extension *. nupkg* :</span><span class="sxs-lookup"><span data-stu-id="229ad-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="229ad-150">Si le répertoire contenant *dotnet.exe* ne se trouve pas dans votre chemin, vous pouvez trouver son emplacement en entrant `where dotnet.exe` dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="229ad-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="229ad-151">Pour plus d’informations sur la création de packages NuGet, consultez [How to Create a NuGet package with the CLI .net Core](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="229ad-151">For more information on creating NuGet packages, see [How to create a NuGet package with the .NET Core CLI](../deploying/creating-nuget-packages.md).</span></span>
