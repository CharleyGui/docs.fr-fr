---
title: Unions discriminées
description: Découvrez comment utiliser F# unions discriminées.
ms.date: 05/16/2016
ms.openlocfilehash: a3958a9ffb021c0c46c24216f17a1e7ee5605dd3
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816244"
---
# <a name="discriminated-unions"></a>Unions discriminées

Les unions discriminées fournissent la prise en charge pour les valeurs qui peuvent s’agir d’un nombre de cas nommés, chacun avec des types et des valeurs différentes. Les unions discriminées sont utiles pour les données hétérogènes ; données qui peuvent avoir des cas spéciaux, y compris valides et cas d’erreur ; données qui varie selon le type d’une instance à l’autre ; et comme alternative pour les petites hiérarchies d’objets. En outre, discriminées récursives unions sont utilisées pour représenter des structures de données d’arborescence.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Notes

Les unions discriminées sont semblables aux types union dans d’autres langages, mais il existe des différences. Comme avec un type union en C++ ou un type variant en Visual Basic, les données stockées dans la valeur ne sont pas fixe ; Il peut prendre l’une des diverses options distinctes. Contrairement aux unions de ces autres langages, toutefois, chacune des options possibles reçoit un *identificateur de cas*. Les identificateurs de cas sont des noms pour les différents types de valeurs susceptibles d’entraîner des objets de ce type ; les valeurs sont facultatives. Si les valeurs ne sont pas présents, le cas équivaut à un cas d’énumération. Si les valeurs sont présentes, chaque valeur peut être une valeur unique d’un type spécifié, ou un tuple qui regroupe plusieurs champs des types identiques ou différents. Vous pouvez donner à un champ individuel un nom, mais le nom est facultatif, même si d’autres champs dans le même cas sont nommés.

Par défaut est d’accessibilité pour les unions discriminées `public`.

Par exemple, considérez la déclaration suivante d’un type de forme.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Le code précédent déclare une union discriminée forme, qui peut avoir des valeurs d’un des trois cas : Rectangle, cercle et prisme. Chaque cas possède un ensemble de champs différent. Le Rectangle a le nom de deux champs, tous deux de type `float`, qui ont le nom largeur et la longueur. Le cercle a un seul champ nommé, radius. Le cas de prisme a trois champs, deux (largeur et hauteur) sont des champs nommés. Les champs sans nom sont appelés des champs anonymes.

Vous construisez des objets en fournissant des valeurs pour les champs nommés et anonymes selon les exemples suivants.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Ce code montre que vous pouvez utiliser les champs nommés dans l’initialisation, ou vous pouvez utiliser l’ordre des champs dans la déclaration et fournir uniquement les valeurs pour chaque champ à son tour. L’appel de constructeur pour `rect` dans le code précédent utilise les champs nommés, mais l’appel de constructeur pour `circ` utilise le classement. Vous pouvez combiner les champs ordonnés et les champs nommés, comme dans la construction de `prism`.

Le `option` type est une union discriminée simple dans le F# bibliothèque principale. Le `option` type est déclaré comme suit.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Le code précédent Spécifie que le type `Option` est une union discriminée qui a deux cas, `Some` et `None`. Le `Some` cas a une valeur associée qui se compose d’un champ anonyme dont le type est représenté par le paramètre de type `'a`. Le `None` cas n’a aucune valeur associée. Par conséquent, le `option` type spécifie un type générique qui a soit une valeur d’un certain type, soit aucune valeur. Le type `Option` a également un alias de type en minuscules, `option`, qui est plus couramment utilisé.

Les identificateurs de cas peuvent être utilisés comme constructeurs pour le type d’union discriminée. Par exemple, le code suivant est utilisé pour créer des valeurs de la `option` type.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Les identificateurs de cas sont également utilisés dans les expressions de critères spéciaux. Dans une expression à critères spéciaux, les identificateurs sont fournis pour les valeurs associées à chaque cas. Par exemple, dans le code suivant, `x` est l’identificateur qui reçoit la valeur qui est associée à la `Some` cas de la `option` type.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Dans les expressions de critères spéciaux, vous pouvez utiliser des champs nommés pour spécifier des correspondances d’unions discriminées. Pour le type de forme qui a été déclaré précédemment, vous pouvez utiliser les champs nommés, comme le montre le code suivant pour extraire les valeurs des champs.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Normalement, les identificateurs de cas peuvent être utilisés sans être qualifiés avec le nom de l’union. Si vous souhaitez que le nom soit toujours qualifié avec le nom de l’union, vous pouvez appliquer le [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribut à la définition de type d’union.

### <a name="unwrapping-discriminated-unions"></a>Unions discriminées désencapsuler

Dans F# Unions discriminées sont souvent utilisées dans la modélisation de domaine pour l’encapsulation d’un type unique. Il est facile d’extraire la valeur sous-jacente par le biais de critères spéciaux ainsi. Vous n’avez pas besoin d’utiliser une expression de correspondance pour un seul cas :

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

Cela est illustré par l'exemple suivant :

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

Critères spéciaux est également autorisée directement dans les paramètres de fonction, donc vous pouvez désencapsuler un cas unique :

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Unions discriminées de structs

Vous pouvez également représenter des Unions discriminées en tant que structures.  Cette opération est effectuée avec la `[<Struct>]` attribut.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Car celles-ci sont des types valeur et pas les types référencent, voici supplémentaire par rapport à la référence de considérations sur les unions discriminées :

1. Ils sont copiés en tant que types de valeur et ont une sémantique de type valeur.
2. Vous ne pouvez pas utiliser une définition de type récursive avec un struct multicase discriminées Union.
3. Vous devez fournir des noms de cas uniques pour un struct multicase discriminées Union.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Utilisation d’Unions discriminées au lieu de hiérarchies d’objets

Vous pouvez souvent utiliser une union discriminée comme alternative plus simple à une petite hiérarchie d’objets. Par exemple, l’union discriminée suivante pourrait être utilisée au lieu d’un `Shape` classe de base qui a des types dérivés pour cercle, carré, et ainsi de suite.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

À la place d’une méthode virtuelle pour calculer une zone ou un périmètre, que vous utiliseriez dans une implémentation orientée objet, vous pouvez utiliser des critères spéciaux à la branche vers les formules appropriées pour calculer ces quantités. Dans l’exemple suivant, différentes formules sont utilisées pour calculer la zone, en fonction de la forme.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

La sortie est la suivante :

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Utilisation d’Unions discriminées pour les Structures de données d’arborescence

Les unions discriminées peuvent être récursives, ce qui signifie que l’union elle-même peut être incluse dans le type d’un ou plusieurs cas. Récursive les unions discriminées peuvent être utilisées pour créer des arborescences, qui sont utilisées pour modeler des expressions dans les langages de programmation. Dans le code suivant, une récursive discriminées union est utilisée pour créer une structure de données d’arborescence binaire. L’union se compose de deux cas, `Node`, qui est un nœud avec une valeur entière et des sous-arborescences gauche et droite, et `Tip`, qui termine l’arborescence.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

Dans le code précédent, `resultSumTree` a la valeur 10. L’illustration suivante montre la structure d’arborescence de `myTree`.

![Diagramme qui montre l’arborescence pour myTree.](../media/discriminated-unions/tree-structure-mytree.png)

Les unions discriminées fonctionnent bien si les nœuds dans l’arborescence sont hétérogènes. Dans le code suivant, le type `Expression` représente l’arborescence de syntaxe abstraite d’une expression dans un langage de programmation simple qui prend en charge l’addition et multiplication de nombres et de variables. Certains cas d’union ne sont pas récursifs et représentent des nombres (`Number`) ou des variables (`Variable`). Autres cas sont récursifs et représentent des opérations (`Add` et `Multiply`), où les opérandes sont également des expressions. Le `Evaluate` fonction utilise une expression de correspondance pour traiter de manière récursive l’arborescence de syntaxe.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Lorsque ce code est exécuté, la valeur de `result` est 5.

## <a name="members"></a>Membres

Il est possible de définir des membres sur les unions discriminées. L’exemple suivant montre comment définir une propriété et d’implémenter une interface :

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a>Attributs courants

Les attributs suivants sont généralement visibles dans les unions discriminées :

* `[<RequireQualifiedAccess>]`
* `[<NoEquality>]`
* `[<NoComparison>]`
* `[<Struct>]`

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
