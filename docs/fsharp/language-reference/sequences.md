---
title: Séquences
description: 'Apprenez à utiliser des séquences F #, lorsque vous disposez d’une collection de données volumineuse et ordonnée, mais que vous n’envisagez pas nécessairement d’utiliser tous les éléments.'
ms.date: 08/13/2020
ms.openlocfilehash: c84e0aebcc79a595c0ae3b9075648fb629bdd65c
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559035"
---
# <a name="sequences"></a>Séquences

Une *séquence* est une série logique d’éléments d’un seul type. Les séquences sont particulièrement utiles lorsque vous disposez d’une collection de données volumineuse et ordonnée, mais que vous n’envisagez pas nécessairement d’utiliser tous les éléments. Les éléments de séquence individuels sont calculés uniquement en fonction des besoins, de sorte qu’une séquence peut fournir de meilleures performances qu’une liste dans les cas où tous les éléments ne sont pas utilisés. Les séquences sont représentées par le `seq<'T>` type, qui est un alias pour <xref:System.Collections.Generic.IEnumerable%601> . Par conséquent, tout type .NET qui implémente l' <xref:System.Collections.Generic.IEnumerable%601> interface peut être utilisé comme une séquence. Le [module Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html) assure la prise en charge des manipulations impliquant des séquences.

## <a name="sequence-expressions"></a>Expressions de séquence

Une *expression de séquence* est une expression qui prend la valeur d’une séquence. Les expressions de séquence peuvent prendre plusieurs formes. La forme la plus simple spécifie une plage. Par exemple, `seq { 1 .. 5 }` crée une séquence qui contient cinq éléments, y compris les points de terminaison 1 et 5. Vous pouvez également spécifier un incrément (ou une décrémentation) entre deux points doubles. Par exemple, le code suivant crée la séquence de multiples de 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Les expressions de séquence sont constituées d’expressions F # qui produisent des valeurs de la séquence. Vous pouvez également générer des valeurs par programmation :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

L’exemple précédent utilise l' `->` opérateur, qui vous permet de spécifier une expression dont la valeur va devenir une partie de la séquence. Vous pouvez utiliser uniquement `->` si chaque partie du code qui le suit retourne une valeur.

Vous pouvez également spécifier le `do` mot clé, avec un facultatif `yield` qui suit :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Le code suivant génère une liste de paires de coordonnées, ainsi qu’un index dans un tableau qui représente la grille. Notez que la première `for` expression requiert la `do` spécification d’un.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

Une `if` expression utilisée dans une séquence est un filtre. Par exemple, pour générer une séquence de nombres premiers uniquement, en supposant que vous avez une fonction `isprime` de type `int -> bool` , construisez la séquence comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Comme mentionné précédemment, `do` est requis ici, car il n’y a aucune `else` branche qui accompagne le `if` . Si vous essayez d’utiliser `->` , vous obtiendrez un message d’erreur indiquant que toutes les branches ne retournent pas de valeur.

## <a name="the-yield-keyword"></a>Le mot clé `yield!`

Parfois, vous souhaiterez peut-être inclure une séquence d’éléments dans une autre séquence. Pour inclure une séquence dans une autre séquence, vous devez utiliser le `yield!` mot clé :

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

Une autre façon de penser `yield!` est qu’il aplatit une séquence interne, puis l’intègre dans la séquence conteneur.

Lorsque `yield!` est utilisé dans une expression, toutes les autres valeurs uniques doivent utiliser le `yield` mot clé :

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

L’exemple précédent produira la valeur de `x` en plus de toutes les valeurs de `1` à `x` pour chaque `x` .

## <a name="examples"></a>Exemples

Le premier exemple utilise une expression de séquence qui contient une itération, un filtre et un yield pour générer un tableau. Ce code imprime une séquence de nombres premiers entre 1 et 100 sur la console.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

L’exemple suivant crée une table de multiplication qui se compose de tuples de trois éléments, chacun comprenant deux facteurs et le produit :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

L’exemple suivant illustre l’utilisation de `yield!` pour combiner des séquences individuelles en une seule séquence finale. Dans ce cas, les séquences pour chaque sous-arborescence d’une arborescence binaire sont concaténées dans une fonction récursive pour produire la séquence finale.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Utilisation de séquences

Les séquences prennent en charge un grand nombre des mêmes fonctions que les [listes](lists.md). Les séquences prennent également en charge des opérations telles que le regroupement et le comptage à l’aide de fonctions génératrices de clé. Les séquences prennent également en charge des fonctions plus variées pour l’extraction de sous-séquences.

De nombreux types de données, tels que les listes, les tableaux, les jeux et les mappages sont implicitement des séquences, car il s’agit de collections énumérables. Une fonction qui prend une séquence comme argument fonctionne avec l’un des types de données F # communs, en plus de tout type de données .NET qui implémente `System.Collections.Generic.IEnumerable<'T>` . Comparez ce à une fonction qui prend une liste comme argument, qui peut uniquement prendre des listes. Le type `seq<'T>` est une abréviation de type pour `IEnumerable<'T>` . Cela signifie que tout type qui implémente le générique `System.Collections.Generic.IEnumerable<'T>` , qui comprend des tableaux, des listes, des jeux et des mappages en F #, ainsi que la plupart des types de collections .net, est compatible avec le `seq` type et peut être utilisé partout où une séquence est attendue.

## <a name="module-functions"></a>Fonctions de module

Le [module Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html) de l' [espace de noms FSharp. Collections](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections.html) contient des fonctions permettant d’utiliser des séquences. Ces fonctions fonctionnent également avec des listes, des tableaux, des mappages et des jeux, car tous ces types sont énumérables et peuvent donc être traités comme des séquences.

## <a name="creating-sequences"></a>Création de séquences

Vous pouvez créer des séquences à l’aide d’expressions de séquence, comme décrit précédemment, ou à l’aide de certaines fonctions.

Vous pouvez créer une séquence vide à l’aide de [Seq. Empty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#empty), ou vous pouvez créer une séquence d’un seul élément spécifié à l’aide de [Seq. Singleton](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#singleton).

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

Vous pouvez utiliser [Seq.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#init) pour créer une séquence pour laquelle les éléments sont créés à l’aide d’une fonction que vous fournissez. Vous fournissez également une taille pour la séquence. Cette fonction est similaire à [List.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#init), sauf que les éléments ne sont pas créés tant que vous n’effectuez pas une itération au sein de la séquence. Le code suivant illustre l’utilisation de `Seq.init` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

La sortie est la suivante :

```console
0 10 20 30 40
```

En utilisant [Seq. ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofArray) et [seq. ofList&#60; ne&#62; fonction](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofList), vous pouvez créer des séquences à partir de tableaux et de listes. Toutefois, vous pouvez également convertir des tableaux et des listes en séquences à l’aide d’un opérateur de cast. Les deux techniques sont présentées dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

En utilisant [Seq. Cast](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cast), vous pouvez créer une séquence à partir d’une collection faiblement typée, telle que celles définies dans `System.Collections` . Ces collections faiblement typées ont le type `System.Object` d’élément et sont énumérées à l’aide du `System.Collections.Generic.IEnumerable&#96;1` type non générique. Le code suivant illustre l’utilisation de `Seq.cast` pour convertir un `System.Collections.ArrayList` en séquence.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

Vous pouvez définir des séquences infinies à l’aide de la fonction [Seq.initInfinite](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#initInfinite) . Pour une telle séquence, vous fournissez une fonction qui génère chaque élément à partir de l’index de l’élément. Les séquences infinies sont possibles en raison de l’évaluation différée ; les éléments sont créés en fonction des besoins en appelant la fonction que vous spécifiez. L’exemple de code suivant produit une séquence infinie de nombres à virgule flottante, dans ce cas, la série alternative de réciproques de carrés d’entiers successifs.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq. Unfold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#unfold) génère une séquence à partir d’une fonction de calcul qui prend un État et le transforme pour produire chaque élément suivant dans la séquence. L’État est simplement une valeur utilisée pour calculer chaque élément et peut changer à mesure que chaque élément est calculé. Le deuxième argument de `Seq.unfold` est la valeur initiale utilisée pour démarrer la séquence. `Seq.unfold` utilise un type d’option pour l’État, ce qui vous permet de terminer la séquence en retournant la `None` valeur. Le code suivant illustre deux exemples de séquences, `seq1` et `fib` , qui sont générés par une `unfold` opération. La première, `seq1` , est simplement une séquence simple avec des nombres allant jusqu’à 20. Le deuxième, `fib` , utilise `unfold` pour calculer la séquence de Fibonacci. Étant donné que chaque élément de la séquence de Fibonacci est la somme des deux nombres de Fibonacci précédents, la valeur d’État est un tuple qui se compose des deux nombres précédents de la séquence. La valeur initiale est `(1,1)` , les deux premiers nombres de la séquence.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

La sortie se présente comme suit :

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Le code suivant est un exemple qui utilise un grand nombre des fonctions de module de séquence décrites ici pour générer et calculer les valeurs de séquences infinies. L’exécution du code peut prendre quelques minutes.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Recherche et recherche d’éléments

Les séquences prennent en charge les fonctionnalités disponibles avec les listes [Seq. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists), [Seq. exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists), [Seq. Find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#find), [Seq. FindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#findIndex), [Seq. Pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pick), [Seq. tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFind)et [Seq. tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex). Les versions de ces fonctions qui sont disponibles pour les séquences évaluent la séquence uniquement jusqu’à l’élément qui fait l’objet de la recherche. Pour obtenir des exemples, consultez [listes](lists.md).

## <a name="obtaining-subsequences"></a>Obtention de sous-séquences

[Seq. Filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#filter) et [Seq. choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#choose) sont semblables aux fonctions correspondantes qui sont disponibles pour les listes, sauf que le filtrage et le choix ne se produisent pas tant que les éléments de séquence ne sont pas évalués.

[Seq. Truncate](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#truncate) crée une séquence à partir d’une autre séquence, mais limite la séquence à un nombre spécifié d’éléments. [Seq. Take](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#take) crée une séquence qui contient uniquement un nombre spécifié d’éléments à partir du début d’une séquence. Si le nombre d’éléments dans la séquence est inférieur à celui que vous spécifiez pour prendre, `Seq.take` lève une `System.InvalidOperationException` . La différence entre `Seq.take` et `Seq.truncate` est que `Seq.truncate` ne produit pas d’erreur si le nombre d’éléments est inférieur au nombre que vous spécifiez.

Le code suivant illustre le comportement de et les différences entre `Seq.truncate` et `Seq.take` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

La sortie, avant l’erreur, se présente comme suit.

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

En utilisant [Seq. TakeWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#takeWhile), vous pouvez spécifier une fonction de prédicat (fonction booléenne) et créer une séquence à partir d’une autre séquence composée de ces éléments de la séquence d’origine pour laquelle le prédicat est `true` , mais s’arrêter avant le premier élément pour lequel le prédicat est retourné `false` . [Seq. Skip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skip) retourne une séquence qui ignore un nombre spécifié de premiers éléments d’une autre séquence et retourne les éléments restants. [Seq. SkipWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skipWhile) retourne une séquence qui ignore les premiers éléments d’une autre séquence tant que le prédicat retourne la valeur `true` , puis retourne les éléments restants, en commençant par le premier élément pour lequel le prédicat retourne `false` .

L’exemple de code suivant illustre le comportement de et les différences entre `Seq.takeWhile` , et `Seq.skip` `Seq.skipWhile` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

La sortie est la suivante.

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Transformation de séquences

[Seq. pairwise](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pairwise) crée une séquence dans laquelle les éléments successifs de la séquence d’entrée sont regroupés en tuples.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq. Windowed](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#windowed) est comme `Seq.pairwise` , mais au lieu de produire une séquence de tuples, il produit une séquence de tableaux qui contiennent des copies d’éléments adjacents (une *fenêtre*) à partir de la séquence. Vous spécifiez le nombre d’éléments adjacents que vous souhaitez dans chaque tableau.

L'exemple de code suivant montre l'utilisation de `Seq.windowed`. Dans ce cas, le nombre d’éléments dans la fenêtre est 3. L’exemple utilise `printSeq` , qui est défini dans l’exemple de code précédent.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

La sortie est la suivante.

Séquence initiale :

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Opérations avec plusieurs séquences

[Seq.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip) et [Seq.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip3) prennent deux ou trois séquences et produisent une séquence de tuples. Ces fonctions sont semblables aux fonctions correspondantes disponibles pour les [listes](lists.md). Il n’existe aucune fonctionnalité correspondante pour séparer une séquence en deux séquences ou plus. Si vous avez besoin de cette fonctionnalité pour une séquence, convertissez la séquence en une liste et utilisez [List. unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip).

## <a name="sorting-comparing-and-grouping"></a>Tri, comparaison et regroupement

Les fonctions de tri prises en charge pour les listes fonctionnent également avec les séquences. Cela comprend [Seq. sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sort) et [Seq. SortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sortBy). Ces fonctions itèrent au sein de l’ensemble de la séquence.

Vous comparez deux séquences à l’aide de la fonction [Seq. compareWith (](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#compareWith) . La fonction compare ensuite les éléments successifs et s’arrête lorsqu’elle rencontre la première paire inégale. Tout élément supplémentaire ne contribue pas à la comparaison.

Le code suivant illustre l'utilisation de `Seq.compareWith`.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

Dans le code précédent, seul le premier élément est calculé et examiné, et le résultat est-1.

[Seq. countBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#countBy) prend une fonction qui génère une valeur appelée *clé* pour chaque élément. Une clé est générée pour chaque élément en appelant cette fonction sur chaque élément. `Seq.countBy` retourne ensuite une séquence qui contient les valeurs de clés et le nombre d’éléments qui ont généré chaque valeur de la clé.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

La sortie est la suivante.

```console
(1, 34) (2, 33) (0, 33)
```

La sortie précédente montre qu’il existait 34 éléments de la séquence d’origine qui ont produit la clé 1, 33 valeurs qui ont produit la clé 2 et 33 valeurs qui ont produit la clé 0.

Vous pouvez regrouper des éléments d’une séquence en appelant [Seq. GroupBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#groupBy). `Seq.groupBy` prend une séquence et une fonction qui génère une clé à partir d’un élément. La fonction est exécutée sur chaque élément de la séquence. `Seq.groupBy` retourne une séquence de tuples, où le premier élément de chaque tuple est la clé et le second est une séquence d’éléments qui produisent cette clé.

L’exemple de code suivant illustre l’utilisation de `Seq.groupBy` pour partitionner la séquence de nombres de 1 à 100 en trois groupes qui ont les valeurs de clé distinctes 0, 1 et 2.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

La sortie est la suivante.

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Vous pouvez créer une séquence qui élimine les doublons d’éléments en appelant [Seq. distinct](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinct). Ou vous pouvez utiliser [Seq. distinctBy (](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinctBy), qui prend une fonction de génération de clé à appeler sur chaque élément. La séquence résultante contient des éléments de la séquence d’origine qui ont des clés uniques ; les éléments ultérieurs qui produisent une clé dupliquée pour un élément antérieur sont ignorés.

L’exemple de code suivant illustre l’utilisation de `Seq.distinct` . `Seq.distinct` est démontré en générant des séquences qui représentent des nombres binaires, puis en indiquant que les seuls éléments distincts sont 0 et 1.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

Le code suivant illustre `Seq.distinctBy` en commençant par une séquence qui contient des nombres négatifs et positifs et en utilisant la fonction de valeur absolue comme fonction de génération de clé. La séquence résultante ne contient pas tous les nombres positifs qui correspondent aux nombres négatifs de la séquence, car les nombres négatifs apparaissent plus tôt dans la séquence et sont donc sélectionnés à la place des nombres positifs ayant la même valeur absolue ou la même clé.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Séquences ReadOnly et mises en cache

[Seq. ReadOnly](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#readonly) crée une copie en lecture seule d’une séquence. `Seq.readonly` est utile lorsque vous disposez d’une collection en lecture-écriture, telle qu’un tableau, et que vous ne souhaitez pas modifier la collection d’origine. Cette fonction peut être utilisée pour conserver l’encapsulation des données. Dans l’exemple de code suivant, un type qui contient un tableau est créé. Une propriété expose le tableau, mais au lieu de retourner un tableau, elle retourne une séquence créée à partir du tableau à l’aide de `Seq.readonly` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq. cache](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cache) crée une version stockée d’une séquence. Utilisez `Seq.cache` pour éviter la réévaluation d’une séquence, ou lorsque vous avez plusieurs threads qui utilisent une séquence, mais que vous devez vous assurer que chaque élément est traité sur une seule fois. Quand vous avez une séquence qui est utilisée par plusieurs threads, vous pouvez avoir un thread qui énumère et calcule les valeurs de la séquence d’origine, et les threads restants peuvent utiliser la séquence mise en cache.

## <a name="performing-computations-on-sequences"></a>Exécution de calculs sur des séquences

Les opérations arithmétiques simples sont similaires à celles des listes, telles que [Seq. Average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#average), [Seq. Sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sum), [Seq. averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#averageBy), [Seq. sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sumBy), et ainsi de suite.

[Seq. fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#fold), [Seq. Reduce](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#reduce)et [Seq. Scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#scan) sont semblables aux fonctions correspondantes qui sont disponibles pour les listes. Les séquences prennent en charge un sous-ensemble des variantes complètes de ces fonctions qui répertorient la prise en charge. Pour plus d’informations et d’exemples, consultez [listes](lists.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Types F#](fsharp-types.md)
