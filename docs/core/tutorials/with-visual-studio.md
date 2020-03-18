---
title: Créez une application Hello World avec .NET Core dans Visual Studio
description: Apprenez à créer votre première application de console .NET Core avec C ou Visual Basic à l’aide de Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713997"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Tutorial: Créer votre première application de console .NET Core dans Visual Studio 2019

Cet article fournit une introduction étape par étape pour créer et exécuter une application de console Hello World .NET Core dans Visual Studio 2019. Une application Hello World est traditionnellement utilisée pour initier les débutants à un nouveau langage de programmation. Ce programme affiche simplement l’expression "Bonjour monde!" à l’écran.

## <a name="prerequisites"></a>Conditions préalables requises

- [Visual Studio 2019 version 16.4 ou une version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail de développement **multiplateforme .NET Core** installé. .NET Core 3.1 SDK est automatiquement installé lorsque vous sélectionnez cette charge de travail.

Pour plus d’informations, voir la section [Installer avec Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) sur [l’installation de l’article .NET Core SDK.](../install/sdk.md?pivots=os-windows)

## <a name="create-the-app"></a>Créer l’application

Les instructions suivantes créent une simple application de console Hello World :

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Ouvrez Visual Studio 2019.

1. Créez un nouveau projet d’application de console c.NET Core nommé "HelloWorld".

   1. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

      ![Créez un nouveau bouton de projet sélectionné sur la fenêtre de démarrage visual Studio](./media/with-visual-studio/start-window.png)

   1. Sur la **page Créer un nouveau projet,** entrez la **console** dans la boîte de recherche. Ensuite, choisissez **C dans** la liste linguistique, puis choisissez toutes **les plates-formes** de la liste de la plate-forme. Choisissez le modèle **Console App (.NET Core),** puis choisissez **Next**.

      ![Créer une nouvelle fenêtre de projet avec des filtres sélectionnés](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Si vous ne voyez pas les modèles .NET Core, vous manquez probablement la charge de travail requise installée. Sous le **message Ne pas trouver ce que vous recherchez?** message, choisissez l’installation plus **d’outils et de fonctionnalités** lien. L’installateur Visual Studio ouvre ses portes. Assurez-vous d’avoir installé la charge de travail **de développement multiplateforme .NET Core.**

   1. Sur la configuration de votre nouvelle page **de projet,** entrez **HelloWorld** dans la boîte **de nom du projet.** Ensuite, choisissez **Créer**.

      ![Configurez votre nouvelle fenêtre de projet avec le nom, l’emplacement et les champs de noms de solution du projet](./media/with-visual-studio/configure-new-project.png)

   Le modèle d’application console C# pour .NET Core définit automatiquement une classe, `Program`, avec une méthode unique, `Main`, qui accepte un tableau de <xref:System.String> comme argument. `Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[Base visuelle](#tab/vb)

1. Ouvrez Visual Studio 2019.

1. Créez un nouveau projet d’application de console Visual Basic .NET Core nommé "HelloWorld".

   1. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

      ![Créez un nouveau bouton de projet sélectionné sur la fenêtre de démarrage visual Studio](./media/with-visual-studio/start-window.png)

   1. Sur la **page Créer un nouveau projet,** entrez la **console** dans la boîte de recherche. Ensuite, choisissez **Visual Basic** dans la liste de langue, puis choisissez toutes **les plates-formes** de la liste de la plate-forme. Choisissez le modèle **Console App (.NET Core),** puis choisissez **Next**.

      ![Choisir le modèle Visual Basic pour l’application console (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > Si vous ne voyez pas les modèles .NET Core, vous manquez probablement la charge de travail requise installée. Sous le **message Ne pas trouver ce que vous recherchez?** message, choisissez l’installation plus **d’outils et de fonctionnalités** lien. L’installateur Visual Studio ouvre ses portes. Assurez-vous d’avoir installé la charge de travail **de développement multiplateforme .NET Core.**

   1. Sur la configuration de votre nouvelle page **de projet,** entrez **HelloWorld** dans la boîte **de nom du projet.** Ensuite, choisissez **Créer**.

   Le modèle d’application console pour .NET `Program`Core définit automatiquement `Main`une classe, , avec une seule méthode, , qui prend un <xref:System.String> tableau comme un argument. `Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Tous les arguments de ligne de commande fournis `args` lors du lancement de l’application sont disponibles dans le paramètre.

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   Le modèle crée une application « Hello World » simple. Il appelle la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World ! » dans la fenêtre de console.

## <a name="run-the-app"></a>Exécuter l’application

1. Pour exécuter le programme, choisissez **HelloWorld** sur la barre d’outils, ou appuyez sur **F5**.

   ![Barre d’outils Visual Studio avec le bouton HelloWorld run sélectionné](./media/with-visual-studio/run-program.png)

   Une fenêtre console s’ouvre sur le texte "Bonjour monde!" imprimés à l’écran et quelques informations de débbug Visual Studio.

   ![Fenêtre de console affichant « Hello World Press any key to continue »](./media/with-visual-studio/hello-world-console.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

## <a name="enhance-the-app"></a>Améliorer l’application

Améliorez votre application pour inviter l’utilisateur à entrer son nom, et pour l’afficher avec la date et l’heure. Les instructions suivantes modifient et exécutent à nouveau l’application :

# <a name="c"></a>[C #](#tab/csharp)

1. Remplacer le contenu `Main` de la méthode, qui `Console.WriteLine`est actuellement juste la ligne qui appelle , avec le code suivant:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Ce code affiche « What is your name? ». dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée. Il stocke cette chaîne dans une variable nommée `name`. Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`. Enfin, elle utilise une [chaîne interpolée](../../csharp/language-reference/tokens/interpolated.md) pour afficher ces valeurs dans la fenêtre de console.

1. Compilez le programme en choisissant **Build** > **Build Solution**.

1. Pour exécuter le programme, choisissez **HelloWorld** sur la barre d’outils, ou appuyez sur **F5**.

1. Répondez à l’invite en entrant un nom et en appuyant sur la clé **Enter.**

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

# <a name="visual-basic"></a>[Base visuelle](#tab/vb)

1. Remplacer le contenu `Main` de la méthode, qui `Console.WriteLine`est actuellement juste la ligne qui appelle , avec le code suivant:

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Ce code affiche « What is your name? ». dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée. Il stocke cette chaîne dans une variable nommée `name`. Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`. Enfin, elle utilise une [chaîne interpolée](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) pour afficher ces valeurs dans la fenêtre de console.

1. Compilez le programme en choisissant **Build** > **Build Solution**.

1. Pour exécuter le programme, choisissez **HelloWorld** sur la barre d’outils, ou appuyez sur **F5**.

1. Répondez à l’invite en entrant un nom et en appuyant sur la clé **Enter.**

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/hello-world-update.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

---

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez créé et exécuté votre première application .NET Core. Dans l’étape suivante, vous déboiffez votre application.

> [!div class="nextstepaction"]
> [Debug a .NET Core Hello World application dans Visual Studio](debugging-with-visual-studio.md)
