---
title: Debug votre application Hello World .NET Core avec Visual Studio
description: Apprenez à déboiffer une application Hello World écrite en C ou Visual Basic avec Visual Studio.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156671"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Débogéez votre application C ou Visual Basic .NET Core Hello World à l’aide de Visual Studio

Jusqu’à présent, vous avez suivi les étapes de [Créer votre première application de console .NET Core dans Visual Studio 2019](with-visual-studio.md) pour créer et exécuter une application de console simple. Une fois que vous avez écrit et compilé votre application, vous pouvez commencer à la tester. Visual Studio comprend un ensemble complet d’outils de débogage que vous pouvez utiliser pour dépanner votre application.

## <a name="debug-build-configuration"></a>Configuration de construction Debug

*Débogage* et *Mise en production* sont deux des configurations de build par défaut de Visual Studio. La configuration de build actuelle s’affiche sur la barre d’outils. L’image suivante de la barre d’outils montre que Visual Studio est configuré pour compiler la version Debug de l’application :

![Barre d’outils Visual Studio avec débogé](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Commencez par exécuter la version Debug de votre application. La configuration de construction Debug éteint la plupart des optimisations de compilateur et fournit des informations plus riches pendant le processus de construction.

## <a name="set-a-breakpoint"></a>Définir un point d'arrêt

Exécutez votre programme et essayez quelques fonctionnalités de débogage :

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Définissez un *point d’arrêt* sur la ligne qui se lit `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` en cliquant sur la marge gauche de la fenêtre de code sur cette ligne. Vous pouvez également définir un point d’arrêt en plaçant le caret dans la ligne de code, puis en appuyant sur **F9** ou en choisissant **Debug** > **Toggle Breakpoint** de la barre de menu.

   Un point d’arrêt interrompt temporairement l’exécution de l’application *avant* que la ligne avec le point d’arrêt ne soit exécutée.

   Comme le montre l’image suivante, Visual Studio indique la ligne sur laquelle le point d’arrêt est réglé en le mettant en évidence et en affichant un cercle rouge dans sa marge gauche.

   ![Fenêtre Programme de Visual Studio avec un point d’arrêt défini](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Exécutez le programme en mode Debug en sélectionnant le bouton **HelloWorld** avec la flèche verte sur la barre d’outils, en appuyant sur **F5**, ou en choisissant **Debug** > **Start Debugging**.

1. Entrez une chaîne dans la fenêtre de la console lorsque le programme invite pour un nom, puis appuyez **sur Enter**.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.

   ![Capture d’écran d’un point d’arrêt dans Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. La fenêtre **Immédiate** vous permet d’interagir avec l’application que vous débogage. Vous pouvez modifier de façon interactive la valeur des variables pour voir comment cela affecte votre programme.

   1. Si la fenêtre **immédiate** n’est pas visible, affichez-la en choisissant **Debug** > **Windows** > **Immediate**.

   1. Entrez `name = "Gracie"` dans la fenêtre **immédiate** et appuyez sur la clé **Enter.**

   1. Entrez `date = DateTime.Parse("11/16/2019 5:25 PM")` dans la fenêtre **immédiate** et appuyez sur la clé **Enter.**

   La fenêtre **immédiate** affiche la valeur de la <xref:System.DateTime> variable de chaîne et les propriétés de la valeur. En outre, les valeurs des variables sont mises à jour dans la fenêtre **Locals.**

   ![Les habitants et les fenêtres immédiates dans Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Continuer l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils ou en sélectionnant **Debug** > **Continuer**. Les valeurs affichées dans la fenêtre de la console correspondent aux modifications que vous avez apportées dans la fenêtre **immédiate.**

   ![Fenêtre de console affichant les valeurs entrées](./media/debugging-with-visual-studio/console-window.png)

1. Appuyez sur n’importe quelle clé pour quitter l’application et arrêter de débogage.

# <a name="visual-basic"></a>[Base visuelle](#tab/vb)

1. Définissez un *point d’arrêt* sur la ligne qui se lit `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` en cliquant sur la marge gauche de la fenêtre de code sur cette ligne. Vous pouvez également définir un point d’arrêt en plaçant le caret sur la ligne désirée, puis en choisissant **Debug** > **Toggle Breakpoint** de la barre de menu.

   Un point d’arrêt interrompt temporairement l’exécution de l’application *avant* que la ligne avec le point d’arrêt ne soit exécutée.

   Comme le montre l’illustration suivante, Visual Studio affiche la ligne sur laquelle le point d’arrêt est défini en la mettant en surbrillance et en affichant un cercle rouge dans la marge de gauche.

   ![Fenêtre Programme de Visual Studio avec un point d’arrêt défini](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Exécutez le programme en mode Debug en sélectionnant le bouton **HelloWorld** avec la flèche verte sur la barre d’outils, en appuyant sur **F5**, ou en choisissant **Debug** > **Start Debugging**.

1. Entrez une chaîne dans la fenêtre de la console lorsque le programme invite pour un nom et appuyez **sur Entrez**.

1. L’exécution du programme s’arrête lorsqu’il atteint le point d’arrêt et avant l’exécution de la méthode `Console.WriteLine`. La fenêtre **Variables locales** affiche les valeurs des variables définies dans la méthode en cours d’exécution.

1. La fenêtre **Immédiate** vous permet d’interagir avec l’application que vous débogage. Vous pouvez modifier de façon interactive la valeur des variables pour voir comment cela affecte votre programme.

   1. Si la fenêtre **immédiate** n’est pas visible, affichez-la en choisissant **Debug** > **Windows** > **Immediate**.

   1. Entrez `name = "Gracie"` dans la fenêtre **immédiate** et appuyez sur la clé **Enter.**

   1. Entrez `date = DateTime.Parse("11/16/2019 5:25 PM")` dans la fenêtre **immédiate** et appuyez sur la clé **Enter.**

   Les valeurs des variables sont mises à jour dans la fenêtre **Locals.**

1. Continuez l’exécution du programme en sélectionnant le bouton **Continuer** dans la barre d’outils ou en sélectionnant l’élément de menu **Débogage** > **Continuer**. Les valeurs affichées dans la fenêtre de la console correspondent aux modifications que vous avez apportées dans la fenêtre **immédiate.**

   ![Fenêtre de console affichant les valeurs entrées](./media/debugging-with-visual-studio/console-window.png)

1. Appuyez sur n’importe quelle clé pour quitter l’application et arrêter de débogage.

---

## <a name="set-a-conditional-breakpoint"></a>Définir un point d’arrêt conditionnel

Votre programme affiche la chaîne entrée par l’utilisateur. Que se passe-t-il si l’utilisateur n’entre rien ? Vous pouvez tester cela avec une fonction de débogage utile appelée *un point d’arrêt conditionnel*, qui rompt l’exécution du programme quand une ou plusieurs conditions sont remplies.

Pour définir un point d’arrêt conditionnel et voir ce qu’il se passe lorsque l’utilisateur n’entre pas de chaîne, procédez comme suit :

# <a name="c"></a>[C #](#tab/csharp)

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt. Dans le menu contextuel, sélectionnez **Conditions** pour ouvrir la boîte de dialogue **Paramètres de point d’arrêt**. Cochez la case pour **les conditions** si elle n’est pas déjà sélectionnée.

   ![Éditeur montrant le panneau des paramètres de point d’arrêt - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Pour **l’expression conditionnelle**, remplacez « par exemple x 5 » par ce qui suit :

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Vous testez pour une condition `String.IsNullOrEmpty(name)` de code, que l’appel de méthode est `true` soit parce qu’il `name` n’a pas été attribué une valeur ou parce que sa valeur est une chaîne vide (""). Au lieu d’une expression conditionnelle, vous pouvez également spécifier un *nombre de coups*, qui interrompt l’exécution du programme avant qu’une déclaration ne soit exécutée un certain nombre de fois, ou une condition de *filtre,* qui interrompt l’exécution du programme en fonction d’attributs tels qu’un identifiant de thread, un nom de processus ou un nom de thread.

1. Sélectionnez **Près** de fermer le dialogue.

1. Commencez le programme avec débogage en appuyant sur **F5**.

1. Dans la fenêtre de la console, appuyez sur la clé **Enter** lorsqu’on vous l’incite à entrer votre nom.

1. Parce que la `name` condition `null` que <xref:System.String.Empty?displayProperty=nameWithType>vous avez spécifiée, est soit ou , a `Console.WriteLine` été satisfait, l’exécution du programme s’arrête quand il atteint le point d’arrêt et avant que la méthode s’exécute.

1. Sélectionnez la fenêtre **Locals,** qui montre les valeurs des variables qui sont locales à la méthode d’exécution actuelle. Dans ce `Main` cas, est la méthode d’exécution actuelle. Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirmer la valeur est une chaîne vide en entrant la déclaration suivante dans la fenêtre **immédiate** et en appuyant **sur Enter**. Le résultat est `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Fenêtre Exécution retournant une valeur true après exécution de l’instruction - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.

1. Appuyez sur n’importe quelle clé pour fermer la fenêtre de la console et arrêter de débogage.

1. Effacer le point d’arrêt en cliquant sur le point dans la marge gauche de la fenêtre de code ou en choisissant **Debug > Toggle Breakpoint** pendant que la ligne de code est sélectionnée.

# <a name="visual-basic"></a>[Base visuelle](#tab/vb)

1. Cliquez avec le bouton droit sur le point rouge qui représente le point d’arrêt. Dans le menu contextuel, sélectionnez **Conditions** pour ouvrir la boîte de dialogue **Paramètres de point d’arrêt**. Cochez la case **Conditions**.

   ![Éditeur montrant le panneau des paramètres de point d’arrêt - Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Pour **l’expression conditionnelle** remplacer "par exemple x 5" avec ce qui suit:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Vous testez pour une condition `String.IsNullOrEmpty(name)` de code, que l’appel de méthode est `true` soit parce qu’il `name` n’a pas été attribué une valeur ou parce que sa valeur est une chaîne vide (""). Au lieu d’une expression conditionnelle, vous pouvez également spécifier un *nombre de coups*, qui interrompt l’exécution du programme avant qu’une déclaration ne soit exécutée un certain nombre de fois, ou une condition de *filtre,* qui interrompt l’exécution du programme en fonction d’attributs tels qu’un identifiant de thread, un nom de processus ou un nom de thread.

1. Sélectionnez **Près** de fermer le dialogue.

1. Commencez le programme avec débogage en appuyant sur **F5**.

1. Dans la fenêtre de la console, appuyez sur la clé **Enter** lorsqu’on vous l’incite à entrer votre nom.

1. Parce que la `name` condition `null` que <xref:System.String.Empty?displayProperty=nameWithType>vous avez spécifiée, est soit ou , a `Console.WriteLine` été satisfait, l’exécution du programme s’arrête quand il atteint le point d’arrêt et avant que la méthode s’exécute.

1. Sélectionnez la fenêtre **Locals,** qui montre les valeurs des variables qui sont locales à la méthode d’exécution actuelle. Dans ce `Main` cas, est la méthode d’exécution actuelle. Notez que la valeur de la variable `name` est `""` ou <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirmer la valeur est une chaîne vide en entrant la déclaration suivante dans la fenêtre **immédiate** et en appuyant **sur Enter**. Le résultat est `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Fenêtre Exécution retournant une valeur true après exécution de l’instruction - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Sélectionnez le bouton **Continuer** dans la barre d’outils pour continuer l’exécution du programme.

1. Appuyez sur n’importe quelle clé pour fermer la fenêtre de la console et arrêter de débogage.

1. Supprimez le point d’arrêt en cliquant sur le point dans la marge gauche de la fenêtre de code, ou en choisissant l’élément de menu **Débogage > Basculer le point d’arrêt** avec la ligne sélectionnée.

---
## <a name="step-through-a-program"></a>Passez par un programme

Visual Studio vous permet également de parcourir un programme ligne par ligne et de surveiller son exécution. En règle générale, on définit un point d’arrêt et on utilise cette fonctionnalité pour suivre le déroulement du programme sur une petite portion de son code. Étant donné que votre programme est petit, vous pouvez passer par l’ensemble du programme :

# <a name="c"></a>[C #](#tab/csharp)

1. Sur la barre de menu, choisissez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.

   ![Méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-method.png)

   À ce stade, la fenêtre **local montre** que votre `args`programme n’a défini qu’une seule variable, . Comme vous n’avez passé aucun argument de ligne de commande au programme, sa valeur est un tableau de chaînes vides. En outre, Visual Studio a ouvert une fenêtre de console vide.

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio place maintenant en surbrillance la ligne suivante à exécuter. Comme l’image montre, il a fallu moins d’une milliseconde pour exécuter le code entre la dernière déclaration et celle-ci. `args` reste la seule variable déclarée et la fenêtre de console reste vide.

   ![Source de la méthode pas à pas détaillée dans Visual Studio - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **Locals** `null`montre que c’est, `name` et la fenêtre de la console affiche la chaîne "Quel est votre nom?".

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de la console et en appuyant **sur Enter**. La console est insensible, et la chaîne que vous avez saisie n’est pas affichée dans la fenêtre de la console, mais la <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> méthode va néanmoins capturer votre entrée.

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `date`. La fenêtre **des sections locales** montre <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> la valeur retournée par l’appel à la méthode. La fenêtre de la console affiche également la chaîne que vous avez saisie à l’invite.

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. La fenêtre **local montre** la `date` valeur de la <xref:System.DateTime.Now?displayProperty=nameWithType> variable après l’affectation de la propriété. La fenêtre de console est inchangée.

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. La fenêtre de la console affiche la chaîne formatée.

1. Sélectionnez **Debug** > **Step Out** ou appuyez sur **Shift**+**F11**. Cela arrête l’exécution pas à pas. La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur n’importe quelle clé pour fermer la fenêtre de la console et arrêter de débogage.

# <a name="visual-basic"></a>[Base visuelle](#tab/vb)

1. Sur la barre de menu, choisissez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio met en surbrillance et affiche une flèche en regard de la ligne suivante de l’exécution.

   ![Méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   À ce stade, la fenêtre **local montre** que votre `args`programme n’a défini qu’une seule variable, . Comme vous n’avez passé aucun argument de ligne de commande au programme, sa valeur est un tableau de chaînes vides. En outre, Visual Studio a ouvert une fenêtre de console vide.

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio place maintenant en surbrillance la ligne suivante à exécuter. Comme le montre l’illustration, il lui a fallu moins d’une milliseconde pour exécuter le code entre la dernière instruction et celle-ci. `args` reste la seule variable déclarée et la fenêtre de console reste vide.

   ![Source de la méthode pas à pas détaillée dans Visual Studio - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `name`. La fenêtre **Locals** `Nothing`montre que c’est, `name` et la fenêtre de la console affiche la chaîne "Quel est votre nom?".

1. Répondez à l’invite en entrant une chaîne dans la fenêtre de la console et en appuyant **sur Enter**. La console ne répond pas et la chaîne que vous entrez ne s’affiche pas dans la fenêtre de console, mais la méthode <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> capture néanmoins votre entrée.

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio met en surbrillance l’instruction qui inclut l’attribution de la variable `currentDate`. La fenêtre **des sections locales** montre <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> la valeur retournée par l’appel à la méthode. La fenêtre de console affiche également la chaîne entrée lorsque vous y avez été invité par la console.

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. La fenêtre de console est inchangée.

1. Sélectionnez **Debug** > **Step Into** ou appuyez sur **F11**. Visual Studio appelle la méthode <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. La fenêtre de la console affiche la chaîne formatée.

1. Sélectionnez **Debug** > **Step Out** ou appuyez sur **Shift**+**F11**. Cela arrête l’exécution pas à pas. La fenêtre de console affiche un message et attend que vous appuyiez sur une touche.

1. Appuyez sur n’importe quelle clé pour fermer la fenêtre de la console et arrêter de débogage.

---

## <a name="build-a-release-version"></a>Construire une version De libération

Une fois que vous avez testé la version Debug de votre application, vous devez également compiler et tester la version Version Libération. La version Release intègre des optimisations du compilateur qui peuvent parfois affecter négativement le comportement d’une application. Par exemple, les optimisations compilatrices conçues pour améliorer les performances peuvent créer des conditions de course dans des applications multithreaded.

Pour générer et tester la version Release de votre application console, changez la configuration de build dans la barre d’outils de **Debug** en **Release**.

![Barre d’outils par défaut Visual Studio avec débogage mis en surbrillance](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Lorsque vous appuyez sur **F5** ou choisissez **Build Solution** dans le menu **Build,** Visual Studio compile la version Version Version Release de l’application. Vous pouvez le tester comme vous l’avez fait la version Debug.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez débogé votre application, l’étape suivante consiste à publier une version déployable de l’application. Pour plus d’informations sur la façon de le faire, voir [Publier votre application .NET Core Hello World avec Visual Studio](publishing-with-visual-studio.md).
