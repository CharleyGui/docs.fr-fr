---
title: Hello World--votre premier programme à l’aide de Visual Studio sur Windows ou Mac-Guide de programmation C#
description: Visual Studio est un environnement de développement professionnel avec de nombreuses fonctionnalités pour le développement .NET. Utilisez Visual Studio pour créer une version C# de Hello World !
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: b78937b8ba1c7d4718bfb6252dac705945336d2a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301825"
---
# <a name="hello-world----your-first-program"></a>Hello World--votre premier programme

Dans cet article, vous allez utiliser Visual Studio pour créer le « Hello World ! » traditionnel . Visual Studio est un environnement de développement intégré (IDE) professionnel avec de nombreuses fonctionnalités conçues pour le développement .NET. Vous n’utiliserez que quelques-unes des fonctionnalités de Visual Studio pour créer ce programme. Pour en savoir plus sur Visual Studio, consultez [prise en main avec Visual C#](/visualstudio/ide/quickstart-csharp-console).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Créer une application

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Démarrez Visual Studio. L’image suivante s’affiche sur Windows :

![Écran de bienvenue de Visual Studio sur Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Sélectionnez **créer un nouveau projet** dans le coin inférieur droit de l’image. Visual Studio affiche la boîte **de dialogue Nouveau projet** :

![Écran nouveau projet de Visual Studio sur Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> S’il s’agit de la première fois que vous démarrez Visual Studio, la liste des **modèles de projet récents** est vide.

Dans la boîte de dialogue Nouveau projet, choisissez application console (.NET Core), puis cliquez sur **suivant**. Donnez un nom à votre projet, tel que « HelloWorld », puis appuyez sur **créer**.

Visual Studio ouvre votre projet. Il s’agit déjà d’un « Hello World ! » de base. « Hello, World! ». Appuyez sur `Ctrl`  +  `F5` pour exécuter votre projet. Visual Studio génère votre projet et convertit le code source en un fichier exécutable. Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application. Vous devez voir le texte suivant dans la fenêtre :

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Appuyez sur une touche pour fermer la fenêtre.

# <a name="macos"></a>[macOS](#tab/macos)

Démarrez Visual Studio pour Mac. L’image suivante s’affiche sur Mac :

![Écran de bienvenue de Visual Studio sur Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> S’il s’agit de la première fois que vous démarrez Visual Studio pour Mac, la liste des **projets récents** est vide.

Sélectionnez **nouveau** dans le coin supérieur droit de l’image. Visual Studio pour Mac affiche la boîte **de dialogue Nouveau projet** :

![Écran nouveau projet de Visual Studio sur Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

Dans la boîte de dialogue Nouveau projet, choisissez « .NET Core » et « application console », puis appuyez sur **suivant**. Vous devez sélectionner la version cible de .NET Framework. La valeur par défaut est correcte. Appuyez sur suivant. Donnez un nom à votre projet, tel que « HelloWorld », puis appuyez sur **créer**. Vous pouvez utiliser l’emplacement de projet par défaut. N’ajoutez pas ce projet au contrôle de code source.

Visual Studio pour Mac ouvre votre projet. Il s’agit déjà d’un « Hello World ! » de base. « Hello, World! ». Appuyez sur `Ctrl`  +  `Fn`  +  `F5` pour exécuter votre projet. Visual Studio pour Mac génère votre projet et convertit le code source en un fichier exécutable. Ensuite, il lance une fenêtre de commande qui exécute votre nouvelle application. Vous devez voir le texte suivant dans la fenêtre :

```console
Hello World!

Press any key to close this window . . .
```

Appuyez sur une touche pour mettre fin à la session.

---

## <a name="elements-of-a-c-program"></a>Éléments d’un programme C#

Examinons les parties importantes de ce programme. La première ligne contient un commentaire. Les caractères `//` convertissent le reste de la ligne en un commentaire.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Vous pouvez également créer un commentaire à partir d’un bloc de texte en le plaçant entre les caractères `/*` et `*/`. Cela est illustré par l'exemple suivant.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

Une application console C# doit contenir une méthode `Main`, dans laquelle le contrôle commence et termine. C’est dans la méthode `Main` que vous créez des objets et exécutez d’autres méthodes.

La méthode `Main` est une méthode [static](../../language-reference/keywords/static.md) qui réside dans une classe ou un struct. Dans l’exemple « Hello World ! » précédent, il réside dans une classe nommée `Hello`. Vous pouvez déclarer la méthode `Main` de l’une des façons suivantes :

- Elle peut retourner `void`. Cela signifie que votre programme ne retourne pas de valeur.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Elle peut également retourner un entier. L’entier est le **Code de sortie** de votre application.

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Elle peut accepter des arguments avec n’importe quel type de retour.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-ou-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Le paramètre `args` de la méthode `Main` est un tableau `string` qui contient les arguments de la ligne de commande utilisés pour appeler le programme.

Pour plus d’informations sur l’utilisation des arguments de ligne de commande, consultez les exemples dans [main () et arguments de ligne de commande](../main-and-command-args/index.md).

## <a name="input-and-output"></a>Entrée et sortie

Les programmes C# utilisent généralement les services d’entrée/sortie fournis par la bibliothèque Runtime de .NET. L’instruction `System.Console.WriteLine("Hello World!");` utilise la méthode <xref:System.Console.WriteLine%2A>. C’est l’une des méthodes de sortie de la classe <xref:System.Console> de la bibliothèque runtime. Elle affiche son paramètre de chaîne dans le flux de sortie standard suivi d’une nouvelle ligne. D’autres méthodes <xref:System.Console> sont disponibles pour différentes opérations d’entrée et de sortie. Si vous incluez la directive `using System;` au début du programme, vous pouvez utiliser directement les classes et les méthodes <xref:System> sans les qualifier complètement. Par exemple, vous pouvez appeler `Console.WriteLine` au lieu de `System.Console.WriteLine` :

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Pour plus d’informations sur les méthodes d’entrée/sortie, consultez <xref:System.IO>.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Exemples et tutoriels](../../../samples-and-tutorials/index.md)
- [Main () et arguments de ligne de commande](../main-and-command-args/index.md)
- [Mise en route de Visual C#](/visualstudio/ide/quickstart-csharp-console)
