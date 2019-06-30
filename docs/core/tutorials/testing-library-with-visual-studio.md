---
title: Tester une bibliothèque .NET Standard avec .NET Core dans Visual Studio 2017
description: Créez un projet de test unitaire pour votre bibliothèque de classes .NET Core. Vérifiez que votre bibliothèque de classes .NET Core fonctionne correctement avec des tests unitaires.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 32593465c1a161aa1293b7b233539fa930c7e1d8
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402210"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a>Tester une bibliothèque .NET Standard avec .NET Core dans Visual Studio 2017

Dans [Générer une bibliothèque .NET Standard avec C# et .NET Core dans Visual Studio 2017](library-with-visual-studio.md) ou [Générer une bibliothèque .NET Standard avec Visual Basic et .NET Core dans Visual Studio 2017](vb-library-with-visual-studio.md), vous avez créé une bibliothèque de classes simple qui ajoute une méthode d’extension à la classe <xref:System.String>. À présent, vous allez créer un test unitaire pour vérifier qu’elle fonctionne comme prévu. Vous allez ajouter votre projet de test unitaire à la solution créée dans l’article précédent.

## <a name="creating-a-unit-test-project"></a>Création d'un projet de test unitaire

Pour créer le projet de test unitaire, procédez comme suit :

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du nœud de la solution **ClassLibraryProjects** et sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud **Visual C#** . Ensuite, sélectionnez le nœud **.NET Core** puis choisissez le modèle de projet **Projet de test MSTest (.NET Core)** . Dans la zone de texte **Nom**, entrez « StringLibraryTest » comme nom de projet. Sélectionnez **OK** pour créer le projet de test unitaire.

   ![Boîte de dialogue Ajouter un nouveau projet avec projet de test unitaire affiché - C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > Outre un projet de test MSTest, vous pouvez utiliser Visual Studio pour créer un projet de test xUnit pour .NET Core.

1. Visual Studio crée le projet et ouvre le fichier *UnitTest1.cs* dans la fenêtre de code.

   ![Fenêtre de code Visual Studio du test unitaire avec la classe de projet et la méthode - C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   Le code source créé par le modèle de test unitaire effectue les opérations suivantes :

   * Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.

   * Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> à la classe `UnitTest1`. Chaque méthode de test dans une classe de test marquée avec l’attribut \[TestMethod\] est exécutée automatiquement quand le test unitaire est exécuté.

   * Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> pour définir `TestMethod1` comme une méthode de test qui doit être exécutée automatiquement quand le test unitaire est exécuté.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet **StringLibraryTest** puis sélectionnez **Ajouter une référence** dans le menu contextuel.

   ![Menu contextuel des dépendances de StringLibraryTest - C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, développez le nœud **Projets**, cochez la case en regard de **StringLibrary**. L’ajout d’une référence à l’assembly `StringLibrary` permet au compilateur de trouver les méthodes **StringLibrary**. Sélectionnez le bouton **OK**. Ceci ajoute une référence à votre projet de bibliothèque de classes `StringLibrary`.

   ![Boîte de dialogue Ajouter une référence de projet dans Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb) 
1. Dans l’**Explorateur de solutions**, ouvrez le menu contextuel du nœud de la solution **ClassLibraryProjects** et sélectionnez **Ajouter** > **Nouveau projet**.

1. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez le nœud **Visual Basic**. Ensuite, sélectionnez le nœud **.NET Core** puis choisissez le modèle de projet **Projet de test MSTest (.NET Core)** . Dans la zone de texte **Nom**, entrez « StringLibraryTest » comme nom de projet. Sélectionnez **OK** pour créer le projet de test unitaire.

   ![Boîte de dialogue Ajouter un nouveau projet avec projet de test unitaire affiché - Visual Basic](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > Outre un projet de test MSTest, vous pouvez utiliser Visual Studio pour créer un projet de test xUnit pour .NET Core.

1. Visual Studio crée le projet et ouvre le fichier *UnitTest1.vb* dans la fenêtre de code.

   ![Fenêtre de code Visual Studio du test unitaire avec la classe de projet et la méthode - Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   Le code source créé par le modèle de test unitaire effectue les opérations suivantes :

   * Il importe l’espace de noms <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType>, qui contient les types utilisés pour les tests unitaires.

   * Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>) à la classe `UnitTest1`. Chaque méthode de test dans une classe de test marquée avec l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> est exécutée automatiquement quand le test unitaire est exécuté.

   * Il applique l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> pour définir `TestMethod1` comme une méthode de test qui doit être exécutée automatiquement quand le test unitaire est exécuté.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Dépendances** du projet **StringLibraryTest** puis sélectionnez **Ajouter une référence** dans le menu contextuel.

   ![Menu contextuel des dépendances de StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. Dans la boîte de dialogue **Gestionnaire de références**, développez le nœud **Projets**, cochez la case en regard de **StringLibrary**. L’ajout d’une référence à l’assembly `StringLibrary` permet au compilateur de trouver les méthodes **StringLibrary**. Sélectionnez le bouton **OK**. Ceci ajoute une référence à votre projet de bibliothèque de classes `StringLibrary`.

   ![Boîte de dialogue Ajouter une référence de projet dans Visual Studio - Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)
---

## <a name="adding-and-running-unit-test-methods"></a>Ajout et exécution de méthodes de test unitaire

Quand Visual Studio exécute un test unitaire, il exécute chaque méthode marquée avec l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> dans une classe de test unitaire, la classe à laquelle l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> est appliqué. Une méthode de test se termine quand la première défaillance survient, ou quand tous les tests contenus dans la méthode ont réussi.

Les tests les plus courants appellent des membres de la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. De nombreuses méthodes d’assertion incluent au moins deux paramètres, à savoir le résultat attendu pour le test et résultat réel du test. Certaines de ses méthodes les plus fréquemment appelées figurent dans le tableau ci-dessous.

Méthodes d’assertion | Fonction
--- | ---
`Assert.AreEqual` | Vérifie que deux valeurs ou objets sont égaux. L’assertion échoue si les valeurs ou les objets ne sont pas égaux.
`Assert.AreSame` | Vérifie que deux variables d’objet référencent le même objet. L’assertion échoue si les variables font référence à des objets différents.
`Assert.IsFalse` | Vérifie qu’une condition est `false`. L’assertion échoue si la condition est `true`.
`Assert.IsNotNull` | Vérifie qu’un objet n’est pas `null`. L’assertion échouera si l’objet est `null`.

Vous pouvez également appliquer l’attribut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> à une méthode de test. Il indique le type d’exception qu’une méthode de test est supposée lever. Le test échoue si l’exception spécifiée n’est pas levée.

Dans le test de la méthode `StringLibrary.StartsWithUpper`, vous voulez fournir une série de chaînes qui commencent par une majuscule. Vous attendez que la méthode retourne `true` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>. De même, vous voulez fournir des chaînes qui commencent par autre chose qu’un caractère majuscule. Vous attendez que la méthode retourne `false` dans de tels cas, et vous pouvez donc appeler la méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.

Dans la mesure où votre méthode de bibliothèque gère les chaînes, vous voulez également vous assurer qu’elle gère correctement une [chaîne vide (`String.Empty`)](xref:System.String.Empty), une chaîne valide sans caractères et dont <xref:System.String.Length> a la valeur 0 et une chaîne `null` qui n’a pas été initialisée. Si vous appelez `StartsWithUpper` comme méthode d’extension sur une instance <xref:System.String>, il n’est pas possible de lui passer une chaîne `null`. Toutefois, vous pouvez également l’appeler directement comme méthode statique et passer un seul argument <xref:System.String>.

Vous allez définir trois méthodes, chacune appelant sa méthode <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> de façon répétée pour chaque élément d’un tableau de chaînes. Comme la méthode de test échoue dès qu’elle rencontre le premier échec, vous appelez une surcharge de méthode qui permet de passer une chaîne indiquant la valeur de chaîne utilisée dans l’appel de méthode.

Pour créer les méthodes de test:

# <a name="ctabcsharp"></a>[C#](#tab/csharp) 
1. Dans la fenêtre de code *UnitTest1.cs*, remplacez le code par le code suivant :

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Notez que votre test de caractères majuscules dans la méthode `TestStartsWithUpper` inclut la lettre majuscule grecque alpha (U+0391) et la lettre majuscule cyrillique EM (U+041C), et que le test de caractères minuscules dans la méthode `TestDoesNotStartWithUpper` inclut la lettre minuscule grecque alpha (U+03B1) et la lettre minuscule cyrillique Gué (U+0433).

1. Dans la barre de menus, sélectionnez **Fichier** > **Enregistrer UnitTest1.cs sous**. Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec l’encodage**.

   ![Boîte de dialogue Enregistrer sous dans Visual Studio - C#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb) 
1. Dans la fenêtre de code *UnitTest1.vb*, remplacez le code par le code suivant :

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Notez que votre test de caractères majuscules dans la méthode `TestStartsWithUpper` inclut la lettre majuscule grecque alpha (U+0391) et la lettre majuscule cyrillique EM (U+041C), et que le test de caractères minuscules dans la méthode `TestDoesNotStartWithUpper` inclut la lettre minuscule grecque alpha (U+03B1) et la lettre minuscule cyrillique Gué (U+0433).

1. Dans la barre de menus, sélectionnez **Fichier** > **Enregistrer UnitTest1.vb sous**. Dans la boîte de dialogue **Enregistrer le fichier sous**, cliquez sur la flèche à côté du bouton **Enregistrer**, puis choisissez **Enregistrer avec l’encodage**.

   ![Boîte de dialogue Enregistrer sous dans Visual Studio - Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)
---

1. Dans la boîte de dialogue **Confirmer l’enregistrement sous**, sélectionnez le bouton **Oui** pour enregistrer le fichier.

1. Dans la boîte de dialogue **Options d’enregistrement avancées**, sélectionnez **Unicode (UTF-8 avec signature) - Page de codes 65001** dans la liste déroulante **Encodage**, puis sélectionnez **OK**.

   ![Boîte de dialogue Options d’enregistrement avancées dans Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Si vous ne parvenez pas à enregistrer votre code source dans un fichier encodé en UTF-8, Visual Studio peut l’enregistrer en tant que fichier ASCII. Dans ce cas, le runtime ne décode pas correctement les caractères UTF-8 en dehors de la plage ASCII, et les résultats des tests ne seront pas exacts.

1. Dans la barre de menus, sélectionnez **Test** > **Exécuter** > **Tous les Tests**. La fenêtre **Explorateur de tests** s’ouvre et montre que les tests ont réussi. Les trois tests sont listés dans la section **Tests réussis** et la section **Résumé** indique le résultat de la série de tests.

   ![Fenêtre Explorateur de tests avec tests réussis](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a>Gestion des échecs des tests

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

   ![Fenêtre Explorateur de tests avec tests ayant échoué](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Dans la section **Tests ayant échoué**, sélectionnez le test ayant échoué, `TestDoesNotStartWith`. La fenêtre **Explorateur de tests** affiche le message généré par l’assertion : « Échec de Assert.IsFalse. « Erreur » : false ; réel : True » était attendu ». En raison de l’échec, toutes les chaînes dans le tableau après « Error » n’ont pas été testées.

   ![Fenêtre Explorateur de tests montrant l’échec de l’assertion IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Annulez la modification que vous avez effectuée à l’étape 1 en supprimant la chaîne « Error ». Réexécutez le test : il réussit maintenant.

## <a name="testing-the-release-version-of-the-library"></a>Test de la version de la version Release de la bibliothèque

Vous avez exécuté vos tests sur la version Debug de la bibliothèque. Maintenant que vos tests ont tous réussi et que vous avez testé votre bibliothèque de façon adéquate, vous devez exécuter les tests une fois de plus sur la version Release de la bibliothèque. Un certain nombre de facteurs, notamment les optimisations du compilateur, peuvent parfois produire un comportement différent entre les versions Debug et Release.

Pour tester la version Release :

1. Dans la barre d’outils de Visual Studio, modifiez la configuration de build de **Debug** à **Release**.

   ![Barre d’outils Visual Studio avec version Release mise en surbrillance](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **StringLibrary** et sélectionnez **Générer** dans le menu contextuel pour recompiler la bibliothèque.

   ![Menu contextuel de StringLibrary avec commande build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Exécutez les tests unitaires en sélectionnant **Test** > **Exécuter** > **Tous les Tests** dans la barre de menus. Les tests réussissent.

Maintenant que vous avez fini de tester votre bibliothèque, l’étape suivante consiste à la rendre accessible aux appelants. Vous pouvez la regrouper avec une ou plusieurs applications, ou vous pouvez la distribuer comme package NuGet. Pour plus d’informations, consultez [Consommation d’une bibliothèque de classes standard .NET](./consuming-library-with-visual-studio.md).
