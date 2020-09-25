---
title: Tester une bibliothèque de classes .NET Standard avec .NET Core à l’aide de Visual Studio
description: Créez un projet de test unitaire pour une bibliothèque de classes .NET Core. Vérifiez que la bibliothèque de classes .NET Core fonctionne correctement avec les tests unitaires.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 04d0120622697d1e0c84fc169dfc50951cb8aa3c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177291"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio"></a><span data-ttu-id="39e22-104">Didacticiel : tester une bibliothèque de classes .NET Standard avec .NET Core à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39e22-104">Tutorial: Test a .NET Standard class library with .NET Core using Visual Studio</span></span>

<span data-ttu-id="39e22-105">Ce didacticiel montre comment automatiser les tests unitaires en ajoutant un projet de test à une solution.</span><span class="sxs-lookup"><span data-stu-id="39e22-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="39e22-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="39e22-106">Prerequisites</span></span>

- <span data-ttu-id="39e22-107">Ce didacticiel fonctionne avec la solution que vous créez dans [créer une bibliothèque de .NET standard à l’aide de Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="39e22-107">This tutorial works with the solution that you create in [Create a .NET Standard library using Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="39e22-108">Créer un projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="39e22-108">Create a unit test project</span></span>

<span data-ttu-id="39e22-109">Les tests unitaires effectuent des tests logiciels automatisés pendant le développement et la publication.</span><span class="sxs-lookup"><span data-stu-id="39e22-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="39e22-110">[MSTest](https://github.com/Microsoft/testfx-docs) est l’un des trois frameworks de test que vous pouvez choisir.</span><span class="sxs-lookup"><span data-stu-id="39e22-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="39e22-111">Les autres sont [xUnit](https://xunit.net/) et [nunit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="39e22-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="39e22-112">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="39e22-112">Start Visual Studio.</span></span>

1. <span data-ttu-id="39e22-113">Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans [créer une bibliothèque de .NET standard à l’aide de Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="39e22-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library using Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="39e22-114">Ajoutez un nouveau projet de test unitaire nommé « StringLibraryTest » à la solution.</span><span class="sxs-lookup"><span data-stu-id="39e22-114">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="39e22-115">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="39e22-115">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="39e22-116">Dans la page **Ajouter un nouveau projet** , entrez **MSTest** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="39e22-116">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="39e22-117">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="39e22-117">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="39e22-118">Choisissez le modèle **projet de test MSTest (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="39e22-118">Choose the **MSTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="39e22-119">Dans la page **configurer votre nouveau projet** , entrez **StringLibraryTest** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="39e22-119">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="39e22-120">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="39e22-120">Then choose **Create**.</span></span>

1. <span data-ttu-id="39e22-121">Visual Studio crée le projet et ouvre le fichier de classe dans la fenêtre de code avec le code suivant.</span><span class="sxs-lookup"><span data-stu-id="39e22-121">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="39e22-122">Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="39e22-122">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   <span data-ttu-id="39e22-123">Le code source créé par le modèle de test unitaire effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="39e22-123">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="39e22-124">Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="39e22-124">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="39e22-125">Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à la classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="39e22-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="39e22-126">Il applique l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut à définir `TestMethod1` en C# ou `TestSub` dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="39e22-126">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="39e22-127">Chaque méthode marquée avec [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) dans une classe de test marquée avec [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) est exécutée automatiquement lorsque le test unitaire est exécuté.</span><span class="sxs-lookup"><span data-stu-id="39e22-127">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="39e22-128">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="39e22-128">Add a project reference</span></span>

<span data-ttu-id="39e22-129">Pour que le projet de test fonctionne avec la `StringLibrary` classe, ajoutez une référence dans le projet **StringLibraryTest** au `StringLibrary` projet.</span><span class="sxs-lookup"><span data-stu-id="39e22-129">For the test project to work with the `StringLibrary` class, add a reference in the **StringLibraryTest** project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="39e22-130">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **dépendances** du projet **StringLibraryTest** et sélectionnez **Ajouter une référence de projet** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="39e22-130">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="39e22-131">Dans la boîte de dialogue **Gestionnaire de références** , développez le nœud **projets** , puis activez la case à cocher en regard de **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="39e22-131">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="39e22-132">L’ajout d’une référence à l' `StringLibrary` assembly permet au compilateur de rechercher des méthodes **StringLibrary** lors de la compilation du projet **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="39e22-132">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="39e22-133">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="39e22-133">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="39e22-134">Ajouter et exécuter des méthodes de test unitaire</span><span class="sxs-lookup"><span data-stu-id="39e22-134">Add and run unit test methods</span></span>

<span data-ttu-id="39e22-135">Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut dans une classe marquée avec l'  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="39e22-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="39e22-136">Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.</span><span class="sxs-lookup"><span data-stu-id="39e22-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="39e22-137">Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="39e22-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="39e22-138">De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test.</span><span class="sxs-lookup"><span data-stu-id="39e22-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="39e22-139">Certaines des `Assert` méthodes les plus fréquemment appelées à la classe sont indiquées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="39e22-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="39e22-140">Méthodes d’assertion</span><span class="sxs-lookup"><span data-stu-id="39e22-140">Assert methods</span></span>     | <span data-ttu-id="39e22-141">Fonction</span><span class="sxs-lookup"><span data-stu-id="39e22-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="39e22-142">Vérifie que deux valeurs ou objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="39e22-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="39e22-143">L’assertion échoue si les valeurs ou les objets ne sont pas égaux.</span><span class="sxs-lookup"><span data-stu-id="39e22-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="39e22-144">Vérifie que deux variables d’objet référencent le même objet.</span><span class="sxs-lookup"><span data-stu-id="39e22-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="39e22-145">L’assertion échoue si les variables font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="39e22-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="39e22-146">Vérifie qu’une condition est `false`.</span><span class="sxs-lookup"><span data-stu-id="39e22-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="39e22-147">L’assertion échoue si la condition est `true`.</span><span class="sxs-lookup"><span data-stu-id="39e22-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="39e22-148">Vérifie qu’un objet n’est pas `null` .</span><span class="sxs-lookup"><span data-stu-id="39e22-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="39e22-149">L’assertion échouera si l’objet est `null`.</span><span class="sxs-lookup"><span data-stu-id="39e22-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="39e22-150">Vous pouvez également utiliser la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> méthode dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever.</span><span class="sxs-lookup"><span data-stu-id="39e22-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="39e22-151">Le test échoue si l’exception spécifiée n’est pas levée.</span><span class="sxs-lookup"><span data-stu-id="39e22-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="39e22-152">Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="39e22-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="39e22-153">Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="39e22-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="39e22-154">De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="39e22-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="39e22-155">Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="39e22-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="39e22-156">Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide ( `String.Empty` )](xref:System.String.Empty), une chaîne valide sans caractères et dont <xref:System.String.Length> a la valeur 0, et une `null` chaîne qui n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="39e22-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="39e22-157">Vous pouvez appeler `StartsWithUpper` directement comme méthode statique et passer un seul <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="39e22-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="39e22-158">Vous pouvez aussi appeler `StartsWithUpper` en tant que méthode d’extension sur une `string` variable assignée à `null` .</span><span class="sxs-lookup"><span data-stu-id="39e22-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="39e22-159">Vous allez définir trois méthodes, chacune appelant une <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> méthode pour chaque élément d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="39e22-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="39e22-160">Vous appellerez une surcharge de méthode qui vous permet de spécifier un message d’erreur à afficher en cas d’échec du test.</span><span class="sxs-lookup"><span data-stu-id="39e22-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="39e22-161">Le message identifie la chaîne à l’origine de l’échec.</span><span class="sxs-lookup"><span data-stu-id="39e22-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="39e22-162">Pour créer les méthodes de test:</span><span class="sxs-lookup"><span data-stu-id="39e22-162">To create the test methods:</span></span>

1. <span data-ttu-id="39e22-163">Dans la fenêtre de code *UnitTest1.cs* ou *UnitTest1. vb* , remplacez le code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="39e22-163">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="39e22-164">Le test de caractères majuscules dans la `TestStartsWithUpper` méthode comprend la lettre majuscule grecque alpha (u + 0391) et la lettre majuscule cyrillique em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="39e22-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="39e22-165">Le test de caractères minuscules dans la `TestDoesNotStartWithUpper` méthode comprend la lettre minuscule grecque alpha (u + 03B1) et la lettre minuscule cyrillique gué (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="39e22-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="39e22-166">Dans la barre de menus, sélectionnez **fichier**  >  **Enregistrer UnitTest1.cs sous** ou enregistrer le **fichier**  >  **UnitTest1. VB sous**.</span><span class="sxs-lookup"><span data-stu-id="39e22-166">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="39e22-167">Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec l’encodage**.</span><span class="sxs-lookup"><span data-stu-id="39e22-167">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="39e22-168">![Boîte de dialogue Enregistrer le fichier sous Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="39e22-168">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="39e22-169">Dans la boîte de dialogue **Confirmer l’enregistrement sous**, sélectionnez le bouton **Oui** pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="39e22-169">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="39e22-170">Dans la boîte de dialogue **Options d’enregistrement avancées**, sélectionnez **Unicode (UTF-8 avec signature) - Page de codes 65001** dans la liste déroulante **Encodage**, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="39e22-170">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="39e22-171">![Boîte de dialogue Options d’enregistrement avancées dans Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="39e22-171">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="39e22-172">Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII.</span><span class="sxs-lookup"><span data-stu-id="39e22-172">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="39e22-173">Lorsque cela se produit, le runtime ne décode pas correctement les caractères UTF8 en dehors de la plage ASCII, et les résultats des tests ne sont pas corrects.</span><span class="sxs-lookup"><span data-stu-id="39e22-173">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="39e22-174">Dans la barre de menus, sélectionnez **tester**  >  **exécuter tous les tests**.</span><span class="sxs-lookup"><span data-stu-id="39e22-174">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="39e22-175">Si la fenêtre **Explorateur de tests** ne s’ouvre pas, ouvrez-la en sélectionnant **tester**l'  >  **Explorateur de tests**.</span><span class="sxs-lookup"><span data-stu-id="39e22-175">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="39e22-176">Les trois tests sont listés dans la section **Tests réussis** et la section **Résumé** indique le résultat de la série de tests.</span><span class="sxs-lookup"><span data-stu-id="39e22-176">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="39e22-177">![Fenêtre Explorateur de tests avec tests réussis](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="39e22-177">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="39e22-178">Gérer les échecs de test</span><span class="sxs-lookup"><span data-stu-id="39e22-178">Handle test failures</span></span>

<span data-ttu-id="39e22-179">Si vous effectuez un développement piloté par les tests (TDD), vous écrivez d’abord des tests et ils échouent la première fois que vous les exécutez.</span><span class="sxs-lookup"><span data-stu-id="39e22-179">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="39e22-180">Ensuite, vous ajoutez du code à l’application qui effectue la tentative de test.</span><span class="sxs-lookup"><span data-stu-id="39e22-180">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="39e22-181">Pour ce didacticiel, vous avez créé le test après avoir écrit le code d’application qu’il valide, donc vous n’avez pas vu le test échouer.</span><span class="sxs-lookup"><span data-stu-id="39e22-181">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="39e22-182">Pour vérifier qu’un test échoue quand vous pensez qu’il échoue, ajoutez une valeur non valide à l’entrée de test.</span><span class="sxs-lookup"><span data-stu-id="39e22-182">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="39e22-183">Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ».</span><span class="sxs-lookup"><span data-stu-id="39e22-183">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="39e22-184">Vous n’avez pas besoin d’enregistrer le fichier, car Visual Studio enregistre automatiquement les fichiers ouverts quand une solution est générée pour exécuter des tests.</span><span class="sxs-lookup"><span data-stu-id="39e22-184">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="39e22-185">Exécutez le test en sélectionnant **test**  >  **exécuter tous les tests** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="39e22-185">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="39e22-186">La fenêtre **Explorateur de tests** indique que deux tests ont réussi et qu’un test a échoué.</span><span class="sxs-lookup"><span data-stu-id="39e22-186">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="39e22-187">![Fenêtre Explorateur de tests avec tests ayant échoué](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="39e22-187">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="39e22-188">Sélectionnez le test qui a échoué, `TestDoesNotStartWith` .</span><span class="sxs-lookup"><span data-stu-id="39e22-188">Select the failed test, `TestDoesNotStartWith`.</span></span>

   <span data-ttu-id="39e22-189">La fenêtre **Explorateur de tests** affiche le message généré par l’assertion : « Échec de Assert.IsFalse.</span><span class="sxs-lookup"><span data-stu-id="39e22-189">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="39e22-190">« Erreur » : false ; réel : True » était attendu ».</span><span class="sxs-lookup"><span data-stu-id="39e22-190">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="39e22-191">En raison de l’échec, aucune chaîne du tableau après « erreur » n’a été testée.</span><span class="sxs-lookup"><span data-stu-id="39e22-191">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="39e22-192">![Fenêtre Explorateur de tests présentant l’échec de l’assertion IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="39e22-192">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="39e22-193">Supprimez la chaîne « Error » que vous avez ajoutée à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="39e22-193">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="39e22-194">Réexécutez le test et les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="39e22-194">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="39e22-195">Tester la version Release de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="39e22-195">Test the Release version of the library</span></span>

<span data-ttu-id="39e22-196">Maintenant que les tests ont tous réussi lors de l’exécution de la version Debug de la bibliothèque, exécutez les tests sur la version Release de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="39e22-196">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="39e22-197">Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.</span><span class="sxs-lookup"><span data-stu-id="39e22-197">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="39e22-198">Pour tester la version Release :</span><span class="sxs-lookup"><span data-stu-id="39e22-198">To test the Release build:</span></span>

1. <span data-ttu-id="39e22-199">Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.</span><span class="sxs-lookup"><span data-stu-id="39e22-199">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="39e22-200">![Barre d’outils Visual Studio avec version Release mise en surbrillance](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="39e22-200">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="39e22-201">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **StringLibrary** et sélectionnez **Générer** dans le menu contextuel pour recompiler la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="39e22-201">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="39e22-202">![Menu contextuel de StringLibrary avec commande build](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="39e22-202">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="39e22-203">Exécutez les tests unitaires en choisissant **test exécuter**  >  **tous les tests** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="39e22-203">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="39e22-204">Les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="39e22-204">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="39e22-205">Déboguer les tests</span><span class="sxs-lookup"><span data-stu-id="39e22-205">Debug tests</span></span>

<span data-ttu-id="39e22-206">Si vous utilisez Visual Studio comme IDE, vous pouvez utiliser le même processus que celui présenté dans [Didacticiel : déboguer une application de console .net core à l’aide de Visual Studio](debugging-with-visual-studio.md) pour déboguer le code à l’aide de votre projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="39e22-206">If you're using Visual Studio as your IDE, you can use the same process shown in [Tutorial: Debug a .NET Core console application using Visual Studio](debugging-with-visual-studio.md) to debug code using your unit test project.</span></span> <span data-ttu-id="39e22-207">Au lieu de démarrer le projet d’application *Showcase* , cliquez avec le bouton droit sur le projet **StringLibraryTests** , puis sélectionnez **déboguer les tests** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="39e22-207">Instead of starting the *ShowCase* app project, right-click the **StringLibraryTests** project, and select **Debug Tests** from the context menu.</span></span>

<span data-ttu-id="39e22-208">Visual Studio démarre le projet de test avec le débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="39e22-208">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="39e22-209">L’exécution s’arrêtera à un point d’arrêt que vous avez ajouté au projet de test ou au code de bibliothèque sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="39e22-209">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="39e22-210">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="39e22-210">Additional resources</span></span>

* [<span data-ttu-id="39e22-211">Concepts de base des tests unitaires-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39e22-211">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
* [<span data-ttu-id="39e22-212">Tests unitaires dans .NET Core et .NET Standard</span><span class="sxs-lookup"><span data-stu-id="39e22-212">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="39e22-213">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="39e22-213">Next steps</span></span>

<span data-ttu-id="39e22-214">Dans ce didacticiel, vous avez testé une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="39e22-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="39e22-215">Vous pouvez mettre la bibliothèque à la disposition d’autres personnes en la publiant sur [NuGet](https://nuget.org) en tant que package.</span><span class="sxs-lookup"><span data-stu-id="39e22-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="39e22-216">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="39e22-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39e22-217">Créer et publier un package NuGet à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39e22-217">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="39e22-218">Si vous publiez une bibliothèque en tant que package NuGet, d’autres peuvent l’installer et l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="39e22-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="39e22-219">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="39e22-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39e22-220">Installer et utiliser un package dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39e22-220">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="39e22-221">Une bibliothèque n’a pas besoin d’être distribuée en tant que package.</span><span class="sxs-lookup"><span data-stu-id="39e22-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="39e22-222">Il peut être fourni avec une application console qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="39e22-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="39e22-223">Pour savoir comment publier une application console, consultez le didacticiel précédent dans cette série :</span><span class="sxs-lookup"><span data-stu-id="39e22-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39e22-224">Publier une application console .NET Core à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39e22-224">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
