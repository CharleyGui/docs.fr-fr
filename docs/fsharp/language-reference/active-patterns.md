---
title: Modèles actifs
description: Apprenez à utiliser des modèles actifs pour définir les partitions nommées qui subdivisent les données d’entrée dans le langage de programmation de F.
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187061"
---
# <a name="active-patterns"></a>Modèles actifs

*Les modèles actifs* vous permettent de définir les partitions nommées qui subdivisent les données d’entrée, de sorte que vous puissiez utiliser ces noms dans une expression de correspondance de modèle comme vous le feriez pour une union discriminée. Vous pouvez utiliser des modèles actifs pour décomposer des données de façon personnalisée pour chaque partition.

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

Dans la syntaxe précédente, les identifiants sont des noms pour les partitions des données d’entrée qui sont représentées par *des arguments,* ou, en d’autres termes, des noms pour les sous-ensembles de l’ensemble de toutes les valeurs des arguments. Il peut y avoir jusqu’à sept partitions dans une définition de modèle actif. *L’expression* décrit la forme dans laquelle décomposer les données. Vous pouvez utiliser une définition de modèle actif pour définir les règles permettant de déterminer laquelle des partitions nommées les valeurs données comme arguments appartiennent. Les symboles (et ) sont appelés *clips* bananes et la fonction créée par ce type de reliure de laisser est appelée *un reconnaisseur actif*.

À titre d’exemple, considérez le modèle actif suivant avec un argument.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Vous pouvez utiliser le modèle actif dans une expression de correspondance de modèle, comme dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

La sortie de ce programme est la suivante :

```console
7 is odd
11 is odd
32 is even
```

Une autre utilisation de modèles actifs consiste à décomposer les types de données de multiples façons, par exemple lorsque les mêmes données sous-jacentes ont diverses représentations possibles. Par exemple, `Color` un objet peut être décomposé en une représentation RGB ou une représentation HSB.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

La sortie du programme ci-dessus est la suivante :

```console
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

En combinaison, ces deux façons d’utiliser des modèles actifs vous permettent de cloisonner et de décomposer les données dans la forme appropriée et d’effectuer les calculs appropriés sur les données appropriées sous la forme la plus pratique pour le calcul.

Les expressions de correspondance de modèles qui en résultent permettent d’écrire des données d’une manière pratique qui est très lisible, simplifiant considérablement le code de branchement et d’analyse des données potentiellement complexe.

## <a name="partial-active-patterns"></a>Modèles actifs partiels

Parfois, vous devez diviser seulement une partie de l’espace d’entrée. Dans ce cas, vous écrivez un ensemble de modèles partiels qui correspondent à certaines entrées, mais ne parviennent pas à correspondre à d’autres entrées. Les modèles actifs qui ne produisent pas toujours une valeur sont appelés *modèles actifs partiels*; ils ont une valeur de retour qui est un type d’option. Pour définir un modèle actif partiel, vous\_utilisez un personnage wildcard ( ) à la fin de la liste des motifs à l’intérieur des clips banane. Le code suivant illustre l’utilisation d’un modèle actif partiel.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

La sortie de l’exemple précédent est la suivante :

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Lorsque vous utilisez des modèles actifs partiels, parfois les choix individuels peuvent être disjoints ou mutuellement exclusifs, mais ils n’ont pas besoin de l’être. Dans l’exemple suivant, le motif Square et le motif Cube ne sont pas disjoints, parce que certains nombres sont à la fois carrés et cubes, tels que 64. Le programme suivant utilise le modèle ET pour combiner les modèles Square et Cube. Il imprime tous les entiers jusqu’à 1000 qui sont à la fois carrés et cubes, ainsi que ceux qui ne sont que des cubes.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

La sortie se présente comme suit :

```console
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

## <a name="parameterized-active-patterns"></a>Modèles actifs paramétrés

Les modèles actifs prennent toujours au moins un argument pour que l’élément soit apparié, mais ils peuvent également prendre des arguments supplémentaires, auquel cas le *modèle actif paramétisé* de nom s’applique. D’autres arguments permettent de se spécialiser dans un schéma général. Par exemple, les modèles actifs qui utilisent des expressions régulières pour analyser les chaînes incluent souvent l’expression régulière `Integer` comme un paramètre supplémentaire, comme dans le code suivant, qui utilise également le modèle actif partiel défini dans l’exemple de code précédent. Dans cet exemple, les chaînes qui utilisent des expressions régulières pour différents formats de date sont données pour personnaliser le modèle actif général ParseRegex. Le modèle actif Integer est utilisé pour convertir les cordes assorties en entiers qui peuvent être passés au constructeur DateTime.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

La sortie du code précédent est la suivante :

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Les modèles actifs ne sont pas limités uniquement aux expressions assorties de modèles, vous pouvez également les utiliser sur les reliures.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

La sortie du code précédent est la suivante :

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Voir aussi

- [Référence linguistique F](index.md)
- [Expressions de correspondance](match-expressions.md)
