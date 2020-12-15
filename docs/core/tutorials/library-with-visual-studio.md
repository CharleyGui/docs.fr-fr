---
title: Créer une bibliothèque de classes .NET à l’aide de Visual Studio
description: Découvrez comment créer une bibliothèque de classes .NET à l’aide de Visual Studio.
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperf-fy21q1
ms.openlocfilehash: 2d9b02a155c950b77565a66417948568f5fa039f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513118"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio"></a>Didacticiel : créer une bibliothèque de classes .NET à l’aide de Visual Studio

Dans ce didacticiel, vous allez créer une bibliothèque de classes simple qui contient une méthode de gestion de chaîne unique.

Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application. Si la bibliothèque cible .NET Standard 2,0, elle peut être appelée par n’importe quelle implémentation .NET (y compris .NET Framework) qui prend en charge .NET Standard 2,0. Si la bibliothèque cible .NET 5, elle peut être appelée par n’importe quelle application qui cible .NET 5. Ce didacticiel montre comment cibler .NET 5.

Lorsque vous créez une bibliothèque de classes, vous pouvez la distribuer en tant que package NuGet ou en tant que composant fourni avec l’application qui l’utilise.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019 version 16,8 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée. Le kit de développement logiciel (SDK) .NET 5,0 est automatiquement installé lorsque vous sélectionnez cette charge de travail. Ce didacticiel part du principe que vous avez activé **l’option Afficher tous les modèles .net core dans le nouveau projet**, comme indiqué dans [Didacticiel : créer une application console .net à l’aide de Visual Studio](with-visual-studio.md).

## <a name="create-a-solution"></a>Créer une solution

Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes. Une solution Visual Studio sert de conteneur pour un ou plusieurs projets. Vous ajouterez des projets connexes supplémentaires à la même solution.

Pour créer la solution vide :

1. Démarrez Visual Studio.

2. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

3. Dans la page **créer un nouveau projet** , entrez **solution** dans la zone de recherche. Choisissez le modèle de **solution vide** , puis cliquez sur **suivant**.

   :::image type="content" source="media/library-with-visual-studio/blank-solution.png" alt-text="Modèle Solution vide dans Visual Studio":::

4. Dans la page **configurer votre nouveau projet** , entrez **ClassLibraryProjects** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

## <a name="create-a-class-library-project"></a>Créer un projet de bibliothèque de classes

1. Ajoutez un nouveau projet de bibliothèque de classes .NET nommé « StringLibrary » à la solution.

   1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.

   1. Dans la page **Ajouter un nouveau projet** , entrez **bibliothèque** dans la zone de recherche. Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **bibliothèque de classes** , puis choisissez **suivant**.

   1. Dans la page **configurer votre nouveau projet** , entrez **StringLibrary** dans la zone **nom du projet** , puis choisissez **suivant**.

   1. Sur la page **informations supplémentaires** , sélectionnez **.net 5,0 (actuel)**, puis cliquez sur **créer**.

1. Assurez-vous que la bibliothèque cible la version correcte de .NET. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**. La zone de texte **Framework cible** indique que le projet cible .net 5,0.

1. Si vous utilisez Visual Basic, effacez le texte dans la zone de texte **espace de noms racine** .

   :::image type="content" source="./media/library-with-visual-studio/vb/library-project-properties.png" alt-text="Propriétés de projet pour la bibliothèque de classes":::

   Pour chaque projet, Visual Basic crée automatiquement un espace de noms qui correspond au nom du projet. Dans ce didacticiel, vous définissez un espace de noms de niveau supérieur à l’aide du [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) mot clé dans le fichier de code.

1. Remplacez le code dans la fenêtre de code pour *Class1.cs*  ou *Class1. vb* par le code suivant, puis enregistrez le fichier. Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   La bibliothèque de classes, `UtilityLibraries.StringLibrary` , contient une méthode nommée `StartsWithUpper` . Cette méthode retourne une <xref:System.Boolean> valeur qui indique si l’instance de chaîne en cours commence par un caractère majuscule. La norme Unicode distingue les caractères minuscules des caractères majuscules. La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.

   `StartsWithUpper` est implémenté en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md) afin que vous puissiez l’appeler comme s’il s’agissait d’un membre de la <xref:System.String> classe.

1. Dans la barre de menus, sélectionnez **générer**  >  **générer la solution** ou appuyez sur <kbd>CTRL</kbd> + <kbd>MAJ</kbd> + <kbd>B</kbd> pour vérifier que le projet se compile sans erreur.

## <a name="add-a-console-app-to-the-solution"></a>Ajouter une application console à la solution

Ajoutez une application console qui utilise la bibliothèque de classes. L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.

1. Ajoutez une nouvelle application console .NET nommée « ShowCase » à la solution.

   1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.

   1. Dans la page **Ajouter un nouveau projet** , dans la zone de recherche, entrez **console** . Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.

   1. Choisissez le modèle **application console** , puis cliquez sur **suivant**.

   1. Dans la page **configurer votre nouveau projet** , entrez **Showcase** dans la zone **nom du projet** . Ensuite, choisissez **Suivant**.

   1. Sur la page **informations supplémentaires** , sélectionnez **.net 5,0 (actuel)** dans la zone **Framework cible** . Choisissez ensuite **Créer**.

1. Dans la fenêtre de code du fichier *Program.cs* ou *Program. vb* , remplacez tout le code par le code suivant.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console. Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.

   Le programme invite l’utilisateur à entrer une chaîne. Il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `ShowCase` nœud **dépendances** du projet, puis sélectionnez **Ajouter une référence de projet**.

   :::image type="content" source="media/library-with-visual-studio/add-reference-context-menu.png" alt-text="Menu contextuel ajouter une référence dans Visual Studio":::

1. Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez le projet **StringLibrary** , puis cliquez sur **OK**.

   :::image type="content" source="media/library-with-visual-studio/manage-project-references.png" alt-text="Boîte de dialogue Gestionnaire de références avec StringLibrary sélectionné":::

## <a name="run-the-app"></a>Exécuter l’application

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.

   :::image type="content" source="media/library-with-visual-studio/set-startup-project-context-menu.png" alt-text="Menu contextuel du projet Visual Studio pour définir le projet de démarrage":::

1. Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour compiler et exécuter le programme sans débogage.

   :::image type="content" source="media/library-with-visual-studio/visual-studio-project-toolbar.png" alt-text="Barre d’outils de projet Visual Studio avec le bouton déboguer":::

1. Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Fenêtre de console avec la vitrine en cours d’exécution":::

## <a name="additional-resources"></a>Ressources supplémentaires

* [Développer des bibliothèques avec l’interface CLI .NET](libraries.md)
* [.NET standard versions et les plateformes qu’ils prennent en charge](../../standard/net-standard.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé une bibliothèque de classes. Dans le didacticiel suivant, vous allez apprendre à effectuer un test unitaire de la bibliothèque de classes.

> [!div class="nextstepaction"]
> [Test unitaire d’une bibliothèque de classes .NET à l’aide de Visual Studio](testing-library-with-visual-studio.md)

Vous pouvez également ignorer les tests unitaires automatisés et apprendre à partager la bibliothèque en créant un package NuGet :

> [!div class="nextstepaction"]
> [Créer et publier un package avec Visual Studio](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

Ou Découvrez comment publier une application console. Si vous publiez l’application console à partir de la solution que vous avez créée dans ce didacticiel, la bibliothèque de classes y est insérée comme un fichier *. dll* .

> [!div class="nextstepaction"]
> [Publier une application console .NET à l’aide de Visual Studio](publishing-with-visual-studio.md)
