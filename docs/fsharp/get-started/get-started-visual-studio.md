---
title: Prise F# en main de dans Visual Studio
description: Découvrez comment utiliser F# avec Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 24c9a81cfa61dc904db9b2213224677696d7eb9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629766"
---
# <a name="get-started-with-f-in-visual-studio"></a>Prise F# en main de dans Visual Studio

F#et les outils F# visuels sont pris en charge dans l’IDE de Visual Studio.

Pour commencer, assurez-vous que [Visual Studio est F#installé avec ](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Création d’une application console

L’un des projets les plus basiques dans Visual Studio est l’application console.  Voici comment faire.  Une fois Visual Studio ouvert:

1. Dans le menu **fichier** , pointez sur **nouveau**, puis choisissez **projet**.

2. Dans la boîte de dialogue Nouveau projet, sous **modèles**, vous devez voir **visuel F#** .  Choisissez cette valeur pour afficher F# les modèles.

3. Sélectionnez **application console .net Core** ou **application console**.

4. Choisissez le bouton **OK** pour créer le F# projet.  Vous devez maintenant voir un F# projet dans le Explorateur de solutions.

## <a name="writing-your-code"></a>Écriture de votre code

Commençons par écrire du code.  Assurez-vous `Program.fs` que le fichier est ouvert, puis remplacez son contenu par ce qui suit:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Dans l’exemple de code précédent, une `square` fonction a été définie et prend une entrée `x` nommée et la multiplie par elle-même.  Étant F# donné que utilise l’inférence de [type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifié.  Le F# compilateur comprend les types où la multiplication est valide, et assigne un type à `x` en fonction de `square` la méthode appelée.  Si vous pointez `square`sur, les éléments suivants doivent s’afficher:

```fsharp
val square: x:int -> int
```

C’est ce que l’on appelle la signature de type de la fonction.  Il peut être lu comme suit: «Square est une fonction qui accepte un entier nommé x et produit un entier «».  Notez que le compilateur a `square` donné `int` le type pour le moment, car la multiplication n’est pas générique pour *tous les* types, mais plutôt générique dans un ensemble fermé de types.  Le F# compilateur a `int` choisi à ce stade, mais il ajuste la signature de type si `square` vous appelez avec un autre type d’entrée, `float`tel qu’un.

Une autre fonction `main`,, est définie, qui est décorée `EntryPoint` avec l’attribut pour F# indiquer au compilateur que l’exécution du programme doit démarrer.  Il suit la même convention que les autres langages de [programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code `0`d’entier est retourné (en général).

C’est dans cette fonction que nous appelons la `square` fonction avec un argument de `12`.  Le F# compilateur assigne ensuite le type de `square` à la `int -> int` valeur (autrement dit, une fonction qui prend `int` un et produit `int`un).  L’appel à `printfn` est une fonction d’impression mise en forme qui utilise une chaîne de format, semblable aux langages de programmation de style C, des paramètres qui correspondent à ceux spécifiés dans la chaîne de format, puis imprime le résultat et une nouvelle ligne.

## <a name="running-your-code"></a>Exécution de votre code

Vous pouvez exécuter le code et afficher les résultats en appuyant sur **CTRL**+**F5**.  Cela exécute le programme sans débogage et vous permet de voir les résultats.  Vous pouvez également choisir l’élément de menu de niveau supérieur de débogage dans Visual Studio et choisir **exécuter sans débogage**.

Vous devez maintenant voir les éléments suivants affichés dans la fenêtre de console affichée par Visual Studio:

```
12 squared is 144!
```

Félicitations !  Vous avez créé votre premier F# projet dans Visual Studio, écrit une F# fonction a imprimé les résultats de l’appel de cette fonction, puis j’exécute le projet pour afficher des résultats.

## <a name="next-steps"></a>Étapes suivantes

Si vous ne l’avez pas déjà fait, consultez la [Présentation de F# ](../tour.md), qui couvre certaines des fonctionnalités principales F# du langage.  Il vous donne une vue d’ensemble des fonctionnalités de F#et fournit de larges exemples de code que vous pouvez copier dans Visual Studio et exécuter.  Vous pouvez également utiliser des ressources externes intéressantes, présentées dans le [ F# Guide](../index.md).

## <a name="see-also"></a>Voir aussi

- [Présentation de F#](../tour.md)
- [F#Référence du langage](../language-reference/index.md)
- [Inférence de type](../language-reference/type-inference.md)
- [Informations de référence sur les symboles et les opérateurs](../language-reference/symbol-and-operator-reference/index.md)
