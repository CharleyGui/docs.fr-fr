---
title: 'Prise en main de F # dans Visual Studio pour Mac'
description: 'Découvrez comment utiliser F # avec Visual Studio pour Mac.'
ms.date: 07/03/2018
ms.openlocfilehash: d2ad24ad18bb31419b39508f2cf555c82fbe2e0b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437995"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Prise en main de F # dans Visual Studio pour Mac

F # et les outils de Visual F# sont pris en charge dans l’IDE Visual Studio pour Mac. Vérifiez que vous avez [Visual Studio pour Mac installé](install-fsharp.md#install-f-with-visual-studio-for-mac).

## <a name="creating-a-console-application"></a>Création d’une application console

L’un des projets les plus basiques de Visual Studio pour Mac est l’application console.  Voici comment procéder.  Une fois Visual Studio pour Mac est ouvert :

1. Dans le menu **fichier** , pointez sur **nouvelle solution**.

2. Dans la boîte de dialogue Nouveau projet, il existe 2 modèles différents pour l’application console.  Il y en a un sous autre-> .NET qui cible le .NET Framework.  L’autre modèle est sous .NET Core-> application qui cible .NET Core.  L’un ou l’autre des modèles doit fonctionner dans le cadre de cet article.

3. Sous application console, remplacez C# par F # si nécessaire.  Choisissez le bouton **suivant** pour avancer !  

4. Donnez un nom à votre projet, puis choisissez les options souhaitées pour l’application.  Notez que le volet de visualisation sur le côté de l’écran affiche la structure de répertoires qui sera créée en fonction des options sélectionnées.  

5. Cliquez sur **Créer**.  Vous devez maintenant voir un projet F # dans le Explorateur de solutions.

## <a name="writing-your-code"></a>Écriture de votre code

Commençons par écrire du code.  Assurez-vous que le `Program.fs` fichier est ouvert, puis remplacez son contenu par ce qui suit :

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Dans l’exemple de code précédent, une fonction `square` a été définie et prend une entrée nommée `x` et la multiplie par elle-même.  Comme F # utilise l' [inférence de type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifié.  Le compilateur F # comprend les types où la multiplication est valide, et assigne un type à `x` en fonction de la méthode `square` appelée.  Si vous pointez sur `square` , les éléments suivants doivent s’afficher :

```console
val square: x:int -> int
```

C’est ce que l’on appelle la signature de type de la fonction.  Il peut être lu comme suit : « Square est une fonction qui prend un entier nommé x et produit un entier ».  Notez que le compilateur `square` a donné le `int` type pour le moment, car la multiplication n’est pas générique pour *tous les* types, mais plutôt générique dans un ensemble fermé de types.  Le compilateur F # `int` a choisi à ce stade, mais il ajuste la signature de type si vous appelez `square` avec un autre type d’entrée, tel qu’un `float` .

Une autre fonction, `main` , est définie, qui est décorée avec l' `EntryPoint` attribut pour indiquer au compilateur F # que l’exécution du programme doit démarrer.  Il suit la même convention que les autres [langages de programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code d’entier est retourné (en général `0` ).

C’est dans cette fonction que nous appelons la `square` fonction avec un argument de `12` .  Le compilateur F # affecte ensuite le type de `square` à la valeur `int -> int` (autrement dit, une fonction qui prend un `int` et produit un `int` ).  L’appel à `printfn` est une fonction d’impression mise en forme qui utilise une chaîne de format, semblable aux langages de programmation de style C, des paramètres qui correspondent à ceux spécifiés dans la chaîne de format, puis imprime le résultat et une nouvelle ligne.

## <a name="running-your-code"></a>Exécution de votre code

Vous pouvez exécuter le code et afficher les résultats en cliquant sur **exécuter** dans le menu de niveau supérieur, puis exécuter **sans débogage**.  Cette opération exécute le programme sans débogage et vous permet de voir les résultats.

Vous devez maintenant voir le code suivant affiché dans la fenêtre de console qui Visual Studio pour Mac affichée :

```console
12 squared is 144!
```

Félicitations !  Vous avez créé votre premier projet F # dans Visual Studio pour Mac, écrit une fonction F # imprimée les résultats de l’appel de cette fonction, et exécuté le projet pour afficher des résultats.

## <a name="using-f-interactive"></a>Utilisation de F# Interactive

L’une des meilleures fonctionnalités des outils de Visual F# dans Visual Studio pour Mac est la fenêtre de F# Interactive.  Elle vous permet d’envoyer du code à un processus dans lequel vous pouvez appeler ce code et consulter le résultat de manière interactive.

Pour commencer à l’utiliser, mettez en surbrillance la `square` fonction définie dans votre code.  Ensuite, cliquez sur **modifier** dans le menu de niveau supérieur.  Sélectionnez ensuite **Envoyer la sélection pour F# Interactive**.  Cela exécute le code dans la fenêtre de F# Interactive.  Vous pouvez également cliquer avec le bouton droit sur la sélection et choisir **Envoyer la sélection pour F# Interactive**.  La fenêtre F# Interactive doit s’afficher avec les éléments suivants :

```console
>

val square : x:int -> int

>
```

Cela montre la même signature de fonction pour la `square` fonction, que vous avez vu précédemment quand vous avez pointé sur la fonction.  Étant donné que `square` est maintenant défini dans le processus de F# Interactive, vous pouvez l’appeler avec des valeurs différentes :

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Cela exécute la fonction, lie le résultat à un nouveau nom `it` et affiche le type et la valeur de `it` .  Notez que vous devez terminer chaque ligne par `;;` .  C’est ainsi que F# Interactive sait quand l’appel de fonction est terminé.  Vous pouvez également définir de nouvelles fonctions dans F# Interactive :

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

La section ci-dessus définit une nouvelle fonction, `isOdd` , qui prend un `int` et vérifie si elle est impaire.  Vous pouvez appeler cette fonction pour voir ce qu’elle retourne avec des entrées différentes.  Vous pouvez appeler des fonctions dans les appels de fonction :

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

Il ne s’agit là que d’une idée de ce que vous pouvez faire avec F# Interactive.  Pour plus d’informations, consultez [programmation interactive avec F #](../tools/fsharp-interactive/index.md).

## <a name="next-steps"></a>Étapes suivantes

Si vous ne l’avez pas déjà fait, consultez la [visite guidée de f #](../tour.md), qui couvre certaines des fonctionnalités principales du langage f #.  Il vous donne une vue d’ensemble des fonctionnalités de F # et fournit de larges exemples de code que vous pouvez copier dans Visual Studio pour Mac et exécuter.  Vous pouvez également utiliser des ressources externes intéressantes, présentées dans le [Guide F #](../index.yml).

## <a name="see-also"></a>Voir aussi

- [Guide F#](../index.yml)
- [Présentation de F#](../tour.md)
- [Informations de référence du langage F#](../language-reference/index.md)
- [Inférence de type](../language-reference/type-inference.md)
- [Informations de référence sur les symboles et les opérateurs](../language-reference/symbol-and-operator-reference/index.md)
