---
title: Unions discriminées
description: Apprenez à utiliser les syndicats discriminés.
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400217"
---
# <a name="discriminated-unions"></a>Unions discriminées

Les syndicats discriminés appuient les valeurs qui peuvent être l’un des nombreux cas nommés, peut-être chacun avec des valeurs et des types différents. Les syndicats discriminés sont utiles pour les données hétérogènes; données pouvant avoir des cas particuliers, y compris les cas valides et les cas d’erreur; données qui varient en type d’un cas à l’autre; et comme alternative pour les hiérarchies de petits objets. En outre, les syndicats récidivants discriminés sont utilisés pour représenter les structures de données sur les arbres.

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Notes 

Les syndicats discriminés sont semblables aux types d’union dans d’autres langues, mais il y a des différences. Comme pour un type d’union dans le C ou un type de variante dans Visual Basic, les données stockées dans la valeur ne sont pas fixes; il peut être l’une des nombreuses options distinctes. Contrairement aux syndicats dans ces autres langues, cependant, chacune des options possibles est donnée un *identificateur de cas*. Les identificateurs de cas sont des noms pour les différents types possibles de valeurs que les objets de ce type pourraient être; les valeurs sont facultatives. Si les valeurs ne sont pas présentes, l’affaire équivaut à un cas de recensement. Si des valeurs sont présentes, chaque valeur peut être soit une valeur unique d’un type spécifié, soit un tuple qui agrége plusieurs champs de même type ou de différents types. Vous pouvez donner un nom à un champ individuel, mais le nom est facultatif, même si d’autres champs dans le même cas sont nommés.

L’accessibilité pour les `public`syndicats discriminés ne fait pas défaut à .

Par exemple, considérez la déclaration suivante d’un type de forme.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Le code précédent déclare une forme syndicale discriminée, qui peut avoir des valeurs de l’un des trois cas: Rectangle, Circle, et Prism. Chaque cas a un ensemble différent de champs. Le boîtier Rectangle a deux champs `float`nommés, tous deux de type , qui ont la largeur des noms et la longueur. L’affaire Circle n’a qu’un champ nommé, le rayon. Le boîtier Prism a trois champs, dont deux (largeur et hauteur) sont nommés champs. Les champs anonymes sont appelés champs anonymes.

Vous construisez des objets en fournissant des valeurs pour les champs nommés et anonymes selon les exemples suivants.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Ce code montre que vous pouvez soit utiliser les champs nommés dans l’initialisation, ou vous pouvez compter sur la commande des champs dans la déclaration et juste fournir les valeurs pour chaque domaine à son tour. L’appel constructeur `rect` dans le code précédent utilise les champs `circ` nommés, mais l’appel constructeur pour les utilisations de la commande. Vous pouvez mélanger les champs commandés et `prism`les champs nommés, comme dans la construction de .

Ce `option` type est un simple syndicat discriminé dans la bibliothèque centrale de F. Le `option` type est déclaré comme suit.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Le code précédent précise que `Option` le type est une union `Some` `None`discriminée qui a deux cas, et . L’affaire `Some` a une valeur associée qui se compose d’un `'a`champ anonyme dont le type est représenté par le paramètre de type . L’affaire `None` n’a aucune valeur associée. Ainsi, `option` le type spécifie un type générique qui a une valeur d’un certain type ou pas de valeur. Le `Option` type a également un alias `option`de type minuscule, , qui est plus couramment utilisé.

Les identificateurs de cas peuvent être utilisés comme constructeurs pour le type de syndicat discriminé. Par exemple, le code suivant est `option` utilisé pour créer des valeurs du type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Les identificateurs de cas sont également utilisés dans les expressions de correspondance de modèle. Dans une expression de correspondance de modèle, des identificateurs sont fournis pour les valeurs associées aux cas individuels. Par exemple, dans le `x` code suivant, est l’identifiant `Some` étant `option` donné la valeur qui est associée au cas du type.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Dans les expressions de correspondance de modèles, vous pouvez utiliser des champs nommés pour spécifier les correspondances syndicales discriminées. Pour le type de forme qui a été déclaré précédemment, vous pouvez utiliser les champs nommés comme le code suivant montre pour extraire les valeurs des champs.

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

Normalement, les identificateurs de cas peuvent être utilisés sans les qualifier avec le nom du syndicat. Si vous voulez que le nom soit toujours qualifié avec le nom du syndicat, vous pouvez appliquer [l’attribut RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) à la définition de type syndicat.

### <a name="unwrapping-discriminated-unions"></a>Déballage des syndicats discriminés

Dans les unions discriminées, les syndicats sont souvent utilisés dans la modélisation de domaine pour l’emballage d’un seul type. Il est facile d’extraire la valeur sous-jacente par l’appariement des motifs ainsi. Vous n’avez pas besoin d’utiliser une expression de match pour un seul cas :

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

Cela est illustré par l'exemple suivant :

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

L’appariement des modèles est également autorisé directement dans les paramètres de fonction, de sorte que vous pouvez déballer un seul cas là-bas:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Structurer les syndicats discriminés

Vous pouvez également représenter les unions discriminées comme des structs.  Cela se fait `[<Struct>]` avec l’attribut.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Étant donné qu’il s’agit de types de valeurs et non de types de références, il y a des considérations supplémentaires par rapport aux syndicats discriminés de référence :

1. Ils sont copiés comme types de valeur et ont la sémantique de type valeur.
2. Vous ne pouvez pas utiliser une définition de type récursif avec une union discriminée multicassive.
3. Vous devez fournir des noms de cas uniques pour une union discriminée multicase.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Utilisation d’unions discriminées au lieu de hiérarchies d’objets

Vous pouvez souvent utiliser une union discriminée comme une alternative plus simple à une hiérarchie de petits objets. Par exemple, l’union discriminée suivante `Shape` pourrait être utilisée au lieu d’une classe de base qui a dérivé des types pour le cercle, carré, et ainsi de suite.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Au lieu d’une méthode virtuelle pour calculer une zone ou un périmètre, comme vous l’utiliseriez dans une implémentation orientée objet, vous pouvez utiliser l’appariement des modèles à la branche pour calculer les formules appropriées pour calculer ces quantités. Dans l’exemple suivant, différentes formules sont utilisées pour calculer la zone, selon la forme.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

La sortie se présente comme suit :

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Utilisation de syndicats discriminés pour les structures de données sur les arbres

Les syndicats discriminés peuvent être récursifs, ce qui signifie que le syndicat lui-même peut être inclus dans le type d’un ou de plusieurs cas. Les syndicats discriminés récursifs peuvent être utilisés pour créer des structures d’arbres, qui sont utilisées pour modéliser les expressions dans les langages de programmation. Dans le code suivant, une union discriminée récursive est utilisée pour créer une structure de données binaires sur les arbres. Le syndicat se compose `Node`de deux cas, , qui est un nœud avec `Tip`une valeur integer et sous-arbres gauche et droite, et , qui met fin à l’arbre.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

Dans le code `resultSumTree` précédent, a la valeur 10. L’illustration suivante montre `myTree`la structure de l’arbre pour .

![Diagramme qui montre la structure de l’arbre pour myTree.](../media/discriminated-unions/tree-structure-mytree.png)

Les syndicats discriminés fonctionnent bien si les nœuds dans l’arbre sont hétérogènes. Dans le code suivant, le type `Expression` représente l’arbre syntaxe abstrait d’une expression dans un langage de programmation simple qui prend en charge l’ajout et la multiplication des nombres et des variables. Certains des cas syndicaux ne sont pas récursifs et représentent soit des nombres ()`Number`ou des variables (`Variable`). D’autres cas sont récursifs, et représentent des opérations (`Add` et `Multiply`), où les opérands sont également des expressions. La `Evaluate` fonction utilise une expression de match pour traiter de façon récursive l’arbre syntaxe.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Lorsque ce code est exécuté, `result` la valeur est de 5.

## <a name="members"></a>Membres

Il est possible de définir les membres sur les syndicats discriminés. L’exemple suivant montre comment définir une propriété et implémenter une interface :

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

Les attributs suivants sont couramment observés dans les syndicats discriminés :

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a>Voir aussi

- [Référence linguistique F](index.md)
