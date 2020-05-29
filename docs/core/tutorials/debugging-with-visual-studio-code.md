---
title: Déboguer une application console .NET Core avec Visual Studio Code
description: Découvrez comment déboguer une application console .NET Core avec Visual Studio Code.
ms.date: 05/26/2020
ms.openlocfilehash: eaeb97f54442006d2f0e29483a68dc3de89b5778
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202588"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a>Didacticiel : déboguer une application console .NET Core à l’aide de Visual Studio Code

Ce didacticiel présente les outils de débogage disponibles dans Visual Studio Code pour l’utilisation des applications .NET Core.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio code](with-visual-studio-code.md).

## <a name="use-debug-build-configuration"></a>Utiliser la configuration de build Debug

*Debug* et *Release* sont deux des configurations de build de .net core. Vous utilisez la configuration de build Debug pour le débogage et la configuration Release pour la distribution de la version finale.

Dans la configuration Debug, un programme est compilé avec des informations de débogage symboliques complètes et aucune optimisation. L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe. La configuration Release d’un programme n’a pas d’informations de débogage symboliques et est entièrement optimisée.

 Par défaut, Visual Studio Code utilise la configuration de build Debug. vous n’avez donc pas besoin de le modifier avant le débogage.

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt

Un point d’arrêt interrompt temporairement l’exécution de l’application *avant* l’exécution de la ligne avec le point d’arrêt.

1. Dans *Program.cs*, définissez un *point d’arrêt* sur la ligne qui affiche le nom, la date et l’heure en cliquant dans la marge de gauche de la fenêtre de code. La marge de gauche se trouve à gauche des numéros de ligne. Vous pouvez également définir un point d’arrêt en plaçant le curseur dans la ligne de code, puis en appuyant sur <kbd>F9</kbd>.

   Comme le montre l’illustration suivante, Visual Studio Code indique la ligne sur laquelle le point d’arrêt est défini en affichant un point rouge dans la marge de gauche.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Point d’arrêt défini":::

## <a name="set-up-for-terminal-input"></a>Configuration des entrées de terminal

Le point d’arrêt se trouve après un `Console.ReadLine` appel de méthode. Le **console de débogage** n’accepte pas les entrées de terminal pour un programme en cours d’exécution. Pour gérer l’entrée de terminal pendant le débogage, vous pouvez utiliser le terminal intégré (l’une des Visual Studio Code Windows) ou un terminal externe. Pour ce didacticiel, vous utilisez le terminal intégré.

1. Ouvrez *. vscode/Launch. JSON*.

1. Remplacez le `console` paramètre par `integratedTerminal` .

   De :

   ```
   "console": "internalConsole",
   ```

   Par :

   ```
   "console": "integratedTerminal",
   ```

1. Enregistrez vos modifications.

## <a name="start-debugging"></a>Démarrer le débogage

1. Ouvrez la vue déboguer en sélectionnant l’icône de débogage dans le menu de gauche.

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Ouvrir l’onglet Débogage dans Visual Studio Code":::

1. Démarrez le débogage en sélectionnant la flèche verte en haut du volet, en regard de **lancement de .net Core (console)**.  Une autre façon de démarrer le débogage consiste à appuyer sur <kbd>F5</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Démarrer le débogage":::

1. Sélectionnez l’onglet **Terminal** pour afficher le « quel est votre nom ? » Invitez le programme à s’afficher avant d’attendre une réponse.

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Sélectionner l’onglet terminal":::

1. Entrez une chaîne dans la fenêtre de **Terminal** en réponse à l’invite de nom, puis appuyez sur <kbd>entrée</kbd>.

   L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. La section variables **locales** de la fenêtre **variables** affiche les valeurs des variables définies dans la méthode en cours d’exécution.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Point d’arrêt atteint, avec des variables locales":::

## <a name="change-variable-values"></a>Modifier les valeurs des variables

La fenêtre **console de débogage** vous permet d’interagir avec l’application que vous déboguez. Vous pouvez modifier la valeur des variables pour voir comment elles affectent votre programme.

1. Sélectionnez l’onglet **console de débogage** .

1. Entrez `name = "Gracie"` à l’invite au bas de la fenêtre de **console de débogage** et appuyez sur la touche <kbd>entrée</kbd> .

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Modifier les valeurs des variables":::

1. Entrez `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` au bas de la fenêtre de **console de débogage** et appuyez sur la touche <kbd>entrée</kbd> .

   La fenêtre **variables** affiche les nouvelles valeurs des `name` variables et `date` .

1. Poursuivez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils. Pour continuer, vous pouvez également appuyer sur <kbd>F5</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Continuer le débogage":::

1. Sélectionnez à nouveau l’onglet **Terminal** .

   Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées au **console de débogage**.

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Terminal présentant les valeurs entrées":::

1. Appuyez sur n’importe quelle touche pour quitter l’application et arrêter le débogage.

## <a name="set-a-conditional-breakpoint"></a>Définir un point d’arrêt conditionnel

Le programme affiche la chaîne que l’utilisateur entre. Que se passe-t-il si l’utilisateur n’entre rien ? Vous pouvez tester cela à l’aide d’une fonctionnalité de débogage utile appelée *point d’arrêt conditionnel*.

1. Cliquez avec le bouton droit (<kbd>CTRL</kbd>+ clic sur MacOS) sur le point rouge représentant le point d’arrêt. Dans le menu contextuel, sélectionnez **modifier le point d’arrêt** pour ouvrir une boîte de dialogue qui vous permet d’entrer une expression conditionnelle.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Menu contextuel Point d'arrêt":::

1. Sélectionnez `Expression` dans la liste déroulante, entrez l’expression conditionnelle suivante, puis appuyez sur <kbd>entrée</kbd>.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Entrer une expression conditionnelle":::

   Chaque fois que le point d’arrêt est atteint, le débogueur appelle la `String.IsNullOrEmpty(name)` méthode et s’arrête sur cette ligne uniquement si l’appel de la méthode retourne `true` .

   Au lieu d’une expression conditionnelle, vous pouvez spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre spécifié de fois, ou une condition de *filtre*qui interrompt l’exécution du programme en fonction d’attributs tels que l’identificateur de thread, le nom de processus ou le nom de thread.

1. Démarrez le programme avec le débogage en appuyant sur <kbd>F5</kbd>.

1. Dans l’onglet **Terminal** , appuyez sur la touche <kbd>entrée</kbd> lorsque vous êtes invité à entrer votre nom.

   Étant donné que la condition que vous avez spécifiée ( `name` est `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant que la `Console.WriteLine` méthode s’exécute.

   La fenêtre **variables** indique que la valeur de la `name` variable est `""` , ou <xref:System.String.Empty?displayProperty=nameWithType> .

1. Confirmez que la valeur est une chaîne vide en entrant l’instruction suivante à l’invite **console de débogage** et en appuyant sur <kbd>entrée</kbd>. Le résultat est `true`.

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Console de débogage retournant la valeur true après l’exécution de l’instruction":::

1. Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.

1. Sélectionnez l’onglet **Terminal** , puis appuyez sur n’importe quelle touche pour quitter le programme et arrêter le débogage.

1. Effacez le point d’arrêt en cliquant sur le point dans la marge de gauche de la fenêtre de code. Pour supprimer un point d’arrêt, vous pouvez également appuyer sur <kbd>F9</kbd> pendant que la ligne de code est sélectionnée.

1. Si vous recevez un avertissement indiquant que la condition de point d’arrêt sera perdue, sélectionnez **supprimer le point d’arrêt**.

## <a name="step-through-a-program"></a>Parcourir un programme

Visual Studio Code vous permet également d’effectuer un pas à pas détaillé ligne par ligne à l’aide d’un programme et de surveiller son exécution. En règle générale, vous définissez un point d’arrêt et suivez le déroulement du programme dans une petite partie de votre code de programme. Étant donné que ce programme est petit, vous pouvez effectuer un pas à pas détaillé dans l’ensemble du programme.

1. Définissez un point d’arrêt sur l’accolade ouvrante de la `Main` méthode.

1. Appuyez sur <kbd>F5</kbd> pour démarrer le débogage.

   Visual Studio Code met en surbrillance la ligne de point d’arrêt.

   À ce stade, la fenêtre **variables** indique que le `args` tableau est vide, et `name` possède les `date` valeurs par défaut.

1. Sélectionnez **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Bouton pas à pas détaillé":::

   Visual Studio Code met en surbrillance la ligne suivante.

1. Sélectionnez **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.

   Visual Studio Code exécute le `Console.WriteLine` pour l’invite de nom et met en surbrillance la ligne suivante d’exécution. La ligne suivante est le `Console.ReadLine` pour le `name` . La fenêtre **variables** est inchangée et l’onglet **Terminal** affiche « quel est votre nom ? ». prompt.

1. Sélectionnez **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.

   Visual Studio met en surbrillance l' `name` attribution de variable. La fenêtre **variables** affiche `name` toujours `null` .

1. Répondez à l’invite en entrant une chaîne dans l’onglet terminal et en appuyant sur <kbd>entrée</kbd>.

   L’onglet **Terminal** peut ne pas afficher la chaîne que vous entrez lors de son entrée, mais la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode capture votre entrée.

1. Sélectionnez **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.

   Visual Studio Code met en surbrillance l' `date` attribution de variable. La fenêtre **variables** affiche la valeur retournée par l’appel à la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode. L’onglet **Terminal** affiche la chaîne que vous avez entrée à l’invite.

1. Sélectionnez **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.

   La fenêtre **variables** affiche la valeur de la `date` variable après l’assignation de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété.

1. Sélectionnez **pas à pas** détaillé ou appuyez sur <kbd>F11</kbd>.

   Visual Studio Code appelle la <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> méthode. La fenêtre de console affiche la chaîne mise en forme.

1. Sélectionnez **pas à pas sortant** ou appuyez sur <kbd>MAJ</kbd> + <kbd>F11</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Bouton de pas à pas sortant":::

1. Sélectionnez l’onglet **Terminal** .

   Le terminal affiche « appuyez sur une touche pour quitter... »

1. Appuyez sur n’importe quelle touche pour quitter le programme.

## <a name="select-release-build-configuration"></a>Sélectionner la configuration de la build Release

Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release. La version Release intègre des optimisations du compilateur qui peuvent affecter le comportement d’une application. Par exemple, les optimisations du compilateur conçues pour améliorer les performances peuvent créer des conditions de concurrence dans les applications multithread.

Pour générer et tester la version Release de votre application console, ouvrez le **Terminal** et exécutez la commande suivante :

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a>Ressources supplémentaires

* [Débogage dans Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez utilisé Visual Studio Code outils de débogage. Pour savoir comment publier une version déployable de l’application, consultez [publication de votre application](cli-create-console-app.md#publish-your-app).

<!--In the next tutorial, you publish a deployable version of the app.

> [!div class="nextstepaction"]
> [Publish a .NET Core console application with Visual Studio Code](publishing-with-visual-studio-code.md)
-->
