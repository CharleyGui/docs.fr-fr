---
title: Déboguer votre application Hello World .NET Core avec Visual Studio
description: Découvrez comment déboguer une application Hello World écrite C# dans ou Visual Basic avec Visual Studio.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156671"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Déboguer votre application ou Visual Basic .NET Core Hello World à l’aide de C# Visual Studio

Jusqu’à présent, vous avez suivi les étapes de la section [créer votre première application de console .net core dans Visual Studio 2019](with-visual-studio.md) pour créer et exécuter une application console simple. Une fois que vous avez écrit et compilé votre application, vous pouvez commencer à la tester. Visual Studio comprend un ensemble complet d’outils de débogage que vous pouvez utiliser pour dépanner votre application.

## <a name="debug-build-configuration"></a>Configuration de build Debug

*Débogage* et *Mise en production* sont deux des configurations de build par défaut de Visual Studio. La configuration de build actuelle s’affiche sur la barre d’outils. L’image de barre d’outils suivante montre que Visual Studio est configuré pour compiler la version de débogage de l’application :

![Barre d’outils Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Commencez par exécuter la version Debug de votre application. La configuration de la build Debug désactive la plupart des optimisations du compilateur et fournit des informations plus détaillées pendant le processus de génération.

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt

Exécutez votre programme et essayez quelques fonctionnalités de débogage :

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

1. Définissez un *point d’arrêt* sur la ligne qui lit `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` en cliquant dans la marge de gauche de la fenêtre de code sur cette ligne. Vous pouvez également définir un point d’arrêt en plaçant le signe insertion dans la ligne de code, puis en appuyant sur **F9** ou en choisissant **déboguer** > **basculer le point d’arrêt** à partir de la barre de menus.

   Un point d’arrêt interrompt temporairement l’exécution de l’application *avant* l’exécution de la ligne avec le point d’arrêt.

   Comme l’illustre l’image suivante, Visual Studio indique la ligne sur laquelle le point d’arrêt est défini en le mettant en surbrillance et en affichant un cercle rouge dans sa marge de gauche.

   ![Fenêtre Programme de Visual Studio avec un point d’arrêt défini](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Exécutez le programme en mode débogage en sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils, en appuyant sur **F5**ou en choisissant **Déboguer** > **Démarrer le débogage**.

1. Entrez une chaîne dans la fenêtre de console lorsque le programme vous invite à entrer un nom, puis appuyez sur **entrée**.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.

   ![Capture d’écran d’un point d’arrêt dans Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. La fenêtre **exécution** vous permet d’interagir avec l’application que vous déboguez. Vous pouvez modifier de manière interactive la valeur des variables pour voir comment elles affectent votre programme.

   1. Si la fenêtre **exécution** n’est pas visible, affichez-la en choisissant **déboguer** > **Windows** > **immédiat**.

   1. Entrez `name = "Gracie"` dans la fenêtre **exécution** et appuyez sur la touche **entrée** .

   1. Entrez `date = DateTime.Parse("11/16/2019 5:25 PM")` dans la fenêtre **exécution** et appuyez sur la touche **entrée** .

   La fenêtre **exécution** affiche la valeur de la variable de chaîne et les propriétés de la valeur de <xref:System.DateTime>. En outre, les valeurs des variables sont mises à jour dans la fenêtre variables **locales** .

   ![Variables locales et fenêtres immédiates dans Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Poursuivez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils ou en sélectionnant **déboguer** > **Continuer**. Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées dans la fenêtre **exécution** .

   ![Fenêtre de console présentant les valeurs entrées](./media/debugging-with-visual-studio/console-window.png)

1. Appuyez sur n’importe quelle touche pour quitter l’application et arrêter le débogage.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Définissez un *point d’arrêt* sur la ligne qui lit `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` en cliquant dans la marge de gauche de la fenêtre de code sur cette ligne. Vous pouvez également définir un point d’arrêt en plaçant le signe insertion sur la ligne souhaitée, puis en choisissant **Déboguer** > **basculer le point d’arrêt** à partir de la barre de menus.

   Un point d’arrêt interrompt temporairement l’exécution de l’application *avant* l’exécution de la ligne avec le point d’arrêt.

   Comme le montre l’illustration suivante, Visual Studio affiche la ligne sur laquelle le point d’arrêt est défini en la mettant en surbrillance et en affichant un cercle rouge dans la marge de gauche.

   ![Fenêtre Programme de Visual Studio avec un point d’arrêt défini](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Exécutez le programme en mode débogage en sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils, en appuyant sur **F5**ou en choisissant **Déboguer** > **Démarrer le débogage**.

1. Entrez une chaîne dans la fenêtre de console lorsque le programme vous invite à entrer un nom et appuyez sur **entrée**.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.

1. La fenêtre **exécution** vous permet d’interagir avec l’application que vous déboguez. Vous pouvez modifier de manière interactive la valeur des variables pour voir comment elles affectent votre programme.

   1. Si la fenêtre **exécution** n’est pas visible, affichez-la en choisissant **déboguer** > **Windows** > **immédiat**.

   1. Entrez `name = "Gracie"` dans la fenêtre **exécution** et appuyez sur la touche **entrée** .

   1. Entrez `date = DateTime.Parse("11/16/2019 5:25 PM")` dans la fenêtre **exécution** et appuyez sur la touche **entrée** .

   Les valeurs des variables sont mises à jour dans la fenêtre **variables locales** .

1. Continuez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils ou en sélectionnant l’élément de menu **Débogage** > **Continuer**. Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées dans la fenêtre **exécution** .

   ![Fenêtre de console présentant les valeurs entrées](./media/debugging-with-visual-studio/console-window.png)

1. Appuyez sur n’importe quelle touche pour quitter l’application et arrêter le débogage.

---

## <a name="set-a-conditional-breakpoint"></a>Définir un point d’arrêt conditionnel

Votre programme affiche la chaîne entrée par l’utilisateur. Que se passe-t-il si l’utilisateur n’entre rien ? Vous pouvez tester cela à l’aide d’une fonctionnalité de débogage utile appelée *point d’arrêt conditionnel*, qui interrompt l’exécution du programme quand une ou plusieurs conditions sont remplies.

Pour définir un point d’arrêt conditionnel et voir ce qu’il se passe lorsque l’utilisateur n’entre pas de chaîne, procédez comme suit :

# <a name="c"></a>[C#](#tab/csharp)

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt. Dans le menu contextuel, sélectionnez **Conditions** pour ouvrir la boîte de dialogue **Paramètres de point d’arrêt**. Cochez la case pour les **conditions** si elle n’est pas déjà sélectionnée.

   ![Éditeur montrant le panneau des paramètres de point d’arrêt - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Pour l' **expression conditionnelle**, remplacez « p. ex. x = = 5 » par ce qui suit :

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Vous testez une condition de code, que l’appel de la méthode `String.IsNullOrEmpty(name)` est `true` soit parce que `name` n’a pas reçu de valeur, soit parce que sa valeur est une chaîne vide (""). Au lieu d’une expression conditionnelle, vous pouvez également spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre spécifié de fois, ou une condition de *filtre*, qui interrompt l’exécution du programme en fonction d’attributs tels que l’identificateur de thread, le nom de processus ou le nom de thread.

1. Sélectionnez **Fermer** pour fermer la boîte de dialogue.

1. Démarrez le programme avec le débogage en appuyant sur **F5**.

1. Dans la fenêtre de la console, appuyez sur la touche **entrée** lorsque vous êtes invité à entrer votre nom.

1. Étant donné que la condition que vous avez spécifiée, `name` est `null` ou <xref:System.String.Empty?displayProperty=nameWithType>, a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant que la méthode `Console.WriteLine` s’exécute.

1. Sélectionnez la fenêtre variables **locales** , qui affiche les valeurs des variables locales pour la méthode en cours d’exécution. Dans ce cas, `Main` est la méthode en cours d’exécution. Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirmez que la valeur est une chaîne vide en entrant l’instruction suivante dans la fenêtre **exécution** et en appuyant sur **entrée**. Le résultat est `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Fenêtre Exécution retournant une valeur true après exécution de l’instruction - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.

1. Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.

1. Effacez le point d’arrêt en cliquant sur le point dans la marge de gauche de la fenêtre de code ou en choisissant **Déboguer > basculer le point d’arrêt** pendant que la ligne de code est sélectionnée.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt. Dans le menu contextuel, sélectionnez **Conditions** pour ouvrir la boîte de dialogue **Paramètres de point d’arrêt**. Cochez la case **Conditions**.

   ![Éditeur montrant le panneau des paramètres de point d’arrêt - Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Pour **l’expression conditionnelle**, remplacez « e.g. x = 5 » par ceci :

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Vous testez une condition de code, que l’appel de la méthode `String.IsNullOrEmpty(name)` est `true` soit parce que `name` n’a pas reçu de valeur, soit parce que sa valeur est une chaîne vide (""). Au lieu d’une expression conditionnelle, vous pouvez également spécifier un *nombre d’accès*, qui interrompt l’exécution du programme avant qu’une instruction soit exécutée un nombre spécifié de fois, ou une condition de *filtre*, qui interrompt l’exécution du programme en fonction d’attributs tels que l’identificateur de thread, le nom de processus ou le nom de thread.

1. Sélectionnez **Fermer** pour fermer la boîte de dialogue.

1. Démarrez le programme avec le débogage en appuyant sur **F5**.

1. Dans la fenêtre de la console, appuyez sur la touche **entrée** lorsque vous êtes invité à entrer votre nom.

1. Étant donné que la condition que vous avez spécifiée, `name` est `null` ou <xref:System.String.Empty?displayProperty=nameWithType>, a été satisfaite, l’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant que la méthode `Console.WriteLine` s’exécute.

1. Sélectionnez la fenêtre variables **locales** , qui affiche les valeurs des variables locales pour la méthode en cours d’exécution. Dans ce cas, `Main` est la méthode en cours d’exécution. Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirmez que la valeur est une chaîne vide en entrant l’instruction suivante dans la fenêtre **exécution** et en appuyant sur **entrée**. Le résultat est `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Fenêtre Exécution retournant une valeur true après exécution de l’instruction - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.

1. Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.

1. Supprimez le point d’arrêt en cliquant sur le point dans la marge gauche de la fenêtre de code, ou en choisissant l’élément de menu **Débogage > Basculer le point d’arrêt** avec la ligne sélectionnée.

---
## <a name="step-through-a-program"></a>Parcourir un programme

Visual Studio vous permet également de parcourir un programme ligne par ligne et de surveiller son exécution. En règle générale, on définit un point d’arrêt et on utilise cette fonctionnalité pour suivre le déroulement du programme sur une petite portion de son code. Étant donné que votre programme est petit, vous pouvez effectuer un pas à pas détaillé dans l’ensemble du programme :

# <a name="c"></a>[C#](#tab/csharp)

1. Dans la barre de menus, choisissez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.

   ![Méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-method.png)

   À ce stade, la fenêtre **variables locales** montre que votre programme n’a défini qu’une seule variable, `args`. Comme vous n’avez passé aucun argument de ligne de commande au programme, sa valeur est un tableau de chaînes vides. En outre, Visual Studio a ouvert une fenêtre de console vide.

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio place maintenant en surbrillance la ligne suivante à exécuter. Comme l’indique l’image, elle a pris moins d’une milliseconde pour exécuter le code entre la dernière instruction et celle-ci. `args` reste la seule variable déclarée et la fenêtre de console reste vide.

   ![Source de la méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **variables locales** indique que `name` est `null`et que la fenêtre de console affiche la chaîne « What is your name ? ».

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur **entrée**. La console ne répond pas et la chaîne que vous avez entrée n’est pas affichée dans la fenêtre de la console, mais la méthode <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> capture néanmoins votre entrée.

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `date`. La fenêtre **variables locales** affiche la valeur retournée par l’appel à la méthode <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. La fenêtre de console affiche également la chaîne que vous avez entrée à l’invite.

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. La fenêtre **variables locales** affiche la valeur de la variable `date` après l’assignation de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>. La fenêtre de console est inchangée.

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. La fenêtre de console affiche la chaîne mise en forme.

1. Sélectionnez **Déboguer** > **pas à pas sortant** ou appuyez sur **MAJ**+**F11**. Cela arrête l’exécution pas à pas. La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Dans la barre de menus, choisissez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.

   ![Méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   À ce stade, la fenêtre **variables locales** montre que votre programme n’a défini qu’une seule variable, `args`. Comme vous n’avez passé aucun argument de ligne de commande au programme, sa valeur est un tableau de chaînes vides. En outre, Visual Studio a ouvert une fenêtre de console vide.

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio place maintenant en surbrillance la ligne suivante à exécuter. Comme le montre l’illustration, il lui a fallu moins d’une milliseconde pour exécuter le code entre la dernière instruction et celle-ci. `args` reste la seule variable déclarée et la fenêtre de console reste vide.

   ![Source de la méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **variables locales** indique que `name` est `Nothing`et que la fenêtre de console affiche la chaîne « What is your name ? ».

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur **entrée**. La console ne répond pas et la chaîne que vous entrez ne s’affiche pas dans la fenêtre de console, mais la méthode <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> capture néanmoins votre entrée.

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `currentDate`. La fenêtre **variables locales** affiche la valeur retournée par l’appel à la méthode <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. La fenêtre de console affiche également la chaîne entrée lorsque vous y avez été invité par la console.

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. La fenêtre de console est inchangée.

1. Sélectionnez **Déboguer** > **pas à pas** détaillé ou appuyez sur **F11**. Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. La fenêtre de console affiche la chaîne mise en forme.

1. Sélectionnez **Déboguer** > **pas à pas sortant** ou appuyez sur **MAJ**+**F11**. Cela arrête l’exécution pas à pas. La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur n’importe quelle touche pour fermer la fenêtre de console et arrêter le débogage.

---

## <a name="build-a-release-version"></a>Créer une version Release

Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release. La version Release intègre des optimisations du compilateur qui peuvent parfois affecter négativement le comportement d’une application. Par exemple, les optimisations du compilateur conçues pour améliorer les performances peuvent créer des conditions de concurrence dans les applications multithread.

Pour générer et tester la version Release de votre application console, changez la configuration de build dans la barre d’outils de **Debug** en **Release**.

![Barre d’outils par défaut Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Quand vous appuyez sur **F5** ou que vous choisissez **générer la solution** dans le menu **générer** , Visual Studio compile la version Release de l’application. Vous pouvez le tester comme vous l’avez fait pour la version de débogage.

## <a name="next-steps"></a>Étapes suivantes :

Une fois que vous avez débogué votre application, l’étape suivante consiste à publier une version déployable de l’application. Pour plus d’informations sur la façon de procéder, consultez [publier votre application .net Core Hello World avec Visual Studio](publishing-with-visual-studio.md).
