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
# <a name="discriminated-unions"></a><span data-ttu-id="ba268-103">Unions discriminées</span><span class="sxs-lookup"><span data-stu-id="ba268-103">Discriminated Unions</span></span>

<span data-ttu-id="ba268-104">Les syndicats discriminés appuient les valeurs qui peuvent être l’un des nombreux cas nommés, peut-être chacun avec des valeurs et des types différents.</span><span class="sxs-lookup"><span data-stu-id="ba268-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="ba268-105">Les syndicats discriminés sont utiles pour les données hétérogènes; données pouvant avoir des cas particuliers, y compris les cas valides et les cas d’erreur; données qui varient en type d’un cas à l’autre; et comme alternative pour les hiérarchies de petits objets.</span><span class="sxs-lookup"><span data-stu-id="ba268-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="ba268-106">En outre, les syndicats récidivants discriminés sont utilisés pour représenter les structures de données sur les arbres.</span><span class="sxs-lookup"><span data-stu-id="ba268-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba268-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba268-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="ba268-108">Notes </span><span class="sxs-lookup"><span data-stu-id="ba268-108">Remarks</span></span>

<span data-ttu-id="ba268-109">Les syndicats discriminés sont semblables aux types d’union dans d’autres langues, mais il y a des différences.</span><span class="sxs-lookup"><span data-stu-id="ba268-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="ba268-110">Comme pour un type d’union dans le C ou un type de variante dans Visual Basic, les données stockées dans la valeur ne sont pas fixes; il peut être l’une des nombreuses options distinctes.</span><span class="sxs-lookup"><span data-stu-id="ba268-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="ba268-111">Contrairement aux syndicats dans ces autres langues, cependant, chacune des options possibles est donnée un *identificateur de cas*.</span><span class="sxs-lookup"><span data-stu-id="ba268-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="ba268-112">Les identificateurs de cas sont des noms pour les différents types possibles de valeurs que les objets de ce type pourraient être; les valeurs sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="ba268-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="ba268-113">Si les valeurs ne sont pas présentes, l’affaire équivaut à un cas de recensement.</span><span class="sxs-lookup"><span data-stu-id="ba268-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="ba268-114">Si des valeurs sont présentes, chaque valeur peut être soit une valeur unique d’un type spécifié, soit un tuple qui agrége plusieurs champs de même type ou de différents types.</span><span class="sxs-lookup"><span data-stu-id="ba268-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="ba268-115">Vous pouvez donner un nom à un champ individuel, mais le nom est facultatif, même si d’autres champs dans le même cas sont nommés.</span><span class="sxs-lookup"><span data-stu-id="ba268-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="ba268-116">L’accessibilité pour les `public`syndicats discriminés ne fait pas défaut à .</span><span class="sxs-lookup"><span data-stu-id="ba268-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="ba268-117">Par exemple, considérez la déclaration suivante d’un type de forme.</span><span class="sxs-lookup"><span data-stu-id="ba268-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="ba268-118">Le code précédent déclare une forme syndicale discriminée, qui peut avoir des valeurs de l’un des trois cas: Rectangle, Circle, et Prism.</span><span class="sxs-lookup"><span data-stu-id="ba268-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="ba268-119">Chaque cas a un ensemble différent de champs.</span><span class="sxs-lookup"><span data-stu-id="ba268-119">Each case has a different set of fields.</span></span> <span data-ttu-id="ba268-120">Le boîtier Rectangle a deux champs `float`nommés, tous deux de type , qui ont la largeur des noms et la longueur.</span><span class="sxs-lookup"><span data-stu-id="ba268-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="ba268-121">L’affaire Circle n’a qu’un champ nommé, le rayon.</span><span class="sxs-lookup"><span data-stu-id="ba268-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="ba268-122">Le boîtier Prism a trois champs, dont deux (largeur et hauteur) sont nommés champs.</span><span class="sxs-lookup"><span data-stu-id="ba268-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="ba268-123">Les champs anonymes sont appelés champs anonymes.</span><span class="sxs-lookup"><span data-stu-id="ba268-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="ba268-124">Vous construisez des objets en fournissant des valeurs pour les champs nommés et anonymes selon les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="ba268-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="ba268-125">Ce code montre que vous pouvez soit utiliser les champs nommés dans l’initialisation, ou vous pouvez compter sur la commande des champs dans la déclaration et juste fournir les valeurs pour chaque domaine à son tour.</span><span class="sxs-lookup"><span data-stu-id="ba268-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="ba268-126">L’appel constructeur `rect` dans le code précédent utilise les champs `circ` nommés, mais l’appel constructeur pour les utilisations de la commande.</span><span class="sxs-lookup"><span data-stu-id="ba268-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="ba268-127">Vous pouvez mélanger les champs commandés et `prism`les champs nommés, comme dans la construction de .</span><span class="sxs-lookup"><span data-stu-id="ba268-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="ba268-128">Ce `option` type est un simple syndicat discriminé dans la bibliothèque centrale de F.</span><span class="sxs-lookup"><span data-stu-id="ba268-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="ba268-129">Le `option` type est déclaré comme suit.</span><span class="sxs-lookup"><span data-stu-id="ba268-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="ba268-130">Le code précédent précise que `Option` le type est une union `Some` `None`discriminée qui a deux cas, et .</span><span class="sxs-lookup"><span data-stu-id="ba268-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="ba268-131">L’affaire `Some` a une valeur associée qui se compose d’un `'a`champ anonyme dont le type est représenté par le paramètre de type .</span><span class="sxs-lookup"><span data-stu-id="ba268-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="ba268-132">L’affaire `None` n’a aucune valeur associée.</span><span class="sxs-lookup"><span data-stu-id="ba268-132">The `None` case has no associated value.</span></span> <span data-ttu-id="ba268-133">Ainsi, `option` le type spécifie un type générique qui a une valeur d’un certain type ou pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="ba268-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="ba268-134">Le `Option` type a également un alias `option`de type minuscule, , qui est plus couramment utilisé.</span><span class="sxs-lookup"><span data-stu-id="ba268-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="ba268-135">Les identificateurs de cas peuvent être utilisés comme constructeurs pour le type de syndicat discriminé.</span><span class="sxs-lookup"><span data-stu-id="ba268-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="ba268-136">Par exemple, le code suivant est `option` utilisé pour créer des valeurs du type.</span><span class="sxs-lookup"><span data-stu-id="ba268-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="ba268-137">Les identificateurs de cas sont également utilisés dans les expressions de correspondance de modèle.</span><span class="sxs-lookup"><span data-stu-id="ba268-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="ba268-138">Dans une expression de correspondance de modèle, des identificateurs sont fournis pour les valeurs associées aux cas individuels.</span><span class="sxs-lookup"><span data-stu-id="ba268-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="ba268-139">Par exemple, dans le `x` code suivant, est l’identifiant `Some` étant `option` donné la valeur qui est associée au cas du type.</span><span class="sxs-lookup"><span data-stu-id="ba268-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="ba268-140">Dans les expressions de correspondance de modèles, vous pouvez utiliser des champs nommés pour spécifier les correspondances syndicales discriminées.</span><span class="sxs-lookup"><span data-stu-id="ba268-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="ba268-141">Pour le type de forme qui a été déclaré précédemment, vous pouvez utiliser les champs nommés comme le code suivant montre pour extraire les valeurs des champs.</span><span class="sxs-lookup"><span data-stu-id="ba268-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

<span data-ttu-id="ba268-142">Normalement, les identificateurs de cas peuvent être utilisés sans les qualifier avec le nom du syndicat.</span><span class="sxs-lookup"><span data-stu-id="ba268-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="ba268-143">Si vous voulez que le nom soit toujours qualifié avec le nom du syndicat, vous pouvez appliquer [l’attribut RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) à la définition de type syndicat.</span><span class="sxs-lookup"><span data-stu-id="ba268-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="ba268-144">Déballage des syndicats discriminés</span><span class="sxs-lookup"><span data-stu-id="ba268-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="ba268-145">Dans les unions discriminées, les syndicats sont souvent utilisés dans la modélisation de domaine pour l’emballage d’un seul type.</span><span class="sxs-lookup"><span data-stu-id="ba268-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="ba268-146">Il est facile d’extraire la valeur sous-jacente par l’appariement des motifs ainsi.</span><span class="sxs-lookup"><span data-stu-id="ba268-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="ba268-147">Vous n’avez pas besoin d’utiliser une expression de match pour un seul cas :</span><span class="sxs-lookup"><span data-stu-id="ba268-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

<span data-ttu-id="ba268-148">Cela est illustré par l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ba268-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="ba268-149">L’appariement des modèles est également autorisé directement dans les paramètres de fonction, de sorte que vous pouvez déballer un seul cas là-bas:</span><span class="sxs-lookup"><span data-stu-id="ba268-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="ba268-150">Structurer les syndicats discriminés</span><span class="sxs-lookup"><span data-stu-id="ba268-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="ba268-151">Vous pouvez également représenter les unions discriminées comme des structs.</span><span class="sxs-lookup"><span data-stu-id="ba268-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="ba268-152">Cela se fait `[<Struct>]` avec l’attribut.</span><span class="sxs-lookup"><span data-stu-id="ba268-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="ba268-153">Étant donné qu’il s’agit de types de valeurs et non de types de références, il y a des considérations supplémentaires par rapport aux syndicats discriminés de référence :</span><span class="sxs-lookup"><span data-stu-id="ba268-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="ba268-154">Ils sont copiés comme types de valeur et ont la sémantique de type valeur.</span><span class="sxs-lookup"><span data-stu-id="ba268-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="ba268-155">Vous ne pouvez pas utiliser une définition de type récursif avec une union discriminée multicassive.</span><span class="sxs-lookup"><span data-stu-id="ba268-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="ba268-156">Vous devez fournir des noms de cas uniques pour une union discriminée multicase.</span><span class="sxs-lookup"><span data-stu-id="ba268-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="ba268-157">Utilisation d’unions discriminées au lieu de hiérarchies d’objets</span><span class="sxs-lookup"><span data-stu-id="ba268-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="ba268-158">Vous pouvez souvent utiliser une union discriminée comme une alternative plus simple à une hiérarchie de petits objets.</span><span class="sxs-lookup"><span data-stu-id="ba268-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="ba268-159">Par exemple, l’union discriminée suivante `Shape` pourrait être utilisée au lieu d’une classe de base qui a dérivé des types pour le cercle, carré, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="ba268-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="ba268-160">Au lieu d’une méthode virtuelle pour calculer une zone ou un périmètre, comme vous l’utiliseriez dans une implémentation orientée objet, vous pouvez utiliser l’appariement des modèles à la branche pour calculer les formules appropriées pour calculer ces quantités.</span><span class="sxs-lookup"><span data-stu-id="ba268-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="ba268-161">Dans l’exemple suivant, différentes formules sont utilisées pour calculer la zone, selon la forme.</span><span class="sxs-lookup"><span data-stu-id="ba268-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="ba268-162">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="ba268-162">The output is as follows:</span></span>

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="ba268-163">Utilisation de syndicats discriminés pour les structures de données sur les arbres</span><span class="sxs-lookup"><span data-stu-id="ba268-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="ba268-164">Les syndicats discriminés peuvent être récursifs, ce qui signifie que le syndicat lui-même peut être inclus dans le type d’un ou de plusieurs cas.</span><span class="sxs-lookup"><span data-stu-id="ba268-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="ba268-165">Les syndicats discriminés récursifs peuvent être utilisés pour créer des structures d’arbres, qui sont utilisées pour modéliser les expressions dans les langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="ba268-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="ba268-166">Dans le code suivant, une union discriminée récursive est utilisée pour créer une structure de données binaires sur les arbres.</span><span class="sxs-lookup"><span data-stu-id="ba268-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="ba268-167">Le syndicat se compose `Node`de deux cas, , qui est un nœud avec `Tip`une valeur integer et sous-arbres gauche et droite, et , qui met fin à l’arbre.</span><span class="sxs-lookup"><span data-stu-id="ba268-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="ba268-168">Dans le code `resultSumTree` précédent, a la valeur 10.</span><span class="sxs-lookup"><span data-stu-id="ba268-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="ba268-169">L’illustration suivante montre `myTree`la structure de l’arbre pour .</span><span class="sxs-lookup"><span data-stu-id="ba268-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Diagramme qui montre la structure de l’arbre pour myTree.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="ba268-171">Les syndicats discriminés fonctionnent bien si les nœuds dans l’arbre sont hétérogènes.</span><span class="sxs-lookup"><span data-stu-id="ba268-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="ba268-172">Dans le code suivant, le type `Expression` représente l’arbre syntaxe abstrait d’une expression dans un langage de programmation simple qui prend en charge l’ajout et la multiplication des nombres et des variables.</span><span class="sxs-lookup"><span data-stu-id="ba268-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="ba268-173">Certains des cas syndicaux ne sont pas récursifs et représentent soit des nombres ()`Number`ou des variables (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="ba268-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="ba268-174">D’autres cas sont récursifs, et représentent des opérations (`Add` et `Multiply`), où les opérands sont également des expressions.</span><span class="sxs-lookup"><span data-stu-id="ba268-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="ba268-175">La `Evaluate` fonction utilise une expression de match pour traiter de façon récursive l’arbre syntaxe.</span><span class="sxs-lookup"><span data-stu-id="ba268-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="ba268-176">Lorsque ce code est exécuté, `result` la valeur est de 5.</span><span class="sxs-lookup"><span data-stu-id="ba268-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="ba268-177">Membres</span><span class="sxs-lookup"><span data-stu-id="ba268-177">Members</span></span>

<span data-ttu-id="ba268-178">Il est possible de définir les membres sur les syndicats discriminés.</span><span class="sxs-lookup"><span data-stu-id="ba268-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="ba268-179">L’exemple suivant montre comment définir une propriété et implémenter une interface :</span><span class="sxs-lookup"><span data-stu-id="ba268-179">The following example shows how to define a property and implement an interface:</span></span>

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

## <a name="common-attributes"></a><span data-ttu-id="ba268-180">Attributs communs</span><span class="sxs-lookup"><span data-stu-id="ba268-180">Common attributes</span></span>

<span data-ttu-id="ba268-181">Les attributs suivants sont couramment observés dans les syndicats discriminés :</span><span class="sxs-lookup"><span data-stu-id="ba268-181">The following attributes are commonly seen in discriminated unions:</span></span>

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="ba268-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba268-182">See also</span></span>

- [<span data-ttu-id="ba268-183">Référence linguistique F</span><span class="sxs-lookup"><span data-stu-id="ba268-183">F# Language Reference</span></span>](index.md)
