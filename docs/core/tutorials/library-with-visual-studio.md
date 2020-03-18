---
title: Construire une bibliothèque de classe Standard .NET à Visual Studio
description: Apprenez à construire une bibliothèque de classe standard .NET écrite en C ou Visual Basic à l’aide de Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714018"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="7be68-103">Construire une bibliothèque .NET Standard à Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7be68-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="7be68-104">Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application.</span><span class="sxs-lookup"><span data-stu-id="7be68-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="7be68-105">Une bibliothèque de classe qui cible .NET Standard 2.0 permet à votre bibliothèque d’être appelée par toute implémentation .NET qui prend en charge cette version de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="7be68-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="7be68-106">Quand vous avez terminé votre bibliothèque de classes, vous pouvez décider de la distribuer ou non comme un composant tiers, ou de l’inclure ou non dans un composant groupé avec une ou plusieurs applications.</span><span class="sxs-lookup"><span data-stu-id="7be68-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="7be68-107">Pour une liste de versions .NET Standard et les plates-formes qu’ils prennent en charge, voir [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="7be68-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="7be68-108">Dans cette rubrique, vous créez une bibliothèque d’utilitaire simple qui contient une seule méthode de gestion de chaîne.</span><span class="sxs-lookup"><span data-stu-id="7be68-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="7be68-109">Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md), pour pouvoir l’appeler comme s’il s’agissait d’un membre de la classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7be68-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="7be68-110">Créer une solution Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7be68-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="7be68-111">Commencez par créer une solution vierge pour mettre le projet de bibliothèque de classe.</span><span class="sxs-lookup"><span data-stu-id="7be68-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="7be68-112">Une solution Visual Studio sert de conteneur pour un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="7be68-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="7be68-113">Vous ajouterez des projets supplémentaires et liés à la même solution si vous continuez avec la série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="7be68-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="7be68-114">Pour créer la solution vierge :</span><span class="sxs-lookup"><span data-stu-id="7be68-114">To create the blank solution:</span></span>

1. <span data-ttu-id="7be68-115">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7be68-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="7be68-116">Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="7be68-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="7be68-117">Sur la **page Créer un nouveau projet,** entrez la **solution** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="7be68-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="7be68-118">Choisissez le modèle **de solution Vierge,** puis choisissez **Next**.</span><span class="sxs-lookup"><span data-stu-id="7be68-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Modèle Solution vide dans Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="7be68-120">Sur la configuration de votre nouvelle page **de projet,** entrez **ClassLibraryProjets** dans la boîte **de nom du projet.**</span><span class="sxs-lookup"><span data-stu-id="7be68-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="7be68-121">Ensuite, choisissez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="7be68-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="7be68-122">Vous pouvez également sauter cette étape et laisser Visual Studio créer la solution pour vous lorsque vous créez le projet dans la prochaine étape.</span><span class="sxs-lookup"><span data-stu-id="7be68-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="7be68-123">Recherchez les options de solution sur la configuration de votre nouvelle page **de projet.**</span><span class="sxs-lookup"><span data-stu-id="7be68-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="7be68-124">Créer un projet de bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="7be68-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="7be68-125">C #</span><span class="sxs-lookup"><span data-stu-id="7be68-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="7be68-126">Ajoutez un nouveau projet de bibliothèque de classe standard CMD .NET nommé « StringLibrary » à la solution.</span><span class="sxs-lookup"><span data-stu-id="7be68-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="7be68-127">Cliquez à droite sur la solution dans **Solution Explorer** et sélectionnez **Ajouter** > **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="7be68-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="7be68-128">Sur la page **Ajouter un nouveau projet,** entrez la **bibliothèque** dans la boîte de recherche.</span><span class="sxs-lookup"><span data-stu-id="7be68-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="7be68-129">Choisissez **C dans** la liste linguistique, puis choisissez toutes les **plates-formes** de la liste de la plate-forme.</span><span class="sxs-lookup"><span data-stu-id="7be68-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="7be68-130">Choisissez le modèle **de bibliothèque de classe (.NET Standard),** puis choisissez **Next**.</span><span class="sxs-lookup"><span data-stu-id="7be68-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="7be68-131">Sur la configuration de votre nouvelle page **de projet,** entrez **StringLibrary** dans la boîte **de nom du projet.**</span><span class="sxs-lookup"><span data-stu-id="7be68-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="7be68-132">Ensuite, choisissez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="7be68-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="7be68-133">Vérifiez que la bibliothèque cible la version correcte de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="7be68-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="7be68-134">Cliquez à droite sur le projet de bibliothèque dans **Solution Explorer**, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7be68-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="7be68-135">La boîte de texte **Target Framework** montre que le projet cible .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="7be68-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="7be68-137">Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="7be68-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="7be68-138">La bibliothèque `UtilityLibraries.StringLibrary`de classe, `StartsWithUpper`, contient une méthode nommée .</span><span class="sxs-lookup"><span data-stu-id="7be68-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="7be68-139">Cette méthode <xref:System.Boolean> renvoie une valeur qui indique si l’instance de chaîne actuelle commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="7be68-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="7be68-140">La norme Unicode distingue les caractères minuscules des caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="7be68-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="7be68-141">La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.</span><span class="sxs-lookup"><span data-stu-id="7be68-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="7be68-142">Sur la barre de menu, sélectionnez **Build** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="7be68-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="7be68-143">Base visuelle</span><span class="sxs-lookup"><span data-stu-id="7be68-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="7be68-144">Ajoutez un nouveau projet de bibliothèque de classe Visual Basic .NET Standard nommé "StringLibrary" à la solution.</span><span class="sxs-lookup"><span data-stu-id="7be68-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="7be68-145">Cliquez à droite sur la solution dans **Solution Explorer** et sélectionnez **Ajouter** > **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="7be68-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="7be68-146">Sur la page **Ajouter un nouveau projet,** entrez la **bibliothèque** dans la boîte de recherche.</span><span class="sxs-lookup"><span data-stu-id="7be68-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="7be68-147">Choisissez **Visual Basic** dans la liste de langue, puis choisissez toutes les **plates-formes** de la liste De la plate-forme.</span><span class="sxs-lookup"><span data-stu-id="7be68-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="7be68-148">Choisissez le modèle **de bibliothèque de classe (.NET Standard),** puis choisissez **Next**.</span><span class="sxs-lookup"><span data-stu-id="7be68-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="7be68-149">Sur la configuration de votre nouvelle page **de projet,** entrez **StringLibrary** dans la boîte **de nom du projet.**</span><span class="sxs-lookup"><span data-stu-id="7be68-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="7be68-150">Ensuite, choisissez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="7be68-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="7be68-151">Vérifiez que la bibliothèque cible la version correcte de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="7be68-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="7be68-152">Cliquez à droite sur le projet de bibliothèque dans **Solution Explorer**, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7be68-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="7be68-153">La boîte de texte **Target Framework** montre que le projet cible .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="7be68-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="7be68-155">Dans le dialogue **Propriétés,** effacer le texte dans la boîte de texte **Root namespace.**</span><span class="sxs-lookup"><span data-stu-id="7be68-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="7be68-156">Pour chaque projet, Visual Basic crée automatiquement un espace de nom qui correspond au nom du projet.</span><span class="sxs-lookup"><span data-stu-id="7be68-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="7be68-157">Dans ce tutoriel, vous définissez un espace [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) de nom de haut niveau en utilisant le mot clé dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="7be68-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="7be68-158">Remplacez le code de la fenêtre de code par le code suivant et enregistrez le fichier :</span><span class="sxs-lookup"><span data-stu-id="7be68-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="7be68-159">La bibliothèque `UtilityLibraries.StringLibrary`de classe, `StartsWithUpper`, contient une méthode nommée .</span><span class="sxs-lookup"><span data-stu-id="7be68-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="7be68-160">Cette méthode <xref:System.Boolean> renvoie une valeur qui indique si l’instance de chaîne actuelle commence par un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="7be68-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="7be68-161">La norme Unicode distingue les caractères minuscules des caractères majuscules.</span><span class="sxs-lookup"><span data-stu-id="7be68-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="7be68-162">La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.</span><span class="sxs-lookup"><span data-stu-id="7be68-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="7be68-163">Sur la barre de menu, sélectionnez **Build** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="7be68-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="7be68-164">Le projet devrait être compilé sans erreur.</span><span class="sxs-lookup"><span data-stu-id="7be68-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7be68-165">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7be68-165">Next steps</span></span>

<span data-ttu-id="7be68-166">Vous avez créé la bibliothèque correctement.</span><span class="sxs-lookup"><span data-stu-id="7be68-166">You've successfully built the library.</span></span> <span data-ttu-id="7be68-167">Comme vous n’avez appelé aucune de ses méthodes, vous ne savez pas si elle fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="7be68-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="7be68-168">La prochaine étape dans le développement de votre bibliothèque est de la tester.</span><span class="sxs-lookup"><span data-stu-id="7be68-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7be68-169">Créer un projet d’essai unitaire</span><span class="sxs-lookup"><span data-stu-id="7be68-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
