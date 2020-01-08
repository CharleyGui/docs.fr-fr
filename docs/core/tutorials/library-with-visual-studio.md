---
title: Créer une bibliothèque de classes .NET Standard dans Visual Studio
description: Découvrez comment créer une bibliothèque de classes .NET Standard écrite dans C# ou Visual Basic à l’aide de Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 160993a4dd40356cde541616a1f15f87712e8ae2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343100"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="c36dc-103">Créer une bibliothèque de .NET Standard dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c36dc-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="c36dc-104">Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application.</span><span class="sxs-lookup"><span data-stu-id="c36dc-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="c36dc-105">Une bibliothèque de classes qui cible .NET Standard 2,0 permet à votre bibliothèque d’être appelée par n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c36dc-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="c36dc-106">Quand vous avez terminé votre bibliothèque de classes, vous pouvez décider de la distribuer ou non comme un composant tiers, ou de l’inclure ou non dans un composant groupé avec une ou plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="c36dc-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="c36dc-107">Pour obtenir la liste des versions de .NET Standard et les plateformes qu’elles prennent en charge, consultez [.NET standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="c36dc-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="c36dc-108">Dans cette rubrique, vous créez une bibliothèque d’utilitaire simple qui contient une seule méthode de gestion de chaîne.</span><span class="sxs-lookup"><span data-stu-id="c36dc-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="c36dc-109">Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md), pour pouvoir l’appeler comme s’il s’agissait d’un membre de la classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c36dc-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="c36dc-110">Créer une solution Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c36dc-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="c36dc-111">Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="c36dc-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="c36dc-112">Une solution Visual Studio sert de conteneur pour un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="c36dc-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="c36dc-113">Vous ajouterez des projets connexes supplémentaires à la même solution si vous continuez avec la série de didacticiels.</span><span class="sxs-lookup"><span data-stu-id="c36dc-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="c36dc-114">Pour créer la solution vide :</span><span class="sxs-lookup"><span data-stu-id="c36dc-114">To create the blank solution:</span></span>

1. <span data-ttu-id="c36dc-115">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c36dc-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="c36dc-116">Dans la fenêtre de démarrage, choisissez **Créer un projet**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="c36dc-117">Dans la page **créer un nouveau projet** , entrez **solution** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="c36dc-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="c36dc-118">Choisissez le modèle de **solution vide** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Modèle Solution vide dans Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="c36dc-120">Dans la page **configurer votre nouveau projet** , entrez **ClassLibraryProjects** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="c36dc-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="c36dc-121">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="c36dc-122">Vous pouvez également ignorer cette étape et laisser Visual Studio créer la solution pour vous quand vous créez le projet à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="c36dc-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="c36dc-123">Recherchez les options de la solution dans la page **configurer votre nouveau projet** .</span><span class="sxs-lookup"><span data-stu-id="c36dc-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="c36dc-124">Créer un projet de bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="c36dc-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="c36dc-125">C#</span><span class="sxs-lookup"><span data-stu-id="c36dc-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="c36dc-126">Ajoutez un nouveau C# projet de bibliothèque de classes .NET standard nommé « StringLibrary » à la solution.</span><span class="sxs-lookup"><span data-stu-id="c36dc-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="c36dc-127">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter** > **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="c36dc-128">Dans la page **Ajouter un nouveau projet** , entrez **bibliothèque** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="c36dc-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="c36dc-129">Choisissez **C#** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="c36dc-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="c36dc-130">Choisissez le modèle **bibliothèque de classes (.NET standard)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="c36dc-131">Dans la page **configurer votre nouveau projet** , entrez **StringLibrary** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="c36dc-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="c36dc-132">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="c36dc-133">Assurez-vous que la bibliothèque cible la version correcte de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c36dc-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="c36dc-134">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="c36dc-135">La zone de texte de la version **cible du .NET Framework** indique que le projet cible .NET standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="c36dc-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="c36dc-137">Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="c36dc-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="c36dc-138">La bibliothèque de classes, `UtilityLibraries.StringLibrary`, contient une méthode nommée `StartsWithUpper`.</span><span class="sxs-lookup"><span data-stu-id="c36dc-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="c36dc-139">Cette méthode retourne une valeur <xref:System.Boolean> qui indique si l’instance de chaîne en cours commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="c36dc-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="c36dc-140">La norme Unicode distingue les caractères minuscules des caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="c36dc-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="c36dc-141">La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.</span><span class="sxs-lookup"><span data-stu-id="c36dc-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="c36dc-142">Dans la barre de menus, sélectionnez **Générer** > **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="c36dc-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c36dc-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="c36dc-144">Ajoutez un nouveau Visual Basic .NET Standard projet de bibliothèque de classes nommé « StringLibrary » à la solution.</span><span class="sxs-lookup"><span data-stu-id="c36dc-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="c36dc-145">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter** > **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="c36dc-146">Dans la page **Ajouter un nouveau projet** , entrez **bibliothèque** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="c36dc-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="c36dc-147">Choisissez **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="c36dc-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="c36dc-148">Choisissez le modèle **bibliothèque de classes (.NET standard)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="c36dc-149">Dans la page **configurer votre nouveau projet** , entrez **StringLibrary** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="c36dc-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="c36dc-150">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="c36dc-151">Assurez-vous que la bibliothèque cible la version correcte de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c36dc-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="c36dc-152">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="c36dc-153">La zone de texte de la version **cible du .NET Framework** indique que le projet cible .NET standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="c36dc-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="c36dc-155">Dans la boîte de dialogue **Propriétés** , effacez le texte de la zone de texte **espace de noms racine** .</span><span class="sxs-lookup"><span data-stu-id="c36dc-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="c36dc-156">Pour chaque projet, Visual Basic crée automatiquement un espace de noms qui correspond au nom du projet.</span><span class="sxs-lookup"><span data-stu-id="c36dc-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="c36dc-157">Dans ce didacticiel, vous définissez un espace de noms de niveau supérieur à l’aide du mot clé [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="c36dc-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="c36dc-158">Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="c36dc-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="c36dc-159">La bibliothèque de classes, `UtilityLibraries.StringLibrary`, contient une méthode nommée `StartsWithUpper`.</span><span class="sxs-lookup"><span data-stu-id="c36dc-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="c36dc-160">Cette méthode retourne une valeur <xref:System.Boolean> qui indique si l’instance de chaîne en cours commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="c36dc-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="c36dc-161">La norme Unicode distingue les caractères minuscules des caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="c36dc-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="c36dc-162">La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.</span><span class="sxs-lookup"><span data-stu-id="c36dc-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="c36dc-163">Dans la barre de menus, sélectionnez **Générer** > **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="c36dc-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="c36dc-164">Le projet devrait être compilé sans erreur.</span><span class="sxs-lookup"><span data-stu-id="c36dc-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c36dc-165">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c36dc-165">Next steps</span></span>

<span data-ttu-id="c36dc-166">Vous avez créé la bibliothèque correctement.</span><span class="sxs-lookup"><span data-stu-id="c36dc-166">You've successfully built the library.</span></span> <span data-ttu-id="c36dc-167">Comme vous n’avez appelé aucune de ses méthodes, vous ne savez pas si elle fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="c36dc-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="c36dc-168">L’étape suivante du développement de votre bibliothèque consiste à la tester.</span><span class="sxs-lookup"><span data-stu-id="c36dc-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c36dc-169">Créer un projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="c36dc-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
