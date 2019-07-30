---
title: Options
description: Apprenez à utiliser F# les types d’option lorsqu’il est possible qu’il n’existe pas de valeur réelle pour une valeur ou une variable nommée.
ms.date: 05/16/2016
ms.openlocfilehash: 9326cf04f53adac7422c09a49a59c4eecd49486d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627353"
---
# <a name="options"></a>Options

Le type d’option F# dans est utilisé lorsqu’il est possible qu’il n’existe pas de valeur réelle pour une valeur ou une variable nommée. Une option a un type sous-jacent et peut contenir une valeur de ce type, ou elle peut ne pas avoir de valeur.

## <a name="remarks"></a>Notes

Le code suivant illustre une fonction qui génère un type d’option.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

Comme vous pouvez le voir, si l' `a` entrée est supérieure à 0 `Some(a)` , est généré.  Sinon, `None` est généré.

La valeur `None` est utilisée lorsqu’une option n’a pas de valeur réelle. Dans le cas contraire `Some( ... )` , l’expression donne une valeur à l’option. Les valeurs `Some` et `None` sont utiles dans les critères spéciaux, comme dans la fonction `exists`suivante, qui `true` retourne si l’option a une valeur `false` et si ce n’est pas le cas.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>Utilisation des options

Les options sont couramment utilisées lorsqu’une recherche ne retourne pas de résultat de correspondance, comme illustré dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

Dans le code précédent, une liste est recherchée de manière récursive. La fonction `tryFindMatch` prend une fonction `pred` de prédicat qui retourne une valeur booléenne et une liste dans laquelle effectuer la recherche. Si un élément qui répond au prédicat est trouvé, la récursivité se termine et la fonction retourne la valeur en tant qu’option dans l’expression `Some(head)`. La récursivité se termine lorsque la liste vide est mise en correspondance. À ce stade, la `head` valeur n’a pas été trouvée `None` et est retournée.

De F# nombreuses fonctions de bibliothèque qui recherchent une valeur qui peut ou non exister dans une collection `option` retournent le type. Par Convention, ces fonctions commencent par le `try` préfixe, par exemple [`Seq.tryFindIndex`](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a),.

Les options peuvent également être utiles lorsqu’une valeur peut ne pas exister, par exemple s’il est possible qu’une exception soit levée quand vous essayez de construire une valeur. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

La `openFile` fonction de l’exemple précédent a le `string -> File option` type, car elle `File` retourne un objet si le fichier s' `None` ouvre correctement et si une exception se produit. Selon la situation, il est possible qu’il ne s’agit pas d’un choix de conception approprié pour intercepter une exception plutôt que de l’autoriser à se propager.

En outre, il est toujours possible de passer `null` ou une valeur null dans le `Some` cas d’une option. Cela est généralement évité, et se trouve généralement dans la programmation F# de routine, mais est possible en raison de la nature des types de référence dans .net.

## <a name="option-properties-and-methods"></a>Propriétés et méthodes de l’option

Le type d’option prend en charge les propriétés et les méthodes suivantes.

|Propriété ou méthode|Type|Description|
|------------------|----|-----------|
|[Aucun](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|Propriété statique qui vous permet de créer une valeur d’option qui a la `None` valeur.|
|[IsNone (](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|Retourne `true` si l’option a la `None` valeur.|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|Retourne `true` si l’option a une valeur qui n’est `None`pas.|
|[Certains](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|Membre statique qui crée une option qui a une valeur qui n’est pas `None`.|
|[Valeur](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|Retourne la valeur sous-jacente ou lève une `System.NullReferenceException` si la valeur est `None`.|

## <a name="option-module"></a>Module d’option

Un module, [option](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c), contient des fonctions utiles qui effectuent des opérations sur les options. Certaines fonctions répètent les fonctionnalités des propriétés, mais elles sont utiles dans les contextes où une fonction est nécessaire. [Option. IsSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79) et [option. IsNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819) sont des fonctions de module qui testent si une option contient une valeur. [Option. obtenir](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea) obtient la valeur, le cas échéant. S’il n’y a aucune valeur, elle `System.ArgumentException`lève une exception.

La fonction [option. bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0) exécute une fonction sur la valeur, s’il y a une valeur. La fonction doit accepter exactement un argument et son type de paramètre doit être le type d’option. La valeur de retour de la fonction est un autre type d’option.

Le module option comprend également des fonctions qui correspondent aux fonctions disponibles pour les listes, les tableaux, les séquences et d’autres types de collections. Ces fonctions incluent [`Option.map`](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622), [`Option.iter`](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191), [`Option.forall`](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428), [`Option.exists`](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99), [,`Option.foldBack`](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb) [et`Option.count`](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876). [`Option.fold`](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8) Ces fonctions permettent d’utiliser des options comme une collection de zéro ou un élément. Pour plus d’informations et d’exemples, consultez la discussion sur les fonctions de collection dans les [listes](lists.md).

## <a name="converting-to-other-types"></a>Convertir en d’autres types

Les options peuvent être converties en listes ou tableaux. Lorsqu’une option est convertie en l’une ou l’autre de ces structures de données, la structure de données résultante a zéro ou un élément. Pour convertir une option en tableau, utilisez [`Option.toArray`](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64). Pour convertir une option en liste, utilisez [`Option.toList`](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1).

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Types F#](fsharp-types.md)
