---
title: Testez une bibliothèque de classe Standard .NET avec .NET Core in Visual Studio
description: Créez un projet de test unitaire pour votre bibliothèque de classes .NET Core. Vérifiez que votre bibliothèque de classes .NET Core fonctionne correctement avec des tests unitaires.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156619"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>Testez une bibliothèque standard .NET avec .NET Core in Visual Studio

Dans [Construire une bibliothèque .NET Standard à Visual Studio](library-with-visual-studio.md), vous avez <xref:System.String> créé une bibliothèque de classe simple qui ajoute une méthode d’extension à la classe. À présent, vous allez créer un test unitaire pour vérifier qu’elle fonctionne comme prévu. Vous allez ajouter votre projet de test unitaire à la solution créée dans l’article précédent.

## <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

Pour créer le projet de test unitaire, procédez comme suit :

1. Ouvrez `ClassLibraryProjects` la solution que vous avez créée dans l’article [Build a .NET Standard dans l’article Visual Studio.](library-with-visual-studio.md)

1. Ajoutez un nouveau projet de test unitaire nommé "StringLibraryTest" à la solution.

   1. Cliquez à droite sur la solution dans **Solution Explorer** et sélectionnez **Ajouter** > **un nouveau projet**.

   1. Sur la page **Ajouter un nouveau projet,** entrez **mstest** dans la boîte de recherche. Choisissez **C ou** Visual **Basic** dans la liste de langue, puis choisissez toutes **les plates-formes** de la liste de la plate-forme. Choisissez le modèle **MsTest Test Project (.NET Core),** puis choisissez **Next**.

   1. Sur la configuration de votre nouvelle page **de projet,** entrez **StringLibraryTest** dans la boîte **de nom du projet.** Sélectionnez ensuite **Créer**.

   > [!NOTE]
   > En plus d’un MSTest, vous pouvez également créer des projets de test xUnit et nUnit pour .NET Core dans Visual Studio.

1. Visual Studio crée le projet et ouvre le fichier de classe dans la fenêtre de code avec le code suivant :

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

   - Il applique l’attribut [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) à la classe `UnitTest1`. Chaque méthode de test dans une classe de test marquée avec l’attribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) est exécutée automatiquement quand le test unitaire est exécuté.

   - Il applique l’attribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) à définir `TestMethod1` dans C ou `TestSub` dans Visual Basic comme méthode de test pour l’exécution automatique lorsque le test unitaire est exécuté.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet **StringLibraryTest** puis sélectionnez **Ajouter une référence** dans le menu contextuel.

   > [!div class="mx-imgBorder"]
   > ![Menu contextuelle des dépendances StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, développez le nœud **Projets**, cochez la case en regard de **StringLibrary**. L’ajout d’une référence à l’assembly `StringLibrary` permet au compilateur de trouver les méthodes **StringLibrary**. Sélectionnez le bouton **OK.** Une référence est ajoutée à `StringLibrary`votre projet de bibliothèque de classe, .

   ![Dialogue de gestionnaire de référence dans Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>Ajouter et exécuter des méthodes d’essai unitaire

Lorsque Visual Studio exécute un test unitaire, il <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> exécute chaque méthode qui est marquée <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> avec l’attribut dans une classe de test unitaire, la classe à laquelle l’attribut est appliqué. Une méthode de test se termine lorsque la première défaillance est constatée ou lorsque tous les tests contenus dans la méthode ont réussi.

Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test. Certaines des `Assert` méthodes les plus fréquemment appelées de la classe sont présentées dans le tableau suivant :

| Méthodes d’assertion     | Fonction |
| ------------------ | -------- |
| `Assert.AreEqual`  | Vérifie que deux valeurs ou objets sont égaux. L’affirmation échoue si les valeurs ou les objets ne sont pas égaux. |
| `Assert.AreSame`   | Vérifie que deux variables d’objet référencent le même objet. L’assertion échoue si les variables font référence à des objets différents. |
| `Assert.IsFalse`   | Vérifie qu’une condition est `false`. L’assertion échoue si la condition est `true`. |
| `Assert.IsNotNull` | Vérifie qu’un objet `null`n’est pas . L’assertion échouera si l’objet est `null`. |

Vous pouvez également <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> utiliser la méthode dans une méthode de test pour indiquer le type d’exception qu’il est censé jeter. Le test échoue si l’exception spécifiée n’est pas lancée.

Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule. Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>. De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule. Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.

Puisque votre méthode de bibliothèque gère des cordes, vous voulez également vous assurer qu’elle gère avec <xref:System.String.Length> succès une chaîne `null` [vide ()`String.Empty`](xref:System.String.Empty), une chaîne valide qui n’a pas de caractères et dont est 0, et une chaîne qui n’a pas été initialisée. Si `StartsWithUpper` est appelé comme une <xref:System.String> méthode d’extension sur `null` une instance, il ne peut pas être passé une chaîne. Toutefois, vous pouvez également l’appeler directement comme méthode statique et passer un seul argument <xref:System.String>.

Vous définirez trois méthodes, chacune <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> appelant une méthode à plusieurs reprises pour chaque élément dans un tableau de cordes. Parce que la méthode de test échoue dès qu’elle trouve la première défaillance, vous appellerez une surcharge de méthode qui vous permet de passer une chaîne qui indique la valeur de chaîne utilisée dans l’appel de méthode.

Pour créer les méthodes de test:

1. Dans la *fenêtre de* code UnitTest1.cs ou *UnitTest1.vb,* remplacez le code par le code suivant :

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Le test des caractères `TestStartsWithUpper` majuscules de la méthode comprend la lettre de majuscule grecque alpha (U-0391) et la lettre de majuscules cyrillique EM (U-041C). Le test des caractères `TestDoesNotStartWithUpper` minuscules de la méthode comprend la petite lettre grecque alpha (U-03B1) et la petite lettre cyrillique Ghe (U-0433).

1. Sur la barre de menu, sélectionnez **Fichier** > **Enregistrer UnitTest1.cs As** ou **Fichier** > Enregistrer**UnitTest1.vb As**. Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec l’encodage**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Enregistrer Fichier comme dialogue](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. Dans la boîte de dialogue **Confirmer l’enregistrement sous**, sélectionnez le bouton **Oui** pour enregistrer le fichier.

1. Dans la boîte de dialogue **Options d’enregistrement avancées**, sélectionnez **Unicode (UTF-8 avec signature) - Page de codes 65001** dans la liste déroulante **Encodage**, puis sélectionnez **OK**.

   > [!div class="mx-imgBorder"]
   > ![Boîte de dialogue Options d’enregistrement avancées dans Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII. Lorsque cela se produit, l’exécution ne décode pas avec précision les caractères UTF8 en dehors de la plage ASCII, et les résultats des tests ne seront pas corrects.

1. Sur la barre de menu, sélectionnez **Test** > **Run** > **All Tests**. La fenêtre **Explorateur de tests** s’ouvre et montre que les tests ont réussi. Les trois tests sont listés dans la section **Tests réussis** et la section **Résumé** indique le résultat de la série de tests.

   > [!div class="mx-imgBorder"]
   > ![Fenêtre Explorateur de tests avec tests réussis](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Gérer les échecs des tests

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

1. Exécutez le test en sélectionnant **Test** > **Run** > **All Tests** à partir de la barre de menu. La fenêtre **Explorateur de tests** indique que deux tests ont réussi et qu’un test a échoué.

   > [!div class="mx-imgBorder"]
   > ![Fenêtre Explorateur de tests avec tests ayant échoué](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Sélectionnez le `TestDoesNotStartWith`test échoué, . La fenêtre **Explorateur de tests** affiche le message généré par l’assertion : « Échec de Assert.IsFalse. « Erreur » : false ; réel : True » était attendu ». En raison de l’échec, toutes les chaînes dans le tableau après "Erreur" n’ont pas été testés.

   > [!div class="mx-imgBorder"]
   > ![Fenêtre Test Explorer montrant l’échec de l’affirmation IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Annulez la modification que vous avez effectuée à l’étape 1 en supprimant la chaîne « Error ». Réexécutez le test : il réussit maintenant.

## <a name="test-the-release-version-of-the-library"></a>Testez la version Libération de la bibliothèque

Vous avez exécuté vos tests sur la version Debug de la bibliothèque. Maintenant que vos tests ont tous réussi et que vous avez testé votre bibliothèque de façon adéquate, vous devez exécuter les tests une fois de plus sur la version Release de la bibliothèque. Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.

Pour tester la version Release :

1. Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.

   > [!div class="mx-imgBorder"]
   > ![Barre d’outils Visual Studio avec version Release mise en surbrillance](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **StringLibrary** et sélectionnez **Générer** dans le menu contextuel pour recompiler la bibliothèque.

   > [!div class="mx-imgBorder"]
   > ![Menu contextuel de StringLibrary avec commande build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Exécutez les tests unitaires en choisissant **Test** > **Run** > **All Tests** à partir de la barre de menu. Les tests réussissent.

Maintenant que vous avez fini de tester votre bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants. Vous pouvez la regrouper avec une ou plusieurs applications, ou vous pouvez la distribuer comme package NuGet. Pour plus d’informations, consultez [Consommation d’une bibliothèque de classes standard .NET](consuming-library-with-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Bases de test unitaire - Visual Studio](/visualstudio/test/unit-test-basics)
