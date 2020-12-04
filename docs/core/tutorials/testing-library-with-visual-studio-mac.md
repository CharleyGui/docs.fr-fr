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
# <a name="test-a-net-class-library-using-visual-studio"></a>Tester une bibliothèque de classes .NET à l’aide de Visual Studio

Ce didacticiel montre comment automatiser les tests unitaires en ajoutant un projet de test à une solution.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec la solution que vous créez dans [créer une bibliothèque de classes .net à l’aide de Visual Studio pour Mac](library-with-visual-studio-mac.md).

## <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

Les tests unitaires effectuent des tests logiciels automatisés pendant le développement et la publication. [MSTest](https://github.com/Microsoft/testfx-docs) est l’un des trois frameworks de test que vous pouvez choisir. Les autres sont [xUnit](https://xunit.net/) et [nunit](https://nunit.org/).

1. Démarrez Visual Studio pour Mac.

1. Ouvrez la `ClassLibraryProjects` solution que vous avez créée dans [créer une bibliothèque de classes .net à l’aide de Visual Studio pour Mac](library-with-visual-studio-mac.md).

1. Dans le panneau **solutions** , cliquez sur la solution en <kbd>appuyant sur la touche Ctrl</kbd> `ClassLibraryProjects` et sélectionnez **Ajouter**  >  **un nouveau projet**.

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez **tests** à partir du nœud **Web et** de la console. Sélectionnez le **projet MSTest** suivi de **Next**.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Boîte de dialogue Nouveau projet Mac de Visual Studio création d’un projet de test":::

1. Sélectionnez **.net 5,0** comme **Framework cible** , puis cliquez sur **suivant**.

1. Nommez le nouveau projet « StringLibraryTest » et sélectionnez **créer**.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="Boîte de dialogue Nouveau projet dans Visual Studio pour Mac indiquant le nom du projet":::

   Visual Studio crée un fichier de classe avec le code suivant :

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
   - Il applique l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut à `TestMethod1` .

   Chaque méthode marquée avec [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) dans une classe de test marquée avec [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) est exécutée automatiquement lorsque le test unitaire est exécuté.

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

Pour que le projet de test fonctionne avec la `StringLibrary` classe, ajoutez une référence au `StringLibrary` projet.

1. Dans le panneau **solutions** , cliquez sur **dépendances** <kbd>CTRL</kbd>+ clic sous **StringLibraryTest**. Sélectionnez **Ajouter une référence** dans le menu contextuel.

1. Dans la boîte de dialogue **références** , sélectionnez le projet **StringLibrary** . Sélectionnez **OK**.

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Boîte de dialogue Modifier les références dans Visual Studio pour Mac":::

## <a name="add-and-run-unit-test-methods"></a>Ajouter et exécuter des méthodes de test unitaire

Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l' <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribut dans une classe marquée avec l'  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribut. Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.

Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test. Certaines des `Assert` méthodes les plus fréquemment appelées à la classe sont indiquées dans le tableau suivant :

| Méthodes d’assertion     | Fonction |
| ------------------ | -------- |
| `Assert.AreEqual`  | Vérifie que deux valeurs ou objets sont égaux. L’assertion échoue si les valeurs ou les objets ne sont pas égaux. |
| `Assert.AreSame`   | Vérifie que deux variables d’objet référencent le même objet. L’assertion échoue si les variables font référence à des objets différents. |
| `Assert.IsFalse`   | Vérifie qu’une condition est `false`. L’assertion échoue si la condition est `true`. |
| `Assert.IsNotNull` | Vérifie qu’un objet n’est pas `null` . L’assertion échouera si l’objet est `null`. |

Vous pouvez également utiliser la <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> méthode dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever. Le test échoue si l’exception spécifiée n’est pas levée.

Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule. Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType>. De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule. Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType>.

Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide ( `String.Empty` )](xref:System.String.Empty), une chaîne valide sans caractères et dont <xref:System.String.Length> a la valeur 0, et une `null` chaîne qui n’a pas été initialisée. Vous pouvez appeler `StartsWithUpper` directement comme méthode statique et passer un seul <xref:System.String> argument. Vous pouvez aussi appeler `StartsWithUpper` en tant que méthode d’extension sur une `string` variable assignée à `null` .

Vous allez définir trois méthodes, chacune appelant une <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> méthode pour chaque élément d’un tableau de chaînes. Vous appellerez une surcharge de méthode qui vous permet de spécifier un message d’erreur à afficher en cas d’échec du test. Le message identifie la chaîne à l’origine de l’échec.

Pour créer les méthodes de test:

1. Ouvrez le fichier *UnitTest1.cs* et remplacez le code par le code suivant :

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   Le test de caractères majuscules dans la `TestStartsWithUpper` méthode comprend la lettre majuscule grecque alpha (u + 0391) et la lettre majuscule cyrillique em (u + 041C). Le test de caractères minuscules dans la `TestDoesNotStartWithUpper` méthode comprend la lettre minuscule grecque alpha (u + 03B1) et la lettre minuscule cyrillique gué (u + 0433).

1. Dans la barre de menus, sélectionnez **fichier**  >  **Enregistrer sous**. Dans la boîte de dialogue, assurez-vous que l' **encodage** est défini sur **Unicode (UTF-8)**.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Boîte de dialogue Enregistrer le fichier sous Visual Studio":::

1. Lorsque vous êtes invité à remplacer le fichier existant, sélectionnez **remplacer**.

   Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII. Lorsque cela se produit, le runtime ne décode pas correctement les caractères UTF8 en dehors de la plage ASCII, et les résultats des tests ne sont pas corrects.

1. Ouvrez le panneau **Tests unitaires** sur le côté droit de l’écran. Sélectionnez **Afficher**  >  les **tests** dans le menu.

1. Cliquez sur l’icône **Ancrer** pour garder le panneau ouvert.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Icône Ancrer du panneau Tests unitaires Visual Studio pour Mac":::

1. Cliquez sur le bouton **Tout exécuter**.

   Tous les tests sont concluants.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio pour Mac réussites de tests attendues":::

## <a name="handle-test-failures"></a>Gérer les échecs de test

Si vous effectuez un développement piloté par les tests (TDD), vous écrivez d’abord des tests et ils échouent la première fois que vous les exécutez. Ensuite, vous ajoutez du code à l’application qui effectue la tentative de test. Pour ce didacticiel, vous avez créé le test après avoir écrit le code d’application qu’il valide, donc vous n’avez pas vu le test échouer. Pour vérifier qu’un test échoue quand vous pensez qu’il échoue, ajoutez une valeur non valide à l’entrée de test.

1. Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ». Vous n’avez pas besoin d’enregistrer le fichier, car Visual Studio enregistre automatiquement les fichiers ouverts quand une solution est générée pour exécuter des tests.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Réexécutez les tests.

   Cette fois-ci, la fenêtre de l' **Explorateur de tests** indique que deux tests ont réussi et un échec.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="Fenêtre Explorateur de tests avec tests ayant échoué":::

1. <kbd>CTRL</kbd>+ clic sur le test ayant échoué, `TestDoesNotStartWithUpper` , puis sélectionnez **Afficher** le panneau résultats dans le menu contextuel.

   Le panneau **résultats** affiche le message produit par l’assertion : «Assert. IsFalse a échoué. « Erreur » : false ; réel : True » était attendu ». En raison de l’échec, aucune chaîne du tableau après « erreur » n’a été testée.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="Fenêtre Explorateur de tests présentant l’échec de l’assertion IsFalse":::

1. Supprimez la chaîne « Error » que vous avez ajoutée à l’étape 1. Réexécutez le test et les tests réussissent.

## <a name="test-the-release-version-of-the-library"></a>Tester la version Release de la bibliothèque

Maintenant que les tests ont tous réussi lors de l’exécution de la version Debug de la bibliothèque, exécutez les tests sur la version Release de la bibliothèque. Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.

Pour tester la version Release :

1. Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Barre d’outils Visual Studio avec version Release mise en surbrillance":::

1. Dans le panneau **solutions** , <kbd>cliquez</kbd>sur le projet **StringLibrary** , puis sélectionnez **générer** dans le menu contextuel pour recompiler la bibliothèque.

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="Menu contextuel de StringLibrary avec commande build":::

1. Réexécutez les tests unitaires.

   Les tests réussissent.

## <a name="debug-tests"></a>Déboguer les tests

Si vous utilisez Visual Studio pour Mac comme IDE, vous pouvez utiliser le même processus que celui présenté dans [Didacticiel : déboguer une application console .net à l’aide d’Visual Studio pour Mac](debugging-with-visual-studio-mac.md) pour déboguer le code à l’aide de votre projet de test unitaire. Au lieu de démarrer le projet d’application *Showcase* <kbd>, cliquez</kbd>sur le projet **StringLibraryTests** , puis sélectionnez **Démarrer le débogage du projet** dans le menu contextuel.

Visual Studio démarre le projet de test avec le débogueur attaché. L’exécution s’arrêtera à un point d’arrêt que vous avez ajouté au projet de test ou au code de bibliothèque sous-jacent.

## <a name="additional-resources"></a>Ressources supplémentaires

* [Tests unitaires dans .NET](../testing/index.md)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez testé une bibliothèque de classes. Vous pouvez mettre la bibliothèque à la disposition d’autres personnes en la publiant sur [NuGet](https://nuget.org) en tant que package. Pour en savoir plus, suivez un didacticiel NuGet :

> [!div class="nextstepaction"]
> [Créer et publier un package (interface CLI dotnet)](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

Si vous publiez une bibliothèque en tant que package NuGet, d’autres peuvent l’installer et l’utiliser. Pour en savoir plus, suivez un didacticiel NuGet :

> [!div class="nextstepaction"]
> [Installer et utiliser un package dans Visual Studio pour Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

Une bibliothèque n’a pas besoin d’être distribuée en tant que package. Il peut être fourni avec une application console qui l’utilise. Pour savoir comment publier une application console, consultez le didacticiel précédent dans cette série :

> [!div class="nextstepaction"]
> [Publier une application console .NET à l’aide de Visual Studio pour Mac](publishing-with-visual-studio-mac.md)
