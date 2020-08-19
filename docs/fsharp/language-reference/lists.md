---
title: Listes
description: 'En savoir plus sur les listes F #, une série immuable et ordonnée d’éléments du même type.'
ms.date: 08/13/2020
ms.openlocfilehash: 16d7195039d25cf63630f5cc3be6563b1bf45c44
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559165"
---
# <a name="lists"></a>Listes

En F#, une liste est une série immuable et ordonnée d'éléments du même type. Pour effectuer des opérations de base sur les listes, utilisez les fonctions dans le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).

## <a name="creating-and-initializing-lists"></a>Création et initialisation de listes

Vous pouvez définir une liste en répertoriant de manière explicite les éléments, séparés par des points-virgules et placés entre crochets, comme indiqué dans la ligne de code suivante.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Vous pouvez également insérer des sauts de ligne entre les éléments, les points-virgules étant facultatifs dans ce cas. Cette syntaxe produit du code plus lisible quand les expressions d'initialisation des éléments sont plus longues, ou quand vous souhaitez ajouter un commentaire pour chaque élément.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Généralement, tous les éléments de liste doivent être du même type. Il existe une exception : une liste dont les éléments sont spécifiés comme type de base peut comporter des éléments qui sont des types dérivés. L'exemple suivant est acceptable, car `Button` et `CheckBox` dérivent de `Control`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Vous pouvez également définir des éléments de liste à l'aide d'une plage indiquée par des entiers séparés par l'opérateur de plage (`..`), comme illustré dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Une liste vide est spécifiée par une paire de crochets vide.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Vous pouvez également utiliser une expression de séquence pour créer une liste. Pour plus d’informations, consultez [expressions de séquence](sequences.md#sequence-expressions) . Par exemple, le code suivant crée une liste d'entiers au carré, de 1 à 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Opérateurs utilisés avec les listes

Vous pouvez joindre des éléments à une liste en utilisant l'opérateur (cons) `::`. Si `list1` est `[2; 3; 4]`, le code suivant crée `list2` sous la forme `[100; 2; 3; 4]`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Vous pouvez concaténer des listes qui présentent des types compatibles à l'aide de l'opérateur `@`, comme dans le code suivant. Si `list1` est `[2; 3; 4]` et `list2` est `[100; 2; 3; 4]`, ce code crée `list3` sous la forme `[2; 3; 4; 100; 2; 3; 4]`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Les fonctions permettant d’effectuer des opérations sur des listes sont disponibles dans le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).

En F#, les listes étant immuables, toute opération de changement a pour effet de générer de nouvelles listes au lieu de modifier les listes existantes.

Les listes en F # sont implémentées en tant que listes à liaison unique, ce qui signifie que les opérations qui accèdent uniquement au début de la liste sont O (1) et que l’accès à l’élément est O (*n*).

## <a name="properties"></a>Propriétés

Le type de liste prend en charge les propriétés suivantes :

|Propriété|Type|Description|
|--------|----|-----------|
|[Siège](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head)|`'T`|Premier élément.|
|[Vide](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Empty)|`'T list`|Propriété statique qui retourne une liste vide du type approprié.|
|[IsEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#IsEmpty)|`bool`|`true` si la liste ne comporte aucun élément.|
|[Item](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Item)|`'T`|Élément au niveau de l'index spécifié (de base zéro).|
|[Longueur](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Length)|`int`|Nombre d'éléments.|
|[Tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail)|`'T list`|Liste sans premier élément.|

Voici quelques exemples d'utilisation de ces propriétés.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>Utilisation de listes

La programmation à l'aide de listes vous permet d'effectuer des opérations complexes avec peu de code. Cette section décrit des opérations courantes sur des listes qui sont importantes pour la programmation fonctionnelle.

### <a name="recursion-with-lists"></a>Récursivité avec des listes

Les listes sont particulièrement adaptées aux techniques de programmation récursive. Prenons en compte une opération à effectuer sur chaque élément d'une liste. Vous pouvez procéder de manière récursive en effectuant l'opération sur le début de la liste, puis en passant à la fin de la liste, qui est une liste plus petite comprenant la liste d'origine sans le premier élément, et en revenant au niveau suivant de récursivité.

Pour écrire ce type de fonction récursive, utilisez l’opérateur cons (`::`) dans les critères spéciaux, qui vous permet de séparer le début d’une liste de sa fin.

L’exemple de code suivant indique comment utiliser les critères spéciaux pour implémenter une fonction récursive qui exécute des opérations sur une liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Le code précédent fonctionne bien dans le cas de petites listes, mais dans le cas de listes plus longues, il peut entraîner un dépassement de capacité de la pile. Le code suivant améliore le précédent à l’aide d’un argument d’accumulation, technique standard utilisée avec les fonctions récursives. L'argument d'accumulation rend la fin de la fonction récursive, ce qui permet de contenir l'espace de pile.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

La fonction `RemoveAllMultiples` est récursive et accepte deux listes. La première liste contient les nombres dont les multiples seront supprimés ; la seconde liste contient les nombres à supprimer. Le code de l’exemple suivant utilise cette fonction récursive pour éliminer tous les nombres non premiers d’une liste, générant ainsi une liste de nombres premiers.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

La sortie se présente comme suit :

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Fonctions de module

Le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html) fournit des fonctions qui accèdent aux éléments d’une liste. L'élément de début offre l'accès le plus simple et rapide. Utilisez l' [en-tête](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) de propriété ou la fonction de module [List. Head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head). Vous pouvez accéder à la fin d’une liste à l’aide de la propriété [tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) ou de la fonction [List. tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) . Pour rechercher un élément par index, utilisez la fonction [List. nth](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) . `List.nth` parcourt la liste. Par conséquent, il s’agit de O (*n*). Si votre code utilise fréquemment `List.nth`, envisagez d'utiliser un tableau à la place d'une liste. L'accès aux éléments des tableaux est O(1).

### <a name="boolean-operations-on-lists"></a>Opérations booléennes sur des listes

La fonction [List. IsEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty) détermine si une liste contient des éléments.

La fonction [List. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists) applique un test booléen aux éléments d’une liste et retourne `true` si un élément satisfait au test. [List. exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) est similaire, mais fonctionne sur des paires d’éléments successifs dans deux listes.

Le code suivant montre l'utilisation de `List.exists`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

La sortie se présente comme suit :

```console
For list [0; 1; 2; 3], contains zero is true
```

L'exemple suivant montre l'utilisation de `List.exists2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

La sortie se présente comme suit :

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

Vous pouvez utiliser [List. forall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) si vous souhaitez tester si tous les éléments d’une liste remplissent une condition.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

La sortie se présente comme suit :

```console
true
false
```

De même, [List. forall2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) détermine si tous les éléments des positions correspondantes dans deux listes satisfont à une expression booléenne qui implique chaque paire d’éléments.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

La sortie se présente comme suit :

```console
true
false
```

### <a name="sort-operations-on-lists"></a>Opérations de tri sur des listes

Les fonctions [List. sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort), [List. SortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy)et [List. sortWith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith) trient les listes. La fonction de tri détermine laquelle de ces trois fonctions utiliser. `List.sort` utilise la comparaison générique par défaut. Celle-ci compare des valeurs à l'aide d'opérateurs globaux reposant sur la fonction de comparaison générique. Elle est efficace avec une large gamme de types d'éléments, tels que les types numériques simples, les tuples, les enregistrements, les unions discriminées, les listes, les tableaux et tout type qui implémente `System.IComparable`. Dans le cas des types implémentant `System.IComparable`, la comparaison générique utilise la fonction `System.IComparable.CompareTo()`. La comparaison générique fonctionne aussi avec les chaînes, mais utilise un ordre de tri indépendant de la culture. Elle ne doit pas être utilisée sur les types non pris en charge, tels que les types de fonction. De plus, les performances de la comparaison générique par défaut sont meilleures dans le cas de petits types structurés. Dans le cas de types structurés plus importants qui impliquent une fréquence de comparaison et de tri plus soutenue, envisagez d'implémenter `System.IComparable` et de fournir une implémentation efficace de la méthode `System.IComparable.CompareTo()`.

`List.sortBy` accepte une fonction qui retourne une valeur utilisée comme critère de tri, et `List.sortWith` accepte une fonction de comparaison comme argument. Ces deux fonctions sont utiles quand les types ne prennent pas en charge la comparaison ou quand la comparaison nécessite une sémantique plus complexe, comme avec les chaînes prenant en compte la culture.

L'exemple suivant montre l'utilisation de `List.sort`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

La sortie se présente comme suit :

```console
[-2; 1; 4; 5; 8]
```

L'exemple suivant montre l'utilisation de `List.sortBy`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

La sortie se présente comme suit :

```console
[1; -2; 4; 5; 8]
```

L'exemple suivant montre l'utilisation de `List.sortWith`. Dans cet exemple, la fonction de comparaison personnalisée `compareWidgets` est utilisée pour comparer en premier un champ de type personnalisé, puis un autre champ quand les valeurs du premier champ sont égales.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

La sortie se présente comme suit :

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Opérations de recherche sur des listes

Les listes prennent en charge plusieurs opérations de recherche. La plus simple, [List. Find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find), vous permet de rechercher le premier élément qui correspond à une condition donnée.

L'exemple de code suivant montre l'utilisation de `List.find` pour rechercher le premier nombre divisible par 5 dans une liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

Le résultat est 5.

Si les éléments doivent être transformés en premier, appelez [List. Pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick), qui prend une fonction qui retourne une option, et recherche la première valeur d’option qui est `Some(x)` . Au lieu de renvoyer l'élément, `List.pick` retourne le résultat `x`. Si aucun élément correspondant n'est trouvé, `List.pick` lève `System.Collections.Generic.KeyNotFoundException`. Le code suivant illustre l'utilisation de `List.pick`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

La sortie se présente comme suit :

```console
"b"
```

Un autre groupe d’opérations de recherche, [List. tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) et les fonctions associées, retournent une valeur d’option. La fonction `List.tryFind` retourne le premier élément d'une liste qui satisfait à une condition, le cas échéant, et la valeur d'option `None` dans le cas contraire. La liste de variantes [. tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) retourne l’index de l’élément, le cas échéant, au lieu de l’élément lui-même. Ces fonctions sont illustrées dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

La sortie se présente comme suit :

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Opérations arithmétiques sur des listes

Les opérations arithmétiques courantes telles que SUM et Average sont intégrées dans le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html). Pour fonctionner avec [List. Sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum), le type d’élément de liste doit prendre en charge l' `+` opérateur et avoir une valeur égale à zéro. Tous les types arithmétiques intégrés remplissent ces conditions. Pour fonctionner avec [List. Average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average), le type d’élément doit prendre en charge la Division sans reste, ce qui exclut les types intégraux, mais autorise les types à virgule flottante. Les fonctions [List. sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy) et [List. averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy) prennent une fonction comme paramètre, et les résultats de cette fonction sont utilisés pour calculer les valeurs de la somme ou de la moyenne.

Le code suivant montre l'utilisation de `List.sum`, `List.sumBy` et `List.average`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

Le résultat est `1.000000`.

Le code suivant illustre l'utilisation de `List.averageBy`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

Le résultat est `5.5`.

### <a name="lists-and-tuples"></a>Listes et tuples

Les listes qui contiennent des tuples peuvent être manipulées par des fonctions de compression et de décompression. Ces fonctions combinent deux listes de valeurs uniques en une seule liste de tuples ou séparent une liste de tuples en deux listes de valeurs uniques. La fonction [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) la plus simple prend deux listes d’éléments uniques et produit une seule liste de paires de tuples. Une autre version, [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3), prend trois listes d’éléments uniques et produit une seule liste de tuples qui ont trois éléments. L'exemple de code suivant montre l'utilisation de `List.zip`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

La sortie se présente comme suit :

```console
[(1, -1); (2, -2); (3; -3)]
```

L'exemple de code suivant montre l'utilisation de `List.zip3`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

La sortie se présente comme suit :

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Les versions de décompression correspondantes, [List. unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip) et [List. unzip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3), prennent des listes de tuples et des listes de retour dans un tuple, où la première liste contient tous les éléments qui étaient en premier dans chaque tuple, et la deuxième liste contient le deuxième élément de chaque tuple, et ainsi de suite.

L’exemple de code suivant illustre l’utilisation de [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

La sortie se présente comme suit :

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

L’exemple de code suivant illustre l’utilisation de [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

La sortie se présente comme suit :

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Opérations sur les éléments de liste

F# prend en charge un éventail d'opérations sur des éléments de liste. La méthode [List. ITER](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter)la plus simple vous permet d’appeler une fonction sur chaque élément d’une liste. Les variations incluent [List. iter2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2), qui vous permet d’effectuer une opération sur les éléments de deux listes, [List. iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri), qui est similaire, `List.iter` à ceci près que l’index de chaque élément est passé comme argument à la fonction appelée pour chaque élément et [List. iteri2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2), qui est une combinaison des fonctionnalités de `List.iter2` et de `List.iteri` . L'exemple de code suivant illustre ces fonctions.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

La sortie se présente comme suit :

```console
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

Une autre fonction fréquemment utilisée qui transforme les éléments de liste est [List. map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map), qui vous permet d’appliquer une fonction à chaque élément d’une liste et de placer tous les résultats dans une nouvelle liste. [List. map2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) et [List. map3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) sont des variations qui acceptent plusieurs listes. Vous pouvez également utiliser [List. MAPI](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi) et [List. mapi2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2), si, en plus de l’élément, la fonction doit être passée à l’index de chaque élément. La seule différence entre `List.mapi2` et `List.mapi` est le fait que `List.mapi2` fonctionne avec les deux listes. L’exemple suivant illustre [List. map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

La sortie se présente comme suit :

```console
[2; 3; 4]
```

L’exemple suivant illustre l’utilisation de `List.map2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

La sortie se présente comme suit :

```console
[5; 7; 9]
```

L’exemple suivant illustre l’utilisation de `List.map3`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

La sortie se présente comme suit :

```console
[7; 10; 13]
```

L’exemple suivant illustre l’utilisation de `List.mapi`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

La sortie se présente comme suit :

```console
[1; 3; 5]
```

L’exemple suivant illustre l’utilisation de `List.mapi2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

La sortie se présente comme suit :

```console
[0; 7; 18]
```

[List. Collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) est semblable `List.map` à, à ceci près que chaque élément produit une liste et que toutes ces listes sont concaténées dans une liste finale. Dans le code suivant, chaque élément de la liste génère trois nombres. Ils sont tous rassemblés dans une liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

La sortie se présente comme suit :

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Vous pouvez également utiliser [List. Filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter), qui prend une condition booléenne et produit une nouvelle liste qui se compose uniquement d’éléments qui répondent à la condition donnée.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

La liste obtenue est `[2; 4; 6]`.

Une combinaison de Map et Filter, [List. choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) vous permet de transformer et de sélectionner des éléments en même temps. `List.choose` applique une fonction qui retourne une option à chaque élément d'une liste et renvoie une nouvelle liste des résultats pour les éléments quand la fonction retourne la valeur d'option `Some`.

Le code suivant illustre l'utilisation de `List.choose` pour sélectionner des mots en majuscules dans une liste de mots.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

La sortie se présente comme suit :

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Opérations sur plusieurs listes

Les listes peuvent être jointes. Pour joindre deux listes en une seule, utilisez [List. Append](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append). Pour joindre plus de deux listes, utilisez [List. Concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Opérations de repli et d'analyse

Certaines opérations de liste impliquent l'interdépendance entre tous les éléments de la liste. Les opérations de repli et d’analyse sont similaires et, dans le cas `List.iter` `List.map` où vous appelez une fonction sur chaque élément, mais ces opérations fournissent un paramètre supplémentaire appelé l' *accumulation* qui transporte des informations via le calcul.

Utilisez `List.fold` pour effectuer un calcul sur une liste.

L’exemple de code suivant illustre l’utilisation de [List. fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) pour effectuer diverses opérations.

La liste est parcourue ; l'accumulateur `acc` est une valeur passée au cours du calcul. Le premier argument prend l'accumulateur et l'élément de liste, puis retourne le résultat intermédiaire du calcul pour cet élément de liste. Le deuxième argument est la valeur initiale de l’accumulateur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

Les versions de ces fonctions dont le nom contient un chiffre s'effectuent sur plusieurs listes. Par exemple, [List. fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) effectue des calculs sur deux listes.

L'exemple suivant montre l'utilisation de `List.fold2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` et [List. Scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) diffère dans qui `List.fold` retourne la valeur finale du paramètre supplémentaire, mais `List.scan` retourne la liste des valeurs intermédiaires (avec la valeur finale) du paramètre supplémentaire.

Chacune de ces fonctions comprend une variation inverse, par exemple [List. foldBack](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack), qui diffère selon l’ordre dans lequel la liste est parcourue et l’ordre des arguments. En outre, `List.fold` et `List.foldBack` ont des variations, [List. fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) et [List. foldBack2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2), qui acceptent deux listes de longueur égale. La fonction qui s'exécute sur chaque élément peut utiliser des éléments correspondants aux deux listes pour effectuer une action. Les types d’éléments des deux listes peuvent être différents, comme dans l’exemple suivant, où une liste contient des montants de transactions sur un compte bancaire et l’autre contient le type de transaction : dépôt ou retrait.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

Pour un calcul tel qu'une addition, `List.fold` et `List.foldBack` ont le même effet car le résultat ne dépend pas de l'ordre de traversée. Dans l'exemple ci-dessous, `List.foldBack` est utilisé pour ajouter les éléments à une liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

Voici à nouveau l'exemple du compte bancaire. Cette fois, un nouveau type de transaction est ajouté : le calcul d'intérêts. Le solde de fin dépend désormais de l'ordre des transactions.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

La fonction [List. Reduce](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) est un peu comme `List.fold` et `List.scan` , à ceci près qu’au lieu de passer autour d’un accumulateur séparé, `List.reduce` prend une fonction qui accepte deux arguments du type d’élément au lieu d’un seul, et l’un de ces arguments joue le rôle d’accumulateur, ce qui signifie qu’elle stocke le résultat intermédiaire du calcul. `List.reduce` commence par fonctionner sur les deux premiers éléments de liste, puis utilise le résultat de l'opération avec l'élément suivant. Comme aucun accumulateur distinct ne possède son propre type, `List.reduce` ne peut être utilisé à la place de `List.fold` si l'accumulateur et le type d'élément ont le même type. Le code suivant montre l'utilisation de `List.reduce`. `List.reduce` lève une exception si la liste fournie ne comporte aucun élément.

Dans le code suivant, le premier appel à l’expression lambda reçoit les arguments 2 et 4, et retourne 6. L’appel suivant reçoit les arguments 6 et 10, le résultat est donc 16.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Conversion entre listes et autres types de collections

Le module `List` fournit des fonctions pour convertir vers et depuis des séquences et des tableaux. Pour convertir vers ou à partir d’une séquence, utilisez [List. toSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) ou [List. ofSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq). Pour convertir vers ou à partir d’un tableau, utilisez [List. ToArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) ou [List. ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray).

### <a name="additional-operations"></a>Opérations supplémentaires

Pour plus d’informations sur les opérations supplémentaires sur les listes, consultez le module de la [liste](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)de rubriques de référence sur la bibliothèque.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Types F#](fsharp-types.md)
- [Séquences](sequences.md)
- [Tableaux](arrays.md)
- [Options](options.md)
