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
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>Tester une bibliothèque .NET Standard avec .NET Core dans Visual Studio

Dans la [génération d’une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md), vous avez créé une bibliothèque de classes simple qui ajoute une méthode d’extension à la classe <xref:System.String>. À présent, vous allez créer un test unitaire pour vérifier qu’elle fonctionne comme prévu. Vous allez ajouter votre projet de test unitaire à la solution créée dans l’article précédent.

## <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

Pour créer le projet de test unitaire, procédez comme suit :

1. Ouvrez la solution `ClassLibraryProjects` que vous avez créée dans l’article [créer une bibliothèque de .NET standard dans Visual Studio](library-with-visual-studio.md) .

1. Ajoutez un nouveau projet de test unitaire nommé « StringLibraryTest » à la solution.

   1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter** > **nouveau projet**.

   1. Dans la page **Ajouter un nouveau projet** , entrez **MSTest** dans la zone de recherche. Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **projet de test MSTest (.net Core)** , puis choisissez **suivant**.

   1. Dans la page **configurer votre nouveau projet** , entrez **StringLibraryTest** dans la zone **nom du projet** . Sélectionnez ensuite **Créer**.

   > [!NOTE]
   > En plus d’un MSTest, vous pouvez également créer des projets de test xUnit et nUnit pour .NET Core dans Visual Studio.

1. Visual Studio crée le projet et ouvre le fichier de classe dans la fenêtre de code avec le code suivant :

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

   Le code source créé par le modèle de test unitaire effectue les opérations suivantes :

   - Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.

   - Elle applique l’attribut [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) à la classe `UnitTest1`. Chaque méthode de test dans une classe de test marquée avec l’attribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) est exécutée automatiquement quand le test unitaire est exécuté.

   - Il applique l’attribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) pour définir `TestMethod1` dans C# ou `TestSub` dans Visual Basic en tant que méthode de test pour une exécution automatique lorsque le test unitaire est exécuté.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet **StringLibraryTest** puis sélectionnez **Ajouter une référence** dans le menu contextuel.

   > [!div class="mx-imgBorder"]
   > ![menu contextuel des dépendances StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, développez le nœud **Projets**, cochez la case en regard de **StringLibrary**. L’ajout d’une référence à l’assembly `StringLibrary` permet au compilateur de trouver les méthodes **StringLibrary**. Cliquez sur le bouton **OK**. Une référence est ajoutée à votre projet de bibliothèque de classes, `StringLibrary`.

   ![Boîte de dialogue Gestionnaire de références dans Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>Ajouter et exécuter des méthodes de test unitaire

Lorsque Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> dans une classe de test unitaire, la classe à laquelle l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> est appliqué. Une méthode de test se termine lorsque le premier échec est trouvé ou lorsque tous les tests contenus dans la méthode ont réussi.

Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test. Certaines des méthodes les plus fréquemment appelées à la classe `Assert` sont présentées dans le tableau suivant :

| Méthodes d’assertion     | Fonction |
| ------------------ | -------- |
| `Assert.AreEqual`  | Vérifie que deux valeurs ou objets sont égaux. L’assertion échoue si les valeurs ou les objets ne sont pas égaux. |
| `Assert.AreSame`   | Vérifie que deux variables d’objet référencent le même objet. L’assertion échoue si les variables font référence à des objets différents. |
| `Assert.IsFalse`   | Vérifie qu’une condition est `false`. L’assertion échoue si la condition est `true`. |
| `Assert.IsNotNull` | Vérifie qu’un objet n’est pas `null`. L’assertion échouera si l’objet est `null`. |

Vous pouvez également utiliser la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> dans une méthode de test pour indiquer le type d’exception qu’il est supposé lever. Le test échoue si l’exception spécifiée n’est pas levée.

Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule. Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>. De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule. Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.

Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide (`String.Empty`)](xref:System.String.Empty), une chaîne valide sans caractères et dont <xref:System.String.Length> est égal à 0, et une chaîne de `null` qui n’a pas été initialisée. Si `StartsWithUpper` est appelée en tant que méthode d’extension sur une instance de <xref:System.String>, une chaîne de `null` ne peut pas être passée. Toutefois, vous pouvez également l’appeler directement comme méthode statique et passer un seul argument <xref:System.String>.

Vous allez définir trois méthodes, chacune appelant une méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> à plusieurs reprises pour chaque élément d’un tableau de chaînes. Étant donné que la méthode de test échoue dès qu’elle trouve le premier échec, vous appelez une surcharge de méthode qui vous permet de passer une chaîne qui indique la valeur de chaîne utilisée dans l’appel de méthode.

Pour créer les méthodes de test:

1. Dans la fenêtre de code *UnitTest1.cs* ou *UnitTest1. vb* , remplacez le code par le code suivant :

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Le test de caractères majuscules dans la méthode `TestStartsWithUpper` comprend la lettre majuscule grecque alpha (U + 0391) et la lettre majuscule cyrillique EM (U + 041C). Le test de caractères minuscules dans la méthode `TestDoesNotStartWithUpper` comprend la lettre minuscule grecque alpha (U + 03B1) et la lettre minuscule cyrillique gué (U + 0433).

1. Dans la barre de menus, sélectionnez **fichier** > **Enregistrer UnitTest1.cs sous** ou **fichier** > **Enregistrer UnitTest1. VB sous**. Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec l’encodage**.

   > [!div class="mx-imgBorder"]
   > ![boîte de dialogue Enregistrer le fichier sous Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. Dans la boîte de dialogue **Confirmer l’enregistrement sous**, sélectionnez le bouton **Oui** pour enregistrer le fichier.

1. Dans la boîte de dialogue **Options d’enregistrement avancées**, sélectionnez **Unicode (UTF-8 avec signature) - Page de codes 65001** dans la liste déroulante **Encodage**, puis sélectionnez **OK**.

   > [!div class="mx-imgBorder"]
   > ![la boîte de dialogue Options d’enregistrement avancées de Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII. Lorsque cela se produit, le runtime ne décode pas correctement les caractères UTF8 en dehors de la plage ASCII, et les résultats des tests ne sont pas corrects.

1. Dans la barre de menus, sélectionnez **Test** > **Exécuter** > **Tous les Tests**. La fenêtre **Explorateur de tests** s’ouvre et montre que les tests ont réussi. Les trois tests sont listés dans la section **Tests réussis** et la section **Résumé** indique le résultat de la série de tests.

   > [!div class="mx-imgBorder"]
   > ![fenêtre de l’Explorateur de tests avec les tests réussis](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Gérer les échecs de test

Votre série de tests n’a rencontré aucun échec : changez-la légèrement de façon à faire échouer une des méthodes de test :

1. Modifiez le tableau `words` dans la méthode `TestDoesNotStartWithUpper` en y incluant la chaîne « Erreur ». Vous n’avez pas besoin d’enregistrer le fichier, car Visual Studio enregistre automatiquement les fichiers ouverts quand une solution est générée pour exécuter des tests.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Exécutez le test en sélectionnant **Test** > **Exécuter** > **Tous les Tests** dans la barre de menus. La fenêtre **Explorateur de tests** indique que deux tests ont réussi et qu’un test a échoué.

   > [!div class="mx-imgBorder"]
   > ![fenêtre de l’Explorateur de tests avec des tests ayant échoué](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Sélectionnez le test qui a échoué, `TestDoesNotStartWith`. La fenêtre **Explorateur de tests** affiche le message généré par l’assertion : « Échec de Assert.IsFalse. « Erreur » : false ; réel : True » était attendu ». En raison de l’échec, toutes les chaînes du tableau après « erreur » n’ont pas été testées.

   > [!div class="mx-imgBorder"]
   > ![fenêtre Explorateur de tests présentant l’échec de l’assertion IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Annulez la modification que vous avez effectuée à l’étape 1 en supprimant la chaîne « Error ». Réexécutez le test : il réussit maintenant.

## <a name="test-the-release-version-of-the-library"></a>Tester la version Release de la bibliothèque

Vous avez exécuté vos tests sur la version Debug de la bibliothèque. Maintenant que vos tests ont tous réussi et que vous avez testé votre bibliothèque de façon adéquate, vous devez exécuter les tests une fois de plus sur la version Release de la bibliothèque. Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.

Pour tester la version Release :

1. Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.

   > [!div class="mx-imgBorder"]
   > ![barre d’outils Visual Studio avec la version Release mise en surbrillance](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **StringLibrary** et sélectionnez **Générer** dans le menu contextuel pour recompiler la bibliothèque.

   > [!div class="mx-imgBorder"]
   > ![menu contextuel StringLibrary avec la commande de génération](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Exécutez les tests unitaires en sélectionnant **Test** > **Exécuter** > **Tous les Tests** dans la barre de menus. Les tests sont concluants.

Maintenant que vous avez fini de tester votre bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants. Vous pouvez la regrouper avec une ou plusieurs applications, ou vous pouvez la distribuer comme package NuGet. Pour plus d’informations, consultez [Consommation d’une bibliothèque de classes standard .NET](consuming-library-with-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Concepts de base des tests unitaires-Visual Studio](/visualstudio/test/unit-test-basics)
