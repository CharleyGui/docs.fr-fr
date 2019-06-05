---
title: Modèles actifs
description: Découvrez comment utiliser des modèles actifs pour définir des partitions nommées qui subdivisent les données d’entrée dans le F# langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: 25ab255574390d3761fe788aeb413c8ee04fda2a
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690413"
---
# <a name="active-patterns"></a>Modèles actifs

*Modèles actifs* vous permettent de définir des partitions nommées qui subdivisent les données d’entrée, afin que vous pouvez utiliser ces noms dans un modèle d’expression de critères comme vous le feriez pour une union discriminée. Vous pouvez utiliser des modèles actifs pour décomposer des données de façon personnalisée pour chaque partition.

## <a name="syntax"></a>Syntaxe

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, les identificateurs sont des noms pour les partitions des données d’entrée qui sont représentées par *arguments*, ou, en d’autres termes, les noms des sous-ensembles du jeu de toutes les valeurs des arguments. Il peut y avoir jusqu'à sept partitions dans une définition de modèle actif. Le *expression* décrit le formulaire décomposition des données. Vous pouvez utiliser une définition de modèle actif pour définir les règles pour déterminer la partition nommée les valeurs fournies comme arguments appartiennent. Le (| et |) les symboles sont appelés *« banana clips »* et la fonction créée par ce type de liaison let est appelée un *module de reconnaissance active*.

Par exemple, considérons le modèle actif suivant avec un argument.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Vous pouvez utiliser le modèle actif dans une expression, comme dans l’exemple suivant de critères spéciaux.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

La sortie de ce programme est comme suit :

```
7 is odd
11 is odd
32 is even
```

Une autre utilisation de modèles actifs consiste à décomposer les types de données de plusieurs façons, par exemple lorsque les mêmes données sous-jacentes ont différentes représentations possible. Par exemple, un `Color` objet peut être décomposé en représentation RVB ou en représentation TSL.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

La sortie du programme ci-dessus est la suivante :

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

Conjointement, ces deux façons d’utiliser des modèles actifs vous permettent de partition et décomposent les données en une forme adéquate et effectuer les calculs appropriés sur les données appropriées sous la forme la plus commode pour le calcul.

Les expressions de critères spéciaux qui en résulte activer les données à écrire dans un moyen pratique qui est très lisible, simplifiant ainsi considérablement le branchement potentiellement complexe et le code d’analyse de données.

## <a name="partial-active-patterns"></a>Modèles actifs partiels

Parfois, vous devez uniquement une partie de l’espace d’entrée de partition. Dans ce cas, vous écrivez un jeu de modèles partiels, chacun d'entre eux correspondant à certaines entrées mais pas à d’autres entrées. Modèles actifs qui ne produisent pas toujours une valeur sont appelées *modèles actifs partiels*; ils ont une valeur de retour est un type d’option. Pour définir un modèle actif partiel, vous utilisez un caractère générique (\_) à la fin de la liste des modèles à l’intérieur des « banana clips ». Le code suivant illustre l’utilisation d’un modèle actif partiel.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

La sortie de l’exemple précédent est comme suit :

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Lorsque vous utilisez des modèles actifs partiels, parfois les choix individuels peuvent être disjoints ou mutuellement exclusifs, mais ils ne sont pas nécessairement. Dans l’exemple suivant, le carré de modèle et le modèle de Cube ne sont pas disjoints, car certains nombres sont des carrés et des cubes, tels que 64. Le programme suivant utilise le modèle AND pour combiner les modèles carré et du Cube. Il imprime tous les entiers jusqu'à 1 000 qui sont à la fois des carrés et des cubes, ainsi que celles qui sont uniquement des cubes. 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

La sortie est la suivante :

```
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a>Modèles actifs paramétrables

Modèles actifs prennent toujours au moins un argument pour l’élément en cours de mise en correspondance, mais ils peuvent également prendre des arguments supplémentaires, auquel cas le nom *modèle actif paramétrable* s’applique. Arguments supplémentaires permettent de spécialiser un modèle général. Par exemple, des modèles actifs qui utilisent des expressions régulières pour analyser des chaînes souvent incluent l’expression régulière comme paramètre supplémentaire, comme dans le code suivant, qui utilise également le modèle actif partiel `Integer` défini dans l’exemple de code précédent. Dans cet exemple, les chaînes qui utilisent des expressions régulières pour différents formats de date sont données pour personnaliser le modèle actif ParseRegex général. Le modèle actif Integer est utilisé pour convertir les chaînes de mise en correspondance en entiers qui peuvent être passés au constructeur DateTime.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

La sortie du code précédent est comme suit :

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Modèles actifs ne sont pas limitées uniquement aux expressions de correspondance de modèle, vous pouvez également les utiliser sur les liaisons de let.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

La sortie du code précédent est comme suit :

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Expressions match](match-expressions.md)
