---
title: Bien démarrer avec F# dans Visual Studio Code
description: Découvrez comment utiliser F# avec Visual Studio code et la suite de plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2aa62bb1afc220348f884865e55c4d7de4359b7f
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980351"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Bien démarrer avec F# dans Visual Studio Code

Vous pouvez écrire F# en [Visual Studio code](https://code.visualstudio.com) avec le [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) pour bénéficier d’une expérience de l’environnement de développement intégré (IDE) multiplateforme et légère avec IntelliSense et les refactorisations de code. Visitez [Ionide.IO](http://ionide.io) pour en savoir plus sur le plug-in.

Pour commencer, assurez-vous que [ F# et le plug-in Ionide sont correctement installés](install-fsharp.md#install-f-with-visual-studio-code).

## <a name="create-your-first-project-with-ionide"></a>Créer votre premier projet avec Ionide

Pour créer un F# projet, ouvrez une ligne de commande et créez un projet avec l’CLI .net Core :

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

Une fois l’opération terminée, accédez au répertoire du projet et ouvrez Visual Studio Code :

```console
cd FirstIonideProject
code .
```

Une fois que le projet est chargé sur Visual Studio Code, le F# volet de Explorateur de solutions à gauche de votre fenêtre doit s’ouvrir. Cela signifie que Ionide a chargé avec succès le projet que vous venez de créer. Vous pouvez écrire du code dans l’éditeur avant ce point dans le temps, mais une fois que cela se produit, tout le chargement est terminé.

## <a name="configure-f-interactive"></a>Configurer F# interactive

Tout d’abord, assurez-vous que le script .NET Core est votre environnement de script par défaut :

1. Ouvrez les paramètres du Visual Studio Code (paramètres **du > de** **code** > **paramètres**).
1. Recherchez le terme  **F# script**.
1. Cochez la case **FSharp : Use SDK scripts**.

Cela est actuellement nécessaire en raison de comportements hérités dans les scripts basés sur .NET Framework qui ne fonctionnent pas avec les scripts .NET Core, et Ionide s’efforce actuellement de la compatibilité descendante. À l’avenir, les scripts .NET Core deviendront la valeur par défaut.

### <a name="write-your-first-script"></a>Écrire votre premier script

Une fois que vous avez configuré Visual Studio Code pour utiliser les scripts .NET Core, accédez à l’affichage de l’Explorateur dans Visual Studio Code et créez un nouveau fichier. Nommez-le *MyFirstScript. FSX*.

Ajoutez maintenant le code suivant :

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Cette fonction convertit un mot en une forme de [porc latin](https://en.wikipedia.org/wiki/Pig_Latin). L’étape suivante consiste à l’évaluer à F# l’aide de l’interactivité (FSI).

Mettez en surbrillance la fonction entière (il doit s’agir de 11 lignes). Une fois qu’elle est mise en surbrillance, maintenez la touche **ALT** enfoncée et appuyez sur **entrée**. Vous remarquerez qu’une fenêtre de terminal s’affiche en bas de l’écran et devrait ressembler à ceci :

![Exemple de F# sortie interactive avec Ionide](./media/getting-started-vscode/vscode-fsi.png)

Cela faisait trois choses :

1. Il a démarré le processus FSI.
2. Il a envoyé le code que vous avez mis en surbrillance au cours du processus FSI.
3. Le processus FSI a évalué le code que vous avez envoyé.

Comme ce que vous avez envoyé via était une [fonction](../language-reference/functions/index.md), vous pouvez maintenant appeler cette fonction avec FSI ! Dans la fenêtre interactive, tapez ce qui suit :

```fsharp
toPigLatin "banana";;
```

Le résultat suivant doit s’afficher :

```fsharp
val it : string = "ananabay"
```

À présent, essayons avec une voyelle comme première lettre. Entrez les informations suivantes :

```fsharp
toPigLatin "apple";;
```

Le résultat suivant doit s’afficher :

```fsharp
val it : string = "appleyay"
```

La fonction semble fonctionner comme prévu. Félicitations, vous venez d’écrire votre F# première fonction dans Visual Studio code et de l’évaluer avec FSI !

> [!NOTE]
> Comme vous l’avez peut-être remarqué, les lignes du FSI se terminent par `;;`. Cela est dû au fait que FSI vous permet d’entrer plusieurs lignes. La `;;` à la fin permet à la FSI de savoir quand le code est terminé.

## <a name="explaining-the-code"></a>Explication du code

Si vous n’êtes pas sûr de ce que fait le code, voici une procédure pas à pas.

Comme vous pouvez le voir, `toPigLatin` est une fonction qui prend un mot comme entrée et la convertit en une représentation porc-latin de ce mot. Les règles applicables sont les suivantes :

Si le premier caractère d’un mot commence par une voyelle, ajoutez « Ouais » à la fin du mot. S’il ne commence pas par une voyelle, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.

Vous avez peut-être remarqué ce qui suit dans FSI :

```fsharp
val toPigLatin : word:string -> string
```

Cela indique que `toPigLatin` est une fonction qui prend un `string` comme entrée (appelé `word`) et retourne un autre `string`. C’est ce que l’on appelle la [signature de type de la fonction](https://fsharpforfunandprofit.com/posts/function-signatures/), un F# élément fondamental de la clé F# de la compréhension du code. Vous remarquerez également cela si vous pointez sur la fonction dans Visual Studio Code.

Dans le corps de la fonction, vous remarquerez deux parties distinctes :

1. Une fonction interne, appelée `isVowel`, qui détermine si un caractère donné (`c`) est une voyelle en vérifiant si elle correspond à l’un des modèles fournis via des [critères spéciaux](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Expression [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) qui vérifie si le premier caractère est une voyelle et construit une valeur de retour en dehors des caractères d’entrée en fonction de si le premier caractère est une voyelle ou non :

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Le déroulement de `toPigLatin` est donc :

Vérifie si le premier caractère du mot d’entrée est une voyelle. Si c’est le cas, attachez « Ouais » à la fin du mot. Dans le cas contraire, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.

Il y a une dernière chose à noter : dans F#, il n’y a pas d’instruction explicite à retourner à partir de la fonction. Cela est dû F# au fait que est basé sur une expression et que la dernière expression évaluée dans le corps d’une fonction détermine la valeur de retour de cette fonction. Étant donné que `if..then..else` est lui-même une expression, l’évaluation du corps du bloc `then` ou du corps du bloc `else` détermine la valeur retournée par la fonction `toPigLatin`.

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>Transformez l’application console en un générateur latin de porc

Les sections précédentes de cet article ont montré une première étape courante dans F# l’écriture de code : écriture d’une fonction initiale et exécution interactive de cette dernière avec le FSI. C’est ce que l’on appelle le développement basé sur REPL, où [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) signifie « lecture-évaluation-impression Loop ». C’est un excellent moyen d’expérimenter les fonctionnalités jusqu’à ce que vous ayez un peu de travail.

L’étape suivante du développement piloté par REPL consiste à déplacer le code de travail F# dans un fichier d’implémentation. Il peut ensuite être compilé par le F# compilateur dans un assembly qui peut être exécuté.

Pour commencer, ouvrez le fichier *Program. FS* que vous avez créé précédemment avec le CLI .net core. Vous remarquerez que du code existe déjà.

Créez ensuite une [`module`](../language-reference/modules.md) appelée `PigLatin` et copiez la fonction `toPigLatin` que vous avez créée précédemment dans celle-ci :

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

Ce module doit être au-dessus de la fonction `main` et se trouve en dessous de la déclaration `open System`. Dans l’ordre des déclarations F#dans, vous devez définir la fonction avant de l’appeler dans un fichier.

Maintenant, dans la fonction `main`, appelez votre fonction de générateur latin de porc sur les arguments :

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

1. Pour obtenir les fonctionnalités d’édition de code de Ionide F# , vous devez enregistrer vos fichiers sur le disque et à l’intérieur d’un dossier qui est ouvert dans l’espace de travail Visual Studio code.
1. Si vous avez apporté des modifications à votre système ou si vous avez installé les composants requis de Ionide avec Visual Studio Code ouvrez, redémarrez Visual Studio Code.
1. Si vos répertoires de projet comportent des caractères non valides, Ionide peut ne pas fonctionner.  Si c’est le cas, renommez les répertoires de votre projet.
1. Si aucune des commandes Ionide ne fonctionne, vérifiez vos [combinaisons de touches de Visual Studio code](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) pour voir si vous les remplacez par accident.
1. Si Ionide est endommagé sur votre ordinateur et qu’aucun des éléments ci-dessus n’a résolu votre problème, essayez de supprimer le répertoire `ionide-fsharp` sur votre ordinateur et de réinstaller la suite de plug-in.
1. En cas d’échec du chargement d’un F# projet (la Explorateur de solutions l’affiche), cliquez avec le bouton droit sur le projet et cliquez sur **afficher les détails** pour obtenir plus d’informations de diagnostic.

Ionide est un projet open source créé et géré par les membres de F# la communauté. Signalez les problèmes et n’hésitez pas à contribuer au [référentiel ionide-vscode-FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).

Vous pouvez également demander de l’aide auprès des développeurs et F# de la communauté Ionide dans le [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Étapes suivantes :

Pour en savoir plus F# sur et les fonctionnalités du langage, consultez la [visite guidée F#de ](../tour.md).
