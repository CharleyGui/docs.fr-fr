---
title: Liaisons let
description: "Apprenez à utiliser une liaison F # 'Let', qui associe un identificateur à une valeur ou à une fonction."
ms.date: 05/16/2016
ms.openlocfilehash: 6f2396f480c5e6c631d0022f4732419ee5b07db6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812222"
---
# <a name="let-bindings"></a>Liaisons let

Une *liaison* associe un identificateur à une valeur ou à une fonction. Vous utilisez le `let` mot clé pour lier un nom à une valeur ou à une fonction.

## <a name="syntax"></a>Syntaxe

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Notes

Le `let` mot clé est utilisé dans les expressions de liaison pour définir des valeurs ou des valeurs de fonction pour un ou plusieurs noms. La forme la plus simple de l' `let` expression lie un nom à une valeur simple, comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Si vous séparez l’expression de l’identificateur à l’aide d’une nouvelle ligne, vous devez mettre en retrait chaque ligne de l’expression, comme dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Au lieu d’un simple nom, un modèle qui contient des noms peut être spécifié, par exemple, un tuple, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Body-expression* est l’expression dans laquelle les noms sont utilisés. L’expression de corps apparaît sur sa propre ligne, mise en retrait pour s’aligner exactement avec le premier caractère du `let` mot clé :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

Une `let` liaison peut apparaître au niveau du module, dans la définition d’un type de classe ou dans des portées locales, comme dans une définition de fonction. Une `let` liaison au niveau supérieur d’un module ou dans un type de classe n’a pas besoin d’une expression de corps, mais à d’autres niveaux de portée, l’expression de corps est requise. Les noms liés sont utilisables après le point de définition, mais pas à un moment donné avant que la `let` liaison n’apparaisse, comme illustré dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>Liaisons de fonction

Les liaisons de fonction suivent les règles pour les liaisons de valeur, à ceci près que les liaisons de fonction incluent le nom de la fonction et les paramètres, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

En général, les paramètres sont des modèles, tels qu’un modèle de tuple :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

Une `let` expression de liaison prend la valeur de la dernière expression. Par conséquent, dans l’exemple de code suivant, la valeur de `result` est calculée à partir de `100 * function3 (1, 2)` , qui prend la valeur `300` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Pour plus d’informations, consultez [Fonctions](index.md).

## <a name="type-annotations"></a>Annotations de type

Vous pouvez spécifier des types pour les paramètres en incluant un signe deux-points ( :) suivi d’un nom de type, tous mis entre parenthèses. Vous pouvez également spécifier le type de la valeur de retour en ajoutant le signe deux-points et le type après le dernier paramètre. Les annotations de type complètes pour `function1` , avec des entiers comme types de paramètres, se présenteront comme suit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Lorsqu’il n’existe aucun paramètre de type explicite, l’inférence de type est utilisée pour déterminer les types de paramètres des fonctions. Cela peut inclure la généralisation automatique du type d’un paramètre à générique.

Pour plus d’informations, consultez [généralisation automatique](../generics/automatic-generalization.md) et [inférence de type](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Liaisons let dans des classes

Une `let` liaison peut apparaître dans un type de classe, mais pas dans une structure ou un type d’enregistrement. Pour utiliser une liaison Let dans un type de classe, la classe doit avoir un constructeur principal. Les paramètres de constructeur doivent apparaître après le nom de type dans la définition de classe. Une `let` liaison dans un type de classe définit des champs et des membres privés pour ce type de classe et, ainsi que des `do` liaisons dans le type, forme le code pour le constructeur principal du type. Les exemples de code suivants illustrent une classe `MyClass` avec des champs privés `field1` et `field2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Les portées de `field1` et `field2` sont limitées au type dans lequel elles sont déclarées. Pour plus d’informations, consultez [ `let` liaisons dans les classes](../members/let-bindings-in-classes.md) et les [classes](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Paramètres de type dans les liaisons Let

Une `let` liaison au niveau du module, dans un type ou dans une expression de calcul peut avoir des paramètres de type explicite. Une liaison Let dans une expression, telle que dans une définition de fonction, ne peut pas avoir de paramètres de type. Pour plus d’informations, consultez [Génériques](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Attributs sur les liaisons Let

Les attributs peuvent être appliqués aux `let` liaisons de niveau supérieur dans un module, comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Portée et accessibilité des liaisons Let

La portée d’une entité déclarée avec une liaison Let est limitée à la partie de l’étendue contenante (telle qu’une fonction, un module, un fichier ou une classe) une fois la liaison affichée. Par conséquent, il peut être dit qu’une liaison Let introduit un nom dans une portée. Dans un module, une valeur ou une fonction avec liaison Let est accessible aux clients d’un module tant que le module est accessible, puisque les liaisons Let dans un module sont compilées dans les fonctions publiques du module. En revanche, les liaisons Let dans une classe sont privées pour la classe.

Normalement, les fonctions dans les modules doivent être qualifiées par le nom du module lorsqu’elles sont utilisées par le code client. Par exemple, si un module `Module1` possède une fonction `function1` , les utilisateurs doivent spécifier `Module1.function1` pour faire référence à la fonction.

Les utilisateurs d’un module peuvent utiliser une déclaration d’importation pour rendre les fonctions contenues dans ce module disponibles pour une utilisation sans être qualifiées par le nom du module. Dans l’exemple qui vient d’être mentionné, les utilisateurs du module peuvent, dans ce cas, ouvrir le module à l’aide de la déclaration d’importation ouverte `Module1` , puis faire référence `function1` directement à.

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

Certains modules ont l’attribut [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), ce qui signifie que les fonctions qu’ils exposent doivent être qualifiées avec le nom du module. Par exemple, le module de liste F # a cet attribut.

Pour plus d’informations sur les modules et le contrôle d’accès, consultez [modules](../modules.md) et [Access Control](../access-control.md).

## <a name="see-also"></a>Voir aussi

- [Fonctions](index.md)
- [`let` Liaisons dans des classes](../members/let-bindings-in-classes.md)
