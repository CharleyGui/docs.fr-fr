---
title: Prise F# en main de dans Visual Studio code
description: Découvrez comment utiliser F# avec Visual Studio code et la suite de plug-in Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2fa0518488d37b2130aaba96028ac92dac77eb97
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082985"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Prise F# en main de dans Visual Studio code

Vous pouvez écrire F# en [Visual Studio code](https://code.visualstudio.com) avec le [plug-in Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) pour bénéficier d’une excellente expérience de l’environnement de développement intégré (IDE) multiplateforme et légère avec IntelliSense et des refactorisations de code de base. Visitez [Ionide.IO](http://ionide.io) pour en savoir plus sur le plug-in.

Pour commencer, assurez-vous que [ F# et le plug-in Ionide sont correctement installés](install-fsharp.md#install-f-with-visual-studio-code).

> [!NOTE]
> Ionide génère des projets F# .NET Framework, pas dotnet Core, qui peuvent avoir des problèmes de compatibilité entre plateformes. Si vous exécutez sur **Linux** ou **OSX**, il est plus simple de commencer à utiliser les outils en [ligne de commande](get-started-command-line.md).

## <a name="creating-your-first-project-with-ionide"></a>Création de votre premier projet avec Ionide

Pour créer un nouveau F# projet, ouvrez Visual Studio code dans un nouveau dossier (vous pouvez le nommer comme vous le souhaitez).

Ensuite, ouvrez la palette de commandes (**afficher > palette de commandes**) et tapez ce qui suit :

```console
> F# new project
```

Ce projet est alimenté par le projet [Forge](https://github.com/fsharp-editing/Forge) .

> [!NOTE]
> Si vous ne voyez pas les options de modèle, essayez d’actualiser les modèles en exécutant la commande `>F#: Refresh Project Templates`suivante dans la palette de commandes :.

Sélectionnez «F#: Nouveau projet» en appuyant sur **entrée**. Vous accédez à l’étape suivante, qui permet de sélectionner un modèle de projet.

Sélectionnez le `classlib` modèle et appuyez sur **entrée**.

Sélectionnez ensuite un répertoire dans lequel créer le projet. Si vous la laissez vide, le répertoire actif est utilisé.

Enfin, nommez votre projet à l’étape finale. F#utilise la [casse Pascal](http://c2.com/cgi/wiki?PascalCase) pour les noms de projet. Cet article utilise `ClassLibraryDemo` comme nom. Une fois que vous avez entré le nom souhaité pour votre projet, appuyez sur **entrée**.

Si vous avez suivi l’étape précédente, vous devez obtenir l’espace de travail Visual Studio Code sur le côté gauche pour qu’il apparaisse comme suit :

1. Le F# projet lui-même, `ClassLibraryDemo` sous le dossier.
2. Structure de répertoire correcte pour l’ajout de [`Paket`](https://fsprojects.github.io/Paket/)packages via.
3. Script de génération multiplateforme avec [`FAKE`](https://fsharp.github.io/FAKE/).
4. `paket.exe` Fichier exécutable qui peut extraire des packages et résoudre les dépendances pour vous.
5. Un `.gitignore` fichier si vous souhaitez ajouter ce projet au contrôle de code source git.

## <a name="writing-some-code"></a>Écrire du code

Ouvrez le dossier *ClassLibraryDemo* .  Les fichiers suivants doivent s’afficher :

1. `ClassLibraryDemo.fs`, un F# fichier d’implémentation avec une classe définie.
2. `ClassLibraryDemo.fsproj`, fichier F# projet utilisé pour générer ce projet.
3. `Script.fsx`, un F# fichier de script qui charge le fichier source.
4. `paket.references`, un fichier Paket qui spécifie les dépendances du projet.

Ouvrez `Script.fsx`et ajoutez le code suivant à la fin de l’opération :

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Cette fonction convertit un mot en une forme de [porc latin](https://en.wikipedia.org/wiki/Pig_Latin). L’étape suivante consiste à l’évaluer à F# l’aide de l’interactivité (FSI).

Mettez en surbrillance la fonction entière (il doit s’agir de 11 lignes). Une fois qu’elle est mise en surbrillance, maintenez la touche **ALT** enfoncée et appuyez sur **entrée**. Vous remarquerez une fenêtre contextuelle ci-dessous, qui devrait afficher ce qui suit :

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
> Comme vous l’avez peut-être remarqué, les lignes du FSI se `;;`terminent par. Cela est dû au fait que FSI vous permet d’entrer plusieurs lignes. Le `;;` à la fin permet à la FSI de savoir à quel moment le code est terminé.

## <a name="explaining-the-code"></a>Explication du code

Si vous n’êtes pas sûr de ce que fait le code, voici une procédure pas à pas.

Comme vous pouvez le voir `toPigLatin` , est une fonction qui prend un mot comme entrée et la convertit en une représentation porc-latin de ce mot. Les règles applicables sont les suivantes :

Si le premier caractère d’un mot commence par une voyelle, ajoutez « Ouais » à la fin du mot. S’il ne commence pas par une voyelle, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.

Vous avez peut-être remarqué ce qui suit dans FSI :

```fsharp
val toPigLatin : word:string -> string
```

Il s’agit d’une fonction qui prend une `string` entrée comme entrée (appelée `word`) et retourne une autre `string`. `toPigLatin` C’est ce que l’on appelle la [signature de type de la fonction](https://fsharpforfunandprofit.com/posts/function-signatures/), un F# élément fondamental de la clé F# de la compréhension du code. Vous remarquerez également cela si vous pointez sur la fonction dans Visual Studio Code.

Dans le corps de la fonction, vous remarquerez deux parties distinctes :

1. Une fonction interne, appelée `isVowel`, qui détermine si un caractère donné (`c`) est une voyelle en vérifiant si elle correspond à l’un des modèles fournis via des [critères spéciaux](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) Expression qui vérifie si le premier caractère est une voyelle et construit une valeur de retour à partir des caractères d’entrée en fonction de si le premier caractère est une voyelle ou non :

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Le déroulement de `toPigLatin` est donc :

Vérifie si le premier caractère du mot d’entrée est une voyelle. Si c’est le cas, attachez « Ouais » à la fin du mot. Dans le cas contraire, déplacez le premier caractère jusqu’à la fin du mot et ajoutez « ay » à celui-ci.

Il y a une dernière chose à noter : il n’existe pas d’instruction explicite à retourner à partir de la fonction, contrairement à de nombreux autres langages. Cela est dû F# au fait que est basé sur une expression et que la dernière expression dans le corps d’une fonction est la valeur de retour. Étant `if..then..else` donné que est lui-même une expression, `then` le corps du bloc `else` ou le corps du bloc sont retournés en fonction de la valeur d’entrée.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Déplacement de votre code de script dans le fichier d’implémentation

Les sections précédentes de cet article ont montré une première étape courante dans F# l’écriture de code : écriture d’une fonction initiale et exécution interactive de cette dernière avec le FSI. C’est ce que l’on appelle le développement basé sur REPL, où [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) signifie « lecture-évaluation-impression Loop ». C’est un excellent moyen d’expérimenter les fonctionnalités jusqu’à ce que vous ayez un peu de travail.

L’étape suivante du développement piloté par REPL consiste à déplacer le code de travail F# dans un fichier d’implémentation. Il peut ensuite être compilé par le F# compilateur dans un assembly qui peut être exécuté.

Pour commencer, ouvrez `ClassLibraryDemo.fs`.  Vous remarquerez que du code existe déjà. Poursuivez et supprimez la définition de classe, mais veillez à [`namespace`](../language-reference/namespaces.md) conserver la déclaration en haut.

Ensuite, créez un nouveau [`module`](../language-reference/modules.md) nommé `PigLatin` et copiez `toPigLatin` -y la fonction comme suit :

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Ensuite, rouvrez le `Script.fsx` fichier et supprimez la fonction entière `toPigLatin` , mais veillez à conserver les deux lignes suivantes dans le fichier :

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

Sélectionnez les deux lignes de texte et appuyez sur Alt + Entrée pour exécuter ces lignes dans FSI. Celles-ci chargent le contenu de la bibliothèque latin de porc dans le `open` processus `ClassLibraryDemo` FSI et l’espace de noms afin que vous ayez accès aux fonctionnalités.

Ensuite, dans la fenêtre FSI, appelez la fonction avec le `PigLatin` module que vous avez défini précédemment :

```console
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Opération réussie Vous recevez les mêmes résultats qu’avant, mais maintenant chargé à partir F# d’un fichier d’implémentation. La principale différence réside dans le F# fait que les fichiers sources sont compilés dans des assemblys qui peuvent être exécutés n’importe où, pas seulement dans le FSI.

## <a name="summary"></a>Récapitulatif

Dans cet article, vous avez appris ce qui suit :

1. Comment configurer Visual Studio Code avec Ionide.
2. Comment créer votre premier F# projet avec Ionide.
3. Comment utiliser F# les scripts pour écrire votre première F# fonction dans Ionide, puis l’exécuter dans le FSI.
4. Comment migrer votre code de script F# vers la source, puis appeler ce code à partir de FSI.

Vous êtes maintenant prêt à écrire un plus F# grand nombre de code à l’aide de Visual Studio code et Ionide.

## <a name="troubleshooting"></a>Résolution des problèmes

Voici quelques façons de résoudre certains problèmes que vous pouvez rencontrer :

1. Pour obtenir les fonctionnalités d’édition de code de Ionide F# , vous devez enregistrer vos fichiers sur le disque et à l’intérieur d’un dossier qui est ouvert dans l’espace de travail Visual Studio code.
2. Si vous avez apporté des modifications à votre système ou si vous avez installé les composants requis de Ionide avec Visual Studio Code ouvrez, redémarrez Visual Studio Code.
3. Vérifiez que vous pouvez utiliser le F# compilateur et F# interactif à partir de la ligne de commande sans un chemin d’accès complet. Pour ce faire, vous pouvez `fsc` taper dans une ligne de commande F# pour le compilateur `fsi` , `fsharpi` et ou pour F# les outils visuels sur Windows et mono sur Mac/Linux, respectivement.
4. Si vos répertoires de projet comportent des caractères non valides, Ionide peut ne pas fonctionner.  Si c’est le cas, renommez les répertoires de votre projet.
5. Si aucune des commandes Ionide ne fonctionne, vérifiez les [combinaisons de touches](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) de votre Visual Studio code pour voir si vous les remplacez par accident.
6. Si Ionide est endommagé sur votre ordinateur et qu’aucun des éléments ci-dessus n’a résolu votre problème `ionide-fsharp` , essayez de supprimer le répertoire sur votre ordinateur et de réinstaller la suite de plug-in.

Ionide est un projet open source créé et géré par les membres de F# la communauté. Signalez les [problèmes et n’hésitez pas à contribuer au Ionide-VSCode : Référentiel GitHub FSharp](https://github.com/ionide/ionide-vscode-fsharp).

Si vous avez un problème à signaler, suivez [les instructions pour obtenir les journaux à utiliser lors du signalement d’un problème](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Vous pouvez également demander de l’aide auprès des développeurs et F# de la communauté Ionide dans le [canal Ionide Gitter](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus F# sur et les fonctionnalités du langage, consultez la [visite guidée F#de ](../tour.md).
