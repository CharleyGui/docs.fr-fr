---
title: Test d’une bibliothèque de classes .NET Standard avec .NET Core dans Visual Studio Code
description: Créez un projet de test unitaire pour une bibliothèque de classes .NET Core. Vérifiez que la bibliothèque de classes .NET Core fonctionne correctement avec les tests unitaires.
ms.date: 05/29/2020
ms.openlocfilehash: be227453bd441028cc6ce348c00fad944140238f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292188"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio-code"></a><span data-ttu-id="68355-104">Didacticiel : tester une bibliothèque .NET Standard avec .NET Core dans Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="68355-104">Tutorial: Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>

<span data-ttu-id="68355-105">Ce didacticiel montre comment automatiser les tests unitaires en ajoutant un projet de test à une solution.</span><span class="sxs-lookup"><span data-stu-id="68355-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68355-106">Prérequis</span><span class="sxs-lookup"><span data-stu-id="68355-106">Prerequisites</span></span>

- <span data-ttu-id="68355-107">Ce didacticiel fonctionne avec la solution que vous créez dans [créer une bibliothèque de .NET standard dans Visual Studio code](library-with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="68355-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="68355-108">Créer un projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="68355-108">Create a unit test project</span></span>

1. <span data-ttu-id="68355-109">Ouvrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="68355-109">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="68355-110">Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans [créer une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="68355-110">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="68355-111">Créez un projet de test unitaire nommé « StringLibraryTest ».</span><span class="sxs-lookup"><span data-stu-id="68355-111">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="68355-112">Le modèle de projet crée un fichier UnitTest1.cs avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="68355-112">The project template creates a UnitTest1.cs file with the following code:</span></span>

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

   <span data-ttu-id="68355-113">Le code source créé par le modèle de test unitaire effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="68355-113">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="68355-114">Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="68355-114">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="68355-115">Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à la classe `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="68355-115">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="68355-116">Il applique l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut à définir `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="68355-116">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="68355-117">Chaque méthode marquée avec [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) dans une classe de test marquée avec [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) est exécutée automatiquement lorsque le test unitaire est exécuté.</span><span class="sxs-lookup"><span data-stu-id="68355-117">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

   > [!NOTE]
   > <span data-ttu-id="68355-118">MSTest est l’un des trois frameworks de test que vous pouvez choisir.</span><span class="sxs-lookup"><span data-stu-id="68355-118">MSTest is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="68355-119">Les autres sont xUnit et nUnit.</span><span class="sxs-lookup"><span data-stu-id="68355-119">The others are xUnit and nUnit.</span></span>

1. <span data-ttu-id="68355-120">Ajoutez le projet de test à la solution.</span><span class="sxs-lookup"><span data-stu-id="68355-120">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

1. <span data-ttu-id="68355-121">Créez une référence de projet au projet de bibliothèque de classes en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="68355-121">Create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="68355-122">Ajouter et exécuter des méthodes de test unitaire</span><span class="sxs-lookup"><span data-stu-id="68355-122">Add and run unit test methods</span></span>

<span data-ttu-id="68355-123">Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut dans une classe marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="68355-123">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="68355-124">Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.</span><span class="sxs-lookup"><span data-stu-id="68355-124">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="68355-125">Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="68355-125">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="68355-126">De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test.</span><span class="sxs-lookup"><span data-stu-id="68355-126">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="68355-127">Certaines des `Assert` méthodes les plus fréquemment appelées à la classe sont indiquées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="68355-127">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="68355-128">Méthodes d’assertion</span><span class="sxs-lookup"><span data-stu-id="68355-128">Assert methods</span></span>     | <span data-ttu-id="68355-129">Fonction</span><span class="sxs-lookup"><span data-stu-id="68355-129">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="68355-130">Vérifie que deux valeurs ou objets sont égaux.</span><span class="sxs-lookup"><span data-stu-id="68355-130">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="68355-131">L’assertion échoue si les valeurs ou les objets ne sont pas égaux.</span><span class="sxs-lookup"><span data-stu-id="68355-131">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="68355-132">Vérifie que deux variables d’objet référencent le même objet.</span><span class="sxs-lookup"><span data-stu-id="68355-132">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="68355-133">L’assertion échoue si les variables font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="68355-133">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="68355-134">Vérifie qu’une condition est `false`.</span><span class="sxs-lookup"><span data-stu-id="68355-134">Verifies that a condition is `false`.</span></span> <span data-ttu-id="68355-135">L’assertion échoue si la condition est `true`.</span><span class="sxs-lookup"><span data-stu-id="68355-135">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="68355-136">Vérifie qu’un objet n’est pas `null` .</span><span class="sxs-lookup"><span data-stu-id="68355-136">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="68355-137">L’assertion échouera si l’objet est `null`.</span><span class="sxs-lookup"><span data-stu-id="68355-137">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="68355-138">Vous pouvez également utiliser la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> méthode dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever.</span><span class="sxs-lookup"><span data-stu-id="68355-138">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="68355-139">Le test échoue si l’exception spécifiée n’est pas levée.</span><span class="sxs-lookup"><span data-stu-id="68355-139">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="68355-140">Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule.</span><span class="sxs-lookup"><span data-stu-id="68355-140">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="68355-141">Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="68355-141">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="68355-142">De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule.</span><span class="sxs-lookup"><span data-stu-id="68355-142">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="68355-143">Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="68355-143">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="68355-144">Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide ( `String.Empty` )](xref:System.String.Empty) et une et une `null` chaîne.</span><span class="sxs-lookup"><span data-stu-id="68355-144">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a and a `null` string.</span></span> <span data-ttu-id="68355-145">Une chaîne vide est une chaîne qui n’a pas de caractères et dont <xref:System.String.Length> a la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="68355-145">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="68355-146">Une `null` chaîne est une chaîne qui n’a pas été initialisée.</span><span class="sxs-lookup"><span data-stu-id="68355-146">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="68355-147">Vous pouvez appeler `StartsWithUpper` directement comme méthode statique et passer un seul <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="68355-147">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="68355-148">Vous pouvez aussi appeler `StartsWithUpper` en tant que méthode d’extension sur une `string` variable assignée à `null` .</span><span class="sxs-lookup"><span data-stu-id="68355-148">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="68355-149">Vous allez définir trois méthodes, chacune appelant une <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> méthode à plusieurs reprises pour chaque élément d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="68355-149">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="68355-150">Étant donné que la méthode de test échoue dès qu’elle trouve le premier échec, vous appelez une surcharge de méthode qui vous permet de passer une chaîne qui indique la valeur de chaîne utilisée dans l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="68355-150">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="68355-151">Pour créer les méthodes de test:</span><span class="sxs-lookup"><span data-stu-id="68355-151">To create the test methods:</span></span>

1. <span data-ttu-id="68355-152">Ouvrez *StringLibraryTest/UnitTest1. cs* et remplacez tout le code par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="68355-152">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="68355-153">Le test de caractères majuscules dans la `TestStartsWithUpper` méthode comprend la lettre majuscule grecque alpha (u + 0391) et la lettre majuscule cyrillique em (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="68355-153">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="68355-154">Le test de caractères minuscules dans la `TestDoesNotStartWithUpper` méthode comprend la lettre minuscule grecque alpha (u + 03B1) et la lettre minuscule cyrillique gué (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="68355-154">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="68355-155">Enregistrez vos modifications.</span><span class="sxs-lookup"><span data-stu-id="68355-155">Save your changes.</span></span>

1. <span data-ttu-id="68355-156">Exécuter les tests :</span><span class="sxs-lookup"><span data-stu-id="68355-156">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="68355-157">La sortie du terminal indique que tous les tests ont réussi.</span><span class="sxs-lookup"><span data-stu-id="68355-157">The terminal output shows that all tests passed.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="68355-158">Gérer les échecs de test</span><span class="sxs-lookup"><span data-stu-id="68355-158">Handle test failures</span></span>

<span data-ttu-id="68355-159">Si vous effectuez un développement piloté par les tests (TDD), vous écrivez d’abord des tests et ils échouent la première fois que vous les exécutez.</span><span class="sxs-lookup"><span data-stu-id="68355-159">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="68355-160">Ensuite, vous ajoutez du code à l’application qui effectue la tentative de test.</span><span class="sxs-lookup"><span data-stu-id="68355-160">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="68355-161">Dans ce cas, vous avez créé le test après avoir écrit le code d’application qu’il a validé, donc vous n’avez pas vu le test échouer.</span><span class="sxs-lookup"><span data-stu-id="68355-161">In this case, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="68355-162">Pour vérifier qu’un test échoue quand vous pensez qu’il échoue, ajoutez une valeur non valide à l’entrée de test.</span><span class="sxs-lookup"><span data-stu-id="68355-162">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="68355-163">Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ».</span><span class="sxs-lookup"><span data-stu-id="68355-163">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="68355-164">Exécuter les tests :</span><span class="sxs-lookup"><span data-stu-id="68355-164">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="68355-165">La sortie du terminal indique qu’un test échoue et fournit un message d’erreur pour le test qui a échoué.</span><span class="sxs-lookup"><span data-stu-id="68355-165">The terminal output shows that one test fails, and it provides an error message for the failed test.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.
     X TestDoesNotStartWithUpper [283ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
     at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper()
       in C:\Projects\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Test Run Failed.
   Total tests: 3
        Passed: 2
        Failed: 1
   Total time: 1.7825 Seconds
   ```

1. <span data-ttu-id="68355-166">Annulez la modification que vous avez effectuée à l’étape 1 en supprimant la chaîne « Error ».</span><span class="sxs-lookup"><span data-stu-id="68355-166">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="68355-167">Réexécutez le test et les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="68355-167">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="68355-168">Tester la version Release de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="68355-168">Test the Release version of the library</span></span>

<span data-ttu-id="68355-169">Maintenant que les tests ont tous réussi lors de l’exécution de la version Debug de la bibliothèque, exécutez les tests sur la version Release de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="68355-169">Now that the tests have all passed when running the Debug version of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="68355-170">Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.</span><span class="sxs-lookup"><span data-stu-id="68355-170">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="68355-171">Exécutez les tests avec la configuration Release Build :</span><span class="sxs-lookup"><span data-stu-id="68355-171">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="68355-172">Les tests réussissent.</span><span class="sxs-lookup"><span data-stu-id="68355-172">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="68355-173">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="68355-173">Additional resources</span></span>

- [<span data-ttu-id="68355-174">Tests unitaires dans .NET Core et .NET Standard</span><span class="sxs-lookup"><span data-stu-id="68355-174">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="68355-175">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="68355-175">Next steps</span></span>

<span data-ttu-id="68355-176">Dans ce didacticiel, vous avez testé une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="68355-176">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="68355-177">Vous pouvez mettre la bibliothèque à la disposition d’autres personnes en la publiant sur [NuGet](https://nuget.org) en tant que package.</span><span class="sxs-lookup"><span data-stu-id="68355-177">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="68355-178">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="68355-178">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="68355-179">Créer et publier un package à l’aide de l’interface CLI dotnet</span><span class="sxs-lookup"><span data-stu-id="68355-179">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="68355-180">Si vous publiez une bibliothèque en tant que package NuGet, d’autres peuvent l’installer et l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="68355-180">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="68355-181">Pour en savoir plus, suivez un didacticiel NuGet :</span><span class="sxs-lookup"><span data-stu-id="68355-181">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="68355-182">Installer et utiliser un package à l’aide de l’interface CLI dotnet</span><span class="sxs-lookup"><span data-stu-id="68355-182">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="68355-183">Une bibliothèque n’a pas besoin d’être distribuée en tant que package.</span><span class="sxs-lookup"><span data-stu-id="68355-183">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="68355-184">Il peut être fourni avec une application console qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="68355-184">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="68355-185">Pour savoir comment publier une application console, consultez le didacticiel précédent dans cette série :</span><span class="sxs-lookup"><span data-stu-id="68355-185">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="68355-186">Publier une application console .NET Core avec Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="68355-186">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
