---
title: Prise F# en main de dans Visual Studio
description: Découvrez comment utiliser F# avec Visual Studio.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337347"
---
# <a name="get-started-with-f-in-visual-studio"></a>Prise F# en main de dans Visual Studio

F#et les outils F# visuels sont pris en charge dans l’environnement de développement intégré (IDE) de Visual Studio.

Pour commencer, assurez-vous que [Visual Studio est F# installé avec la prise en charge](install-fsharp.md#install-f-with-visual-studio).

## <a name="create-a-console-application"></a>Créer une application console

L’un des projets les plus basiques dans Visual Studio est l’application console. Voici comment en créer un :

1. Ouvrez Visual Studio 2019.

2. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

3. Dans la page **créer un nouveau projet** , choisissez **F#** dans la liste langue.

4. Choisissez le modèle **application console (.net Core)** , puis choisissez **suivant**.

5. Dans la page **configurer votre nouveau projet** , entrez un nom dans la zone **nom du projet** . Choisissez ensuite **Créer**.

   Visual Studio crée le nouveau F# projet. Vous pouvez le voir dans la fenêtre de Explorateur de solutions.

## <a name="write-the-code"></a>Écrire le code

Commençons par écrire du code. Assurez-vous que le fichier `Program.fs` est ouvert, puis remplacez son contenu par ce qui suit :

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

L’exemple de code précédent définit une fonction appelée `square` qui prend une entrée nommée `x` et la multiplie par elle-même. Étant F# donné que utilise l' [inférence de type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifié. Le F# compilateur comprend les types où la multiplication est valide et assigne un type à `x` en fonction de la façon dont `square` est appelé. Si vous pointez sur `square`, vous devriez voir ce qui suit :

```fsharp
val square: x:int -> int
```

C’est ce que l’on appelle la signature de type de la fonction. Il peut être lu comme suit : « Square est une fonction qui accepte un entier nommé x et produit un entier ». Le compilateur a donné `square` le type de `int` pour l’instant ; Cela est dû au fait que la multiplication n’est pas générique pour *tous les* types, mais plutôt un ensemble fermé de types. Le F# compilateur ajuste la signature de type si vous appelez `square` avec un autre type d’entrée, tel qu’un `float`.

Une autre fonction, `main`, est définie, qui est décorée avec l’attribut `EntryPoint`. Cet attribut indique au F# compilateur que l’exécution du programme doit démarrer. Il suit la même convention que les autres [langages de programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code d’entier est retourné (généralement `0`).

Il se trouve dans la fonction de point d’entrée, `main`, que vous appelez la fonction `square` avec un argument de `12`. Le F# compilateur assigne ensuite le type de `square` à `int -> int` (autrement dit, une fonction qui prend un `int` et produit une `int`). L’appel à `printfn` est une fonction d’impression mise en forme qui utilise une chaîne de format et imprime le résultat (et une nouvelle ligne). La chaîne de format, similaire aux langages de programmation de style C, contient des paramètres (`%d`) qui correspondent aux arguments qui lui sont transmis, dans ce cas, `12` et `(square 12)`.

## <a name="run-the-code"></a>Exécuter le code

Vous pouvez exécuter le code et afficher les résultats en appuyant sur **Ctrl**+**F5**. Vous pouvez également choisir le > de **débogage** **exécuter sans débogage** à partir de la barre de menus de niveau supérieur. Cela exécute le programme sans débogage.

La sortie suivante s’affiche dans la fenêtre de console ouverte par Visual Studio :

```console
12 squared is: 144!
```

Félicitations ! Vous avez créé votre premier F# projet dans Visual Studio, écrit une F# fonction qui calcule et imprime une valeur, puis exécute le projet pour afficher les résultats.

## <a name="next-steps"></a>Étapes suivantes :

Si vous ne l’avez pas déjà fait, consultez la [Présentation de F# ](../tour.md), qui couvre certaines des fonctionnalités principales F# du langage. Il fournit une vue d’ensemble des fonctionnalités de et F# des exemples de code suffisamment larges que vous pouvez copier dans Visual Studio et exécuter.

> [!div class="nextstepaction"]
> [Présentation de F#](../tour.md)

## <a name="see-also"></a>Voir aussi

- [F#Référence du langage](../language-reference/index.md)
- [Inférence de type](../language-reference/type-inference.md)
- [Informations de référence sur les symboles et les opérateurs](../language-reference/symbol-and-operator-reference/index.md)
