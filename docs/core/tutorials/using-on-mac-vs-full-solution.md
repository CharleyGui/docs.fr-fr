---
title: Construire une solution complète .NET Core à l’aide de Visual Studio pour Mac
description: Cet article vous guide à travers la construction d’une solution .NET Core qui comprend une bibliothèque réutilisable et des tests unitaires.
ms.date: 12/19/2019
ms.openlocfilehash: 8c9fcca404a3875b6bb7f9cf20551a017ff553c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239961"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Construire une solution complète .NET Core sur macOS à l’aide de Visual Studio pour Mac

Visual Studio pour Mac fournit un environnement de développement intégré (IDE) complet pour le développement d’applications .NET Core. Cet article vous guide à travers la construction d’une solution .NET Core qui comprend une bibliothèque réutilisable et des tests unitaires.

Ce didacticiel vous montre comment créer une application qui accepte un terme de recherche et une chaîne de texte saisis par l’utilisateur, compte le nombre de fois où le terme de recherche apparaît dans la chaîne à l’aide d’une méthode dans une bibliothèque de classes puis retourne le résultat à l’utilisateur. La solution inclut également des tests unitaires pour la bibliothèque de classes servant d’introduction aux concepts des tests unitaires. Si vous préférez poursuivre le didacticiel avec un exemple complet, téléchargez l’[exemple de solution](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Vos commentaires sont extrêmement précieux. Il existe deux moyens de transmettre vos commentaires à l’équipe de développement sur Visual Studio pour Mac :
>
> - Dans Visual Studio for Mac, sélectionnez **Help** > **Report a Problem** du menu ou **signalez un problème** à partir de l’écran De bienvenue, qui ouvre une fenêtre pour le dépôt d’un rapport de bogue. Vous pouvez effectuer le suivi de vos commentaires dans le portail de la [communauté des développeurs](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Pour faire une suggestion, sélectionnez **Aide** > **Fournir une suggestion** dans le menu ou fournir une **suggestion** à partir de l’écran de bienvenue, qui vous emmène au studio visuel pour Mac Developer Community [page Web](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Conditions préalables requises

- [.NET Core SDK 3.1 ou plus tard](https://dotnet.microsoft.com/download)
- [Visual Studio 2019 pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Pour plus d’informations sur les conditions préalables, voir les [dépendances et les exigences .NET Core](../install/dependencies.md?pivots=os-macos). Pour les exigences système complète de Visual Studio 2019 pour Mac, voir [Visual Studio 2019 pour Mac Product Family System Requirements](/visualstudio/productinfo/vs2019-system-requirements-mac).

## <a name="building-a-library"></a>Génération d'une bibliothèque

1. Sur la fenêtre de départ, sélectionnez **New Project**. Dans la boîte de dialogue **Nouveau projet**, sous le nœud **.NET Core**, sélectionnez le modèle **Bibliothèque standard .NET**. Cette commande crée une bibliothèque .NET Standard qui cible .NET Core ainsi que toute autre implémentation .NET qui prend en charge la version 2.1 de la [norme .NET](../../standard/net-standard.md). Si vous avez plusieurs versions du .NET Core SDK installé, vous pouvez choisir différentes versions de .NET Standard pour votre bibliothèque. Choisissez ".NET Standard 2.1" et sélectionnez **Next**.

   > [!div class="mx-imgBorder"]
   > ![Boîte de dialogue Nouveau projet Mac dans Visual Studio](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Nommez le projet « TextUtils » (un nom court pour « Utilitaires texte ») et la solution « WordCounter ». Laissez la case **Créez un répertoire de projet dans le répertoire de la solution** cochée. Sélectionnez **Créer**.

   > [!div class="mx-imgBorder"]
   > ![Options de la boîte de dialogue Nouveau projet dans Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. Dans le bloc **solution,** étendre le `TextUtils` nœud pour révéler le fichier de classe fourni par le modèle, *Class1.cs*. Ctrl-cliquez sur le fichier, **sélectionnez Renommer** dans le menu contextuelle, et renommer le fichier à *WordCount.cs*. Ouvrez le fichier et remplacez le contenu par le code suivant :

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/TextUtils/WordCount.cs)]

1. Enregistrez le fichier en utilisant l’une des trois méthodes différentes : utilisez le raccourci clavier <kbd>&#8984;</kbd> + <kbd>s,</kbd>sélectionnez **Fichier** > **Enregistrer** dans le menu, ou cliquez sur l’onglet du fichier et sélectionnez **Enregistrer** dans le menu contextuel. L’image suivante présente la fenêtre de l’IDE :

   > [!div class="mx-imgBorder"]
   > ![Fenêtre de l’IDE Visual Studio pour Mac avec fichier de bibliothèque de classes et méthode](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. Sélectionnez **Erreurs** dans la marge en bas de la fenêtre de l’IDE pour ouvrir le panneau **Erreurs**. Sélectionnez le bouton **Sortie de la build**.

   > [!div class="mx-imgBorder"]
   > ![Marge inférieure de l’IDE Visual Studio pour Mac montrant le bouton Erreurs](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Sélectionnez **Build** > **Build All** dans le menu.

   La solution se génère. Le panneau de sortie de la build indique que la build a réussi.

   > [!div class="mx-imgBorder"]
   > ![Volet Sortie de la build Visual Studio pour Mac du panneau Erreurs avec le message de réussite de la build](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Création d'un projet de test

Les tests unitaires effectuent des tests logiciels automatisés pendant le développement et la publication. Le cadre de test que vous utilisez dans ce tutoriel est [xUnit (version 2.4.0 ou plus tard)](https://xunit.github.io/), qui est installé automatiquement lorsque le projet de test xUnit est ajouté à la solution dans les étapes suivantes:

1. Dans la barre latérale **Solution,** cliquez `WordCounter` sur la solution et **sélectionnez Ajouter** > **nouveau projet**.

1. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Tests** dans le nœud **.NET Core**. Sélectionnez le **projet de test xUnit** puis **suivant**.

   > [!div class="mx-imgBorder"]
   > ![Boîte de dialogue Nouveau projet dans Visual Studio pour Mac afin de créer le projet de test xUnit](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Si vous avez plusieurs versions du .NET Core SDK, vous devrez sélectionner la version pour ce projet. Sélectionnez **.NET Core 3.1**. Nommez le nouveau projet « TestLibrary » et sélectionnez **Créer**.

   > [!div class="mx-imgBorder"]
   > ![Boîte de dialogue Nouveau projet dans Visual Studio pour Mac indiquant le nom du projet](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Pour que la bibliothèque de test fonctionne avec la classe `WordCount`, ajoutez une référence au projet `TextUtils`. Dans la barre latérale **Solution,** ctrl-click **Dépendances** sous **TestLibrary**. Sélectionnez **Modifier les références** dans le menu contextuel.

1. Dans le dialogue **Edit References,** sélectionnez le projet **TextUtils** sur l’onglet **Projets.** Sélectionnez **OK**.

   > [!div class="mx-imgBorder"]
   > ![Boîte de dialogue Modifier les références dans Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. Dans le projet **TestLibrary**, renommez le fichier *UnitTest1.cs**TextUtilsTests.cs*.

1. Ouvrez le fichier et remplacez le code par le code suivant :

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");

               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   L’image suivante montre l’IDE avec le code de test unitaire en place. Faites attention à l’instruction `Assert.NotEqual`.

   > [!div class="mx-imgBorder"]
   > ![Test unitaire initial dans Visual Studio pour Mac dans la fenêtre principale de l’IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Il est important de faire échouer un nouveau test une fois, afin de vérifier que sa logique de test est correcte. La méthode passe le nom « Jack » (majuscule) et une chaîne avec « Jack » et « jack » (majuscules et minuscules). Si la méthode `GetWordCount` fonctionne correctement, elle retourne deux instances du mot recherché. Pour faire échouer ce test intentionnellement, vous implémentez d’abord le test en déclarant que deux instances du mot recherché « Jack » ne sont pas retournées par la méthode `GetWordCount`. Passez à l’étape suivante pour faire échouer le test intentionnellement.

1. Ouvrez le panneau **Tests unitaires** sur le côté droit de l’écran. Sélectionnez **Voir** > **les tests** dans le menu.

   > [!div class="mx-imgBorder"]
   > ![Panneau Tests unitaires Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Cliquez sur l’icône **Ancrer** pour garder le panneau ouvert. (Surlignée dans l’image suivante.)

   > [!div class="mx-imgBorder"]
   > ![Icône Ancrer du panneau Tests unitaires Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Cliquez sur le bouton **Tout exécuter**.

   Le test échoue, ce qui est le résultat correct. La méthode de test déclare que deux instances de `inputString`, « Jack », ne sont pas retournées par la chaîne « Jack jack » fournie à la méthode `GetWordCount`. Étant donné que la méthode `GetWordCount` respecte la casse, les deux instances sont retournées. L’assertion que 2 *n’est pas égal à* 2 échoue. Ce résultat est le bon résultat, et la logique de notre test est bonne.

   > [!div class="mx-imgBorder"]
   > ![Affichage de l’échec du test dans Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Modifiez la méthode de test `IgnoreCasing` en remplaçant `Assert.NotEqual` par `Assert.Equal`. Enregistrez le fichier en utilisant le raccourci clavier <kbd>Ctrl</kbd>+<kbd>s</kbd>, **File** > **Save** du menu, ou ctrl-clicking sur l’onglet du fichier et la sélection **Enregistrer** à partir du menu contextuelle.

   Vous vous attendez à ce que `searchWord` « Jack » retourne deux instances avec `inputString` « Jack jack » passé dans `GetWordCount`. Réexécutez le test en cliquant sur le bouton **Exécuter les tests** du panneau **Tests unitaires** ou sur le bouton **Réexécuter les tests** du panneau **Résultats des tests** en bas de l’écran. Le test réussit. Il existe deux instances de « Jack » dans la chaîne « Jack jack » (casse ignorée) et l’assertion de test est `true`.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pour les tests Mac passer affichage](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Le test des valeurs individuelles retournées avec un `Fact` n'est que le début de ce que vous pouvez faire avec les tests unitaires. Une autre technique puissante vous permet de tester plusieurs valeurs à l’aide d’une `Theory`. Ajoutez la méthode suivante à votre classe `TextUtils_GetWordCountShould`. Vous disposez de deux méthodes dans la classe après avoir ajouté cette méthode :

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count,
                                       string searchWord,
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   `CountInstancesCorrectly` vérifie que la méthode `GetWordCount` compte correctement. `InlineData` fournit un nombre, un terme de recherche et une chaîne d’entrée à vérifier. La méthode de test s’exécute une fois pour chaque ligne de données. Notez que, là encore, vous déclarez tout d’abord un échec en utilisant `Assert.NotEqual`, même si vous savez que les nombres contenus dans les données sont corrects et que les valeurs correspondent aux nombres retournés par la méthode `GetWordCount`. L’exécution de l’étape d’échec intentionnel du test peut sembler a priori une perte de temps, mais la vérification de la logique de test en la faisant échouer est une étape importante pour valider la logique de vos tests. Lorsqu’une méthode de test réussit alors que vous pensiez qu’elle échouerait, c’est que vous avez trouvé un bogue dans la logique du test. Il est recommandé de suivre cette procédure chaque fois que vous créez une méthode de test.

1. Enregistrez le fichier et réexécutez les tests. Le test de la casse réussit, mais les trois tests d’énumération échouent. Ce résultat est exactement ce que vous attendez de se produire.

   > [!div class="mx-imgBorder"]
   > ![Échec du test attendu dans Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Modifiez la méthode de test `CountInstancesCorrectly` en remplaçant `Assert.NotEqual` par `Assert.Equal`. Enregistrez le fichier . Réexécutez les tests. Tous les tests sont concluants.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio pour Mac passe d’essai prévu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Ajout d’une application console

1. Dans la barre latérale **Solution,** cliquez `WordCounter` sur la solution. Ajoutez un nouveau projet **Application console** en sélectionnant le modèle parmi les modèles **.NET Core** > **Application**. Sélectionnez **Suivant**. Nommez le projet **WordCounterApp**. Sélectionnez **Créer** pour créer le projet dans la solution.

1. Dans la barre latérale **Solutions,** cliquez sur le nœud **dépendances** du nouveau projet **WordCounterApp.** Dans la boîte de dialogue **Modifier les références**, cochez la case **TextUtils** puis sélectionnez **OK**.

1. Ouvrez le *fichier Program.cs.* Remplacer le code par le code suivant :

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/WordCounterApp/Program.cs)]

1. Cliquez sur le projet `WordCounterApp` et sélectionnez le **projet Run** dans le menu contextuelle. Lorsque vous exécutez l’application, indiquez les valeurs du mot de recherche et la chaîne d’entrée à l’invite dans la fenêtre de console. L’application indique le nombre de fois où le terme de recherche apparaît dans la chaîne.

   > [!div class="mx-imgBorder"]
   > ![Fenêtre de console Visual Studio pour Mac montrant votre application en cours d’exécution](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. La dernière fonctionnalité à explorer est le débogage avec Visual Studio pour Mac. Définissez un point d’arrêt sur l’instruction `Console.WriteLine`. Sélectionnez dans la marge gauche de la ligne 23 : un cercle rouge apparaît en regard de la ligne de code. Vous pouvez également sélectionner n’importe où sur la ligne de code et sélectionnez **Run** > **Toggle Breakpoint** dans le menu.

   > [!div class="mx-imgBorder"]
   > ![Point d'arrêt défini dans Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. ctrl-cliquez `WordCounterApp` sur le projet. Sélectionnez **Start Debugging Project** dans le menu contextuelle. Lorsque l’application s’exécute, entrez le terme de recherche « cat » et « The dog chased the cat, but the cat escaped. » pour la chaîne à rechercher. Lorsque l’instruction `Console.WriteLine` est atteinte, l’exécution du programme s’arrête avant l’exécution de l’instruction. Dans l’onglet **Locals,** `searchWord`vous `inputString` `wordCount`pouvez `pluralChar` voir le , , , et les valeurs.

   > [!div class="mx-imgBorder"]
   > ![Arrêt de l’exécution du programme débogueur dans Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. Dans le volet **Immédiat**, tapez « wordCount = 999. » et appuyez sur Entrée. Cette commande attribue une valeur absurde de `wordCount` 999 à la variable montrant que vous pouvez remplacer les valeurs variables tout en débogage.

   > [!div class="mx-imgBorder"]
   > ![Modification des valeurs de la fenêtre Exécution dans Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Dans la barre d’outils, cliquez sur la flèche *Continuer*. Regardez le résultat dans la fenêtre de console. Elle affiche la valeur incorrecte de 999 que vous définissez lorsque vous déboguez l’application.

   > [!div class="mx-imgBorder"]
   > ![Bouton Continuer de la barre d’outils dans Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   > [!div class="mx-imgBorder"]
   > ![Sortie de la fenêtre de console Visual Studio pour Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

Vous pouvez utiliser le même processus pour déboiffer le code à l’aide de votre projet de test unitaire. Au lieu de lancer le projet d’application WordCount, cliquez sur le projet **Test Library** et **sélectionnez Start Debugging Project** dans le menu context. Visual Studio pour Mac démarre votre projet de test avec le débbuggeur attaché. L’exécution s’arrêtera à n’importe quel point d’arrêt que vous avez ajouté au projet de test, ou au code de bibliothèque sous-jacent.

## <a name="see-also"></a>Voir aussi

- [Notes de publication de Visual Studio 2019 pour Mac](/visualstudio/releasenotes/vs2019-mac-relnotes)
