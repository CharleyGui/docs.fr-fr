---
title: Hello World -- Votre premier programme - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 9a50de0bb583a1dfccfa609be1cca732868505ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589375"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World -- Votre premier programme (Guide de programmation C#)

La procédure suivante crée une version C# du traditionnel programme « Hello World ! » . Le programme affiche la chaîne `Hello World!`

Pour plus d’exemples concernant les concepts de base, consultez [Bien démarrer avec Visual Basic et Visual C#](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a>Pour créer et exécuter une application console

1. Démarrez Visual Studio.

2. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

3. Développez **Installé**, **Modèles**, **Visual C#** , puis choisissez **Application console**.

4. Dans la zone de texte **Nom**, entrez un nom pour votre projet, puis choisissez le bouton **OK**.

     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.

5. Si Program.cs n’est pas ouvert dans l’**Éditeur de Code**, ouvrez le menu contextuel de **Program.cs** dans **l’Explorateur de solutions**, puis choisissez **Afficher le code**.

6. Remplacez le contenu de Program.cs par le code suivant.

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. Appuyez sur la touche F5 pour exécuter le projet. Une fenêtre d’invite de commandes s’affiche avec la ligne `Hello World!`

Ensuite, les parties importantes de ce programme sont examinées.

## <a name="comments"></a>Commentaires

La première ligne contient un commentaire. Les caractères `//` convertissent le reste de la ligne en un commentaire.

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Vous pouvez également créer un commentaire à partir d’un bloc de texte en le plaçant entre les caractères `/*` et `*/`. L'exemple suivant le démontre.

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a>Main (méthode)

Une application console C# doit contenir une méthode `Main`, dans laquelle le contrôle commence et termine. C’est dans la méthode `Main` que vous créez des objets et exécutez d’autres méthodes.

La méthode `Main` est une méthode [static](../../language-reference/keywords/static.md) qui réside dans une classe ou un struct. Dans l’exemple « Hello World ! » précédent, il réside dans une classe nommée `Hello`. Vous pouvez déclarer la méthode `Main` de l’une des façons suivantes :

- Elle peut retourner `void`.

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Elle peut également retourner un entier.

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Elle peut accepter des arguments avec n’importe quel type de retour.

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     -ou-

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Le paramètre `args` de la méthode `Main` est un tableau `string` qui contient les arguments de la ligne de commande utilisés pour appeler le programme. Contrairement au langage C++, le tableau n’inclut pas le nom du fichier exécutable (exe).

Pour plus d’informations sur l’utilisation des arguments de ligne de commande, consultez les exemples des rubriques [Main() et arguments de ligne de commande](../main-and-command-args/index.md) et [Guide pratique pour créer et utiliser des assemblys à l’aide de la ligne de commande](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).

L’appel à <xref:System.Console.ReadKey%2A> à la fin de la méthode `Main` empêche la fenêtre de console de se fermer avant que vous ayez pu lire la sortie quand vous exécutez votre programme en mode débogage, avec la touche F5.

## <a name="input-and-output"></a>Entrée et sortie

Les programmes C# utilisent généralement les services d’entrée/sortie fournis par la bibliothèque runtime du .NET Framework. L’instruction `System.Console.WriteLine("Hello World!");` utilise la méthode <xref:System.Console.WriteLine%2A>. C’est l’une des méthodes de sortie de la classe <xref:System.Console> de la bibliothèque runtime. Elle affiche son paramètre de chaîne dans le flux de sortie standard suivi d’une nouvelle ligne. D’autres méthodes <xref:System.Console> sont disponibles pour différentes opérations d’entrée et de sortie. Si vous incluez la directive `using System;` au début du programme, vous pouvez utiliser directement les classes et les méthodes <xref:System> sans les qualifier complètement. Par exemple, vous pouvez appeler `Console.WriteLine` au lieu de `System.Console.WriteLine` :

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Pour plus d’informations sur les méthodes d’entrée/sortie, consultez <xref:System.IO>.

## <a name="command-line-compilation-and-execution"></a>Compilation et exécution en ligne de commande

Vous pouvez compiler le programme « Hello World ! » à l’aide de la ligne de commande au lieu de l’environnement de développement intégré (IDE) Visual Studio.

### <a name="to-compile-and-run-from-a-command-prompt"></a>Pour compiler et exécuter à partir d’une invite de commandes

1. Copiez-collez le code de la procédure précédente dans un éditeur de texte, puis enregistrez le fichier en tant que fichier texte. Nommez le fichier `Hello.cs`. Les fichiers de code source C# utilisent l’extension `.cs`.

2. Effectuez l’une des opérations suivantes pour ouvrir une fenêtre d’invite de commandes :

    - Dans Windows 10, dans le menu **Démarrer**, recherchez `Developer Command Prompt`, puis choisissez **Invite de commandes développeur pour VS 2017**.

         Une fenêtre d’invite de commandes développeur s’affiche.

    - Dans Windows 7, ouvrez le menu **Démarrer**, développez le dossier de la version actuelle de Visual Studio, ouvrez le menu contextuel de **Visual Studio Tools**, puis choisissez **Invite de commandes de développeur de VS 2017**.

         Une fenêtre d’invite de commandes développeur s’affiche.

    - Activez les générations en mode ligne de commande à partir d’une fenêtre d’invite de commandes standard.

         Voir [Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).

3. Dans la fenêtre d’invite de commandes, accédez au dossier qui contient le fichier `Hello.cs`.

4. Entrez la commande suivante pour compiler `Hello.cs`.

     `csc Hello.cs`

     Si votre programme ne contient pas d’erreurs de compilation, un fichier exécutable nommé `Hello.exe` est créé.

5. Dans la fenêtre d’invite de commandes, entrez la commande suivante pour exécuter le programme :

     `Hello`

 Pour plus d’informations sur le compilateur C# et ses options, consultez [Options du compilateur C #](../../language-reference/compiler-options/index.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [À l’intérieur d’un programme C#](./index.md)
- [Chaînes](../strings/index.md)
- [Exemples et tutoriels](../../../samples-and-tutorials/index.md)
- [Référence C#](../../language-reference/index.md)
- [Main() et arguments de ligne de commande](../main-and-command-args/index.md)
- [Mises en route de Visual Basic et Visual C#](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
