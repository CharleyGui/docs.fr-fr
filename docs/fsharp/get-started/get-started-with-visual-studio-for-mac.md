---
title: Prise F# en main de dans Visual Studio pour Mac
description: Découvrez comment utiliser F# avec Visual Studio pour Mac.
ms.date: 07/03/2018
ms.openlocfilehash: cd45ab9c59cef76e4bf85a93f39d8e2ee063d200
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552366"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Prise F# en main de dans Visual Studio pour Mac

F#et les outils F# visuels sont pris en charge dans l’IDE Visual Studio pour Mac. Vérifiez que vous avez [Visual Studio pour Mac installé](install-fsharp.md#install-f-with-visual-studio-for-mac).

## <a name="creating-a-console-application"></a>Création d’une application console

L’un des projets les plus basiques de Visual Studio pour Mac est l’application console.  Voici comment faire.  Une fois Visual Studio pour Mac est ouvert :

1. Dans le menu **fichier** , pointez sur **nouvelle solution**.

2. Dans la boîte de dialogue Nouveau projet, il existe 2 modèles différents pour l’application console.  Il y en a un sous autre-> .NET qui cible le .NET Framework.  L’autre modèle est sous .NET Core-> application qui cible .NET Core.  L’un ou l’autre des modèles doit fonctionner dans le cadre de cet article.

3. Sous application console, remplacez C# par F# si nécessaire.  Choisissez le bouton **suivant** pour avancer !  

4. Donnez un nom à votre projet, puis choisissez les options souhaitées pour l’application.  Notez que le volet de visualisation sur le côté de l’écran affiche la structure de répertoires qui sera créée en fonction des options sélectionnées.  

5. Cliquez sur **Créer**.  Vous devez maintenant voir un F# projet dans le Explorateur de solutions.

## <a name="writing-your-code"></a>Écriture de votre code

Commençons par écrire du code.  Assurez-vous que le fichier `Program.fs` est ouvert, puis remplacez son contenu par ce qui suit :

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Dans l’exemple de code précédent, une fonction `square` a été définie, qui prend une entrée nommée `x` et la multiplie par elle-même.  Étant F# donné que utilise l' [inférence de type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifié.  Le F# compilateur comprend les types où la multiplication est valide, et assigne un type à `x` en fonction de la façon dont `square` est appelé.  Si vous pointez sur `square`, vous devriez voir ce qui suit :

```console
val square: x:int -> int
```

C’est ce que l’on appelle la signature de type de la fonction.  Il peut être lu comme suit : « Square est une fonction qui prend un entier nommé x et produit un entier ».  Notez que le compilateur a donné `square` le type de `int` pour le moment, car la multiplication n’est pas générique pour *tous les* types, mais plutôt générique dans un ensemble fermé de types.  Le F# compilateur a choisi `int` à ce stade, mais il ajustera la signature du type si vous appelez `square` avec un type d’entrée différent, tel qu’un `float`.

Une autre fonction, `main`, est définie, qui est décorée avec l’attribut `EntryPoint` pour F# indiquer au compilateur que l’exécution du programme doit démarrer.  Il suit la même convention que les autres [langages de programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code d’entier est retourné (généralement `0`).

C’est dans cette fonction que nous appelons la fonction `square` avec un argument de `12`.  Le F# compilateur assigne ensuite le type de `square` à `int -> int` (autrement dit, une fonction qui prend un `int` et produit une `int`).  L’appel à `printfn` est une fonction d’impression mise en forme qui utilise une chaîne de format, semblable aux langages de programmation de style C, des paramètres qui correspondent à ceux spécifiés dans la chaîne de format, puis imprime le résultat et une nouvelle ligne.

## <a name="running-your-code"></a>Exécution de votre code

Vous pouvez exécuter le code et afficher les résultats en cliquant sur **exécuter** dans le menu de niveau supérieur, puis exécuter **sans débogage**.  Cette opération exécute le programme sans débogage et vous permet de voir les résultats.

Vous devez maintenant voir le code suivant affiché dans la fenêtre de console qui Visual Studio pour Mac affichée :

```console
12 squared is 144!
```

Félicitations !  Vous avez créé votre premier F# projet dans Visual Studio pour Mac, écrit une F# fonction à l’impression des résultats de l’appel de cette fonction, puis j’exécute le projet pour afficher des résultats.

## <a name="using-f-interactive"></a>Utilisation F# du mode interactif

L’une des meilleures fonctionnalités des outils visuels F# dans Visual Studio pour Mac est la F# fenêtre interactive.  Elle vous permet d’envoyer du code à un processus dans lequel vous pouvez appeler ce code et consulter le résultat de manière interactive.

Pour commencer à l’utiliser, mettez en surbrillance la fonction `square` définie dans votre code.  Ensuite, cliquez sur **modifier** dans le menu de niveau supérieur.  Sélectionnez ensuite **Envoyer la sélection F# à interactive**.  Cela exécute le code dans la F# fenêtre interactive.  Vous pouvez également cliquer avec le bouton droit sur la sélection et choisir **Envoyer la F# sélection vers interactive**.  La F# fenêtre interactive doit s’afficher avec les éléments suivants :

```console
>

val square : x:int -> int

>
```

Cela montre la même signature de fonction pour la fonction `square`, que vous avez vu précédemment quand vous avez pointé sur la fonction.  Étant donné que `square` est maintenant défini F# dans le processus interactif, vous pouvez l’appeler avec des valeurs différentes :

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Cela exécute la fonction, lie le résultat à un nouveau nom `it`et affiche le type et la valeur de `it`.  Notez que vous devez mettre fin à chaque ligne avec `;;`.  C’est ainsi F# que l’interactivité sait quand l’appel de fonction est terminé.  Vous pouvez également définir de nouvelles fonctions F# dans Interactive :

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

L’expression ci-dessus définit une nouvelle fonction, `isOdd`, qui prend un `int` et vérifie si elle est impaire.  Vous pouvez appeler cette fonction pour voir ce qu’elle retourne avec des entrées différentes.  Vous pouvez appeler des fonctions dans les appels de fonction :

```console
> isOdd (square 15);;
val it : bool = true
```

Vous pouvez également utiliser l' [opérateur de redirection](../language-reference/symbol-and-operator-reference/index.md) pour canaliser la valeur dans les deux fonctions :

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

L’opérateur de redirection, et bien plus encore, sont traités dans les didacticiels ultérieurs.

Il ne s’agit là que d’une idée de ce F# que vous pouvez faire avec interactive.  Pour plus d’informations, consultez [programmation interactive avec F# ](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Étapes suivantes :

Si vous ne l’avez pas déjà fait, consultez la [Présentation de F# ](../tour.md), qui couvre certaines des fonctionnalités principales F# du langage.  Il vous donne une vue d’ensemble des fonctionnalités de F#et fournit de larges exemples de code que vous pouvez copier dans Visual Studio pour Mac et exécuter.  Vous pouvez également utiliser des ressources externes intéressantes, présentées dans le [ F# Guide](../index.yml).

## <a name="see-also"></a>Voir aussi

- [F#père](../index.yml)
- [Présentation de F#](../tour.md)
- [F#Référence du langage](../language-reference/index.md)
- [Inférence de type](../language-reference/type-inference.md)
- [Informations de référence sur les symboles et les opérateurs](../language-reference/symbol-and-operator-reference/index.md)
