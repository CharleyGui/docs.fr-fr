---
title: Déboguer une application console .NET Core à l’aide de Visual Studio pour Mac
description: Découvrez comment déboguer une application console .NET Core à l’aide de Visual Studio Mac.
ms.date: 06/08/2020
ms.openlocfilehash: 4941605923a9897d481aca4ec31408ab62e873f3
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713818"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a>Didacticiel : déboguer une application console .NET Core à l’aide de Visual Studio pour Mac

Ce didacticiel présente les outils de débogage disponibles dans Visual Studio pour Mac.

## <a name="prerequisites"></a>Prérequis

- Ce didacticiel fonctionne avec l’application console que vous créez dans [créer une application console .net core dans Visual Studio pour Mac](using-on-mac-vs.md).

## <a name="use-debug-build-configuration"></a>Utiliser la configuration de build Debug

*Debug* et *Release* sont des configurations de build intégrées à Visual Studio. Vous utilisez la configuration de build Debug pour le débogage et la configuration Release pour la distribution de la version finale.

Dans la configuration Debug, un programme est compilé avec des informations de débogage symboliques complètes et aucune optimisation. L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe. La configuration Release d’un programme n’a pas d’informations de débogage symboliques et est entièrement optimisée.

Par défaut, Visual Studio utilise la configuration de build Debug. vous n’avez donc pas besoin de le modifier avant le débogage.

1. Démarrez Visual Studio pour Mac.

1. Ouvrez le projet que vous avez créé dans [créer une application console .net core dans Visual Studio pour Mac](using-on-mac-vs.md).

   La configuration de build actuelle s’affiche sur la barre d’outils. L’image de barre d’outils suivante montre que Visual Studio est configuré pour compiler la version de débogage de l’application :

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="Barre d’outils Visual Studio avec débogage mis en surbrillance":::

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt

Un *point d’arrêt* interrompt temporairement l’exécution de l’application avant l’exécution de la ligne avec le point d’arrêt.

1. Définissez un point d’arrêt sur la ligne qui affiche le nom, la date et l’heure. Pour ce faire, placez le curseur dans la ligne de code et appuyez sur <kbd>⌘</kbd> <kbd>\\</kbd> (<kbd>commande</kbd> + <kbd>\\</kbd> ). Une autre façon de définir un point d’arrêt consiste à sélectionner **exécuter**  >  **basculer le point d’arrêt** dans le menu.

   Visual Studio indique la ligne sur laquelle le point d’arrêt est défini en le mettant en surbrillance et en affichant un point rouge dans la marge de gauche.

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="Fenêtre Programme de Visual Studio avec un point d’arrêt défini":::

1. Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour démarrer le programme en mode débogage. Une autre façon de démarrer le débogage consiste à choisir **exécuter**  >  **Démarrer le débogage** dans le menu.

1. Entrez une chaîne dans la fenêtre de terminal lorsque le programme vous invite à entrer un nom, puis appuyez sur <kbd>entrée</kbd>.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt, avant l’exécution de la `Console.WriteLine` méthode.

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Capture d’écran d’un point d’arrêt dans Visual Studio":::

## <a name="use-the-immediate-window"></a>Utiliser la fenêtre exécution

La fenêtre **exécution** vous permet d’interagir avec l’application que vous déboguez. Vous pouvez modifier de manière interactive la valeur des variables pour voir comment elles affectent votre programme.

1. Si la fenêtre **exécution** n’est pas visible, affichez-la en sélectionnant **Afficher**les  >  **blocs de débogage**  >  **immédiats**.

1. Entrez `name = "Gracie"` dans la fenêtre **exécution** et appuyez sur <kbd>entrée</kbd>.

1. Entrez `date = date.AddDays(1)` dans la fenêtre **exécution** et appuyez sur <kbd>entrée</kbd>.

   La fenêtre **exécution** affiche la nouvelle valeur de la variable de chaîne et les propriétés de la <xref:System.DateTime> valeur.

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Fenêtre exécution dans Visual Studio":::

   La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution. Les valeurs des variables que vous venez de modifier sont mises à jour dans la fenêtre **variables locales** .

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Fenêtre variables locales dans Visual Studio":::

1. Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour continuer le débogage.

   Les valeurs affichées dans le terminal correspondent aux modifications que vous avez apportées dans la fenêtre **exécution** .

   Si vous ne voyez pas le terminal, sélectionnez **Terminal-HelloWorld** dans la barre de navigation inférieure.

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="Terminal Hello World dans la barre de navigation inférieure":::

1. Appuyez sur n’importe quelle touche pour quitter le programme.

1. Fermez la fenêtre de terminal.

## <a name="set-a-conditional-breakpoint"></a>Définir un point d’arrêt conditionnel

Le programme affiche une chaîne que l’utilisateur entre. Que se passe-t-il si l’utilisateur n’entre rien ? Vous pouvez tester cela à l’aide d’une fonctionnalité de débogage utile appelée *point d’arrêt conditionnel*.

1. <kbd>CTRL</kbd>+ clic sur le point rouge représentant le point d’arrêt. Dans le menu contextuel, sélectionnez **modifier le point d’arrêt**.

1. Dans la boîte de dialogue **modifier le point d’arrêt** , entrez le code suivant dans le champ qui suit **et la condition suivante est true**, puis sélectionnez **appliquer**.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="Éditeur qui présente le panneau des paramètres de point d’arrêt":::

   Chaque fois que le point d’arrêt est atteint, le débogueur appelle la `String.IsNullOrEmpty(name)` méthode et s’arrête sur cette ligne uniquement si l’appel de la méthode retourne `true` .

   Au lieu d’une expression conditionnelle, vous pouvez spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre de fois spécifié.

1. Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour démarrer le débogage.

1. Dans la fenêtre de terminal, appuyez sur <kbd>entrée</kbd> lorsque vous êtes invité à entrer votre nom.

   Étant donné que la condition que vous avez spécifiée ( `name` a la valeur `null` ou <xref:System.String.Empty?displayProperty=nameWithType> ) a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt.

1. Sélectionnez la fenêtre variables **locales** , qui affiche les valeurs des variables locales pour la méthode en cours d’exécution. Dans ce cas, `Main` est la méthode en cours d’exécution. Notez que la valeur de la `name` variable est `""` , autrement dit, <xref:System.String.Empty?displayProperty=nameWithType> .

1. Vous pouvez également voir que la valeur est une chaîne vide en entrant le `name` nom de la variable dans la fenêtre **exécution** et en appuyant sur <kbd>entrée</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="La fenêtre exécution qui indique le nom est une chaîne vide":::

1. Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour continuer le débogage.

1. Dans la fenêtre de terminal, appuyez sur n’importe quelle touche pour quitter le programme.

1. Fermez la fenêtre de terminal.

1. Effacez le point d’arrêt en cliquant sur le point rouge dans la marge de gauche de la fenêtre de code. Pour supprimer un point d’arrêt, vous pouvez également choisir **exécuter > basculer le point d’arrêt** pendant que la ligne de code est sélectionnée.

## <a name="step-through-a-program"></a>Parcourir un programme

Visual Studio vous permet également de parcourir un programme ligne par ligne et de surveiller son exécution. En règle générale, vous définissez un point d’arrêt et suivez le déroulement du programme dans une petite partie de votre code de programme. Étant donné que ce programme est petit, vous pouvez effectuer un pas à pas détaillé dans l’ensemble du programme.

1. Définissez un point d’arrêt sur l’accolade qui marque le début de la `Main` méthode (appuyez sur <kbd>commande</kbd> + <kbd>\\</kbd> ).

1. Appuyez sur <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>commande</kbd> + <kbd>entrée</kbd>) pour démarrer le débogage.

   Visual Studio s’arrête sur la ligne avec le point d’arrêt.

1. Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>) ou sélectionnez **exécuter**  >  un**pas à pas détaillé** pour avancer d’une ligne.

   Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Méthode pas à pas détaillé de Visual Studio":::

   À ce stade, la fenêtre **variables locales** indique que le `args` tableau est vide et `name` possède les `date` valeurs par défaut. En outre, Visual Studio a ouvert un terminal vide.

1. Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>).

   Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **variables locales** affiche la `name` `null` valeur, et le terminal affiche la chaîne « quel est votre nom ? ».

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur <kbd>entrée</kbd>.

1. Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>).

   Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `date`. La fenêtre **variables locales** affiche la valeur retournée par l’appel à la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode. Le terminal affiche la chaîne que vous avez entrée à l’invite.

1. Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>).

   La fenêtre **variables locales** affiche la valeur de la `date` variable après l’affectation de la <xref:System.DateTime.Now?displayProperty=nameWithType> propriété. Le terminal est inchangé.

1. Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (commande de<kbd>déplacement</kbd> + <kbd>command</kbd> + <kbd>i</kbd>).

   Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. Le terminal affiche la chaîne mise en forme.

1. Appuyez sur <kbd>⇧</kbd><kbd>⌘</kbd><kbd>u</kbd> (<kbd>MAJ</kbd> + <kbd>commande</kbd> + <kbd>u</kbd>) ou sélectionnez **exécuter l’exécution**  >  **pas à pas**.

   Le terminal affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur n’importe quelle touche pour quitter le programme.

## <a name="use-release-build-configuration"></a>Utiliser la configuration de build Release

Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release. La version Release intègre des optimisations du compilateur qui peuvent affecter négativement le comportement d’une application. Par exemple, les optimisations du compilateur conçues pour améliorer les performances peuvent créer des conditions de concurrence dans les applications multithread.

Pour générer et tester la version Release de l’application console, procédez comme suit :

1. Modifiez la configuration de build dans la barre d’outils de **Debug** à **Release**.

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="Barre d’outils par défaut Visual Studio avec débogage mis en surbrillance":::

1. Appuyez sur <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>commande</kbd> + <kbd>entrée</kbd>) pour exécuter sans débogage.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez utilisé les outils de débogage de Visual Studio. Dans le didacticiel suivant, vous allez publier une version déployable de l’application.

> [!div class="nextstepaction"]
> [Publier une application console .NET Core avec Visual Studio pour Mac](publishing-with-visual-studio-mac.md)
