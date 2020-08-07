---
title: Listes
description: 'En savoir plus sur les listes F #, une série immuable et ordonnée d’éléments du même type.'
ms.date: 05/16/2016
ms.openlocfilehash: 236ae77813a3448f159228c5c58d9fe3d024fbd8
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854969"
---
# <a name="lists"></a>Listes

En F#, une liste est une série immuable et ordonnée d'éléments du même type. Pour effectuer des opérations de base sur les listes, utilisez les fonctions dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

> [!NOTE]
> La référence de l’API docs.microsoft.com pour F # n’est pas terminée. Si vous rencontrez des liens rompus, consultez plutôt [la documentation de la bibliothèque principale F #](https://fsharp.github.io/fsharp-core-docs/) .

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

Les fonctions permettant d’effectuer des opérations sur des listes sont disponibles dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

En F#, les listes étant immuables, toute opération de changement a pour effet de générer de nouvelles listes au lieu de modifier les listes existantes.

Les listes en F # sont implémentées en tant que listes à liaison unique, ce qui signifie que les opérations qui accèdent uniquement au début de la liste sont O (1) et que l’accès à l’élément est O (*n*).

## <a name="properties"></a>Propriétés

Le type de liste prend en charge les propriétés suivantes :

|Propriété|Type|Description|
|--------|----|-----------|
|[Siège](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|Premier élément.|
|[Vide](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Propriété statique qui retourne une liste vide du type approprié.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true` si la liste ne comporte aucun élément.|
|[Item](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|Élément au niveau de l'index spécifié (de base zéro).|
|[Longueur](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Nombre d'éléments.|
|[Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|Liste sans premier élément.|

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

Le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) fournit des fonctions qui accèdent aux éléments d’une liste. L'élément de début offre l'accès le plus simple et rapide. Utilisez l' [en-tête](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) de propriété ou la fonction de module [List. Head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2). Vous pouvez accéder à la fin d’une liste à l’aide de la propriété [tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) ou de la fonction [List. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) . Pour rechercher un élément par index, utilisez la fonction [List. nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) . `List.nth` parcourt la liste. Par conséquent, il s’agit de O (*n*). Si votre code utilise fréquemment `List.nth`, envisagez d'utiliser un tableau à la place d'une liste. L'accès aux éléments des tableaux est O(1).

### <a name="boolean-operations-on-lists"></a>Opérations booléennes sur des listes

La fonction [List. IsEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) détermine si une liste contient des éléments.

La fonction [List. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) applique un test booléen aux éléments d’une liste et retourne `true` si un élément satisfait au test. [List. exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) est similaire, mais fonctionne sur des paires d’éléments successifs dans deux listes.

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

Vous pouvez utiliser [List. forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) si vous souhaitez tester si tous les éléments d’une liste remplissent une condition.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

La sortie se présente comme suit :

```console
true
false
```

De même, [List. forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) détermine si tous les éléments des positions correspondantes dans deux listes satisfont à une expression booléenne qui implique chaque paire d’éléments.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

La sortie se présente comme suit :

```console
true
false
```

### <a name="sort-operations-on-lists"></a>Opérations de tri sur des listes

Les fonctions [List. sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List. SortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)et [List. sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) trient les listes. La fonction de tri détermine laquelle de ces trois fonctions utiliser. `List.sort` utilise la comparaison générique par défaut. Celle-ci compare des valeurs à l'aide d'opérateurs globaux reposant sur la fonction de comparaison générique. Elle est efficace avec une large gamme de types d'éléments, tels que les types numériques simples, les tuples, les enregistrements, les unions discriminées, les listes, les tableaux et tout type qui implémente `System.IComparable`. Dans le cas des types implémentant `System.IComparable`, la comparaison générique utilise la fonction `System.IComparable.CompareTo()`. La comparaison générique fonctionne aussi avec les chaînes, mais utilise un ordre de tri indépendant de la culture. Elle ne doit pas être utilisée sur les types non pris en charge, tels que les types de fonction. De plus, les performances de la comparaison générique par défaut sont meilleures dans le cas de petits types structurés. Dans le cas de types structurés plus importants qui impliquent une fréquence de comparaison et de tri plus soutenue, envisagez d'implémenter `System.IComparable` et de fournir une implémentation efficace de la méthode `System.IComparable.CompareTo()`.

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

Les listes prennent en charge plusieurs opérations de recherche. La plus simple, [List. Find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), vous permet de rechercher le premier élément qui correspond à une condition donnée.

L'exemple de code suivant montre l'utilisation de `List.find` pour rechercher le premier nombre divisible par 5 dans une liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

Le résultat est 5.

Si les éléments doivent être transformés en premier, appelez [List. Pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), qui prend une fonction qui retourne une option, et recherche la première valeur d’option qui est `Some(x)` . Au lieu de renvoyer l'élément, `List.pick` retourne le résultat `x`. Si aucun élément correspondant n'est trouvé, `List.pick` lève `System.Collections.Generic.KeyNotFoundException`. Le code suivant illustre l'utilisation de `List.pick`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

La sortie se présente comme suit :

```console
"b"
```

Un autre groupe d’opérations de recherche, [List. tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) et les fonctions associées, retournent une valeur d’option. La fonction `List.tryFind` retourne le premier élément d'une liste qui satisfait à une condition, le cas échéant, et la valeur d'option `None` dans le cas contraire. La liste de variantes [. tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) retourne l’index de l’élément, le cas échéant, au lieu de l’élément lui-même. Ces fonctions sont illustrées dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

La sortie se présente comme suit :

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Opérations arithmétiques sur des listes

Les opérations arithmétiques courantes telles que SUM et Average sont intégrées dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Pour fonctionner avec [List. Sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), le type d’élément de liste doit prendre en charge l' `+` opérateur et avoir une valeur égale à zéro. Tous les types arithmétiques intégrés remplissent ces conditions. Pour fonctionner avec [List. Average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), le type d’élément doit prendre en charge la Division sans reste, ce qui exclut les types intégraux, mais autorise les types à virgule flottante. Les fonctions [List. sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) et [List. averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) prennent une fonction comme paramètre, et les résultats de cette fonction sont utilisés pour calculer les valeurs de la somme ou de la moyenne.

Le code suivant montre l'utilisation de `List.sum`, `List.sumBy` et `List.average`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

Le résultat est `1.000000`.

Le code suivant illustre l'utilisation de `List.averageBy`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

Le résultat est `5.5`.

### <a name="lists-and-tuples"></a>Listes et tuples

Les listes qui contiennent des tuples peuvent être manipulées par des fonctions de compression et de décompression. Ces fonctions combinent deux listes de valeurs uniques en une seule liste de tuples ou séparent une liste de tuples en deux listes de valeurs uniques. La fonction [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) la plus simple prend deux listes d’éléments uniques et produit une seule liste de paires de tuples. Une autre version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), prend trois listes d’éléments uniques et produit une seule liste de tuples qui ont trois éléments. L'exemple de code suivant montre l'utilisation de `List.zip`.

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

Les versions de décompression correspondantes, [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) et [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), prennent des listes de tuples et des listes de retour dans un tuple, où la première liste contient tous les éléments qui étaient en premier dans chaque tuple, et la deuxième liste contient le deuxième élément de chaque tuple, et ainsi de suite.

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

F# prend en charge un éventail d'opérations sur des éléments de liste. La méthode [List. ITER](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f)la plus simple vous permet d’appeler une fonction sur chaque élément d’une liste. Les variations incluent [List. iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), qui vous permet d’effectuer une opération sur les éléments de deux listes, [List. iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), qui est similaire, `List.iter` à ceci près que l’index de chaque élément est passé comme argument à la fonction appelée pour chaque élément et [List. iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), qui est une combinaison des fonctionnalités de `List.iter2` et de `List.iteri` . L'exemple de code suivant illustre ces fonctions.

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

Une autre fonction fréquemment utilisée qui transforme les éléments de liste est [List. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), qui vous permet d’appliquer une fonction à chaque élément d’une liste et de placer tous les résultats dans une nouvelle liste. [List. map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) et [List. map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) sont des variations qui acceptent plusieurs listes. Vous pouvez également utiliser [List. MAPI](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) et [List. mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), si, en plus de l’élément, la fonction doit être passée à l’index de chaque élément. La seule différence entre `List.mapi2` et `List.mapi` est le fait que `List.mapi2` fonctionne avec les deux listes. L’exemple suivant illustre [List. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

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

[List. Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) est semblable `List.map` à, à ceci près que chaque élément produit une liste et que toutes ces listes sont concaténées dans une liste finale. Dans le code suivant, chaque élément de la liste génère trois nombres. Ils sont tous rassemblés dans une liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

La sortie se présente comme suit :

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Vous pouvez également utiliser [List. Filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), qui prend une condition booléenne et produit une nouvelle liste qui se compose uniquement d’éléments qui répondent à la condition donnée.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

La liste obtenue est `[2; 4; 6]`.

Une combinaison de Map et Filter, [List. choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) vous permet de transformer et de sélectionner des éléments en même temps. `List.choose` applique une fonction qui retourne une option à chaque élément d'une liste et renvoie une nouvelle liste des résultats pour les éléments quand la fonction retourne la valeur d'option `Some`.

Le code suivant illustre l'utilisation de `List.choose` pour sélectionner des mots en majuscules dans une liste de mots.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

La sortie se présente comme suit :

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Opérations sur plusieurs listes

Les listes peuvent être jointes. Pour joindre deux listes en une seule, utilisez [List. Append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). Pour joindre plus de deux listes, utilisez [List. Concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Opérations de repli et d'analyse

Certaines opérations de liste impliquent l'interdépendance entre tous les éléments de la liste. Les opérations de repli et d’analyse sont similaires et, dans le cas `List.iter` `List.map` où vous appelez une fonction sur chaque élément, mais ces opérations fournissent un paramètre supplémentaire appelé l' *accumulation* qui transporte des informations via le calcul.

Utilisez `List.fold` pour effectuer un calcul sur une liste.

L’exemple de code suivant illustre l’utilisation de [List. fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) pour effectuer diverses opérations.

La liste est parcourue ; l'accumulateur `acc` est une valeur passée au cours du calcul. Le premier argument prend l'accumulateur et l'élément de liste, puis retourne le résultat intermédiaire du calcul pour cet élément de liste. Le deuxième argument est la valeur initiale de l’accumulateur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

Les versions de ces fonctions dont le nom contient un chiffre s'effectuent sur plusieurs listes. Par exemple, [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) effectue des calculs sur deux listes.

L'exemple suivant montre l'utilisation de `List.fold2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold`et [List. Scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) diffère dans qui `List.fold` retourne la valeur finale du paramètre supplémentaire, mais `List.scan` retourne la liste des valeurs intermédiaires (avec la valeur finale) du paramètre supplémentaire.

Chacune de ces fonctions comprend une variation inverse, par exemple [List. foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), qui diffère selon l’ordre dans lequel la liste est parcourue et l’ordre des arguments. En outre, `List.fold` et `List.foldBack` ont des variations, [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) et [List. foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), qui acceptent deux listes de longueur égale. La fonction qui s'exécute sur chaque élément peut utiliser des éléments correspondants aux deux listes pour effectuer une action. Les types d’éléments des deux listes peuvent être différents, comme dans l’exemple suivant, où une liste contient des montants de transactions sur un compte bancaire et l’autre contient le type de transaction : dépôt ou retrait.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

Pour un calcul tel qu'une addition, `List.fold` et `List.foldBack` ont le même effet car le résultat ne dépend pas de l'ordre de traversée. Dans l'exemple ci-dessous, `List.foldBack` est utilisé pour ajouter les éléments à une liste.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

Voici à nouveau l'exemple du compte bancaire. Cette fois, un nouveau type de transaction est ajouté : le calcul d'intérêts. Le solde de fin dépend désormais de l'ordre des transactions.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

La fonction [List. Reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) est un peu comme `List.fold` et `List.scan` , à ceci près qu’au lieu de passer autour d’un accumulateur séparé, `List.reduce` prend une fonction qui accepte deux arguments du type d’élément au lieu d’un seul, et l’un de ces arguments joue le rôle d’accumulateur, ce qui signifie qu’elle stocke le résultat intermédiaire du calcul. `List.reduce` commence par fonctionner sur les deux premiers éléments de liste, puis utilise le résultat de l'opération avec l'élément suivant. Comme aucun accumulateur distinct ne possède son propre type, `List.reduce` ne peut être utilisé à la place de `List.fold` si l'accumulateur et le type d'élément ont le même type. Le code suivant montre l'utilisation de `List.reduce`. `List.reduce` lève une exception si la liste fournie ne comporte aucun élément.

Dans le code suivant, le premier appel à l’expression lambda reçoit les arguments 2 et 4, et retourne 6. L’appel suivant reçoit les arguments 6 et 10, le résultat est donc 16.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Conversion entre listes et autres types de collections

Le module `List` fournit des fonctions pour convertir vers et depuis des séquences et des tableaux. Pour convertir vers ou à partir d’une séquence, utilisez [List. toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) ou [List. ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). Pour convertir vers ou à partir d’un tableau, utilisez [List. ToArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) ou [List. ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).

### <a name="additional-operations"></a>Opérations supplémentaires

Pour plus d’informations sur les opérations supplémentaires sur les listes, consultez le [module Collections. List](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d)de la rubrique de référence de la bibliothèque.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Types F#](fsharp-types.md)
- [Séquences](sequences.md)
- [Tableaux](arrays.md)
- [Options](options.md)
