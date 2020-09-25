---
title: Test d’une bibliothèque de classes .NET Standard avec .NET Core à l’aide de Visual Studio Code
description: Créez un projet de test unitaire pour une bibliothèque de classes .NET Core. Vérifiez que la bibliothèque de classes .NET Core fonctionne correctement avec les tests unitaires.
ms.date: 06/08/2020
ms.openlocfilehash: 6ae8f6637319cd2c8c24f3e673fb6094f36b9f2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180450"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio-code"></a><span data-ttu-id="b20b7-104">Didacticiel : tester une bibliothèque de classes .NET Standard avec .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b20b7-104">Tutorial: Test a .NET Standard class library with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="b20b7-105">Ce didacticiel montre comment automatiser les tests unitaires en ajoutant un projet de test à une solution.</span><span class="sxs-lookup"><span data-stu-id="b20b7-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b20b7-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="b20b7-106">Prerequisites</span></span>

- <span data-ttu-id="b20b7-107">Ce didacticiel fonctionne avec la solution que vous créez dans [créer une bibliothèque de .NET standard à l’aide de Visual Studio code](library-with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="b20b7-107">This tutorial works with the solution that you create in [Create a .NET Standard library using Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="b20b7-108">Créer un projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="b20b7-108">Create a unit test project</span></span>

<span data-ttu-id="b20b7-109">Les tests unitaires effectuent des tests logiciels automatisés pendant le développement et la publication.</span><span class="sxs-lookup"><span data-stu-id="b20b7-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="b20b7-110">L’infrastructure de test que vous utilisez dans ce didacticiel est MSTest.</span><span class="sxs-lookup"><span data-stu-id="b20b7-110">The testing framework that you use in this tutorial is MSTest.</span></span> <span data-ttu-id="b20b7-111">[MSTest](https://github.com/Microsoft/testfx-docs) est l’un des trois frameworks de test que vous pouvez choisir.</span><span class="sxs-lookup"><span data-stu-id="b20b7-111">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="b20b7-112">Les autres sont [xUnit](https://xunit.net/) et [nunit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="b20b7-112">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="b20b7-113">Démarrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b20b7-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="b20b7-114">Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans [créer une bibliothèque de .NET standard à l’aide de Visual Studio code](library-with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="b20b7-114">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library using Visual Studio Code](library-with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="b20b7-115">Créez un projet de test unitaire nommé « StringLibraryTest ».</span><span class="sxs-lookup"><span data-stu-id="b20b7-115">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="b20b7-116">Le modèle de projet crée un fichier UnitTest1.cs avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b20b7-116">The project template creates a UnitTest1.cs file with the following code:</span></span>

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

   <span data-ttu-id="b20b7-117">Le code source créé par le modèle de test unitaire effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b20b7-117">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="b20b7-118">Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="b20b7-118">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="b20b7-119">Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à la classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="b20b7-119">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="b20b7-120">Il applique l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut à définir `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="b20b7-120">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="b20b7-121">Chaque méthode marquée avec [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) dans une classe de test marquée avec [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) est exécutée automatiquement lorsque le test unitaire est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b20b7-121">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="b20b7-122">Ajoutez le projet de test à la solution.</span><span class="sxs-lookup"><span data-stu-id="b20b7-122">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a><span data-ttu-id="b20b7-123">Ajouter une référence au projet</span><span class="sxs-lookup"><span data-stu-id="b20b7-123">Add a project reference</span></span>

<span data-ttu-id="b20b7-124">Pour que le projet de test fonctionne avec la `StringLibrary` classe, ajoutez une référence au projet dans le `StringLibraryTest` projet `StringLibrary` .</span><span class="sxs-lookup"><span data-stu-id="b20b7-124">For the test project to work with the `StringLibrary` class, add a reference in the `StringLibraryTest` project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="b20b7-125">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b20b7-125">Run the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="b20b7-126">Ajouter et exécuter des méthodes de test unitaire</span><span class="sxs-lookup"><span data-stu-id="b20b7-126">Add and run unit test methods</span></span>

<span data-ttu-id="b20b7-127">Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut dans une classe marquée avec l'  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="b20b7-127">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="b20b7-128">Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.</span><span class="sxs-lookup"><span data-stu-id="b20b7-128">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="b20b7-129">Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="b20b7-129">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="b20b7-130">De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test.</span><span class="sxs-lookup"><span data-stu-id="b20b7-130">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="b20b7-131">Certaines des `Assert` méthodes les plus fréquemment appelées à la classe sont indiquées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="b20b7-131">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="b20b7-132">Méthodes d’assertion</span><span class="sxs-lookup"><span data-stu-id="b20b7-132">Assert methods</span></span>     | <span data-ttu-id="b20b7-133">Fonction</span><span class="sxs-lookup"><span data-stu-id="b20b7-133">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="b20b7-134">Vérifie que deux valeurs ou objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="b20b7-134">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="b20b7-135">L’assertion échoue si les valeurs ou les objets ne sont pas égaux.</span><span class="sxs-lookup"><span data-stu-id="b20b7-135">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="b20b7-136">Vérifie que deux variables d’objet référencent le même objet.</span><span class="sxs-lookup"><span data-stu-id="b20b7-136">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="b20b7-137">L’assertion échoue si les variables font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="b20b7-137">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="b20b7-138">Vérifie qu’une condition est `false`.</span><span class="sxs-lookup"><span data-stu-id="b20b7-138">Verifies that a condition is `false`.</span></span> <span data-ttu-id="b20b7-139">L’assertion échoue si la condition est `true`.</span><span class="sxs-lookup"><span data-stu-id="b20b7-139">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="b20b7-140">Vérifie qu’un objet n’est pas `null` .</span><span class="sxs-lookup"><span data-stu-id="b20b7-140">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="b20b7-141">L’assertion échouera si l’objet est `null`.</span><span class="sxs-lookup"><span data-stu-id="b20b7-141">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="b20b7-142">Vous pouvez également utiliser la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> méthode dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever.</span><span class="sxs-lookup"><span data-stu-id="b20b7-142">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="b20b7-143">Le test échoue si l’exception spécifiée n’est pas levée.</span><span class="sxs-lookup"><span data-stu-id="b20b7-143">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="b20b7-144">Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="b20b7-144">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="b20b7-145">Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b20b7-145">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b20b7-146">De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="b20b7-146">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="b20b7-147">Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b20b7-147">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b20b7-148">Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide ( `String.Empty` )](xref:System.String.Empty) et une et une `null` chaîne.</span><span class="sxs-lookup"><span data-stu-id="b20b7-148">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a and a `null` string.</span></span> <span data-ttu-id="b20b7-149">Une chaîne vide est une chaîne qui n’a pas de caractères et dont <xref:System.String.Length> a la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="b20b7-149">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="b20b7-150">Une `null` chaîne est une chaîne qui n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="b20b7-150">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="b20b7-151">Vous pouvez appeler `StartsWithUpper` directement comme méthode statique et passer un seul <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="b20b7-151">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="b20b7-152">Vous pouvez aussi appeler `StartsWithUpper` en tant que méthode d’extension sur une `string` variable assignée à `null` .</span><span class="sxs-lookup"><span data-stu-id="b20b7-152">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="b20b7-153">Vous allez définir trois méthodes, chacune appelant une <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> méthode pour chaque élément d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="b20b7-153">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="b20b7-154">Vous appellerez une surcharge de méthode qui vous permet de spécifier un message d’erreur à afficher en cas d’échec du test.</span><span class="sxs-lookup"><span data-stu-id="b20b7-154">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="b20b7-155">Le message identifie la chaîne à l’origine de l’échec.</span><span class="sxs-lookup"><span data-stu-id="b20b7-155">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="b20b7-156">Pour créer les méthodes de test:</span><span class="sxs-lookup"><span data-stu-id="b20b7-156">To create the test methods:</span></span>

1. <span data-ttu-id="b20b7-157">Ouvrez *StringLibraryTest/UnitTest1. cs* et remplacez tout le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b20b7-157">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="b20b7-158">Le test de caractères majuscules dans la `TestStartsWithUpper` méthode comprend la lettre majuscule grecque alpha (u + 0391) et la lettre majuscule cyrillique em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="b20b7-158">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="b20b7-159">Le test de caractères minuscules dans la `TestDoesNotStartWithUpper` méthode comprend la lettre minuscule grecque alpha (u + 03B1) et la lettre minuscule cyrillique gué (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="b20b7-159">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="b20b7-160">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="b20b7-160">Save your changes.</span></span>

1. <span data-ttu-id="b20b7-161">Exécuter les tests :</span><span class="sxs-lookup"><span data-stu-id="b20b7-161">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="b20b7-162">La sortie du terminal indique que tous les tests ont réussi.</span><span class="sxs-lookup"><span data-stu-id="b20b7-162">The terminal output shows that all tests passed.</span></span>

   ```output
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
    Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="b20b7-163">Gérer les échecs de test</span><span class="sxs-lookup"><span data-stu-id="b20b7-163">Handle test failures</span></span>

<span data-ttu-id="b20b7-164">Si vous effectuez un développement piloté par les tests (TDD), vous écrivez d’abord des tests et ils échouent la première fois que vous les exécutez.</span><span class="sxs-lookup"><span data-stu-id="b20b7-164">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="b20b7-165">Ensuite, vous ajoutez du code à l’application qui effectue la tentative de test.</span><span class="sxs-lookup"><span data-stu-id="b20b7-165">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="b20b7-166">Pour ce didacticiel, vous avez créé le test après avoir écrit le code d’application qu’il valide, donc vous n’avez pas vu le test échouer.</span><span class="sxs-lookup"><span data-stu-id="b20b7-166">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="b20b7-167">Pour vérifier qu’un test échoue quand vous pensez qu’il échoue, ajoutez une valeur non valide à l’entrée de test.</span><span class="sxs-lookup"><span data-stu-id="b20b7-167">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="b20b7-168">Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ».</span><span class="sxs-lookup"><span data-stu-id="b20b7-168">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="b20b7-169">Exécuter les tests :</span><span class="sxs-lookup"><span data-stu-id="b20b7-169">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="b20b7-170">La sortie du terminal indique qu’un test échoue et génère un message d’erreur pour le test qui a échoué : «Assert. IsFalse a échoué.</span><span class="sxs-lookup"><span data-stu-id="b20b7-170">The terminal output shows that one test fails, and it provides an error message for the failed test: "Assert.IsFalse failed.</span></span> <span data-ttu-id="b20b7-171">« Erreur » : false ; réel : True » était attendu ».</span><span class="sxs-lookup"><span data-stu-id="b20b7-171">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="b20b7-172">En raison de l’échec, aucune chaîne du tableau après « erreur » n’a été testée.</span><span class="sxs-lookup"><span data-stu-id="b20b7-172">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   ```output
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.
     X TestDoesNotStartWithUpper [283ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
        at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper() in C:\
   Projects\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Test Run Failed.
   Total tests: 3
        Passed: 2
        Failed: 1
    Total time: 1.7825 Seconds
   ```

1. <span data-ttu-id="b20b7-173">Supprimez la chaîne « Error » que vous avez ajoutée à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="b20b7-173">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="b20b7-174">Réexécutez le test et les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="b20b7-174">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="b20b7-175">Tester la version Release de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="b20b7-175">Test the Release version of the library</span></span>

<span data-ttu-id="b20b7-176">Maintenant que les tests ont tous réussi lors de l’exécution de la version Debug de la bibliothèque, exécutez les tests sur la version Release de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="b20b7-176">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="b20b7-177">Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.</span><span class="sxs-lookup"><span data-stu-id="b20b7-177">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="b20b7-178">Exécutez les tests avec la configuration Release Build :</span><span class="sxs-lookup"><span data-stu-id="b20b7-178">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="b20b7-179">Les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="b20b7-179">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="b20b7-180">Déboguer les tests</span><span class="sxs-lookup"><span data-stu-id="b20b7-180">Debug tests</span></span>

<span data-ttu-id="b20b7-181">Si vous utilisez Visual Studio Code comme IDE, vous pouvez utiliser le même processus que celui présenté dans [déboguer une application de console .net core à l’aide de Visual Studio code](debugging-with-visual-studio-code.md) pour déboguer le code à l’aide de votre projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="b20b7-181">If you're using Visual Studio Code as your IDE, you can use the same process shown in [Debug a .NET Core console application using Visual Studio Code](debugging-with-visual-studio-code.md) to debug code using your unit test project.</span></span> <span data-ttu-id="b20b7-182">Au lieu de démarrer le projet d’application *Showcase* , ouvrez *StringLibraryTest/UnitTest1. cs*, puis sélectionnez **exécuter tous les tests entre les** lignes 7 et 8.</span><span class="sxs-lookup"><span data-stu-id="b20b7-182">Instead of starting the *ShowCase* app project, open *StringLibraryTest/UnitTest1.cs*, and select **Run All Tests** between lines 7 and 8.</span></span> <span data-ttu-id="b20b7-183">Si vous ne parvenez pas à la trouver, appuyez sur <kbd>CTRL</kbd> + <kbd>MAJ</kbd> + <kbd>P</kbd> pour ouvrir la palette de commandes et entrez **recharger la fenêtre**.</span><span class="sxs-lookup"><span data-stu-id="b20b7-183">If you're unable to find it, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the command palette and enter **Reload Window**.</span></span>

<span data-ttu-id="b20b7-184">Visual Studio Code démarre le projet de test avec le débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="b20b7-184">Visual Studio Code starts the test project with the debugger attached.</span></span> <span data-ttu-id="b20b7-185">L’exécution s’arrêtera à un point d’arrêt que vous avez ajouté au projet de test ou au code de bibliothèque sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="b20b7-185">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b20b7-186">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b20b7-186">Additional resources</span></span>

* [<span data-ttu-id="b20b7-187">Tests unitaires dans .NET Core et .NET Standard</span><span class="sxs-lookup"><span data-stu-id="b20b7-187">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="b20b7-188">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b20b7-188">Next steps</span></span>

<span data-ttu-id="b20b7-189">Dans ce didacticiel, vous avez testé une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="b20b7-189">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="b20b7-190">Vous pouvez mettre la bibliothèque à la disposition d’autres personnes en la publiant sur [NuGet](https://nuget.org) en tant que package.</span><span class="sxs-lookup"><span data-stu-id="b20b7-190">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="b20b7-191">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="b20b7-191">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b20b7-192">Créer et publier un package à l’aide de l’interface CLI dotnet</span><span class="sxs-lookup"><span data-stu-id="b20b7-192">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="b20b7-193">Si vous publiez une bibliothèque en tant que package NuGet, d’autres peuvent l’installer et l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="b20b7-193">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="b20b7-194">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="b20b7-194">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b20b7-195">Installer et utiliser un package à l’aide de l’interface CLI dotnet</span><span class="sxs-lookup"><span data-stu-id="b20b7-195">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="b20b7-196">Une bibliothèque n’a pas besoin d’être distribuée en tant que package.</span><span class="sxs-lookup"><span data-stu-id="b20b7-196">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="b20b7-197">Il peut être fourni avec une application console qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="b20b7-197">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="b20b7-198">Pour savoir comment publier une application console, consultez le didacticiel précédent dans cette série :</span><span class="sxs-lookup"><span data-stu-id="b20b7-198">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b20b7-199">Publier une application console .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b20b7-199">Publish a .NET Core console application using Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
