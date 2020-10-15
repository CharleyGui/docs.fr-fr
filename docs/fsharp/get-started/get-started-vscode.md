---
title: Bien démarrer avec F# dans Visual Studio Code
description: 'Découvrez comment utiliser F # avec Visual Studio Code et la suite de plug-in Ionide.'
ms.date: 12/23/2018
ms.openlocfilehash: 3317d0037d3c14a6b55079385d7b27e499c0c392
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050544"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Bien démarrer avec F# dans Visual Studio Code

Vous pouvez écrire du code F # dans [Visual Studio code](https://code.visualstudio.com) avec le [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) pour obtenir une expérience de l’environnement de développement intégré (IDE) multiplateforme et légère avec IntelliSense et les refactorisations de code. Visitez [Ionide.IO](https://ionide.io) pour en savoir plus sur le plug-in.

Pour commencer, assurez-vous que [F # et le plug-in Ionide sont correctement installés](install-fsharp.md#install-f-with-visual-studio-code).

## <a name="create-your-first-project-with-ionide"></a>Créer votre premier projet avec Ionide

Pour créer un projet F #, ouvrez une ligne de commande et créez un projet avec l’CLI .NET Core :

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

Une fois l’opération terminée, accédez au répertoire du projet et ouvrez Visual Studio Code :

```console
cd FirstIonideProject
code .
```

Une fois le projet chargé sur Visual Studio Code, vous devez voir le volet de Explorateur de solutions F # sur le côté gauche de votre fenêtre ouvert. Cela signifie que Ionide a chargé avec succès le projet que vous venez de créer. Vous pouvez écrire du code dans l’éditeur avant ce point dans le temps, mais une fois que cela se produit, tout le chargement est terminé.

## <a name="configure-f-interactive"></a>Configurer F # Interactive

Tout d’abord, assurez-vous que le script .NET Core est votre environnement de script par défaut :

1. Ouvrez les paramètres du Visual Studio code (paramètres des préférences de**code**  >  **Preferences**  >  **Settings**).
1. Recherchez le terme **script F #**.
1. Cochez la case **FSharp : Use SDK scripts**.

Cela est actuellement nécessaire en raison de comportements hérités dans les scripts basés sur .NET Framework qui ne fonctionnent pas avec les scripts .NET Core, et Ionide s’efforce actuellement de la compatibilité descendante. À l’avenir, les scripts .NET Core deviendront la valeur par défaut.

### <a name="write-your-first-script"></a>Écrire votre premier script R

Une fois que vous avez configuré Visual Studio Code pour utiliser les scripts .NET Core, accédez à l’affichage de l’Explorateur dans Visual Studio Code et créez un nouveau fichier. Nommez-le *MyFirstScript. FSX*.

Ajoutez maintenant le code suivant :

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Cette fonction convertit un mot en une forme de [porc latin](https://en.wikipedia.org/wiki/Pig_Latin). L’étape suivante consiste à l’évaluer à l’aide de F# Interactive (FSI).

Mettez en surbrillance la fonction entière (il doit s’agir de 11 lignes). Une fois qu’elle est mise en surbrillance, maintenez la touche **ALT** enfoncée et appuyez sur **entrée**. Vous remarquerez qu’une fenêtre de terminal s’affiche en bas de l’écran et devrait ressembler à ceci :

![Exemple de sortie de F# Interactive avec Ionide](./media/getting-started-vscode/vscode-fsi.png)

Cela faisait trois choses :

1. Il a démarré le processus FSI.
2. Il a envoyé le code que vous avez mis en surbrillance au cours du processus FSI.
3. Le processus FSI a évalué le code que vous avez envoyé.

Comme ce que vous avez envoyé via était une [fonction](../language-reference/functions/index.md), vous pouvez maintenant appeler cette fonction avec FSI ! Dans la fenêtre interactive, tapez ce qui suit :

```fsharp
toPigLatin "banana";;
```

Le résultat suivant s’affiche :

```fsharp
val it : string = "ananabay"
```

À présent, essayons avec une voyelle comme première lettre. Entrez les informations suivantes :

```fsharp
toPigLatin "apple";;
```

Le résultat suivant s’affiche :

```fsharp
val it : string = "appleyay"
```

La fonction semble fonctionner comme prévu. Félicitations, vous venez d’écrire votre première fonction F # dans Visual Studio Code et de l’évaluer avec FSI !

> [!NOTE]
> Comme vous l’avez peut-être remarqué, les lignes du FSI se terminent par `;;` . Cela est dû au fait que FSI vous permet d’entrer plusieurs lignes. Le `;;` à la fin permet à la FSI de savoir à quel moment le code est terminé.

## <a name="explaining-the-code"></a>Explication du code

Si vous n’êtes pas sûr de ce que fait le code, voici une procédure pas à pas.

Comme vous pouvez le voir, `toPigLatin` est une fonction qui prend un mot comme entrée et la convertit en une représentation Pig-Latin de ce mot. Les règles applicables sont les suivantes :

Si le premier caractère d’un mot commence par une voyelle, ajoutez « Ouais » à la fin du mot. S’il ne commence pas par une voyelle, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.

Vous avez peut-être remarqué ce qui suit dans FSI :

```fsharp
val toPigLatin : word:string -> string
```

Il `toPigLatin` s’agit d’une fonction qui prend une `string` entrée comme entrée (appelée `word` ) et retourne une autre `string` . C’est ce que l’on appelle la [signature de type de la fonction](https://fsharpforfunandprofit.com/posts/function-signatures/), un élément fondamental de f # qui est essentiel pour comprendre le code f #. Vous remarquerez également cela si vous pointez sur la fonction dans Visual Studio Code.

Dans le corps de la fonction, vous remarquerez deux parties distinctes :

1. Une fonction interne, appelée `isVowel` , qui détermine si un caractère donné ( `c` ) est une voyelle en vérifiant si elle correspond à l’un des modèles fournis via des [critères spéciaux](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)Expression qui vérifie si le premier caractère est une voyelle et construit une valeur de retour à partir des caractères d’entrée en fonction de si le premier caractère est une voyelle ou non :

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Le déroulement de `toPigLatin` est donc :

Vérifie si le premier caractère du mot d’entrée est une voyelle. Si c’est le cas, attachez « Ouais » à la fin du mot. Dans le cas contraire, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.

Il y a une dernière chose à noter : en F #, il n’y a pas d’instruction explicite à retourner à partir de la fonction. En effet, F # est basé sur une expression et la dernière expression évaluée dans le corps d’une fonction détermine la valeur de retour de cette fonction. Étant donné que `if..then..else` est lui-même une expression, l’évaluation du corps du `then` bloc ou le corps du `else` bloc détermine la valeur retournée par la `toPigLatin` fonction.

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>Transformez l’application console en un générateur latin de porc

Les sections précédentes de cet article ont montré une première étape courante dans l’écriture de code F # : écriture d’une fonction initiale et exécution interactive de cette dernière avec FSI. C’est ce que l’on appelle le développement basé sur REPL, où [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) signifie « lecture-évaluation-impression Loop ». C’est un excellent moyen d’expérimenter les fonctionnalités jusqu’à ce que vous ayez un peu de travail.

L’étape suivante du développement piloté par REPL consiste à déplacer le code de travail dans un fichier d’implémentation F #. Il peut ensuite être compilé par le compilateur F # dans un assembly qui peut être exécuté.

Pour commencer, ouvrez le fichier *Program. FS* que vous avez créé précédemment avec le CLI .net core. Vous remarquerez que du code existe déjà.

Ensuite, créez un nouveau [`module`](../language-reference/modules.md) nommé `PigLatin` et copiez la `toPigLatin` fonction que vous avez créée précédemment dans celui-ci en tant que tel :

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

Ce module doit être au-dessus de la `main` fonction et se trouver sous la `open System` déclaration. L’ordre des déclarations est important en F #. vous devez donc définir la fonction avant de l’appeler dans un fichier.

Maintenant, dans la `main` fonction, appelez la fonction de générateur latin du porc sur les arguments :

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

Vous pouvez maintenant exécuter votre application console à partir de la ligne de commande :

```dotnetcli
dotnet run apple banana
```

Vous verrez qu’elle génère le même résultat que votre fichier de script, mais cette fois en tant que programme en cours d’exécution !

## <a name="troubleshooting-ionide"></a>Résolution des problèmes Ionide

Voici quelques façons de résoudre certains problèmes que vous pouvez rencontrer :

1. Pour obtenir les fonctionnalités d’édition de code de Ionide, vos fichiers F # doivent être enregistrés sur le disque et se trouver à l’intérieur d’un dossier qui est ouvert dans l’espace de travail Visual Studio Code.
1. Si vous avez apporté des modifications à votre système ou si vous avez installé les composants requis de Ionide avec Visual Studio Code ouvrez, redémarrez Visual Studio Code.
1. Si vos répertoires de projet comportent des caractères non valides, Ionide peut ne pas fonctionner.  Si c’est le cas, renommez les répertoires de votre projet.
1. Si aucune des commandes Ionide ne fonctionne, vérifiez vos [combinaisons de touches de Visual Studio code](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) pour voir si vous les remplacez par accident.
1. Si Ionide est endommagé sur votre ordinateur et qu’aucun des éléments ci-dessus n’a résolu votre problème, essayez de supprimer le `ionide-fsharp` répertoire sur votre ordinateur et de réinstaller la suite de plug-in.
1. En cas d’échec du chargement d’un projet (F # Explorateur de solutions l’affiche), cliquez avec le bouton droit sur ce projet et cliquez sur **afficher les détails** pour obtenir plus d’informations de diagnostic.

Ionide est un projet open source créé et géré par les membres de la communauté F #. Signalez les problèmes et n’hésitez pas à contribuer au [référentiel ionide-vscode-FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).

Vous pouvez également demander de l’aide auprès des développeurs Ionide et de la communauté F # dans le [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur F # et les fonctionnalités du langage, consultez [visite guidée de f #](../tour.md).
