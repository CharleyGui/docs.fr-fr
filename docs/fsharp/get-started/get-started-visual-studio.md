---
title: Prise F# en main de dans Visual Studio
description: Découvrez comment utiliser F# avec Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 80b4fc5b7631eace719832fe32003cad578ead27
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552818"
---
# <a name="get-started-with-f-in-visual-studio"></a>Prise F# en main de dans Visual Studio

F#et les outils F# visuels sont pris en charge dans l’IDE de Visual Studio.

Pour commencer, assurez-vous que [Visual Studio est F#installé avec ](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Création d’une application console

L’un des projets les plus basiques dans Visual Studio est l’application console.  Voici comment faire.  Une fois Visual Studio ouvert :

1. Dans le menu **fichier** , pointez sur **nouveau**, puis choisissez **projet**.

2. Dans la boîte de dialogue Nouveau projet, sous **modèles**, vous devez voir **visuel F#** .  Choisissez cette valeur pour afficher F# les modèles.

3. Sélectionnez **application console .net Core** ou **application console**.

4. Choisissez le bouton **OK** pour créer le F# projet.  Vous devez maintenant voir un F# projet dans le Explorateur de solutions.

## <a name="writing-your-code"></a>Écriture de votre code

Commençons par écrire du code.  Assurez-vous que le fichier `Program.fs` est ouvert, puis remplacez son contenu par ce qui suit :

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Dans l’exemple de code précédent, une fonction `square` a été définie, qui prend une entrée nommée `x` et la multiplie par elle-même.  Étant F# donné que utilise l' [inférence de type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifié.  Le F# compilateur comprend les types où la multiplication est valide, et assigne un type à `x` en fonction de la façon dont `square` est appelé.  Si vous pointez sur `square`, vous devriez voir ce qui suit :

```fsharp
val square: x:int -> int
```

C’est ce que l’on appelle la signature de type de la fonction.  Il peut être lu comme suit : « Square est une fonction qui prend un entier nommé x et produit un entier ».  Notez que le compilateur a donné `square` le type de `int` pour le moment, car la multiplication n’est pas générique pour *tous les* types, mais plutôt générique dans un ensemble fermé de types.  Le F# compilateur a choisi `int` à ce stade, mais il ajustera la signature du type si vous appelez `square` avec un type d’entrée différent, tel qu’un `float`.

Une autre fonction, `main`, est définie, qui est décorée avec l’attribut `EntryPoint` pour F# indiquer au compilateur que l’exécution du programme doit démarrer.  Il suit la même convention que les autres [langages de programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code d’entier est retourné (généralement `0`).

C’est dans cette fonction que nous appelons la fonction `square` avec un argument de `12`.  Le F# compilateur assigne ensuite le type de `square` à `int -> int` (autrement dit, une fonction qui prend un `int` et produit une `int`).  L’appel à `printfn` est une fonction d’impression mise en forme qui utilise une chaîne de format, semblable aux langages de programmation de style C, des paramètres qui correspondent à ceux spécifiés dans la chaîne de format, puis imprime le résultat et une nouvelle ligne.

## <a name="running-your-code"></a>Exécution de votre code

Vous pouvez exécuter le code et afficher les résultats en appuyant sur **Ctrl**+**F5**.  Cela exécute le programme sans débogage et vous permet de voir les résultats.  Vous pouvez également choisir l’élément de menu de niveau supérieur de **débogage** dans Visual Studio et choisir **exécuter sans débogage**.

Vous devez maintenant voir les éléments suivants affichés dans la fenêtre de console affichée par Visual Studio :

```console
12 squared is 144!
```

Félicitations !  Vous avez créé votre premier F# projet dans Visual Studio, écrit une F# fonction a imprimé les résultats de l’appel de cette fonction, puis j’exécute le projet pour afficher des résultats.

## <a name="next-steps"></a>Étapes suivantes :

Si vous ne l’avez pas déjà fait, consultez la [Présentation de F# ](../tour.md), qui couvre certaines des fonctionnalités principales F# du langage.  Il vous donne une vue d’ensemble des fonctionnalités de F#et fournit de larges exemples de code que vous pouvez copier dans Visual Studio et exécuter.  Vous pouvez également en savoir plus sur F# la documentation dans la [ F# page d’accueil docs](../index.yml).

## <a name="see-also"></a>Voir aussi

- [Présentation de F#](../tour.md)
- [F#Référence du langage](../language-reference/index.md)
- [Inférence de type](../language-reference/type-inference.md)
- [Informations de référence sur les symboles et les opérateurs](../language-reference/symbol-and-operator-reference/index.md)
