---
title: Hello World -- Votre premier programme utilisant Visual Studio sur Windows ou Mac - Guide de programmation C
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712141"
---
# <a name="hello-world----your-first-program"></a>Bonjour Monde -- Votre premier programme

Dans cet article, vous utiliserez Visual Studio pour créer le traditionnel "Hello World!" . Visual Studio est un environnement de développement intégré professionnel (IDE) avec de nombreuses fonctionnalités conçues pour le développement .NET. Vous n’utiliserez que quelques-unes des fonctionnalités de Visual Studio pour créer ce programme. Pour en savoir plus sur Visual Studio, voir [Getting Started with Visual C .](/visualstudio/ide/quickstart-csharp-console)

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Créer une application

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Démarrez Visual Studio. Vous verrez l’image suivante sur Windows :

![Écran de bienvenue Visual Studio sur Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Sélectionnez **Créer un nouveau projet** dans le coin inférieur droit de l’image. Visual Studio affiche le dialogue **du nouveau projet** :

![Visual Studio nouvel écran de projet sur Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> Si c’est la première fois que vous lancez Visual Studio, la liste **des modèles de projets récents** est vide.

Sur le nouveau dialogue de projet, choisissez "Console App (.NET Core)" et appuyez ensuite **sur Next**. Donnez à votre projet un nom, tel que "HelloWorld", puis appuyez sur **Créer**.

Visual Studio ouvre votre projet. C’est déjà un "Bonjour Monde!" « Hello, World! ». Appuyez `Ctrl`  +  `F5` pour exécuter votre projet. Visual Studio construit votre projet, convertissant le code source en un exécutable. Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application. Vous devriez voir le texte suivant dans la fenêtre:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Appuyez sur une touche pour fermer la fenêtre.

# <a name="macos"></a>[macOS](#tab/macos)

Démarrer Visual Studio pour Mac. Vous verrez l’image suivante sur Mac :

![Écran de bienvenue Visual Studio sur Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Si c’est la première fois que vous avez commencé Visual Studio pour Mac, la liste **des projets récents** est vide.

Sélectionnez **Nouveau** dans le coin supérieur droit de l’image. Visual Studio pour Mac affiche le dialogue **du nouveau projet** :

![Visual Studio nouvel écran de projet sur Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

Sur le nouveau dialogue de projet, choisissez ".NET Core", et "Console App" et appuyez ensuite sur **Next**. Vous devrez sélectionner le cadre cible. La valeur par défaut est très bien, alors appuyez ensuite. Donnez à votre projet un nom, tel que "HelloWorld", puis appuyez sur **Créer**. Vous pouvez utiliser l’emplacement par défaut du projet. N’ajoutez pas ce projet au contrôle des sources.

Visual Studio pour Mac ouvre votre projet. C’est déjà un "Bonjour Monde!" « Hello, World! ». `Ctrl`  +  `Fn` Appuyez  +  `F5` pour exécuter votre projet. Visual Studio pour Mac construit votre projet, convertissant le code source en un exécutable. Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application. Vous devriez voir le texte suivant dans la fenêtre:

```console
Hello World!

Press any key to close this window . . .
```

Appuyez sur une clé pour terminer la session.

---

## <a name="elements-of-a-c-program"></a>Éléments d’un programme C

Examinons les parties importantes de ce programme. La première ligne contient un commentaire. Les caractères `//` convertissent le reste de la ligne en un commentaire.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Vous pouvez également créer un commentaire à partir d’un bloc de texte en le plaçant entre les caractères `/*` et `*/`. Cela est illustré par l'exemple suivant.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

Une application console C# doit contenir une méthode `Main`, dans laquelle le contrôle commence et termine. C’est dans la méthode `Main` que vous créez des objets et exécutez d’autres méthodes.

La méthode `Main` est une méthode [static](../../language-reference/keywords/static.md) qui réside dans une classe ou un struct. Dans l’exemple « Hello World ! » précédent, il réside dans une classe nommée `Hello`. Vous pouvez déclarer la méthode `Main` de l’une des façons suivantes :

- Elle peut retourner `void`. Cela signifie que votre programme ne retourne pas de valeur.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Elle peut également retourner un entier. L’integer est le **code de sortie** de votre application.

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Elle peut accepter des arguments avec n’importe quel type de retour.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-ou-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Le paramètre `args` de la méthode `Main` est un tableau `string` qui contient les arguments de la ligne de commande utilisés pour appeler le programme.

Pour plus d’informations sur la façon d’utiliser les arguments de la ligne de commande, voir les exemples dans [Main() et Command-Line Arguments](../main-and-command-args/index.md).

## <a name="input-and-output"></a>Entrée et sortie

Les programmes C# utilisent généralement les services d’entrée/sortie fournis par la bibliothèque runtime du .NET Framework. L’instruction `System.Console.WriteLine("Hello World!");` utilise la méthode <xref:System.Console.WriteLine%2A>. C’est l’une des méthodes de sortie de la classe <xref:System.Console> de la bibliothèque runtime. Elle affiche son paramètre de chaîne dans le flux de sortie standard suivi d’une nouvelle ligne. D’autres méthodes <xref:System.Console> sont disponibles pour différentes opérations d’entrée et de sortie. Si vous incluez la directive `using System;` au début du programme, vous pouvez utiliser directement les classes et les méthodes <xref:System> sans les qualifier complètement. Par exemple, vous pouvez appeler `Console.WriteLine` au lieu de `System.Console.WriteLine` :

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Pour plus d’informations sur les méthodes d’entrée/sortie, consultez <xref:System.IO>.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Échantillons et tutoriels](../../../samples-and-tutorials/index.md)
- [Main() et arguments de ligne de commande](../main-and-command-args/index.md)
- [Mise en route de Visual C#](/visualstudio/ide/quickstart-csharp-console)
