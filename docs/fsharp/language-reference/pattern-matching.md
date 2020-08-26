---
title: Critères spéciaux
description: 'Découvrez comment les modèles sont utilisés en F # pour comparer des données avec des structures logiques, décomposer des données en parties constituantes ou extraire des informations à partir de données.'
ms.date: 08/15/2020
ms.openlocfilehash: 6d284b941824bc15a8e872a4e28e22c0e159191d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811507"
---
# <a name="pattern-matching"></a>Critères spéciaux

Les modèles sont des règles de transformation des données d’entrée. Ils sont utilisés dans le langage F # pour comparer des données avec une structure logique ou des structures, décomposer des données en parties constitutives ou extraire des informations de données de différentes façons.

## <a name="remarks"></a>Notes

Les modèles sont utilisés dans de nombreuses constructions de langage, telles que l' `match` expression. Elles sont utilisées lorsque vous traitez des arguments pour les fonctions dans `let` les liaisons, les expressions lambda et dans les gestionnaires d’exceptions associés à l' `try...with` expression. Pour plus d’informations, [consultez expressions de correspondance](match-expressions.md), [liaisons Let](./functions/let-bindings.md), [expressions lambda : le `fun` mot clé](./functions/lambda-expressions-the-fun-keyword.md)et [exceptions : l' `try...with` expression](./exception-handling/the-try-with-expression.md).

Par exemple, dans l' `match` expression, le *modèle* correspond à ce qui suit le symbole de barre verticale.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Chaque modèle agit comme une règle de transformation d’entrée d’une certaine façon. Dans l' `match` expression, chaque modèle est examiné à son tour pour déterminer si les données d’entrée sont compatibles avec le modèle. Si une correspondance est trouvée, l’expression de résultat est exécutée. Si aucune correspondance n’est trouvée, la règle de modèle suivante est testée. Le composant facultatif when *condition* est expliqué dans [expressions de correspondance](match-expressions.md).

Les modèles pris en charge sont présentés dans le tableau suivant. Au moment de l’exécution, l’entrée est testée par rapport à chacun des modèles suivants dans l’ordre indiqué dans le tableau, et les modèles sont appliqués de manière récursive, de la première à la dernière telle qu’ils apparaissent dans votre code, et de gauche à droite pour les modèles sur chaque ligne.

|Nom|Description|Exemple|
|----|-----------|-------|
|Modèle de constante|Tout littéral numérique, de caractère ou de chaîne, une constante d’énumération ou un identificateur littéral défini|`1.0`, `"test"`, `30`, `Color.Red`|
|Modèle d’identificateur|Une valeur case d’une union discriminée, une étiquette d’exception ou un cas de modèle actif|`Some(x)`<br /><br />`Failure(msg)`|
|Modèle de variable|*identificateur*|`a`|
|`as` répétition|*modèle* en tant qu' *identificateur*|`(a, b) as tuple1`|
|OU modèle|*pattern1* &#124; *pattern2*|<code>([h] &#124; [h; _])</code>|
|ET modèle|*pattern1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Modèle cons|*identificateur* :: *List-identifier*|`h :: t`|
|Modèle de liste|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Modèle de tableau|[&#124; *pattern_1*;..; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Modèle entre parenthèses|( *modèle* )|`( a )`|
|Modèle de Tuple|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Modèle d’enregistrement|{ *identificateur1*  =  *pattern_1*; ... ; *identifier_n*  =  *pattern_n* }|`{ Name = name; }`|
|Modèle de caractère générique|_|`_`|
|Modèle avec annotation de type|*modèle* : *type*|`a : int`|
|Modèle de test de type|:? *type* [ *identificateur* ]|`:? System.DateTime as dt`|
|Modèle null|null|`null`|

## <a name="constant-patterns"></a>Modèles de constante

Les modèles de constantes sont des littéraux numériques, de caractère et de chaîne, des constantes d’énumération (avec le nom du type d’énumération inclus). Une `match` expression qui possède uniquement des modèles de constantes peut être comparée à une instruction case dans d’autres langages. L’entrée est comparée à la valeur littérale et le modèle correspond si les valeurs sont égales. Le type du littéral doit être compatible avec le type de l’entrée.

L’exemple suivant illustre l’utilisation de modèles littéraux et utilise également un modèle de variable et un modèle ou.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Un autre exemple de modèle littéral est un modèle basé sur des constantes d’énumération. Vous devez spécifier le nom du type d’énumération lorsque vous utilisez des constantes d’énumération.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Modèles d’identificateur

Si le modèle est une chaîne de caractères qui forme un identificateur valide, le formulaire de l’identificateur détermine la façon dont le modèle est mis en correspondance. Si l’identificateur est plus long qu’un caractère unique et commence par un caractère majuscule, le compilateur tente d’établir une correspondance avec le modèle d’identificateur. L’identificateur de ce modèle peut être une valeur marquée avec l’attribut Literal, un cas d’union discriminée, un identificateur d’exception ou un cas de modèle actif. Si aucun identificateur correspondant n’est trouvé, la correspondance échoue et la règle de modèle suivante, le modèle de variable, est comparée à l’entrée.

Les modèles d’union discriminée peuvent être des cas nommés simples ou ils peuvent avoir une valeur, ou un tuple contenant plusieurs valeurs. S’il y a une valeur, vous devez spécifier un identificateur pour la valeur. Dans le cas d’un tuple, vous devez fournir un modèle de tuple avec un identificateur pour chaque élément du tuple ou un identificateur avec un nom de champ pour un ou plusieurs champs d’Union nommés. Consultez les exemples de code de cette section pour obtenir des exemples.

Le `option` type est une union discriminée qui a deux cas, `Some` et `None` . Un cas ( `Some` ) a une valeur, mais l’autre ( `None` ) est simplement un cas nommé. Par conséquent, `Some` doit avoir une variable pour la valeur associée à la `Some` casse, mais `None` doit s’afficher par lui-même. Dans le code suivant, la variable `var1` reçoit la valeur obtenue en faisant correspondre le `Some` cas.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

Dans l’exemple suivant, l' `PersonName` union discriminée contient un mélange de chaînes et de caractères qui représentent les formes possibles des noms. Les cas de l’union discriminée sont `FirstOnly` , `LastOnly` et `FirstLast` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Pour les unions discriminées qui ont des champs nommés, vous utilisez le signe égal (=) pour extraire la valeur d’un champ nommé. Par exemple, considérez une union discriminée avec une déclaration semblable à la suivante.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

Vous pouvez utiliser les champs nommés dans une expression de critères spéciaux comme suit.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

L’utilisation du champ nommé est facultative. par conséquent, dans l’exemple précédent, les deux `Circle(r)` et `Circle(radius = r)` ont le même effet.

Lorsque vous spécifiez plusieurs champs, utilisez le point-virgule (;) comme séparateur.

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

Les modèles actifs vous permettent de définir des critères spéciaux personnalisés plus complexes. Pour plus d’informations sur les modèles actifs, consultez [modèles actifs](active-patterns.md).

Le cas dans lequel l’identificateur est une exception est utilisé dans les critères spéciaux dans le contexte des gestionnaires d’exceptions. Pour plus d’informations sur les critères spéciaux dans la gestion des exceptions, consultez [exceptions : l' `try...with` expression](./exception-handling/the-try-with-expression.md).

## <a name="variable-patterns"></a>Modèles de variables

Le modèle de variable affecte la valeur mise en correspondance à un nom de variable, qui peut ensuite être utilisée dans l’expression d’exécution à droite du `->` symbole. Un modèle de variable ne correspond à aucune entrée, mais les modèles de variable apparaissent souvent dans d’autres modèles, ce qui permet de décomposer les structures plus complexes, telles que les tuples et les tableaux, en variables.

L’exemple suivant illustre un modèle de variable dans un modèle de Tuple.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>Modèle As

Le `as` modèle est un modèle auquel une `as` clause est ajoutée. La `as` clause lie la valeur correspondante à un nom qui peut être utilisé dans l’expression d’exécution d’une `match` expression, ou, dans le cas où ce modèle est utilisé dans une `let` liaison, le nom est ajouté en tant que liaison à la portée locale.

L’exemple suivant utilise un `as` modèle.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>OU modèle

Le modèle ou est utilisé lorsque les données d’entrée peuvent correspondre à plusieurs modèles et que vous souhaitez exécuter le même code en tant que résultat. Les types des deux côtés du modèle ou doivent être compatibles.

L’exemple suivant illustre le modèle ou.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>ET modèle

Le modèle et requiert que l’entrée corresponde à deux modèles. Les types des deux côtés du modèle et doivent être compatibles.

L’exemple suivant est similaire `detectZeroTuple` à celui présenté dans la section modèle de tuple plus loin dans cette rubrique, mais ici `var1` et `var2` sont obtenus comme valeurs à l’aide du modèle et.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Modèle cons

Le modèle cons est utilisé pour décomposer une liste en premier élément, l' *en-tête*et une liste qui contient les éléments restants, la *fin*.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Modèle de liste

Le modèle de liste permet de décomposer des listes en plusieurs éléments. Le modèle de liste lui-même peut mettre en correspondance uniquement les listes d’un nombre spécifique d’éléments.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Modèle de tableau

Le modèle de tableau ressemble au modèle de liste et peut être utilisé pour décomposer des tableaux d’une longueur spécifique.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Modèle entre parenthèses

Les parenthèses peuvent être regroupées autour des modèles pour atteindre l’associativité souhaitée. Dans l’exemple suivant, les parenthèses sont utilisées pour contrôler l’associativité entre un modèle et et un modèle cons.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Modèle de Tuple

Le modèle de tuple correspond à l’entrée sous forme de tuple et permet de décomposer le tuple en éléments constitutifs à l’aide de variables de critères spéciaux pour chaque position dans le tuple.

L’exemple suivant illustre le modèle de tuple et utilise également des modèles de littéral, des modèles de variable et le modèle de caractère générique.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Modèle d’enregistrement

Le modèle d’enregistrement est utilisé pour décomposer les enregistrements afin d’extraire les valeurs des champs. Le modèle n’a pas besoin de référencer tous les champs de l’enregistrement ; tout champ omis ne fait pas partie de la correspondance et n’est pas extrait.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Modèle de caractère générique

Le modèle de caractère générique est représenté par le caractère de soulignement ( `_` ) et correspond à toute entrée, comme le modèle de variable, sauf que l’entrée est ignorée au lieu d’être affectée à une variable. Le modèle de caractère générique est souvent utilisé dans d’autres modèles comme un espace réservé pour les valeurs qui ne sont pas nécessaires dans l’expression à droite du `->` symbole. Le modèle de caractère générique est également fréquemment utilisé à la fin d’une liste de modèles pour faire correspondre n’importe quelle entrée sans correspondance. Le modèle de caractère générique est illustré dans de nombreux exemples de code de cette rubrique. Pour obtenir un exemple, consultez le code précédent.

## <a name="patterns-that-have-type-annotations"></a>Modèles avec des annotations de type

Les modèles peuvent avoir des annotations de type. Ils se comportent comme d’autres annotations de type et l’inférence de guide comme d’autres annotations de type. Les parenthèses sont requises autour des annotations de type dans les modèles. Le code suivant illustre un modèle qui a une annotation de type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Modèle de test de type

Le modèle de test de type est utilisé pour faire correspondre l’entrée à un type. Si le type d’entrée correspond à (ou à un type dérivé de) le type spécifié dans le modèle, la correspondance est établie.

L’exemple suivant illustre le modèle de test de type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

Si vous vérifiez uniquement si un identificateur est d’un type dérivé particulier, vous n’avez pas besoin `as identifier` de la partie du modèle, comme illustré dans l’exemple suivant :

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a>Modèle null

Le modèle null correspond à la valeur null qui peut s’afficher lorsque vous utilisez des types qui autorisent une valeur null. Les modèles NULL sont fréquemment utilisés lors de l’interopérabilité avec .NET Framework code. Par exemple, la valeur de retour d’une API .NET peut être l’entrée d’une `match` expression. Vous pouvez contrôler le déroulement du programme selon que la valeur de retour est null et également d’autres caractéristiques de la valeur retournée. Vous pouvez utiliser le modèle null pour empêcher la propagation de valeurs Null vers le reste de votre programme.

L’exemple suivant utilise le modèle null et le modèle de variable.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Voir aussi

- [Expressions de correspondance](match-expressions.md)
- [Modèles actifs](active-patterns.md)
- [Informations de référence sur le langage F #](index.md)
