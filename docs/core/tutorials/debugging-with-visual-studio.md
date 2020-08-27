---
title: Déboguer une application console .NET Core à l’aide de Visual Studio
description: Découvrez comment déboguer une application console .NET Core à l’aide de Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4e408d5bd0976d88f368615860ac373142d0fe1e
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957223"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a>Didacticiel : déboguer une application console .NET Core à l’aide de Visual Studio

Ce didacticiel présente les outils de débogage disponibles dans Visual Studio.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core à l’aide de Visual Studio](with-visual-studio.md).

## <a name="use-debug-build-configuration"></a>Utiliser la configuration de build Debug

*Debug* et *Release* sont des configurations de build intégrées à Visual Studio. Vous utilisez la configuration de build Debug pour le débogage et la configuration Release pour la distribution de la version finale.

Dans la configuration Debug, un programme est compilé avec des informations de débogage symboliques complètes et aucune optimisation. L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe. La configuration Release d’un programme n’a pas d’informations de débogage symboliques et est entièrement optimisée.

 Par défaut, Visual Studio utilise la configuration de build Debug. vous n’avez donc pas besoin de le modifier avant le débogage.

1. Démarrez Visual Studio.

1. Ouvrez le projet que vous avez créé dans [créer une application console .net core à l’aide de Visual Studio](with-visual-studio.md).

   La configuration de build actuelle s’affiche sur la barre d’outils. L’image de barre d’outils suivante montre que Visual Studio est configuré pour compiler la version de débogage de l’application :

   ![Barre d’outils Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt

Un *point d’arrêt* interrompt temporairement l’exécution de l’application avant l’exécution de la ligne avec le point d’arrêt.

1. Définissez un *point d’arrêt* sur la ligne qui affiche le nom, la date et l’heure en cliquant dans la marge de gauche de la fenêtre de code sur cette ligne. La marge de gauche se trouve à gauche des numéros de ligne.  D’autres façons de définir un point d’arrêt consiste à placer le curseur dans la ligne de code, puis à appuyer sur <kbd>F9</kbd> ou à choisir **Déboguer**le  >  **point d’arrêt** dans la barre de menus.

   Comme le montre l’illustration suivante, Visual Studio indique la ligne sur laquelle le point d’arrêt est défini en le mettant en surbrillance et en affichant un point rouge dans la marge de gauche.

   ![Fenêtre Programme de Visual Studio avec un point d’arrêt défini](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Appuyez sur <kbd>F5</kbd> pour exécuter le programme en mode débogage. Une autre façon de démarrer le débogage consiste à choisir **Déboguer**  >  **Démarrer le débogage** dans le menu.

1. Entrez une chaîne dans la fenêtre de console lorsque le programme vous invite à entrer un nom, puis appuyez sur <kbd>entrée</kbd>.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.

   ![Capture d’écran d’un point d’arrêt dans Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a>Utiliser la fenêtre exécution

La fenêtre **exécution** vous permet d’interagir avec l’application que vous déboguez. Vous pouvez modifier de manière interactive la valeur des variables pour voir comment elles affectent votre programme.

1. Si la fenêtre **exécution** n’est pas visible, affichez-la en sélectionnant **Déboguer**les  >  **fenêtres**  >  **immédiates**.

1. Entrez `name = "Gracie"` dans la fenêtre **exécution** et appuyez sur la touche <kbd>entrée</kbd> .

1. Entrez `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` dans la fenêtre **exécution** et appuyez sur la touche <kbd>entrée</kbd> .

   La fenêtre **exécution** affiche la valeur de la variable de chaîne et les propriétés de la <xref:System.DateTime> valeur. En outre, les valeurs des variables sont mises à jour dans la fenêtre variables **locales** .

   ![Variables locales et fenêtres immédiates dans Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Appuyez sur <kbd>F5</kbd> pour continuer l’exécution du programme. Pour continuer, vous pouvez également choisir **Déboguer**  >  **Continuer** dans le menu.

   Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées dans la fenêtre **exécution** .

   ![Fenêtre de console présentant les valeurs entrées](./media/debugging-with-visual-studio/console-window.png)

1. Appuyez sur n’importe quelle touche pour quitter l’application et arrêter le débogage.

## <a name="set-a-conditional-breakpoint"></a>Définir un point d’arrêt conditionnel

Le programme affiche la chaîne que l’utilisateur entre. Que se passe-t-il si l’utilisateur n’entre rien ? Vous pouvez tester cela à l’aide d’une fonctionnalité de débogage utile appelée *point d’arrêt conditionnel*.

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt. Dans le menu contextuel, sélectionnez **conditions** pour ouvrir la boîte de dialogue **paramètres de point d’arrêt** . Activez la case à cocher des **conditions** si elle n’est pas déjà sélectionnée.

   ![Éditeur montrant le panneau des paramètres de point d’arrêt - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Pour l' **expression conditionnelle**, entrez le code suivant dans le champ qui montre un exemple de code qui teste si a la touche `x` 5. Si la langue que vous souhaitez utiliser n’est pas affichée, modifiez le sélecteur de langue en haut de la page.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Chaque fois que le point d’arrêt est atteint, le débogueur appelle la `String.IsNullOrEmpty(name)` méthode et s’arrête sur cette ligne uniquement si l’appel de la méthode retourne `true` .

   Au lieu d’une expression conditionnelle, vous pouvez spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre de fois spécifié. Une autre option consiste à spécifier une *condition de filtre*, qui interrompt l’exécution du programme en fonction d’attributs tels qu’un identificateur de thread, un nom de processus ou un nom de thread.

1. Sélectionnez **Fermer** pour fermer la boîte de dialogue.

1. Démarrez le programme avec le débogage en appuyant sur <kbd>F5</kbd>.

1. Dans la fenêtre de la console, appuyez sur la touche <kbd>entrée</kbd> lorsque vous êtes invité à entrer votre nom.

1. Étant donné que la condition que vous avez spécifiée ( `name` a la valeur `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant que la `Console.WriteLine` méthode s’exécute.

1. Sélectionnez la fenêtre variables **locales** , qui affiche les valeurs des variables locales pour la méthode en cours d’exécution. Dans ce cas, `Main` est la méthode en cours d’exécution. Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirmez que la valeur est une chaîne vide en entrant l’instruction suivante dans la fenêtre **exécution** et en appuyant sur <kbd>entrée</kbd>. Le résultat est `true`.

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   Le point d’interrogation dirige la fenêtre exécution pour [évaluer une expression](/visualstudio/ide/reference/immediate-window#enter-commands).

   ![Fenêtre Exécution retournant une valeur true après exécution de l’instruction - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Appuyez sur <kbd>F5</kbd> pour continuer l’exécution du programme.

1. Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.

1. Effacez le point d’arrêt en cliquant sur le point dans la marge de gauche de la fenêtre de code. Pour supprimer un point d’arrêt, vous pouvez notamment appuyer sur <kbd>F9</kbd> ou choisir **déboguer > basculer le point d’arrêt** pendant que la ligne de code est sélectionnée.

## <a name="step-through-a-program"></a>Parcourir un programme

Visual Studio vous permet également de parcourir un programme ligne par ligne et de surveiller son exécution. En règle générale, vous définissez un point d’arrêt et suivez le déroulement du programme dans une petite partie de votre code de programme. Étant donné que ce programme est petit, vous pouvez effectuer un pas à pas détaillé dans l’ensemble du programme.

1. Choisissez **Déboguer**  >  **pas à pas**détaillé. Vous pouvez également déboguer une instruction à la fois en appuyant sur <kbd>F11</kbd>.

   Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.

   C#

   ![Méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-method.png)

   Visual Basic

   ![Méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   À ce stade, la fenêtre **variables locales** indique que le `args` tableau est vide et `name` possède les `date` valeurs par défaut. En outre, Visual Studio a ouvert une fenêtre de console vide.

1. Appuyez sur <kbd>F11</kbd>. Visual Studio place maintenant en surbrillance la ligne suivante à exécuter. La fenêtre **variables locales** est inchangée et la fenêtre de console reste vide.

   C#

   ![Source de la méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

   Visual Basic

   ![Source de la méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Appuyez sur <kbd>F11</kbd>. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **variables locales** affiche la `name` `null` valeur et la fenêtre de console affiche la chaîne « quel est votre nom ? ».

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur <kbd>entrée</kbd>. La console ne répond pas et la chaîne que vous avez entrée n’est pas affichée dans la fenêtre de console, mais la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode capture néanmoins votre entrée.

1. Appuyez sur <kbd>F11</kbd>. Visual Studio met en surbrillance l’instruction qui comprend l' `date` affectation de la variable ( `currentDate` dans Visual Basic). La fenêtre **variables locales** affiche la valeur retournée par l’appel à la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode. La fenêtre de console affiche également la chaîne que vous avez entrée à l’invite.

1. Appuyez sur <kbd>F11</kbd>. La fenêtre **variables locales** affiche la valeur de la `date` variable après l’affectation de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété. La fenêtre de console est inchangée.

1. Appuyez sur <kbd>F11</kbd>. Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. La fenêtre de console affiche la chaîne mise en forme.

1. Choisissez **Déboguer**  >  **pas à pas sortant**. Pour arrêter l’exécution pas à pas, vous pouvez également appuyer sur <kbd>MAJ</kbd> + <kbd>F11</kbd>.

   La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.

## <a name="use-release-build-configuration"></a>Utiliser la configuration de build Release

Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release. La version Release intègre des optimisations du compilateur qui peuvent parfois affecter négativement le comportement d’une application. Par exemple, les optimisations du compilateur conçues pour améliorer les performances peuvent créer des conditions de concurrence dans les applications multithread.

Pour générer et tester la version Release de votre application console, changez la configuration de build dans la barre d’outils de **Debug** en **Release**.

![Barre d’outils par défaut Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Quand vous appuyez sur <kbd>F5</kbd> ou que vous choisissez **générer la solution** dans le menu **générer** , Visual Studio compile la version Release de l’application. Vous pouvez le tester comme vous l’avez fait pour la version de débogage.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez utilisé les outils de débogage de Visual Studio. Dans le didacticiel suivant, vous allez publier une version déployable de l’application.

> [!div class="nextstepaction"]
> [Publier une application console .NET Core à l’aide de Visual Studio](publishing-with-visual-studio.md)
