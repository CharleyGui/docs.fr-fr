---
title: Tester une bibliothèque de classes .NET à l’aide de Visual Studio pour Mac
description: Créez un projet de test unitaire pour une bibliothèque de classes .NET. Vérifiez que la bibliothèque de classes .NET fonctionne correctement avec les tests unitaires.
ms.date: 11/18/2020
ms.openlocfilehash: 02d5aa74258ec15c5447b23246a3c7e9c61a6760
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599524"
---
# <a name="test-a-net-class-library-using-visual-studio"></a><span data-ttu-id="a31e5-104">Tester une bibliothèque de classes .NET à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a31e5-104">Test a .NET class library using Visual Studio</span></span>

<span data-ttu-id="a31e5-105">Ce didacticiel montre comment automatiser les tests unitaires en ajoutant un projet de test à une solution.</span><span class="sxs-lookup"><span data-stu-id="a31e5-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a31e5-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="a31e5-106">Prerequisites</span></span>

- <span data-ttu-id="a31e5-107">Ce didacticiel fonctionne avec la solution que vous créez dans [créer une bibliothèque de classes .net à l’aide de Visual Studio pour Mac](library-with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="a31e5-107">This tutorial works with the solution that you create in [Create a .NET class library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="a31e5-108">Créer un projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="a31e5-108">Create a unit test project</span></span>

<span data-ttu-id="a31e5-109">Les tests unitaires effectuent des tests logiciels automatisés pendant le développement et la publication.</span><span class="sxs-lookup"><span data-stu-id="a31e5-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="a31e5-110">[MSTest](https://github.com/Microsoft/testfx-docs) est l’un des trois frameworks de test que vous pouvez choisir.</span><span class="sxs-lookup"><span data-stu-id="a31e5-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="a31e5-111">Les autres sont [xUnit](https://xunit.net/) et [nunit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="a31e5-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="a31e5-112">Démarrez Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="a31e5-112">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="a31e5-113">Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans [créer une bibliothèque de classes .net à l’aide de Visual Studio pour Mac](library-with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="a31e5-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET class library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="a31e5-114">Dans le panneau **solutions** , cliquez sur la solution en <kbd>appuyant sur la touche Ctrl</kbd> `ClassLibraryProjects` et sélectionnez **Ajouter**  >  **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-114">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="a31e5-115">Dans la boîte de dialogue **nouveau projet** , sélectionnez **tests** à partir du nœud **Web et** de la console.</span><span class="sxs-lookup"><span data-stu-id="a31e5-115">In the **New Project** dialog, select **Tests** from the **Web and Console** node.</span></span> <span data-ttu-id="a31e5-116">Sélectionnez le **projet MSTest** suivi de **Next**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-116">Select the **MSTest Project** followed by **Next**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Boîte de dialogue Nouveau projet Mac de Visual Studio création d’un projet de test":::

1. <span data-ttu-id="a31e5-118">Sélectionnez **.net 5,0** comme **Framework cible** , puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-118">Select **.NET 5.0** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="a31e5-119">Nommez le nouveau projet « StringLibraryTest » et sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-119">Name the new project "StringLibraryTest" and select **Create**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="Boîte de dialogue Nouveau projet dans Visual Studio pour Mac indiquant le nom du projet":::

   <span data-ttu-id="a31e5-121">Visual Studio crée un fichier de classe avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a31e5-121">Visual Studio creates a class file with the following code:</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   <span data-ttu-id="a31e5-122">Le code source créé par le modèle de test unitaire effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a31e5-122">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="a31e5-123">Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="a31e5-123">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="a31e5-124">Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à la classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="a31e5-125">Il applique l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut à `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="a31e5-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to `TestMethod1`.</span></span>

   <span data-ttu-id="a31e5-126">Chaque méthode marquée avec [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) dans une classe de test marquée avec [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) est exécutée automatiquement lorsque le test unitaire est exécuté.</span><span class="sxs-lookup"><span data-stu-id="a31e5-126">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="a31e5-127">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="a31e5-127">Add a project reference</span></span>

<span data-ttu-id="a31e5-128">Pour que le projet de test fonctionne avec la `StringLibrary` classe, ajoutez une référence au `StringLibrary` projet.</span><span class="sxs-lookup"><span data-stu-id="a31e5-128">For the test project to work with the `StringLibrary` class, add a reference to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="a31e5-129">Dans le panneau **solutions** , cliquez sur **dépendances** <kbd>CTRL</kbd>+ clic sous **StringLibraryTest**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-129">In the **Solution** pad, <kbd>ctrl</kbd>-click **Dependencies** under **StringLibraryTest**.</span></span> <span data-ttu-id="a31e5-130">Sélectionnez **Ajouter une référence** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="a31e5-130">Select **Add Reference** from the context menu.</span></span>

1. <span data-ttu-id="a31e5-131">Dans la boîte de dialogue **références** , sélectionnez le projet **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="a31e5-131">In the **References** dialog, select the **StringLibrary** project.</span></span> <span data-ttu-id="a31e5-132">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-132">Select **OK**.</span></span>

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Boîte de dialogue Modifier les références dans Visual Studio pour Mac":::

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="a31e5-134">Ajouter et exécuter des méthodes de test unitaire</span><span class="sxs-lookup"><span data-stu-id="a31e5-134">Add and run unit test methods</span></span>

<span data-ttu-id="a31e5-135">Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut dans une classe marquée avec l'  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="a31e5-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="a31e5-136">Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.</span><span class="sxs-lookup"><span data-stu-id="a31e5-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="a31e5-137">Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="a31e5-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="a31e5-138">De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test.</span><span class="sxs-lookup"><span data-stu-id="a31e5-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="a31e5-139">Certaines des `Assert` méthodes les plus fréquemment appelées à la classe sont indiquées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="a31e5-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="a31e5-140">Méthodes d’assertion</span><span class="sxs-lookup"><span data-stu-id="a31e5-140">Assert methods</span></span>     | <span data-ttu-id="a31e5-141">Fonction</span><span class="sxs-lookup"><span data-stu-id="a31e5-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="a31e5-142">Vérifie que deux valeurs ou objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="a31e5-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="a31e5-143">L’assertion échoue si les valeurs ou les objets ne sont pas égaux.</span><span class="sxs-lookup"><span data-stu-id="a31e5-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="a31e5-144">Vérifie que deux variables d’objet référencent le même objet.</span><span class="sxs-lookup"><span data-stu-id="a31e5-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="a31e5-145">L’assertion échoue si les variables font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="a31e5-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="a31e5-146">Vérifie qu’une condition est `false`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="a31e5-147">L’assertion échoue si la condition est `true`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="a31e5-148">Vérifie qu’un objet n’est pas `null` .</span><span class="sxs-lookup"><span data-stu-id="a31e5-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="a31e5-149">L’assertion échouera si l’objet est `null`.</span><span class="sxs-lookup"><span data-stu-id="a31e5-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="a31e5-150">Vous pouvez également utiliser la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> méthode dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever.</span><span class="sxs-lookup"><span data-stu-id="a31e5-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="a31e5-151">Le test échoue si l’exception spécifiée n’est pas levée.</span><span class="sxs-lookup"><span data-stu-id="a31e5-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="a31e5-152">Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="a31e5-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="a31e5-153">Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a31e5-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a31e5-154">De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="a31e5-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="a31e5-155">Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a31e5-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="a31e5-156">Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide ( `String.Empty` )](xref:System.String.Empty), une chaîne valide sans caractères et dont <xref:System.String.Length> a la valeur 0, et une `null` chaîne qui n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="a31e5-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="a31e5-157">Vous pouvez appeler `StartsWithUpper` directement comme méthode statique et passer un seul <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="a31e5-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="a31e5-158">Vous pouvez aussi appeler `StartsWithUpper` en tant que méthode d’extension sur une `string` variable assignée à `null` .</span><span class="sxs-lookup"><span data-stu-id="a31e5-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="a31e5-159">Vous allez définir trois méthodes, chacune appelant une <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> méthode pour chaque élément d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a31e5-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="a31e5-160">Vous appellerez une surcharge de méthode qui vous permet de spécifier un message d’erreur à afficher en cas d’échec du test.</span><span class="sxs-lookup"><span data-stu-id="a31e5-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="a31e5-161">Le message identifie la chaîne à l’origine de l’échec.</span><span class="sxs-lookup"><span data-stu-id="a31e5-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="a31e5-162">Pour créer les méthodes de test:</span><span class="sxs-lookup"><span data-stu-id="a31e5-162">To create the test methods:</span></span>

1. <span data-ttu-id="a31e5-163">Ouvrez le fichier *UnitTest1.cs* et remplacez le code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a31e5-163">Open the *UnitTest1.cs* file and replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="a31e5-164">Le test de caractères majuscules dans la `TestStartsWithUpper` méthode comprend la lettre majuscule grecque alpha (u + 0391) et la lettre majuscule cyrillique em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="a31e5-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="a31e5-165">Le test de caractères minuscules dans la `TestDoesNotStartWithUpper` méthode comprend la lettre minuscule grecque alpha (u + 03B1) et la lettre minuscule cyrillique gué (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="a31e5-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="a31e5-166">Dans la barre de menus, sélectionnez **fichier**  >  **Enregistrer sous**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-166">On the menu bar, select **File** > **Save As**.</span></span> <span data-ttu-id="a31e5-167">Dans la boîte de dialogue, assurez-vous que l' **encodage** est défini sur **Unicode (UTF-8)**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-167">In the dialog, make sure that **Encoding** is set to **Unicode (UTF-8)**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Boîte de dialogue Enregistrer le fichier sous Visual Studio":::

1. <span data-ttu-id="a31e5-169">Lorsque vous êtes invité à remplacer le fichier existant, sélectionnez **remplacer**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-169">When you're asked if you want to replace the existing file, select **Replace**.</span></span>

   <span data-ttu-id="a31e5-170">Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII.</span><span class="sxs-lookup"><span data-stu-id="a31e5-170">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="a31e5-171">Lorsque cela se produit, le runtime ne décode pas correctement les caractères UTF8 en dehors de la plage ASCII, et les résultats des tests ne sont pas corrects.</span><span class="sxs-lookup"><span data-stu-id="a31e5-171">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="a31e5-172">Ouvrez le panneau **Tests unitaires** sur le côté droit de l’écran.</span><span class="sxs-lookup"><span data-stu-id="a31e5-172">Open the **Unit Tests** panel on the right side of the screen.</span></span> <span data-ttu-id="a31e5-173">Sélectionnez **Afficher**  >  les **tests** dans le menu.</span><span class="sxs-lookup"><span data-stu-id="a31e5-173">Select **View** > **Tests** from the menu.</span></span>

1. <span data-ttu-id="a31e5-174">Cliquez sur l’icône **Ancrer** pour garder le panneau ouvert.</span><span class="sxs-lookup"><span data-stu-id="a31e5-174">Click the **Dock** icon to keep the panel open.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Icône Ancrer du panneau Tests unitaires Visual Studio pour Mac":::

1. <span data-ttu-id="a31e5-176">Cliquez sur le bouton **Tout exécuter**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-176">Click the **Run All** button.</span></span>

   <span data-ttu-id="a31e5-177">Tous les tests sont concluants.</span><span class="sxs-lookup"><span data-stu-id="a31e5-177">All tests pass.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio pour Mac réussites de tests attendues":::

## <a name="handle-test-failures"></a><span data-ttu-id="a31e5-179">Gérer les échecs de test</span><span class="sxs-lookup"><span data-stu-id="a31e5-179">Handle test failures</span></span>

<span data-ttu-id="a31e5-180">Si vous effectuez un développement piloté par les tests (TDD), vous écrivez d’abord des tests et ils échouent la première fois que vous les exécutez.</span><span class="sxs-lookup"><span data-stu-id="a31e5-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="a31e5-181">Ensuite, vous ajoutez du code à l’application qui effectue la tentative de test.</span><span class="sxs-lookup"><span data-stu-id="a31e5-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="a31e5-182">Pour ce didacticiel, vous avez créé le test après avoir écrit le code d’application qu’il valide, donc vous n’avez pas vu le test échouer.</span><span class="sxs-lookup"><span data-stu-id="a31e5-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="a31e5-183">Pour vérifier qu’un test échoue quand vous pensez qu’il échoue, ajoutez une valeur non valide à l’entrée de test.</span><span class="sxs-lookup"><span data-stu-id="a31e5-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="a31e5-184">Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ».</span><span class="sxs-lookup"><span data-stu-id="a31e5-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="a31e5-185">Vous n’avez pas besoin d’enregistrer le fichier, car Visual Studio enregistre automatiquement les fichiers ouverts quand une solution est générée pour exécuter des tests.</span><span class="sxs-lookup"><span data-stu-id="a31e5-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="a31e5-186">Réexécutez les tests.</span><span class="sxs-lookup"><span data-stu-id="a31e5-186">Run the tests again.</span></span>

   <span data-ttu-id="a31e5-187">Cette fois-ci, la fenêtre de l' **Explorateur de tests** indique que deux tests ont réussi et un échec.</span><span class="sxs-lookup"><span data-stu-id="a31e5-187">This time, the **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="Fenêtre Explorateur de tests avec tests ayant échoué":::

1. <span data-ttu-id="a31e5-189"><kbd>CTRL</kbd>+ clic sur le test ayant échoué, `TestDoesNotStartWithUpper` , puis sélectionnez **Afficher** le panneau résultats dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="a31e5-189"><kbd>ctrl</kbd>-click the failed test, `TestDoesNotStartWithUpper`, and select **Show Results Pad** from the context menu.</span></span>

   <span data-ttu-id="a31e5-190">Le panneau **résultats** affiche le message produit par l’assertion : «Assert. IsFalse a échoué.</span><span class="sxs-lookup"><span data-stu-id="a31e5-190">The **Results** pad displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="a31e5-191">« Erreur » : false ; réel : True » était attendu ».</span><span class="sxs-lookup"><span data-stu-id="a31e5-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="a31e5-192">En raison de l’échec, aucune chaîne du tableau après « erreur » n’a été testée.</span><span class="sxs-lookup"><span data-stu-id="a31e5-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="Fenêtre Explorateur de tests présentant l’échec de l’assertion IsFalse":::

1. <span data-ttu-id="a31e5-194">Supprimez la chaîne « Error » que vous avez ajoutée à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="a31e5-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="a31e5-195">Réexécutez le test et les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="a31e5-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="a31e5-196">Tester la version Release de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="a31e5-196">Test the Release version of the library</span></span>

<span data-ttu-id="a31e5-197">Maintenant que les tests ont tous réussi lors de l’exécution de la version Debug de la bibliothèque, exécutez les tests sur la version Release de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a31e5-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="a31e5-198">Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.</span><span class="sxs-lookup"><span data-stu-id="a31e5-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="a31e5-199">Pour tester la version Release :</span><span class="sxs-lookup"><span data-stu-id="a31e5-199">To test the Release build:</span></span>

1. <span data-ttu-id="a31e5-200">Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.</span><span class="sxs-lookup"><span data-stu-id="a31e5-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Barre d’outils Visual Studio avec version Release mise en surbrillance":::

1. <span data-ttu-id="a31e5-202">Dans le panneau **solutions** , <kbd>cliquez</kbd>sur le projet **StringLibrary** , puis sélectionnez **générer** dans le menu contextuel pour recompiler la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a31e5-202">In the **Solution** pad, <kbd>ctrl</kbd>-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="Menu contextuel de StringLibrary avec commande build":::

1. <span data-ttu-id="a31e5-204">Réexécutez les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="a31e5-204">Run the unit tests again.</span></span>

   <span data-ttu-id="a31e5-205">Les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="a31e5-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="a31e5-206">Déboguer les tests</span><span class="sxs-lookup"><span data-stu-id="a31e5-206">Debug tests</span></span>

<span data-ttu-id="a31e5-207">Si vous utilisez Visual Studio pour Mac comme IDE, vous pouvez utiliser le même processus que celui présenté dans [Didacticiel : déboguer une application console .net à l’aide d’Visual Studio pour Mac](debugging-with-visual-studio-mac.md) pour déboguer le code à l’aide de votre projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="a31e5-207">If you're using Visual Studio for Mac as your IDE, you can use the same process shown in [Tutorial: Debug a .NET console application using Visual Studio for Mac](debugging-with-visual-studio-mac.md) to debug code using your unit test project.</span></span> <span data-ttu-id="a31e5-208">Au lieu de démarrer le projet d’application *Showcase* <kbd>, cliquez</kbd>sur le projet **StringLibraryTests** , puis sélectionnez **Démarrer le débogage du projet** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="a31e5-208">Instead of starting the *ShowCase* app project, <kbd>ctrl</kbd>-click the **StringLibraryTests** project, and select **Start Debugging Project** from the context menu.</span></span>

<span data-ttu-id="a31e5-209">Visual Studio démarre le projet de test avec le débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="a31e5-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="a31e5-210">L’exécution s’arrêtera à un point d’arrêt que vous avez ajouté au projet de test ou au code de bibliothèque sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="a31e5-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a31e5-211">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a31e5-211">Additional resources</span></span>

* [<span data-ttu-id="a31e5-212">Tests unitaires dans .NET</span><span class="sxs-lookup"><span data-stu-id="a31e5-212">Unit testing in .NET</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="a31e5-213">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a31e5-213">Next steps</span></span>

<span data-ttu-id="a31e5-214">Dans ce didacticiel, vous avez testé une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="a31e5-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="a31e5-215">Vous pouvez mettre la bibliothèque à la disposition d’autres personnes en la publiant sur [NuGet](https://nuget.org) en tant que package.</span><span class="sxs-lookup"><span data-stu-id="a31e5-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="a31e5-216">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="a31e5-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a31e5-217">Créer et publier un package (interface CLI dotnet)</span><span class="sxs-lookup"><span data-stu-id="a31e5-217">Create and publish a package (dotnet CLI)</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="a31e5-218">Si vous publiez une bibliothèque en tant que package NuGet, d’autres peuvent l’installer et l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="a31e5-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="a31e5-219">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="a31e5-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a31e5-220">Installer et utiliser un package dans Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="a31e5-220">Install and use a package in Visual Studio for Mac</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

<span data-ttu-id="a31e5-221">Une bibliothèque n’a pas besoin d’être distribuée en tant que package.</span><span class="sxs-lookup"><span data-stu-id="a31e5-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="a31e5-222">Il peut être fourni avec une application console qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="a31e5-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="a31e5-223">Pour savoir comment publier une application console, consultez le didacticiel précédent dans cette série :</span><span class="sxs-lookup"><span data-stu-id="a31e5-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a31e5-224">Publier une application console .NET à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="a31e5-224">Publish a .NET console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
