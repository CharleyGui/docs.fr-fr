---
title: Créer une application Hello World avec .NET Core dans Visual Studio
description: Découvrez comment créer votre première application de console .NET Core avec C# ou Visual Basic à l’aide de Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 738fc49a820c3c5d94fb35c1bf7a8b718ed75cb3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394828"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Didacticiel : créer votre première application de console .NET Core dans Visual Studio 2019

Cet article fournit une présentation pas à pas de la création et de l’exécution d’une application console Hello World .NET Core dans Visual Studio 2019. Une application Hello World est traditionnellement utilisée pour introduire des débutants dans un nouveau langage de programmation. Ce programme affiche simplement l’expression « Hello World ! » à l’écran.

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2019 version 16,4 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail **développement multiplateforme .net Core** installée. Le kit de développement logiciel (SDK) .NET Core 3,1 est automatiquement installé lorsque vous sélectionnez cette charge de travail.

Pour plus d’informations, consultez la section [install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) de l’article [install the kit SDK .net Core](../install/sdk.md?pivots=os-windows) .

## <a name="create-the-app"></a>Créer l’application

Les instructions suivantes créent une application console Hello World simple :

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

1. Ouvrez Visual Studio 2019.

1. Créez un nouveau projet d’application console C# .NET Core nommé « HelloWorld ».

   1. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

      ![Bouton créer un projet sélectionné dans la fenêtre de démarrage de Visual Studio](./media/with-visual-studio/start-window.png)

   1. Sur la page **créer un nouveau projet** , dans la zone de recherche, entrez **console** . Ensuite, choisissez **C#** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.

      ![Créer une fenêtre de projet avec les filtres sélectionnés](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Si vous ne voyez pas les modèles .NET Core, vous ne disposez probablement pas de la charge de travail requise installée. Sous le message **vous ne trouvez pas ce que vous recherchez ?** , choisissez le lien **installer d’autres outils et fonctionnalités** . Le Visual Studio Installer s’ouvre. Assurez-vous que la charge de travail de **développement multiplateforme .net Core** est installée.

   1. Dans la page **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** . Ensuite, choisissez **créer**.

      ![Configurer votre nouvelle fenêtre de projet avec les champs nom du projet, emplacement et nom de la solution](./media/with-visual-studio/configure-new-project.png)

   Le modèle d’application console C# pour .NET Core définit automatiquement une classe, `Program`, avec une méthode unique, `Main`, qui accepte un tableau de <xref:System.String> comme argument. `Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Ouvrez Visual Studio 2019.

1. Créez un projet d’application console .NET Core Visual Basic nommé « HelloWorld ».

   1. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

      ![Bouton créer un projet sélectionné dans la fenêtre de démarrage de Visual Studio](./media/with-visual-studio/start-window.png)

   1. Sur la page **créer un nouveau projet** , dans la zone de recherche, entrez **console** . Ensuite, choisissez **Visual Basic** dans la liste langue, puis choisissez **toutes les plateformes** dans la liste plateforme. Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.

      ![Choisir le modèle Visual Basic pour l’application console (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > Si vous ne voyez pas les modèles .NET Core, vous ne disposez probablement pas de la charge de travail requise installée. Sous le message **vous ne trouvez pas ce que vous recherchez ?** , choisissez le lien **installer d’autres outils et fonctionnalités** . Le Visual Studio Installer s’ouvre. Assurez-vous que la charge de travail de **développement multiplateforme .net Core** est installée.

   1. Dans la page **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** . Ensuite, choisissez **créer**.

   Le modèle d’application console pour .NET Core définit automatiquement une classe, `Program` , avec une méthode unique, `Main` , qui prend un <xref:System.String> tableau en tant qu’argument. `Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Les arguments de ligne de commande fournis lorsque l’application est lancée sont disponibles dans le `args` paramètre.

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   Le modèle crée une application « Hello World » simple. Il appelle la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World ! » dans la fenêtre de console.

## <a name="run-the-app"></a>Exécuter l’application

1. Pour exécuter le programme, choisissez **HelloWorld** dans la barre d’outils, ou appuyez sur **F5**.

   ![Barre d’outils Visual Studio avec le bouton Exécuter HelloWorld sélectionné](./media/with-visual-studio/run-program.png)

   Une fenêtre de console s’ouvre avec le texte « Hello World ! » imprimé à l’écran et certaines informations de débogage de Visual Studio.

   ![Fenêtre de console affichant « Hello World Press any key to continue »](./media/with-visual-studio/hello-world-console.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

## <a name="enhance-the-app"></a>Améliorer l’application

Améliorez votre application pour inviter l’utilisateur à entrer son nom, et pour l’afficher avec la date et l’heure. Les instructions suivantes modifient et réexécutent l’application :

# <a name="c"></a>[C#](#tab/csharp)

1. Remplacez le contenu de la `Main` méthode, qui est actuellement simplement la ligne qui appelle `Console.WriteLine` , par le code suivant :

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   Ce code affiche « What is your name? ». dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée. Il stocke cette chaîne dans une variable nommée `name`. Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`. Enfin, elle utilise une [chaîne interpolée](../../csharp/language-reference/tokens/interpolated.md) pour afficher ces valeurs dans la fenêtre de console.

1. Compilez le programme en choisissant **générer**  >  **générer la solution**.

1. Pour exécuter le programme, choisissez **HelloWorld** dans la barre d’outils, ou appuyez sur **F5**.

1. Répondez à l’invite en entrant un nom et en appuyant sur la touche **entrée** .

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Remplacez le contenu de la `Main` méthode, qui est actuellement simplement la ligne qui appelle `Console.WriteLine` , par le code suivant :

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   Ce code affiche « What is your name? ». dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée. Il stocke cette chaîne dans une variable nommée `name`. Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`. Enfin, elle utilise une [chaîne interpolée](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) pour afficher ces valeurs dans la fenêtre de console.

1. Compilez le programme en choisissant **générer**  >  **générer la solution**.

1. Pour exécuter le programme, choisissez **HelloWorld** dans la barre d’outils, ou appuyez sur **F5**.

1. Répondez à l’invite en entrant un nom et en appuyant sur la touche **entrée** .

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

---

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez créé et exécuté votre première application .NET Core. À l’étape suivante, vous allez déboguer votre application.

> [!div class="nextstepaction"]
> [Déboguer une application Hello World .NET Core dans Visual Studio](debugging-with-visual-studio.md)
