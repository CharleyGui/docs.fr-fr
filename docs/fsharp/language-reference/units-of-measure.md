---
title: Unités de mesure
description: 'Découvrez comment les valeurs entières et signées de virgule flottante en F # peuvent être associées à des unités de mesure, qui sont généralement utilisées pour indiquer la longueur, le volume et la masse.'
ms.date: 08/15/2020
ms.openlocfilehash: 0262f89e80697dd86161c93fe37381122972b56f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811572"
---
# <a name="units-of-measure"></a>Unités de mesure

Les valeurs de type virgule flottante et entier signé en F # peuvent être associées à des unités de mesure, qui sont généralement utilisées pour indiquer la longueur, le volume, la masse, etc. En utilisant des quantités avec des unités, vous permettez au compilateur de vérifier que les relations arithmétiques disposent des unités appropriées, ce qui permet d’éviter les erreurs de programmation.

## <a name="syntax"></a>Syntaxe

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>Notes

La syntaxe précédente définit *unit-name* comme unité de mesure. La partie facultative est utilisée pour définir une nouvelle mesure en termes d’unités précédemment définies. Par exemple, la ligne suivante définit la mesure `cm` (centimètre).

```fsharp
[<Measure>] type cm
```

La ligne suivante définit la mesure `ml` (milliliter) en tant que centimètre cube ( `cm^3` ).

```fsharp
[<Measure>] type ml = cm^3
```

Dans la syntaxe précédente, *measure* est une formule qui implique des unités. Dans les formules qui impliquent des unités, les puissances entières sont prises en charge (positives et négatives), les espaces entre les unités indiquent un produit des deux unités, indiquent `*` également un produit d’unités et `/` indiquent un quotient d’unités. Pour une unité réciproque, vous pouvez utiliser un entier négatif ou une valeur `/` qui indique une séparation entre le numérateur et le dénominateur d’une formule d’unité. Les unités multiples dans le dénominateur doivent être placées entre parenthèses. Les unités séparées par des espaces après un `/` sont interprétées comme faisant partie du dénominateur, mais toutes les unités qui suivent un `*` sont interprétées comme faisant partie du numérateur.

Vous pouvez utiliser 1 dans les expressions d’unité, soit pour indiquer une quantité sans dimension, soit avec d’autres unités, comme dans le numérateur. Par exemple, les unités d’un taux sont écrites sous la forme `1/s` , où `s` indique des secondes. Les parenthèses ne sont pas utilisées dans les formules d’unité. Vous ne spécifiez pas de constantes de conversion numérique dans les formules d’unité ; Toutefois, vous pouvez définir des constantes de conversion avec des unités séparément et les utiliser dans des calculs Check Unit.

Les formules d’unités qui signifient la même chose peuvent être écrites de différentes façons équivalentes. Par conséquent, le compilateur convertit les formules d’unités sous une forme cohérente, ce qui convertit les puissances négatives en valeurs réciproques, regroupe les unités en un seul numérateur et un dénominateur, et alphabetizes les unités dans le numérateur et le dénominateur.

Par exemple, les formules `kg m s^-2` d’unité et `m /s s * kg` sont toutes deux converties en `kg m/s^2` .

Les unités de mesure sont utilisées dans les expressions à virgule flottante. L’utilisation de nombres à virgule flottante avec des unités de mesure associées ajoute un autre niveau de sécurité de type et permet d’éviter les erreurs d’incompatibilité d’unités qui peuvent se produire dans les formules lorsque vous utilisez des nombres à virgule flottante faiblement typés. Si vous écrivez une expression à virgule flottante qui utilise des unités, les unités de l’expression doivent correspondre.

Vous pouvez annoter des littéraux à l’aide d’une formule d’unité entre crochets pointus, comme indiqué dans les exemples suivants.

```fsharp
1.0<cm>
55.0<miles/hour>
```

Vous ne placez pas d’espace entre le nombre et le Chevron ; Toutefois, vous pouvez inclure un suffixe littéral, tel que `f` , comme dans l’exemple suivant.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

Une telle annotation modifie le type du littéral de son type primitif (tel que `float` ) en un type dimensionné, tel que `float<cm>` ou, dans ce cas, `float<miles/hour>` . Une annotation d’unité de `<1>` indique une quantité sans dimension, et son type est équivalent au type primitif sans paramètre d’unité.

Le type d’une unité de mesure est une virgule flottante ou un type intégral signé avec une annotation d’unité supplémentaire, indiquée entre crochets. Ainsi, lorsque vous écrivez le type d’une conversion de `g` (grammes) à `kg` (kilogrammes), vous décrivez les types comme suit.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

Les unités de mesure sont utilisées pour la vérification des unités au moment de la compilation, mais ne sont pas conservées dans l’environnement d’exécution. Par conséquent, elles n’affectent pas les performances.

Les unités de mesure peuvent être appliquées à n’importe quel type, pas seulement aux types à virgule flottante ; Toutefois, seuls les types à virgule flottante, les types intégraux signés et les types décimaux prennent en charge les quantités dimensionnelles. Par conséquent, il est judicieux d’utiliser des unités de mesure sur les types primitifs et sur les agrégats qui contiennent ces types primitifs.

L’exemple suivant illustre l’utilisation d’unités de mesure.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

L’exemple de code suivant montre comment convertir un nombre à virgule flottante sans dimension en valeur à virgule flottante dimensionnée. Vous multipliez simplement par 1,0, en appliquant les dimensions aux 1,0. Vous pouvez l’extraire dans une fonction comme `degreesFahrenheit` .

En outre, lorsque vous transmettez des valeurs dimensionnées à des fonctions qui attendent des nombres à virgule flottante sans dimension, vous devez annuler les unités ou effectuer un cast en à `float` l’aide de l' `float` opérateur. Dans cet exemple, vous divisez par `1.0<degC>` pour les arguments à `printf` , car `printf` attend des quantités sans dimension.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

L’exemple de session suivant montre les sorties de et les entrées de ce code.

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>Utilisation d’unités génériques

Vous pouvez écrire des fonctions génériques qui opèrent sur des données qui ont une unité de mesure associée. Pour ce faire, vous devez spécifier un type avec une unité générique comme paramètre de type, comme indiqué dans l’exemple de code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a>Création de types d’agrégats avec des unités génériques

Le code suivant montre comment créer un type d’agrégat qui se compose de valeurs à virgule flottante individuelles qui ont des unités génériques. Cela permet de créer un type unique qui fonctionne avec diverses unités. En outre, les unités génériques préservent la cohérence des types en s’assurant qu’un type générique qui a un ensemble d’unités est un type différent du même type générique avec un autre ensemble d’unités. La base de cette technique est que l' `Measure` attribut peut être appliqué au paramètre de type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a>Unités au moment de l’exécution

Les unités de mesure sont utilisées pour la vérification de type statique. Lorsque les valeurs à virgule flottante sont compilées, les unités de mesure sont éliminées, de sorte que les unités sont perdues au moment de l’exécution. Par conséquent, toute tentative d’implémentation de la fonctionnalité qui dépend de la vérification des unités au moment de l’exécution n’est pas possible. Par exemple, l’implémentation d’une `ToString` fonction pour imprimer les unités n’est pas possible.

## <a name="conversions"></a>Conversions

Pour convertir un type qui a des unités (par exemple, `float<'u>` ) en un type qui n’a pas d’unités, vous pouvez utiliser la fonction de conversion standard. Par exemple, vous pouvez utiliser `float` pour convertir en une `float` valeur qui n’a pas d’unités, comme illustré dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

Pour convertir une valeur sans unité en une valeur qui a des unités, vous pouvez multiplier par une valeur 1 ou 1,0 qui est annotée avec les unités appropriées. Toutefois, pour écrire des couches d’interopérabilité, il existe également des fonctions explicites que vous pouvez utiliser pour convertir des valeurs sans unité en valeurs avec unités. Celles-ci se trouvent dans le module [FSharp. Core. LanguagePrimitives](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) . Par exemple, pour effectuer une conversion d’une unité sans unité `float` en `float<cm>` , utilisez [FloatWithMeasure](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure), comme indiqué dans le code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a>Unités de mesure dans la bibliothèque principale F #

Une bibliothèque d’unités est disponible dans l' `FSharp.Data.UnitSystems.SI` espace de noms. Elle comprend des unités SI dans leur forme de symbole (comme `m` pour le compteur) dans le `UnitSymbols` sous-espace de noms, et leur nom complet (comme `meter` pour le compteur) dans le `UnitNames` sous-espace de noms.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
