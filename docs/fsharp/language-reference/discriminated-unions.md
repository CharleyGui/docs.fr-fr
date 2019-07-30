---
title: Unions discriminées
description: Découvrez comment utiliser F# des unions discriminées.
ms.date: 05/16/2016
ms.openlocfilehash: 940bc51f49e283c31846dd2047b749769b919838
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630350"
---
# <a name="discriminated-unions"></a>Unions discriminées

Les unions discriminées prennent en charge les valeurs qui peuvent être un nombre de cas nommés, chacun avec des valeurs et des types différents. Les unions discriminées sont utiles pour les données hétérogènes; données qui peuvent avoir des cas spéciaux, y compris des cas d’erreur et valides; données qui varient en fonction du type d’une instance à l’autre; et comme alternative pour les hiérarchies d’objets de petite taille. En outre, les unions discriminées récursives sont utilisées pour représenter des structures de données d’arborescence.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Notes

Les unions discriminées sont semblables aux types Union dans d’autres langages, mais il existe des différences. Comme avec un type d’Union C++ dans ou un type variant dans Visual Basic, les données stockées dans la valeur ne sont pas fixes; Il peut s’agir de l’une des différentes options distinctes. Contrairement aux unions dans ces autres langages, toutefois, chacune des options possibles reçoit un *identificateur de cas*. Les identificateurs de cas sont des noms pour les différents types de valeurs possibles que les objets de ce type peuvent avoir; les valeurs sont facultatives. Si les valeurs ne sont pas présentes, le cas est équivalent à un cas d’énumération. Si des valeurs sont présentes, chaque valeur peut être une valeur unique d’un type spécifié ou un tuple qui agrège plusieurs champs du même type ou de types différents. Vous pouvez attribuer un nom à un champ individuel, mais le nom est facultatif, même si d’autres champs dans le même cas sont nommés.

L’accessibilité des unions discriminées est `public`par défaut.

Par exemple, considérez la déclaration suivante d’un type de forme.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Le code précédent déclare une forme d’union discriminée, qui peut avoir des valeurs de l’un des trois cas: Rectangle, cercle et prisme. Chaque cas a un ensemble de champs différent. Le rectangle a deux champs nommés, de type `float`, dont la largeur et la longueur sont les noms. La casse du cercle n’a qu’un seul champ nommé, RADIUS. Le cas Prism comporte trois champs, dont deux (largeur et hauteur) sont des champs nommés. Les champs sans nom sont appelés champs anonymes.

Vous construisez des objets en fournissant des valeurs pour les champs nommés et anonymes conformément aux exemples suivants.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Ce code montre que vous pouvez utiliser les champs nommés dans l’initialisation, ou vous pouvez vous appuyer sur l’ordre des champs dans la déclaration et simplement fournir les valeurs de chaque champ. L’appel de constructeur `rect` pour dans le code précédent utilise les champs nommés, mais l’appel de `circ` constructeur pour utilise le classement. Vous pouvez mélanger les champs ordonnés et les champs nommés, comme dans la `prism`construction de.

Le `option` type est une union discriminée simple dans la F# bibliothèque principale. Le `option` type est déclaré comme suit.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Le code précédent spécifie que le `Option` type est une union discriminée qui a deux cas `Some` , `None`et. Le `Some` cas a une valeur associée qui se compose d’un champ anonyme dont le type est représenté par le `'a`paramètre de type. Le `None` cas n’a aucune valeur associée. Par conséquent `option` , le type spécifie un type générique qui a une valeur d’un certain type ou aucune valeur. Le type `Option` a également un alias de type minuscule `option`,, qui est plus couramment utilisé.

Les identificateurs de cas peuvent être utilisés comme constructeurs pour le type d’union discriminée. Par exemple, le code suivant est utilisé pour créer des valeurs du `option` type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Les identificateurs de cas sont également utilisés dans les expressions de critères spéciaux. Dans une expression de critères spéciaux, les identificateurs sont fournis pour les valeurs associées aux cas individuels. Par exemple, dans le code suivant, `x` est l’identificateur en fonction de la valeur associée à la `Some` casse du `option` type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Dans les expressions de critères spéciaux, vous pouvez utiliser des champs nommés pour spécifier des correspondances d’union discriminée. Pour le type de forme qui a été déclaré précédemment, vous pouvez utiliser les champs nommés comme le montre le code suivant pour extraire les valeurs des champs.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Normalement, les identificateurs de cas peuvent être utilisés sans les qualifier avec le nom de l’Union. Si vous souhaitez que le nom soit toujours qualifié avec le nom de l’Union, vous pouvez appliquer l’attribut [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) à la définition du type d’Union.

### <a name="unwrapping-discriminated-unions"></a>Désencapsulage d’unions discriminées

Dans F# , les unions discriminées sont souvent utilisées dans la modélisation de domaine pour l’encapsulation d’un type unique. Il est également facile d’extraire la valeur sous-jacente via la mise en correspondance des modèles. Vous n’avez pas besoin d’utiliser une expression de correspondance pour un cas unique:

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

Les critères spéciaux sont également autorisés directement dans les paramètres de fonction, ce qui vous permet de désencapsuler un cas unique ici:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Unions discriminées de struct

Vous pouvez également représenter des unions discriminées comme des structs.  Cette opération s’effectue avec `[<Struct>]` l’attribut.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Étant donné qu’il s’agit de types valeur et non de types référence, des considérations supplémentaires sont à prendre en compte par rapport aux unions discriminées de référence:

1. Ils sont copiés en tant que types valeur et ont une sémantique de type valeur.
2. Vous ne pouvez pas utiliser une définition de type récursive avec une union discriminée de struct à cas.
3. Vous devez fournir des noms de cas uniques pour une union discriminée de struct à cas unique.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Utilisation d’unions discriminées au lieu de hiérarchies d’objets

Vous pouvez souvent utiliser une union discriminée comme alternative plus simple à une petite hiérarchie d’objets. Par exemple, l’union discriminée suivante peut être utilisée à la place `Shape` d’une classe de base qui a des types dérivés pour Circle, Square, etc.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Au lieu d’une méthode virtuelle pour calculer une zone ou un périmètre, comme vous le feriez dans une implémentation orientée objet, vous pouvez utiliser des critères spéciaux pour créer une branche vers des formules appropriées afin de calculer ces quantités. Dans l’exemple suivant, différentes formules sont utilisées pour calculer la zone, en fonction de la forme.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

La sortie est la suivante :

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Utilisation d’unions discriminées pour les structures de données d’arborescence

Les unions discriminées peuvent être récursives, ce qui signifie que l’Union elle-même peut être incluse dans le type d’un ou de plusieurs cas. Les unions discriminées récursives peuvent être utilisées pour créer des structures d’arborescence, qui sont utilisées pour modéliser des expressions dans des langages de programmation. Dans le code suivant, une union discriminée récursive est utilisée pour créer une structure de données d’arborescence binaire. L’Union se compose de deux cas `Node`,, qui est un nœud avec une valeur entière et des sous-arborescences gauche et `Tip`droite, et, qui termine l’arborescence.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

Dans le code précédent, `resultSumTree` a la valeur 10. L’illustration suivante montre l’arborescence de `myTree`.

![Diagramme qui affiche l’arborescence pour myTree.](../media/discriminated-unions/tree-structure-mytree.png)

Les unions discriminées fonctionnent bien si les nœuds de l’arborescence sont hétérogènes. Dans le code suivant, le type `Expression` représente l’arborescence de syntaxe abstraite d’une expression dans un langage de programmation simple qui prend en charge l’addition et la multiplication de nombres et de variables. Certains des cas d’Union ne sont pas récursifs et représentent des nombres`Number`() ou des`Variable`variables (). D’autres cas sont récursifs et représentent des opérations`Add` ( `Multiply`et), où les opérandes sont également des expressions. La `Evaluate` fonction utilise une expression de correspondance pour traiter de manière récursive l’arborescence de syntaxe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Lorsque ce code est exécuté, la valeur de `result` est 5.

## <a name="members"></a>Membres

Il est possible de définir des membres sur des unions discriminées. L’exemple suivant montre comment définir une propriété et implémenter une interface:

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

## <a name="common-attributes"></a>Attributs communs

Les attributs suivants sont généralement affichés dans des unions discriminées:

* `[<RequireQualifiedAccess>]`
* `[<NoEquality>]`
* `[<NoComparison>]`
* `[<Struct>]`

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
