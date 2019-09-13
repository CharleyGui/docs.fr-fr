---
title: Déboguer une application .NET Core Hello World avec Visual Studio 2017
description: Découvrez comment déboguer une application Hello World écrite en C# ou Visual Basic avec Visual Studio 2017.
ms.date: 12/15/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f318c163db6cfdd6de5aa99edebfeeb4bb470a02
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926165"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio-2017"></a>Déboguer une application Hello World .NET Core C# ou Visual Basic avec Visual Studio 2017

Jusqu’à présent, vous avez suivi la procédure [Générer une application C# Hello World avec .NET Core dans Visual Studio 2017](with-visual-studio.md) ou [Générer une application Visual Basic Hello World avec .NET Core dans Visual Studio 2017](vb-with-visual-studio.md) pour créer et exécuter une application console simple. Une fois que vous avez écrit et compilé votre application, vous pouvez commencer à la tester. Visual Studio inclut un ensemble complet d’outils de débogage qui vous permettent de tester et dépanner votre application. 

## <a name="debugging-in-debug-mode"></a>Débogage en mode débogage

*Débogage* et *Mise en production* sont deux des configurations de build par défaut de Visual Studio. La configuration de build actuelle s’affiche sur la barre d’outils. L’image suivante de la barre d’outils montre que Visual Studio est configuré pour compiler votre application en mode **Débogage**.

   ![Barre d’outils par défaut Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Vous devez toujours commencer par tester votre programme en mode Débogage. Le mode Débogage désactive la plupart des optimisations du compilateur et fournit des informations plus détaillées pendant le processus de génération.

## <a name="setting-a-breakpoint"></a>Définition d'un point d'arrêt

Exécutez votre programme en mode Débogage et essayez quelques fonctionnalités de débogage :

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Un *point d’arrêt* interrompt temporairement l’exécution de l’application *avant* la ligne sur laquelle le point d’arrêt est exécuté. 

   Définissez un point d’arrêt sur la ligne `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` en cliquant dans la marge de gauche de la fenêtre de code ou en choisissant l’élément de menu **Débogage** > **Basculer le point d’arrêt** avec la ligne sélectionnée. Comme le montre l’illustration suivante, Visual Studio affiche la ligne sur laquelle le point d’arrêt est défini en la mettant en surbrillance et en affichant un cercle rouge dans la marge de gauche.

   ![Fenêtre Programme de Visual Studio avec un point d’arrêt défini](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Exécutez le programme en mode Debug en sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils, en appuyant sur F5 ou en choisissant **Débogage** > **Démarrer le débogage**.

1. Entrez une chaîne dans la fenêtre de console lorsque le programme vous invite à entrer un nom, puis appuyez sur Entrée.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. La fenêtre **Automatique** affiche les valeurs des variables utilisées autour de la ligne actuelle. La fenêtre **Variables locales** (que vous pouvez afficher en cliquant sur l’onglet **Variables locales**) affiche les valeurs des variables définies dans la méthode en cours d’exécution.

   ![Capture d’écran d’un point d’arrêt dans Visual Studio.](./media/debugging-with-visual-studio/breakpoint-console-window.png)

1. Vous pouvez changer la valeur des variables pour voir comment cela affecte votre programme. Si la **fenêtre Exécution** n’est pas visible, affichez-la en choisissant l’élément de menu **Débogage** > **Fenêtres** > **Exécution**. La **fenêtre Exécution** vous permet d’interagir avec l’application que vous déboguez.

1. Elle permet de modifier interactivement la valeur des variables. Entrez `name = "Gracie"` dans la **fenêtre Exécution** et appuyez sur la touche Entrée.

1. Entrez `date = new DateTime(2016,11,01,11,59,00)` dans la **fenêtre Exécution** et appuyez sur la touche Entrée.

   La **fenêtre Exécution** affiche la valeur de la variable de chaîne et les propriétés de la valeur <xref:System.DateTime>. En outre, la valeur des variables est mise à jour dans les fenêtres **Automatiques** et **Variables locales**.

   ![Fenêtre Automatique et fenêtre Exécution](./media/debugging-with-visual-studio/autos-immediate-window.png)

1. Continuez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils ou en sélectionnant l’élément de menu **Débogage** > **Continuer**. Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées dans la **fenêtre Exécution**.

   ![Fenêtre de console montrant la valeur Jack à l’invite What is your name?, suivie de Hello Gracie](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Appuyez sur n’importe quelle touche pour quitter l’application et terminer le mode Debug.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Un *point d’arrêt* interrompt temporairement l’exécution de l’application *avant* la ligne sur laquelle le point d’arrêt est exécuté. 

   Définissez un point d’arrêt sur la ligne `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` en cliquant dans la marge de gauche de la fenêtre de code ou en choisissant l’élément de menu **Débogage** > **Basculer le point d’arrêt** avec la ligne sélectionnée. Comme le montre l’illustration suivante, Visual Studio affiche la ligne sur laquelle le point d’arrêt est défini en la mettant en surbrillance et en affichant un cercle rouge dans la marge de gauche.

   ![Fenêtre Programme de Visual Studio avec un point d’arrêt défini](./media/debugging-with-visual-studio/vb-set-breakpoint-in-editor.png)

1. Exécutez le programme en mode Debug en sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils, en appuyant sur F5 ou en choisissant **Débogage** > **Démarrer le débogage**.

1. Entrez une chaîne dans la fenêtre de console lorsque le programme vous invite à entrer un nom, puis appuyez sur Entrée.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. La fenêtre **Automatique** affiche les valeurs des variables utilisées autour de la ligne actuelle. La fenêtre **Variables locales** (que vous pouvez afficher en cliquant sur l’onglet **Variables locales**) affiche les valeurs des variables définies dans la méthode en cours d’exécution.

   ![Fenêtre Application de Visual Studio au point d'arrêt](./media/debugging-with-visual-studio/vb-stop-at-breakpoint.png)

1. Vous pouvez changer la valeur des variables pour voir comment cela affecte votre programme. Si la **fenêtre Exécution** n’est pas visible, affichez-la en choisissant l’élément de menu **Débogage** > **Fenêtres** > **Exécution**. La **fenêtre Exécution** vous permet d’interagir avec l’application que vous déboguez.

1. Elle permet de modifier interactivement la valeur des variables. Entrez `name = "Gracie"` dans la **fenêtre Exécution** et appuyez sur la touche Entrée.

1. Entrez `currentDate = new DateTime(2016,11,01,11,59,00)` dans la **fenêtre Exécution** et appuyez sur la touche Entrée.

1. Continuez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils ou en sélectionnant l’élément de menu **Débogage** > **Continuer**. Les valeurs affichées dans la fenêtre de console correspondent aux modifications que vous avez apportées dans la **fenêtre Exécution**.

   ![Fenêtre de console montrant les valeurs modifiées entrées dans la fenêtre Exécution](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Appuyez sur n’importe quelle touche pour quitter l’application et terminer le mode Debug.

---

## <a name="setting-a-conditional-breakpoint"></a>Définition d’un point d'arrêt conditionnel

Votre programme affiche la chaîne entrée par l’utilisateur. Que se passe-t-il si l’utilisateur n’entre rien ? Vous pouvez le tester avec une fonctionnalité de débogage pratique, le *point d’arrêt conditionnel*, qui arrête l’exécution du programme quand une ou plusieurs conditions sont remplies.

Pour définir un point d’arrêt conditionnel et voir ce qu’il se passe lorsque l’utilisateur n’entre pas de chaîne, procédez comme suit :

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt. Dans le menu contextuel, sélectionnez **Conditions** pour ouvrir la boîte de dialogue **Paramètres de point d’arrêt**. Cochez la case **Conditions**.

   ![Éditeur montrant le panneau des paramètres de point d’arrêt - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Pour l’**expression conditionnelle**, remplacez « e.g. x == 5 » par ceci :

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Vous testez une condition de code, à savoir que l’appel de méthode `String.IsNullOrEmpty(name)` est `true` car *name* ne s’est pas vu affecter de valeur ou que sa valeur est une chaîne vide (""). Vous pouvez également spécifier un *nombre d’accès*, qui interrompt l’exécution avant qu’une instruction soit exécutée un nombre spécifié de fois, ou une *condition de filtre*, qui interrompt l’exécution du programme en fonction d’attributs, comme un identificateur de thread, un nom de processus ou un nom de thread.

1. Sélectionnez le bouton **Fermer** pour fermer la boîte de dialogue.

1. Exécutez le programme en mode débogage.

1. Dans la fenêtre de console, appuyez sur la touche Entrée lorsque vous êtes invité à entrer votre nom.

1. Comme la condition que nous avons spécifiée (`name` ayant la valeur `null` ou <xref:System.String.Empty?displayProperty=nameWithType>) a été satisfaite, l’exécution du programme s’arrête quand elle atteint le point d’arrêt et avant que la méthode `Console.WriteLine` s’exécute.

1. Sélectionnez la fenêtre **Variables locales**, qui montre les valeurs des variables locales pour la méthode en cours d’exécution, qui est la méthode `Main` dans votre programme. Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Vérifiez que la valeur est une chaîne vide en entrant l’instruction suivante dans la **fenêtre Exécution**. Le résultat est `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Fenêtre Exécution retournant une valeur true après exécution de l’instruction - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.

1. Appuyez sur une touche pour fermer la fenêtre de console et quitter le mode débogage.

1. Supprimez le point d’arrêt en cliquant sur le point dans la marge gauche de la fenêtre de code, ou en choisissant l’élément de menu **Débogage > Basculer le point d’arrêt** avec la ligne sélectionnée.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt. Dans le menu contextuel, sélectionnez **Conditions** pour ouvrir la boîte de dialogue **Paramètres de point d’arrêt**. Cochez la case **Conditions**.

   ![Éditeur montrant le panneau des paramètres de point d’arrêt - Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Pour **l’expression conditionnelle**, remplacez « e.g. x = 5 » par ceci :

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Vous testez une condition de code, à savoir que l’appel de méthode `String.IsNullOrEmpty(name)` est `True` car *name* ne s’est pas vu affecter de valeur ou que sa valeur est une chaîne vide (""). Vous pouvez également spécifier un *nombre d’accès*, qui interrompt l’exécution avant qu’une instruction soit exécutée un nombre spécifié de fois, ou une *condition de filtre*, qui interrompt l’exécution du programme en fonction d’attributs, comme un identificateur de thread, un nom de processus ou un nom de thread.

1. Sélectionnez le bouton **Fermer** pour fermer la boîte de dialogue.

1. Exécutez le programme en mode débogage.

1. Dans la fenêtre de console, appuyez sur la touche Entrée lorsque vous êtes invité à entrer votre nom.

1. Comme la condition que nous avons spécifiée (`name` ayant la valeur `null` ou <xref:System.String.Empty?displayProperty=nameWithType>) a été satisfaite, l’exécution du programme s’arrête quand elle atteint le point d’arrêt et avant que la méthode `Console.WriteLine` s’exécute.

1. Sélectionnez la fenêtre **Variables locales**, qui montre les valeurs des variables locales pour la méthode en cours d’exécution, qui est la méthode `Main` dans votre programme. Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Vérifiez que la valeur est une chaîne vide en entrant l’instruction suivante dans la **fenêtre Exécution**. Le résultat est `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

  ![Fenêtre Exécution retournant une valeur true après exécution de l’instruction - Visual Basic](./media/debugging-with-visual-studio/vb-immediate-window-output.png)

1. Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.

1. Appuyez sur une touche pour fermer la fenêtre de console et quitter le mode débogage.

1. Supprimez le point d’arrêt en cliquant sur le point dans la marge gauche de la fenêtre de code, ou en choisissant l’élément de menu **Débogage > Basculer le point d’arrêt** avec la ligne sélectionnée.

---
## <a name="stepping-through-a-program"></a>Exécution pas à pas d’un programme

Visual Studio vous permet également de parcourir un programme ligne par ligne et de surveiller son exécution. En règle générale, on définit un point d’arrêt et on utilise cette fonctionnalité pour suivre le déroulement du programme sur une petite portion de son code. Comme votre programme est petit, nous pouvons exécuter pas à pas la totalité du programme en procédant comme suit :

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Dans la barre de menus, choisissez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.

   ![Méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-method.png)

   À ce stade, la fenêtre **Automatique** montre que notre programme n’a défini qu’une seule variable, `args`. Comme vous n’avez passé aucun argument de ligne de commande au programme, sa valeur est un tableau de chaînes vides. En outre, Visual Studio a ouvert une fenêtre de console vide.

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio place maintenant en surbrillance la ligne suivante à exécuter. Comme le montre l’illustration, il lui a fallu moins d’une milliseconde pour exécuter le code entre la dernière instruction et celle-ci. `args` reste la seule variable déclarée et la fenêtre de console reste vide.

   ![Source de la méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **Automatiques** fenêtre montre que `name` est `null`, et la fenêtre de console affiche la chaîne « What is your name? ».

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur Entrée. La console ne répond pas et la chaîne que vous entrez ne s’affiche pas dans la fenêtre de console, mais la méthode <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> capture néanmoins votre entrée.

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `date` (en C#) ou `currentDate` (en Visual Basic). La fenêtre **Automatique** montre la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType> et la valeur retournée par l’appel à la méthode <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. La fenêtre de console affiche également la chaîne entrée lorsque vous y avez été invité par la console.

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. La fenêtre **Automatique** montre la valeur de la variable `date` après l’attribution de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>. La fenêtre de console est inchangée.

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. Les valeurs des variables `date` (ou `currentDate`) et `name` apparaissent dans la fenêtre **Automatique** et la fenêtre de console affiche la chaîne mise en forme.

1. Sélectionnez **Débogage** > **Pas à pas sortant**, ou appuyez sur Maj et la touche F11. Cela arrête l’exécution pas à pas. La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur une touche pour fermer la fenêtre de console et quitter le mode débogage.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Dans la barre de menus, choisissez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.

   ![Méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   À ce stade, comme vous n’avez passé aucun argument de ligne de commande au programme, la fenêtre **Automatique** qui affiche la valeur de la variable `args` est un tableau de chaînes vide. En outre, Visual Studio a ouvert une fenêtre de console vide.

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio place maintenant en surbrillance la ligne suivante à exécuter. Comme le montre l’illustration, il lui a fallu moins d’une milliseconde pour exécuter le code entre la dernière instruction et celle-ci. `args` reste la seule variable déclarée et la fenêtre de console reste vide.

   ![Source de la méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **Automatiques** fenêtre montre que `name` est `Nothing`, et la fenêtre de console affiche la chaîne « What is your name? ».

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de console et en appuyant sur Entrée. La console ne répond pas et la chaîne que vous entrez ne s’affiche pas dans la fenêtre de console, mais la méthode <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> capture néanmoins votre entrée.

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `date` (en C#) ou `currentDate` (en Visual Basic). La fenêtre **Automatique** montre la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType> et la valeur retournée par l’appel à la méthode <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. La fenêtre de console affiche également la chaîne entrée lorsque vous y avez été invité par la console.

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. La fenêtre **Automatique** montre la valeur de la variable `date` après l’attribution de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>. La fenêtre de console est inchangée.

1. Sélectionnez **Débogage** > **Pas à pas détaillé** ou appuyez sur la touche F11. Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. Les valeurs des variables `date` (ou `currentDate`) et `name` apparaissent dans la fenêtre **Automatique** et la fenêtre de console affiche la chaîne mise en forme.

1. Sélectionnez **Débogage** > **Pas à pas sortant**, ou appuyez sur Maj et la touche F11. Cela arrête l’exécution pas à pas. La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur une touche pour fermer la fenêtre de console et quitter le mode débogage.

---

## <a name="building-a-release-version"></a>Génération d’une version Release

Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Release. La version Release intègre des optimisations du compilateur qui peuvent parfois affecter négativement le comportement d’une application. Par exemple, les optimisations du compilateur qui sont conçues pour améliorer les performances peuvent créer des conditions de concurrence critique dans les applications asynchrones ou multithreads.

Pour générer et tester la version Release de votre application console, changez la configuration de build dans la barre d’outils de **Debug** en **Release**.

![Barre d’outils par défaut Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Quand vous appuyez sur F5 ou que vous choisissez **Générer la solution** à partir du menu **Build**, Visual Studio compile la version Release de votre application. Vous pouvez la tester comme vous l’avez fait pour la version Debug de l’application.

Une fois que vous avez terminé de déboguer votre application, l’étape suivante consiste à publier une version déployable de votre application. Pour plus d’informations sur la procédure à suivre, consultez [Publier l’application Hello World avec Visual Studio 2017](publishing-with-visual-studio.md).
