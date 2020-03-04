---
title: Tester une bibliothèque de classes .NET Standard avec .NET Core dans Visual Studio
description: Créez un projet de test unitaire pour votre bibliothèque de classes .NET Core. Vérifiez que votre bibliothèque de classes .NET Core fonctionne correctement avec des tests unitaires.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156619"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="4c117-104">Tester une bibliothèque .NET Standard avec .NET Core dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4c117-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="4c117-105">Dans la [génération d’une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md), vous avez créé une bibliothèque de classes simple qui ajoute une méthode d’extension à la classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4c117-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="4c117-106">À présent, vous allez créer un test unitaire pour vérifier qu’elle fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="4c117-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="4c117-107">Vous allez ajouter votre projet de test unitaire à la solution créée dans l’article précédent.</span><span class="sxs-lookup"><span data-stu-id="4c117-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="4c117-108">Créer un projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="4c117-108">Create a unit test project</span></span>

<span data-ttu-id="4c117-109">Pour créer le projet de test unitaire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4c117-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="4c117-110">Ouvrez la solution `ClassLibraryProjects` que vous avez créée dans l’article [créer une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md) .</span><span class="sxs-lookup"><span data-stu-id="4c117-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="4c117-111">Ajoutez un nouveau projet de test unitaire nommé « StringLibraryTest » à la solution.</span><span class="sxs-lookup"><span data-stu-id="4c117-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="4c117-112">Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter** > **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="4c117-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="4c117-113">Dans la page **Ajouter un nouveau projet** , entrez **MSTest** dans la zone de recherche.</span><span class="sxs-lookup"><span data-stu-id="4c117-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="4c117-114">Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.</span><span class="sxs-lookup"><span data-stu-id="4c117-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="4c117-115">Choisissez le modèle **projet de test MSTest (.net Core)** , puis choisissez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="4c117-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="4c117-116">Dans la page **configurer votre nouveau projet** , entrez **StringLibraryTest** dans la zone **nom du projet** .</span><span class="sxs-lookup"><span data-stu-id="4c117-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="4c117-117">Sélectionnez ensuite **Créer**.</span><span class="sxs-lookup"><span data-stu-id="4c117-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="4c117-118">En plus d’un MSTest, vous pouvez également créer des projets de test xUnit et nUnit pour .NET Core dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4c117-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="4c117-119">Visual Studio crée le projet et ouvre le fichier de classe dans la fenêtre de code avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4c117-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="4c117-120">Le code source créé par le modèle de test unitaire effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4c117-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="4c117-121">Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="4c117-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="4c117-122">Elle applique l’attribut [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) à la classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="4c117-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="4c117-123">Chaque méthode de test dans une classe de test marquée avec l’attribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) est exécutée automatiquement quand le test unitaire est exécuté.</span><span class="sxs-lookup"><span data-stu-id="4c117-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="4c117-124">Il applique l’attribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) pour définir `TestMethod1` dans C# ou `TestSub` dans Visual Basic en tant que méthode de test pour une exécution automatique lorsque le test unitaire est exécuté.</span><span class="sxs-lookup"><span data-stu-id="4c117-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="4c117-125">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet **StringLibraryTest** puis sélectionnez **Ajouter une référence** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="4c117-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4c117-126">![menu contextuel des dépendances StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="4c117-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="4c117-127">Dans la boîte de dialogue **Gestionnaire de références**, développez le nœud **Projets**, cochez la case en regard de **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="4c117-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="4c117-128">L’ajout d’une référence à l’assembly `StringLibrary` permet au compilateur de trouver les méthodes **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="4c117-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="4c117-129">Cliquez sur le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c117-129">Select the **OK** button.</span></span> <span data-ttu-id="4c117-130">Une référence est ajoutée à votre projet de bibliothèque de classes, `StringLibrary`.</span><span class="sxs-lookup"><span data-stu-id="4c117-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![Boîte de dialogue Gestionnaire de références dans Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="4c117-132">Ajouter et exécuter des méthodes de test unitaire</span><span class="sxs-lookup"><span data-stu-id="4c117-132">Add and run unit test methods</span></span>

<span data-ttu-id="4c117-133">Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> dans une classe de test unitaire, la classe à laquelle l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> est appliqué.</span><span class="sxs-lookup"><span data-stu-id="4c117-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="4c117-134">Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.</span><span class="sxs-lookup"><span data-stu-id="4c117-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="4c117-135">Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="4c117-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="4c117-136">De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test.</span><span class="sxs-lookup"><span data-stu-id="4c117-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="4c117-137">Certaines des méthodes les plus fréquemment appelées à la classe `Assert` sont présentées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="4c117-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="4c117-138">Méthodes d’assertion</span><span class="sxs-lookup"><span data-stu-id="4c117-138">Assert methods</span></span>     | <span data-ttu-id="4c117-139">Fonction</span><span class="sxs-lookup"><span data-stu-id="4c117-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="4c117-140">Vérifie que deux valeurs ou objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="4c117-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="4c117-141">L’assertion échoue si les valeurs ou les objets ne sont pas égaux.</span><span class="sxs-lookup"><span data-stu-id="4c117-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="4c117-142">Vérifie que deux variables d’objet référencent le même objet.</span><span class="sxs-lookup"><span data-stu-id="4c117-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="4c117-143">L’assertion échoue si les variables font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="4c117-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="4c117-144">Vérifie qu’une condition est `false`.</span><span class="sxs-lookup"><span data-stu-id="4c117-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="4c117-145">L’assertion échoue si la condition est `true`.</span><span class="sxs-lookup"><span data-stu-id="4c117-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="4c117-146">Vérifie qu’un objet n’est pas `null`.</span><span class="sxs-lookup"><span data-stu-id="4c117-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="4c117-147">L’assertion échouera si l’objet est `null`.</span><span class="sxs-lookup"><span data-stu-id="4c117-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="4c117-148">Vous pouvez également utiliser la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever.</span><span class="sxs-lookup"><span data-stu-id="4c117-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="4c117-149">Le test échoue si l’exception spécifiée n’est pas levée.</span><span class="sxs-lookup"><span data-stu-id="4c117-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="4c117-150">Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="4c117-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="4c117-151">Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c117-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="4c117-152">De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="4c117-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="4c117-153">Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c117-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="4c117-154">Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide (`String.Empty`)](xref:System.String.Empty), une chaîne valide sans caractères et dont <xref:System.String.Length> est égal à 0, et une chaîne de `null` qui n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="4c117-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="4c117-155">Si `StartsWithUpper` est appelée en tant que méthode d’extension sur une instance de <xref:System.String>, une chaîne de `null` ne peut pas être passée.</span><span class="sxs-lookup"><span data-stu-id="4c117-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="4c117-156">Toutefois, vous pouvez également l’appeler directement comme méthode statique et passer un seul argument <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4c117-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="4c117-157">Vous allez définir trois méthodes, chacune appelant une méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> à plusieurs reprises pour chaque élément d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="4c117-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="4c117-158">Étant donné que la méthode de test échoue dès qu’elle trouve le premier échec, vous appelez une surcharge de méthode qui vous permet de passer une chaîne qui indique la valeur de chaîne utilisée dans l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="4c117-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="4c117-159">Pour créer les méthodes de test:</span><span class="sxs-lookup"><span data-stu-id="4c117-159">To create the test methods:</span></span>

1. <span data-ttu-id="4c117-160">Dans la fenêtre de code *UnitTest1.cs* ou *UnitTest1. vb* , remplacez le code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4c117-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="4c117-161">Le test de caractères majuscules dans la méthode `TestStartsWithUpper` comprend la lettre majuscule grecque alpha (U + 0391) et la lettre majuscule cyrillique EM (U + 041C).</span><span class="sxs-lookup"><span data-stu-id="4c117-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="4c117-162">Le test de caractères minuscules dans la méthode `TestDoesNotStartWithUpper` comprend la lettre minuscule grecque alpha (U + 03B1) et la lettre minuscule cyrillique gué (U + 0433).</span><span class="sxs-lookup"><span data-stu-id="4c117-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="4c117-163">Dans la barre de menus, sélectionnez **fichier** > **Enregistrer UnitTest1.cs sous** ou **fichier** > **Enregistrer UnitTest1. VB sous**.</span><span class="sxs-lookup"><span data-stu-id="4c117-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="4c117-164">Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec l’encodage**.</span><span class="sxs-lookup"><span data-stu-id="4c117-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4c117-165">![boîte de dialogue Enregistrer le fichier sous Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="4c117-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="4c117-166">Dans la boîte de dialogue **Confirmer l’enregistrement sous**, sélectionnez le bouton **Oui** pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="4c117-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="4c117-167">Dans la boîte de dialogue **Options d’enregistrement avancées**, sélectionnez **Unicode (UTF-8 avec signature) - Page de codes 65001** dans la liste déroulante **Encodage**, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c117-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4c117-168">![la boîte de dialogue Options d’enregistrement avancées de Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="4c117-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="4c117-169">Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII.</span><span class="sxs-lookup"><span data-stu-id="4c117-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="4c117-170">Lorsque cela se produit, le runtime ne décode pas correctement les caractères UTF8 en dehors de la plage ASCII, et les résultats des tests ne sont pas corrects.</span><span class="sxs-lookup"><span data-stu-id="4c117-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="4c117-171">Dans la barre de menus, sélectionnez **Test** > **Exécuter** > **Tous les Tests**.</span><span class="sxs-lookup"><span data-stu-id="4c117-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="4c117-172">La fenêtre **Explorateur de tests** s’ouvre et montre que les tests ont réussi.</span><span class="sxs-lookup"><span data-stu-id="4c117-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="4c117-173">Les trois tests sont listés dans la section **Tests réussis** et la section **Résumé** indique le résultat de la série de tests.</span><span class="sxs-lookup"><span data-stu-id="4c117-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4c117-174">![fenêtre de l’Explorateur de tests avec les tests réussis](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="4c117-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="4c117-175">Gérer les échecs de test</span><span class="sxs-lookup"><span data-stu-id="4c117-175">Handle test failures</span></span>

<span data-ttu-id="4c117-176">Votre série de tests n’a rencontré aucun échec : changez-la légèrement de façon à faire échouer une des méthodes de test :</span><span class="sxs-lookup"><span data-stu-id="4c117-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="4c117-177">Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ».</span><span class="sxs-lookup"><span data-stu-id="4c117-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="4c117-178">Vous n’avez pas besoin d’enregistrer le fichier, car Visual Studio enregistre automatiquement les fichiers ouverts quand une solution est générée pour exécuter des tests.</span><span class="sxs-lookup"><span data-stu-id="4c117-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="4c117-179">Exécutez le test en sélectionnant **Test** > **Exécuter** > **Tous les Tests** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="4c117-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="4c117-180">La fenêtre **Explorateur de tests** indique que deux tests ont réussi et qu’un test a échoué.</span><span class="sxs-lookup"><span data-stu-id="4c117-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4c117-181">![fenêtre de l’Explorateur de tests avec des tests ayant échoué](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="4c117-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="4c117-182">Sélectionnez le test qui a échoué, `TestDoesNotStartWith`.</span><span class="sxs-lookup"><span data-stu-id="4c117-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="4c117-183">La fenêtre **Explorateur de tests** affiche le message généré par l’assertion : « Échec de Assert.IsFalse.</span><span class="sxs-lookup"><span data-stu-id="4c117-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="4c117-184">« Erreur » : false ; réel : True » était attendu ».</span><span class="sxs-lookup"><span data-stu-id="4c117-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="4c117-185">En raison de l’échec, toutes les chaînes du tableau après « erreur » n’ont pas été testées.</span><span class="sxs-lookup"><span data-stu-id="4c117-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4c117-186">![fenêtre Explorateur de tests présentant l’échec de l’assertion IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="4c117-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="4c117-187">Annulez la modification que vous avez effectuée à l’étape 1 en supprimant la chaîne « Error ».</span><span class="sxs-lookup"><span data-stu-id="4c117-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="4c117-188">Réexécutez le test : il réussit maintenant.</span><span class="sxs-lookup"><span data-stu-id="4c117-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="4c117-189">Tester la version Release de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="4c117-189">Test the Release version of the library</span></span>

<span data-ttu-id="4c117-190">Vous avez exécuté vos tests sur la version Debug de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="4c117-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="4c117-191">Maintenant que vos tests ont tous réussi et que vous avez testé votre bibliothèque de façon adéquate, vous devez exécuter les tests une fois de plus sur la version Release de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="4c117-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="4c117-192">Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.</span><span class="sxs-lookup"><span data-stu-id="4c117-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="4c117-193">Pour tester la version Release :</span><span class="sxs-lookup"><span data-stu-id="4c117-193">To test the Release build:</span></span>

1. <span data-ttu-id="4c117-194">Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.</span><span class="sxs-lookup"><span data-stu-id="4c117-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4c117-195">![barre d’outils Visual Studio avec la version Release mise en surbrillance](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="4c117-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="4c117-196">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **StringLibrary** et sélectionnez **Générer** dans le menu contextuel pour recompiler la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="4c117-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4c117-197">![menu contextuel StringLibrary avec la commande de génération](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="4c117-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="4c117-198">Exécutez les tests unitaires en sélectionnant **Test** > **Exécuter** > **Tous les Tests** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="4c117-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="4c117-199">Les tests sont concluants.</span><span class="sxs-lookup"><span data-stu-id="4c117-199">The tests pass.</span></span>

<span data-ttu-id="4c117-200">Maintenant que vous avez fini de tester votre bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants.</span><span class="sxs-lookup"><span data-stu-id="4c117-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="4c117-201">Vous pouvez la regrouper avec une ou plusieurs applications, ou vous pouvez la distribuer comme package NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c117-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="4c117-202">Pour plus d’informations, consultez [Consommation d’une bibliothèque de classes standard .NET](consuming-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="4c117-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c117-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c117-203">See also</span></span>

- [<span data-ttu-id="4c117-204">Concepts de base des tests unitaires-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4c117-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
