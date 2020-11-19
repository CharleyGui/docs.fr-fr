---
title: Tester une bibliothèque de classes .NET à l’aide de Visual Studio
description: Découvrez comment utiliser Visual Studio pour créer et exécuter un projet de test unitaire pour une bibliothèque de classes .NET.
ms.date: 11/18/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 3d56627b937fa0ad5f8002f396ce617e09ce9d2c
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916124"
---
# <a name="tutorial-test-a-net-class-library-with-net-using-visual-studio"></a><span data-ttu-id="df31d-103">Didacticiel : tester une bibliothèque de classes .NET avec .NET à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df31d-103">Tutorial: Test a .NET class library with .NET using Visual Studio</span></span>

<span data-ttu-id="df31d-104">Ce didacticiel montre comment automatiser les tests unitaires en ajoutant un projet de test à une solution.</span><span class="sxs-lookup"><span data-stu-id="df31d-104">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="df31d-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="df31d-105">Prerequisites</span></span>

- <span data-ttu-id="df31d-106">Ce didacticiel fonctionne avec la solution que vous créez dans [créer une bibliothèque de classes .net à l’aide de Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="df31d-106">This tutorial works with the solution that you create in [Create a .NET class library using Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="df31d-107">Créer un projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="df31d-107">Create a unit test project</span></span>

<span data-ttu-id="df31d-108">Les tests unitaires effectuent des tests logiciels automatisés pendant le développement et la publication.</span><span class="sxs-lookup"><span data-stu-id="df31d-108">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="df31d-109">[MSTest](https://github.com/Microsoft/testfx-docs) est l’un des trois frameworks de test que vous pouvez choisir.</span><span class="sxs-lookup"><span data-stu-id="df31d-109">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="df31d-110">Les autres sont [xUnit](https://xunit.net/) et [nunit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="df31d-110">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="df31d-111">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df31d-111">Start Visual Studio.</span></span>

1. <span data-ttu-id="df31d-112">Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans [créer une bibliothèque de classes .net à l’aide de Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="df31d-112">Open the `ClassLibraryProjects` solution you created in [Create a .NET class library using Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="df31d-113">Ajoutez un nouveau projet de test unitaire nommé « StringLibraryTest » à la solution.</span><span class="sxs-lookup"><span data-stu-id="df31d-113">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="df31d-114">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="df31d-114">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="df31d-115">Dans la page **Ajouter un nouveau projet** , entrez **MSTest** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="df31d-115">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="df31d-116">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="df31d-116">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="df31d-117">Choisissez le modèle de **projet de test unitaire** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="df31d-117">Choose the **Unit Test Project** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="df31d-118">Dans la page **configurer votre nouveau projet** , entrez **StringLibraryTest** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="df31d-118">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="df31d-119">Ensuite, choisissez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="df31d-119">Then choose **Next**.</span></span>

   1. <span data-ttu-id="df31d-120">Sur la page **informations supplémentaires** , sélectionnez **.net 5,0 (actuel)** dans la zone **Framework cible** .</span><span class="sxs-lookup"><span data-stu-id="df31d-120">On the **Additional information** page, select **.NET 5.0 (Current)** in the **Target Framework** box.</span></span> <span data-ttu-id="df31d-121">Choisissez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="df31d-121">Then choose **Create**.</span></span>

1. <span data-ttu-id="df31d-122">Visual Studio crée le projet et ouvre le fichier de classe dans la fenêtre de code avec le code suivant.</span><span class="sxs-lookup"><span data-stu-id="df31d-122">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="df31d-123">Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.</span><span class="sxs-lookup"><span data-stu-id="df31d-123">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   <span data-ttu-id="df31d-124">Le code source créé par le modèle de test unitaire effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="df31d-124">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="df31d-125">Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="df31d-125">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="df31d-126">Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à la classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="df31d-126">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="df31d-127">Il applique l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut à définir `TestMethod1` en C# ou `TestSub` dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="df31d-127">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="df31d-128">Chaque méthode marquée avec [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) dans une classe de test marquée avec [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) est exécutée automatiquement lorsque le test unitaire est exécuté.</span><span class="sxs-lookup"><span data-stu-id="df31d-128">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="df31d-129">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="df31d-129">Add a project reference</span></span>

<span data-ttu-id="df31d-130">Pour que le projet de test fonctionne avec la `StringLibrary` classe, ajoutez une référence dans le projet **StringLibraryTest** au `StringLibrary` projet.</span><span class="sxs-lookup"><span data-stu-id="df31d-130">For the test project to work with the `StringLibrary` class, add a reference in the **StringLibraryTest** project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="df31d-131">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **dépendances** du projet **StringLibraryTest** et sélectionnez **Ajouter une référence de projet** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="df31d-131">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="df31d-132">Dans la boîte de dialogue **Gestionnaire de références** , développez le nœud **projets** , puis activez la case à cocher en regard de **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="df31d-132">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="df31d-133">L’ajout d’une référence à l' `StringLibrary` assembly permet au compilateur de rechercher des méthodes **StringLibrary** lors de la compilation du projet **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="df31d-133">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="df31d-134">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="df31d-134">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="df31d-135">Ajouter et exécuter des méthodes de test unitaire</span><span class="sxs-lookup"><span data-stu-id="df31d-135">Add and run unit test methods</span></span>

<span data-ttu-id="df31d-136">Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut dans une classe marquée avec l'  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="df31d-136">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="df31d-137">Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.</span><span class="sxs-lookup"><span data-stu-id="df31d-137">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="df31d-138">Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="df31d-138">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="df31d-139">De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test.</span><span class="sxs-lookup"><span data-stu-id="df31d-139">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="df31d-140">Certaines des `Assert` méthodes les plus fréquemment appelées à la classe sont indiquées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="df31d-140">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="df31d-141">Méthodes d’assertion</span><span class="sxs-lookup"><span data-stu-id="df31d-141">Assert methods</span></span>     | <span data-ttu-id="df31d-142">Fonction</span><span class="sxs-lookup"><span data-stu-id="df31d-142">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="df31d-143">Vérifie que deux valeurs ou objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="df31d-143">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="df31d-144">L’assertion échoue si les valeurs ou les objets ne sont pas égaux.</span><span class="sxs-lookup"><span data-stu-id="df31d-144">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="df31d-145">Vérifie que deux variables d’objet référencent le même objet.</span><span class="sxs-lookup"><span data-stu-id="df31d-145">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="df31d-146">L’assertion échoue si les variables font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="df31d-146">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="df31d-147">Vérifie qu’une condition est `false`.</span><span class="sxs-lookup"><span data-stu-id="df31d-147">Verifies that a condition is `false`.</span></span> <span data-ttu-id="df31d-148">L’assertion échoue si la condition est `true`.</span><span class="sxs-lookup"><span data-stu-id="df31d-148">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="df31d-149">Vérifie qu’un objet n’est pas `null` .</span><span class="sxs-lookup"><span data-stu-id="df31d-149">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="df31d-150">L’assertion échouera si l’objet est `null`.</span><span class="sxs-lookup"><span data-stu-id="df31d-150">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="df31d-151">Vous pouvez également utiliser la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> méthode dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever.</span><span class="sxs-lookup"><span data-stu-id="df31d-151">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="df31d-152">Le test échoue si l’exception spécifiée n’est pas levée.</span><span class="sxs-lookup"><span data-stu-id="df31d-152">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="df31d-153">Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="df31d-153">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="df31d-154">Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df31d-154">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="df31d-155">De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="df31d-155">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="df31d-156">Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="df31d-156">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="df31d-157">Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide ( `String.Empty` )](xref:System.String.Empty), une chaîne valide sans caractères et dont <xref:System.String.Length> a la valeur 0, et une `null` chaîne qui n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="df31d-157">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="df31d-158">Vous pouvez appeler `StartsWithUpper` directement comme méthode statique et passer un seul <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="df31d-158">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="df31d-159">Vous pouvez aussi appeler `StartsWithUpper` en tant que méthode d’extension sur une `string` variable assignée à `null` .</span><span class="sxs-lookup"><span data-stu-id="df31d-159">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="df31d-160">Vous allez définir trois méthodes, chacune appelant une <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> méthode pour chaque élément d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="df31d-160">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="df31d-161">Vous appellerez une surcharge de méthode qui vous permet de spécifier un message d’erreur à afficher en cas d’échec du test.</span><span class="sxs-lookup"><span data-stu-id="df31d-161">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="df31d-162">Le message identifie la chaîne à l’origine de l’échec.</span><span class="sxs-lookup"><span data-stu-id="df31d-162">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="df31d-163">Pour créer les méthodes de test:</span><span class="sxs-lookup"><span data-stu-id="df31d-163">To create the test methods:</span></span>

1. <span data-ttu-id="df31d-164">Dans la fenêtre de code *UnitTest1.cs* ou *UnitTest1. vb* , remplacez le code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="df31d-164">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="df31d-165">Le test de caractères majuscules dans la `TestStartsWithUpper` méthode comprend la lettre majuscule grecque alpha (u + 0391) et la lettre majuscule cyrillique em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="df31d-165">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="df31d-166">Le test de caractères minuscules dans la `TestDoesNotStartWithUpper` méthode comprend la lettre minuscule grecque alpha (u + 03B1) et la lettre minuscule cyrillique gué (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="df31d-166">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="df31d-167">Dans la barre de menus, sélectionnez **fichier**  >  **Enregistrer UnitTest1.cs sous** ou enregistrer le **fichier**  >  **UnitTest1. VB sous**.</span><span class="sxs-lookup"><span data-stu-id="df31d-167">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="df31d-168">Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec l’encodage**.</span><span class="sxs-lookup"><span data-stu-id="df31d-168">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/save-file-as-dialog.png" alt-text="Boîte de dialogue Enregistrer le fichier sous Visual Studio":::

1. <span data-ttu-id="df31d-170">Dans la boîte de dialogue **Confirmer l’enregistrement sous**, sélectionnez le bouton **Oui** pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="df31d-170">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="df31d-171">Dans la boîte de dialogue **Options d’enregistrement avancées**, sélectionnez **Unicode (UTF-8 avec signature) - Page de codes 65001** dans la liste déroulante **Encodage**, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="df31d-171">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/advanced-save-options.png" alt-text="Boîte de dialogue Options d’enregistrement avancées dans Visual Studio":::

   <span data-ttu-id="df31d-173">Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII.</span><span class="sxs-lookup"><span data-stu-id="df31d-173">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="df31d-174">Lorsque cela se produit, le runtime ne décode pas correctement les caractères UTF8 en dehors de la plage ASCII, et les résultats des tests ne sont pas corrects.</span><span class="sxs-lookup"><span data-stu-id="df31d-174">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="df31d-175">Dans la barre de menus, sélectionnez **tester**  >  **exécuter tous les tests**.</span><span class="sxs-lookup"><span data-stu-id="df31d-175">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="df31d-176">Si la fenêtre **Explorateur de tests** ne s’ouvre pas, ouvrez-la en sélectionnant **tester** l'  >  **Explorateur de tests**.</span><span class="sxs-lookup"><span data-stu-id="df31d-176">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="df31d-177">Les trois tests sont listés dans la section **Tests réussis** et la section **Résumé** indique le résultat de la série de tests.</span><span class="sxs-lookup"><span data-stu-id="df31d-177">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/test-explorer-window.png" alt-text="Fenêtre Explorateur de tests avec tests réussis":::

## <a name="handle-test-failures"></a><span data-ttu-id="df31d-179">Gérer les échecs de test</span><span class="sxs-lookup"><span data-stu-id="df31d-179">Handle test failures</span></span>

<span data-ttu-id="df31d-180">Si vous effectuez un développement piloté par les tests (TDD), vous écrivez d’abord des tests et ils échouent la première fois que vous les exécutez.</span><span class="sxs-lookup"><span data-stu-id="df31d-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="df31d-181">Ensuite, vous ajoutez du code à l’application qui effectue la tentative de test.</span><span class="sxs-lookup"><span data-stu-id="df31d-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="df31d-182">Pour ce didacticiel, vous avez créé le test après avoir écrit le code d’application qu’il valide, donc vous n’avez pas vu le test échouer.</span><span class="sxs-lookup"><span data-stu-id="df31d-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="df31d-183">Pour vérifier qu’un test échoue quand vous pensez qu’il échoue, ajoutez une valeur non valide à l’entrée de test.</span><span class="sxs-lookup"><span data-stu-id="df31d-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="df31d-184">Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ».</span><span class="sxs-lookup"><span data-stu-id="df31d-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="df31d-185">Vous n’avez pas besoin d’enregistrer le fichier, car Visual Studio enregistre automatiquement les fichiers ouverts quand une solution est générée pour exécuter des tests.</span><span class="sxs-lookup"><span data-stu-id="df31d-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="df31d-186">Exécutez le test en sélectionnant **test**  >  **exécuter tous les tests** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="df31d-186">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="df31d-187">La fenêtre **Explorateur de tests** indique que deux tests ont réussi et qu’un test a échoué.</span><span class="sxs-lookup"><span data-stu-id="df31d-187">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/failed-test-window.png" alt-text="Fenêtre Explorateur de tests avec tests ayant échoué":::

1. <span data-ttu-id="df31d-189">Sélectionnez le test qui a échoué, `TestDoesNotStartWith` .</span><span class="sxs-lookup"><span data-stu-id="df31d-189">Select the failed test, `TestDoesNotStartWith`.</span></span>

   <span data-ttu-id="df31d-190">La fenêtre **Explorateur de tests** affiche le message généré par l’assertion : « Échec de Assert.IsFalse.</span><span class="sxs-lookup"><span data-stu-id="df31d-190">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="df31d-191">« Erreur » : false ; réel : True » était attendu ».</span><span class="sxs-lookup"><span data-stu-id="df31d-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="df31d-192">En raison de l’échec, aucune chaîne du tableau après « erreur » n’a été testée.</span><span class="sxs-lookup"><span data-stu-id="df31d-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/failed-test-detail.png" alt-text="Fenêtre Explorateur de tests présentant l’échec de l’assertion IsFalse":::

1. <span data-ttu-id="df31d-194">Supprimez la chaîne « Error » que vous avez ajoutée à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="df31d-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="df31d-195">Réexécutez le test et les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="df31d-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="df31d-196">Tester la version Release de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="df31d-196">Test the Release version of the library</span></span>

<span data-ttu-id="df31d-197">Maintenant que les tests ont tous réussi lors de l’exécution de la version Debug de la bibliothèque, exécutez les tests sur la version Release de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="df31d-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="df31d-198">Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.</span><span class="sxs-lookup"><span data-stu-id="df31d-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="df31d-199">Pour tester la version Release :</span><span class="sxs-lookup"><span data-stu-id="df31d-199">To test the Release build:</span></span>

1. <span data-ttu-id="df31d-200">Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.</span><span class="sxs-lookup"><span data-stu-id="df31d-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png" alt-text="Barre d’outils Visual Studio avec version Release mise en surbrillance":::

1. <span data-ttu-id="df31d-202">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **StringLibrary** et sélectionnez **Générer** dans le menu contextuel pour recompiler la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="df31d-202">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/build-library-context-menu.png" alt-text="Menu contextuel de StringLibrary avec commande build":::

1. <span data-ttu-id="df31d-204">Exécutez les tests unitaires en choisissant **test exécuter**  >  **tous les tests** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="df31d-204">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="df31d-205">Les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="df31d-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="df31d-206">Déboguer les tests</span><span class="sxs-lookup"><span data-stu-id="df31d-206">Debug tests</span></span>

<span data-ttu-id="df31d-207">Si vous utilisez Visual Studio comme IDE, vous pouvez utiliser le même processus que celui présenté dans [Didacticiel : déboguer une application console .net à l’aide de Visual Studio](debugging-with-visual-studio.md) pour déboguer du code à l’aide de votre projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="df31d-207">If you're using Visual Studio as your IDE, you can use the same process shown in [Tutorial: Debug a .NET console application using Visual Studio](debugging-with-visual-studio.md) to debug code using your unit test project.</span></span> <span data-ttu-id="df31d-208">Au lieu de démarrer le projet d’application *Showcase* , cliquez avec le bouton droit sur le projet **StringLibraryTests** , puis sélectionnez **déboguer les tests** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="df31d-208">Instead of starting the *ShowCase* app project, right-click the **StringLibraryTests** project, and select **Debug Tests** from the context menu.</span></span>

<span data-ttu-id="df31d-209">Visual Studio démarre le projet de test avec le débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="df31d-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="df31d-210">L’exécution s’arrêtera à un point d’arrêt que vous avez ajouté au projet de test ou au code de bibliothèque sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="df31d-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="df31d-211">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="df31d-211">Additional resources</span></span>

* [<span data-ttu-id="df31d-212">Concepts de base des tests unitaires-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df31d-212">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
* [<span data-ttu-id="df31d-213">Tests unitaires dans .NET</span><span class="sxs-lookup"><span data-stu-id="df31d-213">Unit testing in .NET</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="df31d-214">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="df31d-214">Next steps</span></span>

<span data-ttu-id="df31d-215">Dans ce didacticiel, vous avez testé une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="df31d-215">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="df31d-216">Vous pouvez mettre la bibliothèque à la disposition d’autres personnes en la publiant sur [NuGet](https://nuget.org) en tant que package.</span><span class="sxs-lookup"><span data-stu-id="df31d-216">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="df31d-217">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="df31d-217">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df31d-218">Créer et publier un package NuGet à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df31d-218">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="df31d-219">Si vous publiez une bibliothèque en tant que package NuGet, d’autres peuvent l’installer et l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="df31d-219">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="df31d-220">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="df31d-220">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df31d-221">Installer et utiliser un package dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df31d-221">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="df31d-222">Une bibliothèque n’a pas besoin d’être distribuée en tant que package.</span><span class="sxs-lookup"><span data-stu-id="df31d-222">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="df31d-223">Il peut être fourni avec une application console qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="df31d-223">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="df31d-224">Pour savoir comment publier une application console, consultez le didacticiel précédent dans cette série :</span><span class="sxs-lookup"><span data-stu-id="df31d-224">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df31d-225">Publier une application console .NET à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df31d-225">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
