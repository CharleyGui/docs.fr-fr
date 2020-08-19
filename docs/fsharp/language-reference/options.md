---
title: Options
description: 'Apprenez à utiliser les types d’option F # lorsqu’il est possible qu’il n’existe pas de valeur réelle pour une valeur ou une variable nommée.'
ms.date: 08/13/2020
ms.openlocfilehash: 0618590c10f6ecac51a23483ca0ab6cd66f2df4f
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557566"
---
# <a name="options"></a>Options

Le type d’option en F # est utilisé lorsqu’il est possible qu’il n’existe pas de valeur réelle pour une valeur ou une variable nommée. Une option a un type sous-jacent et peut contenir une valeur de ce type, ou elle peut ne pas avoir de valeur.

## <a name="remarks"></a>Notes

Le code suivant illustre une fonction qui génère un type d’option.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Comme vous pouvez le voir, si l’entrée `a` est supérieure à 0, `Some(a)` est généré.  Sinon, `None` est généré.

La valeur `None` est utilisée lorsqu’une option n’a pas de valeur réelle. Dans le cas contraire, l’expression `Some( ... )` donne une valeur à l’option. Les valeurs `Some` et `None` sont utiles dans les critères spéciaux, comme dans la fonction suivante `exists` , qui retourne `true` si l’option a une valeur et `false` si ce n’est pas le cas.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Utilisation d’options

Les options sont couramment utilisées lorsqu’une recherche ne retourne pas de résultat de correspondance, comme illustré dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

Dans le code précédent, une liste est recherchée de manière récursive. La fonction `tryFindMatch` prend une fonction de prédicat `pred` qui retourne une valeur booléenne et une liste dans laquelle effectuer la recherche. Si un élément qui répond au prédicat est trouvé, la récursivité se termine et la fonction retourne la valeur en tant qu’option dans l’expression `Some(head)` . La récursivité se termine lorsque la liste vide est mise en correspondance. À ce stade, la valeur n' `head` a pas été trouvée et `None` est retournée.

De nombreuses fonctions de bibliothèque F # qui recherchent une valeur qui peut ou non exister dans une collection retournent le `option` type. Par Convention, ces fonctions commencent par le `try` préfixe, par exemple, [`Seq.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex) .

Les options peuvent également être utiles lorsqu’une valeur peut ne pas exister, par exemple s’il est possible qu’une exception soit levée quand vous essayez de construire une valeur. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

La `openFile` fonction de l’exemple précédent a le type `string -> File option` , car elle retourne un `File` objet si le fichier s’ouvre correctement et `None` si une exception se produit. Selon la situation, il est possible qu’il ne s’agit pas d’un choix de conception approprié pour intercepter une exception plutôt que de l’autoriser à se propager.

En outre, il est toujours possible de passer `null` ou une valeur null dans le `Some` cas d’une option. Cela est généralement évité, et se trouve généralement dans la programmation F # routine, mais est possible en raison de la nature des types de référence dans .NET.

## <a name="option-properties-and-methods"></a>Propriétés et méthodes de l’option

Le type d’option prend en charge les propriétés et les méthodes suivantes.

|Propriété ou méthode|Type|Description|
|------------------|----|-----------|
|[Aucun](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#None)|`'T option`|Propriété statique qui vous permet de créer une valeur d’option qui a la `None` valeur.|
|[IsNone (](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#IsNone)|`bool`|Retourne `true` si l’option a la `None` valeur.|
|[IsSome (](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#IsSome)|`bool`|Retourne `true` si l’option a une valeur qui n’est pas `None` .|
|[Certains](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#Some)|`'T option`|Membre statique qui crée une option qui a une valeur qui n’est pas `None` .|
|[Valeur](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-fsharpoption-1.html#Value)|`'T`|Retourne la valeur sous-jacente ou lève une `System.NullReferenceException` si la valeur est `None` .|

## <a name="option-module"></a>Module d’option

Un module, [option](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html), contient des fonctions utiles qui effectuent des opérations sur les options. Certaines fonctions répètent les fonctionnalités des propriétés, mais elles sont utiles dans les contextes où une fonction est nécessaire. [Option. IsSome](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#isSome) et [option. IsNone](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#isNone) sont des fonctions de module qui testent si une option contient une valeur. [Option. obtenir](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#get) obtient la valeur, le cas échéant. S’il n’y a aucune valeur, elle lève une exception `System.ArgumentException` .

La fonction [option. bind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#bind) exécute une fonction sur la valeur, s’il y a une valeur. La fonction doit accepter exactement un argument et son type de paramètre doit être le type d’option. La valeur de retour de la fonction est un autre type d’option.

Le module option comprend également des fonctions qui correspondent aux fonctions disponibles pour les listes, les tableaux, les séquences et d’autres types de collections. Ces fonctions incluent [`Option.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#map) , [`Option.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#iter) , [`Option.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#forall) , [`Option.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#exists) , [`Option.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#foldBack) , [`Option.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#fold) et [`Option.count`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#count) . Ces fonctions permettent d’utiliser des options comme une collection de zéro ou un élément. Pour plus d’informations et d’exemples, consultez la discussion sur les fonctions de collection dans les [listes](lists.md).

## <a name="converting-to-other-types"></a>Convertir en d’autres types

Les options peuvent être converties en listes ou tableaux. Lorsqu’une option est convertie en l’une ou l’autre de ces structures de données, la structure de données résultante a zéro ou un élément. Pour convertir une option en tableau, utilisez [`Option.toArray`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#toArray) . Pour convertir une option en liste, utilisez [`Option.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-optionmodule.html#toList) .

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Types F#](fsharp-types.md)
