---
title: Test d’une bibliothèque de classes .NET Standard avec .NET Core à l’aide de Visual Studio Code
description: Créez un projet de test unitaire pour une bibliothèque de classes .NET Core. Vérifiez que la bibliothèque de classes .NET Core fonctionne correctement avec les tests unitaires.
ms.date: 06/08/2020
ms.openlocfilehash: a61fd952eea2dec0d5a9f351d3f3d01c738e8fad
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701031"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio-code"></a>Didacticiel : tester une bibliothèque de classes .NET Standard avec .NET Core à l’aide de Visual Studio Code

Ce didacticiel montre comment automatiser les tests unitaires en ajoutant un projet de test à une solution.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec la solution que vous créez dans [créer une bibliothèque de .NET standard dans Visual Studio code](library-with-visual-studio-code.md).

## <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

Les tests unitaires effectuent des tests logiciels automatisés pendant le développement et la publication. L’infrastructure de test que vous utilisez dans ce didacticiel est MSTest. [MSTest](https://github.com/Microsoft/testfx-docs) est l’un des trois frameworks de test que vous pouvez choisir. Les autres sont [xUnit](https://xunit.net/) et [nunit](https://nunit.org/).

1. Démarrez Visual Studio Code.

1. Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans [créer une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md).

1. Créez un projet de test unitaire nommé « StringLibraryTest ».

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   Le modèle de projet crée un fichier UnitTest1.cs avec le code suivant :

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

   Le code source créé par le modèle de test unitaire effectue les opérations suivantes :

   - Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.
   - Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à la classe `UnitTest1`.
   - Il applique l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut à définir `TestMethod1` .

   Chaque méthode marquée avec [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) dans une classe de test marquée avec [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) est exécutée automatiquement lorsque le test unitaire est exécuté.

1. Ajoutez le projet de test à la solution.

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

Pour que le projet de test fonctionne avec la `StringLibrary` classe, ajoutez une référence au projet dans le `StringLibraryTest` projet `StringLibrary` .

1. Exécutez la commande suivante :

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a>Ajouter et exécuter des méthodes de test unitaire

Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut dans une classe marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribut. Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.

Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test. Certaines des `Assert` méthodes les plus fréquemment appelées à la classe sont indiquées dans le tableau suivant :

| Méthodes d’assertion     | Fonction |
| ------------------ | -------- |
| `Assert.AreEqual`  | Vérifie que deux valeurs ou objets sont égaux. L’assertion échoue si les valeurs ou les objets ne sont pas égaux. |
| `Assert.AreSame`   | Vérifie que deux variables d’objet référencent le même objet. L’assertion échoue si les variables font référence à des objets différents. |
| `Assert.IsFalse`   | Vérifie qu’une condition est `false`. L’assertion échoue si la condition est `true`. |
| `Assert.IsNotNull` | Vérifie qu’un objet n’est pas `null` . L’assertion échouera si l’objet est `null`. |

Vous pouvez également utiliser la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> méthode dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever. Le test échoue si l’exception spécifiée n’est pas levée.

Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule. Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>. De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule. Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.

Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide ( `String.Empty` )](xref:System.String.Empty) et une et une `null` chaîne. Une chaîne vide est une chaîne qui n’a pas de caractères et dont <xref:System.String.Length> a la valeur 0. Une `null` chaîne est une chaîne qui n’a pas été initialisée. Vous pouvez appeler `StartsWithUpper` directement comme méthode statique et passer un seul <xref:System.String> argument. Vous pouvez aussi appeler `StartsWithUpper` en tant que méthode d’extension sur une `string` variable assignée à `null` .

Vous allez définir trois méthodes, chacune appelant une <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> méthode pour chaque élément d’un tableau de chaînes. Vous appellerez une surcharge de méthode qui vous permet de spécifier un message d’erreur à afficher en cas d’échec du test. Le message identifie la chaîne à l’origine de l’échec.

Pour créer les méthodes de test:

1. Ouvrez *StringLibraryTest/UnitTest1. cs* et remplacez tout le code par le code suivant.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   Le test de caractères majuscules dans la `TestStartsWithUpper` méthode comprend la lettre majuscule grecque alpha (u + 0391) et la lettre majuscule cyrillique em (u + 041C). Le test de caractères minuscules dans la `TestDoesNotStartWithUpper` méthode comprend la lettre minuscule grecque alpha (u + 03B1) et la lettre minuscule cyrillique gué (u + 0433).

1. Enregistrez vos modifications.

1. Exécuter les tests :

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   La sortie du terminal indique que tous les tests ont réussi.

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a>Gérer les échecs de test

Si vous effectuez un développement piloté par les tests (TDD), vous écrivez d’abord des tests et ils échouent la première fois que vous les exécutez. Ensuite, vous ajoutez du code à l’application qui effectue la tentative de test. Pour ce didacticiel, vous avez créé le test après avoir écrit le code d’application qu’il valide, donc vous n’avez pas vu le test échouer. Pour vérifier qu’un test échoue quand vous pensez qu’il échoue, ajoutez une valeur non valide à l’entrée de test.

1. Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ».

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Exécuter les tests :

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   La sortie du terminal indique qu’un test échoue et génère un message d’erreur pour le test qui a échoué : «Assert. IsFalse a échoué. « Erreur » : false ; réel : True » était attendu ». En raison de l’échec, aucune chaîne du tableau après « erreur » n’a été testée.

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

1. Supprimez la chaîne « Error » que vous avez ajoutée à l’étape 1. Réexécutez le test et les tests réussissent.

## <a name="test-the-release-version-of-the-library"></a>Tester la version Release de la bibliothèque

Maintenant que les tests ont tous réussi lors de l’exécution de la version Debug de la bibliothèque, exécutez les tests sur la version Release de la bibliothèque. Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.

1. Exécutez les tests avec la configuration Release Build :

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   Les tests réussissent.

## <a name="additional-resources"></a>Ressources supplémentaires

* [Tests unitaires dans .NET Core et .NET Standard](../testing/index.md)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez testé une bibliothèque de classes. Vous pouvez mettre la bibliothèque à la disposition d’autres personnes en la publiant sur [NuGet](https://nuget.org) en tant que package. Pour en savoir plus, suivez un didacticiel NuGet :

> [!div class="nextstepaction"]
> [Créer et publier un package à l’aide de l’interface CLI dotnet](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

Si vous publiez une bibliothèque en tant que package NuGet, d’autres peuvent l’installer et l’utiliser. Pour en savoir plus, suivez un didacticiel NuGet :

> [!div class="nextstepaction"]
> [Installer et utiliser un package à l’aide de l’interface CLI dotnet](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

Une bibliothèque n’a pas besoin d’être distribuée en tant que package. Il peut être fourni avec une application console qui l’utilise. Pour savoir comment publier une application console, consultez le didacticiel précédent dans cette série :

> [!div class="nextstepaction"]
> [Publier une application console .NET Core avec Visual Studio Code](publishing-with-visual-studio-code.md)
