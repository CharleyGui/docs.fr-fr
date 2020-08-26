---
title: Fonctions de première classe
description: 'En savoir plus sur les fonctions de première classe et leur importance pour la programmation fonctionnelle en F #.'
ms.date: 10/29/2018
ms.openlocfilehash: 1dc8eae1655187282f05bf4e9501ecc8a17deba8
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810909"
---
# <a name="first-class-functions"></a>Fonctions de première classe

Une caractéristique de définition des langages de programmation fonctionnelle est l’élévation de fonctions à l’état de première classe. Vous devez être en mesure de faire avec une fonction tout ce que vous pouvez faire avec les valeurs des autres types intégrés et être en mesure de le faire avec un degré comparable d’effort.

Les mesures typiques de l’état de première classe sont les suivantes :

- Pouvez-vous lier des fonctions à des identificateurs ? Autrement dit, pouvez-vous leur attribuer des noms ?

- Pouvez-vous stocker des fonctions dans des structures de données, comme dans une liste ?

- Pouvez-vous passer une fonction en tant qu’argument dans un appel de fonction ?

- Pouvez-vous retourner une fonction à partir d’un appel de fonction ?

Les deux dernières mesures définissent ce que l’on appelle des *opérations d’ordre supérieur* ou *des fonctions d’ordre supérieur*. Les fonctions d’ordre supérieur acceptent des fonctions comme arguments et retournent des fonctions comme valeur d’appels de fonction. Ces opérations prennent en charge un tel mainstays de la programmation fonctionnelle comme fonctions de mappage et la composition de fonctions.

## <a name="give-the-value-a-name"></a>Donnez un nom à la valeur

Si une fonction est une valeur de première classe, vous devez être en mesure de la nommer, tout comme vous pouvez nommer des entiers, des chaînes et d’autres types intégrés. Pour ce faire, vous pouvez faire appel à la documentation sur la programmation fonctionnelle pour lier un identificateur à une valeur. F # utilise des [ `let` liaisons](../language-reference/functions/let-bindings.md) pour lier les noms aux valeurs : `let <identifier> = <value>` . Le code suivant illustre deux exemples.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

Vous pouvez nommer une fonction tout aussi facilement. L’exemple suivant définit une fonction nommée `squareIt` en liant l’identificateur `squareIt` à l' [expression lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n` . `squareIt`La fonction a un paramètre, `n` , et retourne le carré de ce paramètre.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

F # fournit la syntaxe plus concise suivante pour obtenir le même résultat avec moins de frappes.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

Les exemples qui suivent utilisent principalement le premier style, `let <function-name> = <lambda-expression>` , pour mettre en évidence les similarités entre la déclaration de fonctions et la déclaration d’autres types de valeurs. Toutefois, toutes les fonctions nommées peuvent également être écrites avec la syntaxe concise. Certains des exemples sont écrits d’une manière ou d’une autre.

## <a name="store-the-value-in-a-data-structure"></a>Stocker la valeur dans une structure de données

Une valeur de première classe peut être stockée dans une structure de données. Le code suivant montre des exemples qui stockent des valeurs dans des listes et dans des tuples.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

Pour vérifier qu’un nom de fonction stocké dans un tuple correspond en fait à une fonction, l’exemple suivant utilise `fst` les `snd` opérateurs et pour extraire le premier et le deuxième élément du Tuple `funAndArgTuple` . Le premier élément du tuple est `squareIt` et le deuxième élément est `num` . L’identificateur `num` est lié dans un exemple précédent à l’entier 10, un argument valide pour la `squareIt` fonction. La deuxième expression applique le premier élément du tuple au deuxième élément du tuple : `squareIt num` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

De même, tout comme l’identificateur `num` et l’entier 10 peuvent être utilisés indifféremment, l’identificateur et l' `squareIt` expression lambda peuvent être utilisés `fun n -> n * n` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>Passer la valeur en tant qu’argument

Si une valeur a un état de première classe dans une langue, vous pouvez la passer en tant qu’argument à une fonction. Par exemple, il est courant de passer des entiers et des chaînes en tant qu’arguments. Le code suivant affiche les entiers et les chaînes passés comme arguments en F #.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

Si les fonctions ont l’état de première classe, vous devez être en mesure de les passer comme arguments de la même façon. N’oubliez pas qu’il s’agit de la première caractéristique des fonctions d’ordre supérieur.

Dans l’exemple suivant, la fonction `applyIt` a deux paramètres, `op` et `arg` . Si vous envoyez dans une fonction avec un paramètre pour `op` et un argument approprié pour la fonction à `arg` , la fonction retourne le résultat de l’application de `op` à `arg` . Dans l’exemple suivant, l’argument de fonction et l’argument entier sont envoyés de la même manière, à l’aide de leurs noms.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

La possibilité d’envoyer une fonction en tant qu’argument à une autre fonction sous-tend des abstractions courantes dans des langages de programmation fonctionnelle, tels que des opérations de mappage ou de filtre. Une opération de mappage, par exemple, est une fonction d’ordre supérieur qui capture le calcul partagé par des fonctions qui parcourent une liste, effectuent une opération sur chaque élément, puis renvoient une liste des résultats. Vous pouvez incrémenter chaque élément dans une liste d’entiers, ou pour placer chaque élément dans une liste de chaînes en majuscules. La partie sujette aux erreurs du calcul est le processus récursif qui parcourt la liste et génère une liste des résultats à retourner. Cette partie est capturée dans la fonction de mappage. Tout ce que vous devez écrire pour une application particulière est la fonction que vous souhaitez appliquer à chaque élément de la liste (ajout, élévation, modification de la casse). Cette fonction est envoyée en tant qu’argument à la fonction de mappage, de la même façon que `squareIt` `applyIt` dans l’exemple précédent.

F # fournit des méthodes cartographiques pour la plupart des types de collections, y compris les [listes](../language-reference/lists.md), les [tableaux](../language-reference/arrays.md)et les [séquences](../language-reference/sequences.md). Les exemples suivants utilisent des listes. La syntaxe est `List.map <the function> <the list>`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

Pour plus d’informations, consultez [listes](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Retourne la valeur d’un appel de fonction

Enfin, si une fonction a l’état de première classe dans un langage, vous devez être en mesure de la retourner comme valeur d’un appel de fonction, de la même façon que vous retournez d’autres types, tels que des entiers et des chaînes.

Les appels de fonction suivants retournent des entiers et les affichent.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

L’appel de fonction suivant retourne une chaîne.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

L’appel de fonction suivant, déclaré Inline, retourne une valeur booléenne. La valeur affichée est `True` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

La possibilité de retourner une fonction comme valeur d’un appel de fonction est la deuxième caractéristique des fonctions d’ordre supérieur. Dans l’exemple suivant, `checkFor` est défini comme une fonction qui accepte un argument, `item` , et retourne une nouvelle fonction comme sa valeur. La fonction retournée prend une liste comme argument, `lst` , et recherche `item` dans `lst` . Si `item` est présent, la fonction retourne `true` . Si `item` n’est pas présent, la fonction retourne `false` . Comme dans la section précédente, le code suivant utilise une fonction de liste fournie, [List. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists), pour effectuer une recherche dans la liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

Le code suivant utilise `checkFor` pour créer une fonction qui accepte un argument, une liste et recherche 7 dans la liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

L’exemple suivant utilise l’état de première classe des fonctions en F # pour déclarer une fonction, `compose` , qui retourne une composition de deux arguments de fonction.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> Pour une version encore plus concise, consultez la section suivante, « fonctions curryfiée ».

Le code suivant envoie deux fonctions comme arguments à `compose` , qui acceptent toutes deux un seul argument du même type. La valeur de retour est une nouvelle fonction qui est une composition des deux arguments de fonction.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> F # fournit deux opérateurs, `<<` et `>>` , qui composent des fonctions. Par exemple, `let squareAndDouble2 = doubleIt << squareIt` est équivalent à `let squareAndDouble = compose doubleIt squareIt` dans l’exemple précédent.

L’exemple suivant de retour d’une fonction comme valeur d’un appel de fonction crée un jeu d’estimation simple. Pour créer un jeu, appelez `makeGame` avec la valeur que vous souhaitez qu’une personne devine soit envoyée pour `target` . La valeur de retour de la fonction `makeGame` est une fonction qui accepte un argument (l’estimation) et indique si l’estimation est correcte.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

Le code suivant appelle `makeGame` , en envoyant la valeur `7` pour `target` . L’identificateur `playGame` est lié à l’expression lambda retournée. Par conséquent, `playGame` est une fonction qui prend comme valeur un argument pour `guess` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>Fonctions curryfiée

La plupart des exemples de la section précédente peuvent être écrits de façon plus concise en tirant parti de la *curryfication* implicite dans les déclarations de fonction F #. La curryfication est un processus qui transforme une fonction qui a plusieurs paramètres en une série de fonctions incorporées, chacune d’elles ayant un seul paramètre. En F #, les fonctions qui ont plusieurs paramètres sont curryfiée par nature. Par exemple, `compose` dans la section précédente, vous pouvez écrire comme indiqué dans le style concis suivant, avec trois paramètres.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

Toutefois, le résultat est une fonction d’un paramètre qui retourne une fonction d’un paramètre qui, à son tour, retourne une autre fonction d’un paramètre, comme indiqué dans `compose4curried` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

Vous pouvez accéder à cette fonction de plusieurs façons. Chacun des exemples suivants retourne et affiche 18. Vous pouvez remplacer `compose4` par `compose4curried` dans l’un des exemples.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

Pour vérifier que la fonction fonctionne toujours comme auparavant, réessayez les cas de test d’origine.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> Vous pouvez restreindre la curryfication en encadrant les paramètres dans les tuples. Pour plus d’informations, consultez « modèles de paramètres » dans [paramètres et arguments](../language-reference/parameters-and-arguments.md).

L’exemple suivant utilise une curryfication implicite pour écrire une version plus petite de `makeGame` . Les détails de la façon dont `makeGame` construit et retourne la `game` fonction sont moins explicites dans ce format, mais vous pouvez vérifier en utilisant les cas de test d’origine que le résultat est le même.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

Pour plus d’informations sur la curryfication, consultez « application partielle d’arguments » dans les [fonctions](../language-reference/functions/index.md).

## <a name="identifier-and-function-definition-are-interchangeable"></a>L’identificateur et la définition de fonction sont interchangeables

Le nom de la variable `num` dans les exemples précédents correspond à l’entier 10, et il n’est pas surprenant que `num` , si est valide, 10 soit également valide. Il en va de même pour les identificateurs de fonction et leurs valeurs : partout où le nom de la fonction peut être utilisé, l’expression lambda à laquelle elle est liée peut être utilisée.

L’exemple suivant définit une `Boolean` fonction appelée `isNegative` , puis utilise le nom de la fonction et la définition de la fonction de façon interchangeable. Les trois exemples suivants retournent et affichent `False` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

Pour aller plus loin, remplacez la valeur `applyIt` de pour `applyIt` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>Les fonctions sont des valeurs de première classe en F\#

Les exemples des sections précédentes montrent que les fonctions en F # satisfont les critères pour les valeurs de première classe en F # :

- Vous pouvez lier un identificateur à une définition de fonction.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- Vous pouvez stocker une fonction dans une structure de données.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- Vous pouvez passer une fonction comme argument.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- Vous pouvez retourner une fonction comme valeur d’un appel de fonction.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

Pour plus d’informations sur F #, consultez la référence sur le [langage f #](../language-reference/index.md).

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Le code suivant contient tous les exemples de cette rubrique.

### <a name="code"></a>Code

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>Voir aussi

- [Listes](../language-reference/lists.md)
- [Tuples](../language-reference/tuples.md)
- [Fonctions](../language-reference/functions/index.md)
- [`let` Liaisons](../language-reference/functions/let-bindings.md)
- [Expressions lambda : `fun` mot clé](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
