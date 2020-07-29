---
title: Constructeurs
description: 'Découvrez comment définir et utiliser des constructeurs en F # pour créer et initialiser des objets de classe et de structure.'
ms.date: 05/16/2016
ms.openlocfilehash: be8fc3f1d82a9a7c778a6d094139f14150a28813
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303437"
---
# <a name="constructors"></a>Constructeurs

Cet article explique comment définir et utiliser des constructeurs pour créer et initialiser des objets de classe et de structure.

## <a name="construction-of-class-objects"></a>Construction d’objets de classe

Les objets des types de classe ont des constructeurs. Il existe deux genres de constructeurs. L’un est le constructeur principal, dont les paramètres apparaissent entre parenthèses juste après le nom du type. Vous spécifiez d’autres constructeurs supplémentaires facultatifs à l’aide du `new` mot clé. Ces constructeurs supplémentaires doivent appeler le constructeur principal.

Le constructeur principal contient `let` des `do` liaisons et qui s’affichent au début de la définition de classe. Une `let` liaison déclare des champs et des méthodes privés de la classe ; une `do` liaison exécute du code. Pour plus d’informations sur les `let` liaisons dans les constructeurs de classe, consultez [ `let` liaisons dans les classes](let-bindings-in-classes.md). Pour plus d’informations sur les `do` liaisons dans les constructeurs, consultez [ `do` liaisons dans les classes](do-bindings-in-classes.md).

Que le constructeur que vous souhaitez appeler soit un constructeur principal ou un constructeur supplémentaire, vous pouvez créer des objets à l’aide d’une `new` expression, avec ou sans le `new` mot clé facultatif. Vous initialisez vos objets avec les arguments de constructeur, soit en répertoriant les arguments dans l’ordre et en les séparant par des virgules et placés entre parenthèses, soit en utilisant des arguments nommés et des valeurs entre parenthèses. Vous pouvez également définir des propriétés sur un objet pendant la construction de l’objet en utilisant les noms de propriété et en assignant des valeurs de la même façon que vous utilisez des arguments de constructeur nommé.

Le code suivant illustre une classe qui a un constructeur et différentes manières de créer des objets :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

La sortie se présente comme suit :

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Construction de structures

Les structures suivent toutes les règles des classes. Par conséquent, vous pouvez avoir un constructeur principal et vous pouvez fournir des constructeurs supplémentaires à l’aide de `new` . Toutefois, il existe une différence importante entre les structures et les classes : les structures peuvent avoir un constructeur sans paramètre (autrement dit, un sans argument) même si aucun constructeur principal n’est défini. Le constructeur sans paramètre initialise tous les champs à la valeur par défaut de ce type, généralement zéro ou son équivalent. Les constructeurs que vous définissez pour les structures doivent avoir au moins un argument afin qu’ils n’entrent pas en conflit avec le constructeur sans paramètre.

En outre, les structures ont souvent des champs qui sont créés à l’aide du `val` mot clé ; les classes peuvent également avoir ces champs. Les structures et les classes qui ont des champs définis à l’aide du `val` mot clé peuvent également être initialisées dans des constructeurs supplémentaires à l’aide d’expressions d’enregistrement, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Pour plus d’informations, consultez [champs explicites : le `val` mot clé](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Exécution d’effets secondaires dans les constructeurs

Un constructeur principal dans une classe peut exécuter du code dans une `do` liaison. Toutefois, que se passe-t-il si vous devez exécuter du code dans un constructeur supplémentaire, sans `do` liaison ? Pour ce faire, vous utilisez le `then` mot clé.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Les effets secondaires du constructeur principal s’exécutent toujours. Par conséquent, la sortie est la suivante :

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

La raison pour laquelle `then` est requis au lieu d’un autre `do` est que le `do` mot clé a sa signification standard de délimiter une `unit` expression de retour lorsqu’elle est présente dans le corps d’un constructeur supplémentaire. Il a une signification particulière dans le contexte des constructeurs principaux.

## <a name="self-identifiers-in-constructors"></a>Identificateurs automatiques dans les constructeurs

Dans les autres membres, vous fournissez un nom pour l’objet actuel dans la définition de chaque membre. Vous pouvez également placer l’auto-identificateur sur la première ligne de la définition de classe en utilisant le `as` mot clé immédiatement après les paramètres du constructeur. L’exemple suivant illustre cette syntaxe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

Dans les constructeurs supplémentaires, vous pouvez également définir un auto-identificateur en plaçant la `as` clause juste après les paramètres du constructeur. L’exemple suivant illustre cette syntaxe :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Des problèmes peuvent se produire lorsque vous essayez d’utiliser un objet avant qu’il soit entièrement défini. Par conséquent, les utilisations de l’auto-identificateur peuvent entraîner l’émission d’un avertissement par le compilateur et l’insertion de vérifications supplémentaires pour s’assurer que les membres d’un objet ne sont pas accessibles avant l’initialisation de l’objet. Vous devez uniquement utiliser l’auto-identificateur dans les `do` liaisons du constructeur principal, ou après le `then` mot clé dans les constructeurs supplémentaires.

Il n’est pas nécessaire que le nom de l’auto-identificateur soit `this` . Il peut s’agir de n’importe quel identificateur valide.

## <a name="assigning-values-to-properties-at-initialization"></a>Assigner des valeurs aux propriétés lors de l’initialisation

Vous pouvez assigner des valeurs aux propriétés d’un objet de classe dans le code d’initialisation en ajoutant une liste d’assignations du formulaire `property = value` à la liste d’arguments d’un constructeur. Cela est illustré par l'exemple de code suivant :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

La version suivante du code précédent illustre la combinaison d’arguments ordinaires, d’arguments facultatifs et de paramètres de propriété dans un appel de constructeur :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Constructeurs dans la classe héritée

Lorsque vous héritez d’une classe de base qui a un constructeur, vous devez spécifier ses arguments dans la clause Inherit. Pour plus d’informations, consultez [constructeurs et héritage](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Constructeurs statiques ou constructeurs de type

En plus de spécifier du code pour la création d’objets, des liaisons et des statiques `let` `do` peuvent être créés dans des types de classe qui s’exécutent avant que le type ne soit utilisé pour la première fois au niveau du type. Pour plus d’informations, consultez [ `let` liaisons dans les classes](let-bindings-in-classes.md) et [ `do` liaisons dans les classes](do-bindings-in-classes.md).

## <a name="see-also"></a>Voir aussi

- [Membres](index.md)
