---
title: Créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio
description: Découvrez comment créer une bibliothèque de classes .NET Standard à l’aide de Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 69259b1d47a8e30945c578db10c6d697c81fa261
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164400"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a>Didacticiel : créer une bibliothèque de .NET Standard à l’aide de Visual Studio

Dans ce didacticiel, vous allez créer une bibliothèque d’utilitaire simple qui contient une méthode de gestion de chaîne unique. Vous l’implémentez en tant que [méthode d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md) pour pouvoir l’appeler comme s’il s’agissait d’un membre de la <xref:System.String> classe.

Une *bibliothèque de classes* définit des types et des méthodes qui peuvent être appelés par une application. Une bibliothèque de classes qui cible .NET Standard 2,0 permet à votre bibliothèque d’être appelée par n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard. Lorsque vous avez terminé votre bibliothèque de classes, vous pouvez la distribuer en tant que composant tiers ou en tant que composant groupé avec une ou plusieurs applications.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019 version 16,6 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée. Le kit de développement logiciel (SDK) .NET Core 3,1 est automatiquement installé lorsque vous sélectionnez cette charge de travail.

  Pour plus d’informations, consultez la section [install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) de l’article [install the kit SDK .net Core](../install/sdk.md?pivots=os-windows) .

## <a name="create-a-solution"></a>Créer une solution

Commencez par créer une solution vide dans laquelle placer le projet de bibliothèque de classes. Une solution Visual Studio sert de conteneur pour un ou plusieurs projets. Vous ajouterez des projets connexes supplémentaires à la même solution.

Pour créer la solution vide :

1. Démarrez Visual Studio.

2. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

3. Dans la page **créer un nouveau projet** , entrez **solution** dans la zone de recherche. Choisissez le modèle de **solution vide** , puis cliquez sur **suivant**.

   ![Modèle Solution vide dans Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Dans la page **configurer votre nouveau projet** , entrez **ClassLibraryProjects** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

## <a name="create-a-class-library-project"></a>Créer un projet de bibliothèque de classes

1. Ajoutez un nouveau projet de bibliothèque de classes .NET Standard nommé « StringLibrary » à la solution.

   1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.

   1. Dans la page **Ajouter un nouveau projet** , entrez **bibliothèque** dans la zone de recherche. Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **bibliothèque de classes (.NET standard)** , puis choisissez **suivant**.

   1. Dans la page **configurer votre nouveau projet** , entrez **StringLibrary** dans la zone **nom du projet** . Ensuite, choisissez **créer**.

1. Assurez-vous que la bibliothèque cible la version correcte de .NET Standard. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet de bibliothèque, puis sélectionnez **Propriétés**. La zone de texte de la version **cible du .NET Framework** indique que le projet cible .NET standard 2,0.

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/library-project-properties.png)

1. Si vous utilisez Visual Basic, effacez le texte dans la zone de texte **espace de noms racine** .

   ![Propriétés de projet pour la bibliothèque de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

   Pour chaque projet, Visual Basic crée automatiquement un espace de noms qui correspond au nom du projet. Dans ce didacticiel, vous définissez un espace de noms de niveau supérieur à l’aide du [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) mot clé dans le fichier de code.

1. Remplacez le code dans la fenêtre de code pour *Class1.cs* ou *Class1. vb* par le code suivant, puis enregistrez le fichier. Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   La bibliothèque de classes, `UtilityLibraries.StringLibrary` , contient une méthode nommée `StartsWithUpper` . Cette méthode retourne une <xref:System.Boolean> valeur qui indique si l’instance de chaîne en cours commence par un caractère majuscule. La norme Unicode distingue les caractères minuscules des caractères majuscules. La méthode <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retourne `true` si un caractère est en majuscule.

1. Dans la barre de menus, sélectionnez **générer**  >  **générer la solution** pour vérifier que le projet se compile sans erreur.

## <a name="add-a-console-app-to-the-solution"></a>Ajouter une application console à la solution

Ajoutez une application console qui utilise la bibliothèque de classes. L’application invite l’utilisateur à entrer une chaîne et signale si la chaîne commence par un caractère majuscule.

1. Ajoutez une nouvelle application console .NET Core nommée « ShowCase » à la solution.

   1. Cliquez avec le bouton droit sur la solution dans **Explorateur de solutions** , puis sélectionnez **Ajouter**  >  **un nouveau projet**.

   1. Dans la page **Ajouter un nouveau projet** , dans la zone de recherche, entrez **console** . Choisissez **C#** ou **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme.

   1. Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.

   1. Dans la page **configurer votre nouveau projet** , entrez **Showcase** dans la zone **nom du projet** . Choisissez ensuite **Créer**.

1. Dans la fenêtre de code du fichier *Program.cs* ou *Program. vb* , remplacez tout le code par le code suivant.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   Le code utilise la variable `row` pour comptabiliser le nombre de lignes de données écrites dans la fenêtre de console. Lorsqu’il est supérieur ou égal à 25, le code efface la fenêtre de console et affiche un message à l’utilisateur.

   Le programme invite l’utilisateur à entrer une chaîne. Il indique si la chaîne commence par une majuscule. Si l’utilisateur appuie sur la touche <kbd>entrée</kbd> sans entrer de chaîne, l’application se termine et la fenêtre de console se ferme.

## <a name="add-a-project-reference"></a>Ajouter une référence au projet

Initialement, le nouveau projet d’application console n’a pas accès à la bibliothèque de classes. Pour lui permettre d’appeler des méthodes dans la bibliothèque de classes, créez une référence de projet au projet de bibliothèque de classes.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `ShowCase` nœud **dépendances** du projet, puis sélectionnez **Ajouter une référence de projet**.

   ![Menu contextuel ajouter une référence dans Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez le projet **StringLibrary** , puis cliquez sur **OK**.

   ![Boîte de dialogue Gestionnaire de références avec StringLibrary sélectionné](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a>Exécuter l’application

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet **ShowCase**, puis sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.

   ![Menu contextuel du projet Visual Studio pour définir le projet de démarrage](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour compiler et exécuter le programme sans débogage.

   ![Barre d’outils de projet Visual Studio avec le bouton déboguer](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. Essayez le programme en entrant des chaînes et en appuyant sur <kbd>entrée</kbd>, puis appuyez sur <kbd>entrée</kbd> pour quitter.

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Fenêtre de console avec la vitrine en cours d’exécution":::

## <a name="additional-resources"></a>Ressources supplémentaires

* [Développer des bibliothèques avec le CLI .NET Core](libraries.md)
* [.NET standard versions et les plateformes qu’ils prennent en charge](../../standard/net-standard.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez créé une solution, ajouté un projet de bibliothèque et ajouté un projet d’application console qui utilise la bibliothèque. Dans le didacticiel suivant, vous allez ajouter un projet de test unitaire à la solution.

> [!div class="nextstepaction"]
> [Tester une bibliothèque .NET Standard avec .NET Core à l’aide de Visual Studio](testing-library-with-visual-studio.md)
