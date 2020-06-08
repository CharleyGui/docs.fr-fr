---
title: Modèles actifs
description: 'Découvrez comment utiliser des modèles actifs pour définir des partitions nommées qui subdivisent les données d’entrée dans le langage de programmation F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 7b6da38baa35f30ae6de8a930be60a4e4fc0fc0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493889"
---
# <a name="active-patterns"></a>Modèles actifs

Les *modèles actifs* vous permettent de définir des partitions nommées qui subdivisent les données d’entrée, afin que vous puissiez utiliser ces noms dans une expression de critères spéciaux comme vous le feriez pour une union discriminée. Vous pouvez utiliser des modèles actifs pour décomposer des données de façon personnalisée pour chaque partition.

## <a name="syntax"></a>Syntaxe

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch = expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, les identificateurs sont des noms de partitions des données d’entrée qui sont représentées par des *arguments*, ou, en d’autres termes, des noms pour les sous-ensembles de l’ensemble de toutes les valeurs des arguments. Il peut y avoir jusqu’à sept partitions dans une définition de modèle actif. L' *expression* décrit le formulaire dans lequel décomposer les données. Vous pouvez utiliser une définition de modèle actif pour définir les règles de détermination des partitions nommées auxquelles les valeurs fournies comme arguments appartiennent. Les symboles (| et |) sont appelés « *Banana clips* » et la fonction créée par ce type de liaison Let est appelée « module de *reconnaissance actif*».

Par exemple, considérez le modèle actif suivant avec un argument.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

Vous pouvez utiliser le modèle actif dans une expression de critères spéciaux, comme dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

Le résultat de ce programme est le suivant :

```console
7 is odd
11 is odd
32 is even
```

Une autre utilisation des modèles actifs consiste à décomposer les types de données de plusieurs façons, par exemple quand les mêmes données sous-jacentes ont différentes représentations possibles. Par exemple, un `Color` objet peut être décomposé en représentation RVB ou en représentation TSL.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

La sortie du programme ci-dessus est la suivante :

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

En combinaison, ces deux méthodes d’utilisation des modèles actifs vous permettent de partitionner et de décomposer des données sous la forme appropriée et d’effectuer les calculs appropriés sur les données appropriées au format le plus pratique pour le calcul.

Les expressions de critères spéciaux qui en résultent permettent d’écrire des données de manière pratique et très lisible, ce qui simplifie considérablement le code d’analyse de données et de branchement potentiellement complexe.

## <a name="partial-active-patterns"></a>Modèles actifs partiels

Parfois, vous devez partitionner uniquement une partie de l’espace d’entrée. Dans ce cas, vous écrivez un ensemble de modèles partiels, chacun d’entre eux correspondant à des entrées, mais ne parviennent pas à mettre en correspondance d’autres entrées. Les modèles actifs qui ne produisent pas toujours une valeur sont appelés *modèles actifs partiels*; elles ont une valeur de retour qui est un type d’option. Pour définir un modèle actif partiel, utilisez un caractère générique ( \_ ) à la fin de la liste de modèles à l’intérieur des éléments Banana. Le code suivant illustre l’utilisation d’un modèle actif partiel.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

La sortie de l’exemple précédent est la suivante :

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

Lorsque vous utilisez des modèles actifs partiels, les choix individuels peuvent être disjoints ou mutuellement exclusifs, mais ils n’ont pas besoin d’être. Dans l’exemple suivant, le modèle Square et le cube pattern ne sont pas disjoint, car certains nombres sont à la fois des carrés et des cubes, par exemple 64. Le programme suivant utilise le modèle et pour combiner les modèles de carré et de cube. Il imprime tous les entiers jusqu’à 1000 qui sont tous deux des carrés et des cubes, ainsi que ceux qui ne sont que des cubes.

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

Les modèles actifs prennent toujours au moins un argument pour l’élément qui est mis en correspondance, mais ils peuvent également prendre des arguments supplémentaires, auquel cas le *modèle actif paramétré* pour le nom s’applique. Les arguments supplémentaires permettent à un modèle général d’être spécialisé. Par exemple, les modèles actifs qui utilisent des expressions régulières pour analyser des chaînes incluent souvent l’expression régulière comme paramètre supplémentaire, comme dans le code suivant, qui utilise également le modèle actif partiel `Integer` défini dans l’exemple de code précédent. Dans cet exemple, les chaînes qui utilisent des expressions régulières pour différents formats de date sont fournies pour personnaliser le modèle actif ParseRegex général. Le modèle actif entier est utilisé pour convertir les chaînes mises en correspondance en entiers qui peuvent être passés au constructeur DateTime.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

La sortie du code précédent est la suivante :

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

Les modèles actifs ne sont pas limités uniquement aux expressions de critères spéciaux, vous pouvez également les utiliser dans les liaisons Let.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

La sortie du code précédent est la suivante :

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Expressions de correspondance](match-expressions.md)
