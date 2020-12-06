---
title: Unions discriminées
description: 'Découvrez comment utiliser des unions discriminées F #.'
ms.date: 08/15/2020
ms.openlocfilehash: f90ac2c2ea21182cf5fd3657d2ada00a763139fe
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740235"
---
# <a name="discriminated-unions"></a><span data-ttu-id="8732e-103">Unions discriminées</span><span class="sxs-lookup"><span data-stu-id="8732e-103">Discriminated Unions</span></span>

<span data-ttu-id="8732e-104">Les unions discriminées prennent en charge les valeurs qui peuvent être un nombre de cas nommés, chacun avec des valeurs et des types différents.</span><span class="sxs-lookup"><span data-stu-id="8732e-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="8732e-105">Les unions discriminées sont utiles pour les données hétérogènes ; données qui peuvent avoir des cas spéciaux, y compris des cas d’erreur et valides ; données qui varient en fonction du type d’une instance à l’autre ; et comme alternative pour les hiérarchies d’objets de petite taille.</span><span class="sxs-lookup"><span data-stu-id="8732e-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="8732e-106">En outre, les unions discriminées récursives sont utilisées pour représenter des structures de données d’arborescence.</span><span class="sxs-lookup"><span data-stu-id="8732e-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="8732e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8732e-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="8732e-108">Notes</span><span class="sxs-lookup"><span data-stu-id="8732e-108">Remarks</span></span>

<span data-ttu-id="8732e-109">Les unions discriminées sont semblables aux types Union dans d’autres langages, mais il existe des différences.</span><span class="sxs-lookup"><span data-stu-id="8732e-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="8732e-110">Comme avec un type d’Union en C++ ou un type Variant dans Visual Basic, les données stockées dans la valeur ne sont pas fixes ; Il peut s’agir de l’une des différentes options distinctes.</span><span class="sxs-lookup"><span data-stu-id="8732e-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="8732e-111">Contrairement aux unions dans ces autres langages, toutefois, chacune des options possibles reçoit un *identificateur de cas*.</span><span class="sxs-lookup"><span data-stu-id="8732e-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="8732e-112">Les identificateurs de cas sont des noms pour les différents types de valeurs possibles que les objets de ce type peuvent avoir ; les valeurs sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="8732e-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="8732e-113">Si les valeurs ne sont pas présentes, le cas est équivalent à un cas d’énumération.</span><span class="sxs-lookup"><span data-stu-id="8732e-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="8732e-114">Si des valeurs sont présentes, chaque valeur peut être une valeur unique d’un type spécifié ou un tuple qui agrège plusieurs champs du même type ou de types différents.</span><span class="sxs-lookup"><span data-stu-id="8732e-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="8732e-115">Vous pouvez attribuer un nom à un champ individuel, mais le nom est facultatif, même si d’autres champs dans le même cas sont nommés.</span><span class="sxs-lookup"><span data-stu-id="8732e-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="8732e-116">L’accessibilité des unions discriminées est par défaut `public` .</span><span class="sxs-lookup"><span data-stu-id="8732e-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="8732e-117">Par exemple, considérez la déclaration suivante d’un type de forme.</span><span class="sxs-lookup"><span data-stu-id="8732e-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="8732e-118">Le code précédent déclare une forme d’union discriminée, qui peut avoir des valeurs de l’un des trois cas : rectangle, cercle et prisme.</span><span class="sxs-lookup"><span data-stu-id="8732e-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="8732e-119">Chaque cas a un ensemble de champs différent.</span><span class="sxs-lookup"><span data-stu-id="8732e-119">Each case has a different set of fields.</span></span> <span data-ttu-id="8732e-120">Le rectangle a deux champs nommés, de type `float` , dont la largeur et la longueur sont les noms.</span><span class="sxs-lookup"><span data-stu-id="8732e-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="8732e-121">La casse du cercle n’a qu’un seul champ nommé, RADIUS.</span><span class="sxs-lookup"><span data-stu-id="8732e-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="8732e-122">Le cas Prism comporte trois champs, dont deux (largeur et hauteur) sont des champs nommés.</span><span class="sxs-lookup"><span data-stu-id="8732e-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="8732e-123">Les champs sans nom sont appelés champs anonymes.</span><span class="sxs-lookup"><span data-stu-id="8732e-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="8732e-124">Vous construisez des objets en fournissant des valeurs pour les champs nommés et anonymes conformément aux exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="8732e-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="8732e-125">Ce code montre que vous pouvez utiliser les champs nommés dans l’initialisation, ou vous pouvez vous appuyer sur l’ordre des champs dans la déclaration et simplement fournir les valeurs de chaque champ.</span><span class="sxs-lookup"><span data-stu-id="8732e-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="8732e-126">L’appel de constructeur pour `rect` dans le code précédent utilise les champs nommés, mais l’appel de constructeur pour `circ` utilise le classement.</span><span class="sxs-lookup"><span data-stu-id="8732e-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="8732e-127">Vous pouvez mélanger les champs ordonnés et les champs nommés, comme dans la construction de `prism` .</span><span class="sxs-lookup"><span data-stu-id="8732e-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="8732e-128">Le `option` type est une union discriminée simple dans la bibliothèque principale F #.</span><span class="sxs-lookup"><span data-stu-id="8732e-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="8732e-129">Le `option` type est déclaré comme suit.</span><span class="sxs-lookup"><span data-stu-id="8732e-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="8732e-130">Le code précédent spécifie que le type `Option` est une union discriminée qui a deux cas, `Some` et `None` .</span><span class="sxs-lookup"><span data-stu-id="8732e-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="8732e-131">Le `Some` cas a une valeur associée qui se compose d’un champ anonyme dont le type est représenté par le paramètre de type `'a` .</span><span class="sxs-lookup"><span data-stu-id="8732e-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="8732e-132">Le `None` cas n’a aucune valeur associée.</span><span class="sxs-lookup"><span data-stu-id="8732e-132">The `None` case has no associated value.</span></span> <span data-ttu-id="8732e-133">Par conséquent, le `option` type spécifie un type générique qui a une valeur d’un certain type ou aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="8732e-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="8732e-134">Le type `Option` a également un alias de type minuscule, `option` , qui est plus couramment utilisé.</span><span class="sxs-lookup"><span data-stu-id="8732e-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="8732e-135">Les identificateurs de cas peuvent être utilisés comme constructeurs pour le type d’union discriminée.</span><span class="sxs-lookup"><span data-stu-id="8732e-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="8732e-136">Par exemple, le code suivant est utilisé pour créer des valeurs du `option` type.</span><span class="sxs-lookup"><span data-stu-id="8732e-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="8732e-137">Les identificateurs de cas sont également utilisés dans les expressions de critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="8732e-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="8732e-138">Dans une expression de critères spéciaux, les identificateurs sont fournis pour les valeurs associées aux cas individuels.</span><span class="sxs-lookup"><span data-stu-id="8732e-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="8732e-139">Par exemple, dans le code suivant, `x` est l’identificateur en fonction de la valeur associée à la `Some` casse du `option` type.</span><span class="sxs-lookup"><span data-stu-id="8732e-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="8732e-140">Dans les expressions de critères spéciaux, vous pouvez utiliser des champs nommés pour spécifier des correspondances d’union discriminée.</span><span class="sxs-lookup"><span data-stu-id="8732e-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="8732e-141">Pour le type de forme qui a été déclaré précédemment, vous pouvez utiliser les champs nommés comme le montre le code suivant pour extraire les valeurs des champs.</span><span class="sxs-lookup"><span data-stu-id="8732e-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

<span data-ttu-id="8732e-142">Normalement, les identificateurs de cas peuvent être utilisés sans les qualifier avec le nom de l’Union.</span><span class="sxs-lookup"><span data-stu-id="8732e-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="8732e-143">Si vous souhaitez que le nom soit toujours qualifié avec le nom de l’Union, vous pouvez appliquer l’attribut [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) à la définition du type d’Union.</span><span class="sxs-lookup"><span data-stu-id="8732e-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="8732e-144">Désencapsulage d’unions discriminées</span><span class="sxs-lookup"><span data-stu-id="8732e-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="8732e-145">En F #, les unions discriminées sont souvent utilisées dans la modélisation de domaine pour l’encapsulation d’un type unique.</span><span class="sxs-lookup"><span data-stu-id="8732e-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="8732e-146">Il est également facile d’extraire la valeur sous-jacente via la mise en correspondance des modèles.</span><span class="sxs-lookup"><span data-stu-id="8732e-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="8732e-147">Vous n’avez pas besoin d’utiliser une expression de correspondance pour un cas unique :</span><span class="sxs-lookup"><span data-stu-id="8732e-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

<span data-ttu-id="8732e-148">Cela est illustré par l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8732e-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="8732e-149">Les critères spéciaux sont également autorisés directement dans les paramètres de fonction, ce qui vous permet de désencapsuler un cas unique ici :</span><span class="sxs-lookup"><span data-stu-id="8732e-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="8732e-150">Unions discriminées de struct</span><span class="sxs-lookup"><span data-stu-id="8732e-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="8732e-151">Vous pouvez également représenter des unions discriminées comme des structs.</span><span class="sxs-lookup"><span data-stu-id="8732e-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="8732e-152">Cette opération s’effectue avec l' `[<Struct>]` attribut.</span><span class="sxs-lookup"><span data-stu-id="8732e-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="8732e-153">Étant donné qu’il s’agit de types valeur et non de types référence, des considérations supplémentaires sont à prendre en compte par rapport aux unions discriminées de référence :</span><span class="sxs-lookup"><span data-stu-id="8732e-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="8732e-154">Ils sont copiés en tant que types valeur et ont une sémantique de type valeur.</span><span class="sxs-lookup"><span data-stu-id="8732e-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="8732e-155">Vous ne pouvez pas utiliser une définition de type récursive avec une union discriminée de struct à cas.</span><span class="sxs-lookup"><span data-stu-id="8732e-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="8732e-156">Vous devez fournir des noms de cas uniques pour une union discriminée de struct à cas unique.</span><span class="sxs-lookup"><span data-stu-id="8732e-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="8732e-157">Utilisation d’unions discriminées au lieu de hiérarchies d’objets</span><span class="sxs-lookup"><span data-stu-id="8732e-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="8732e-158">Vous pouvez souvent utiliser une union discriminée comme alternative plus simple à une petite hiérarchie d’objets.</span><span class="sxs-lookup"><span data-stu-id="8732e-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="8732e-159">Par exemple, l’union discriminée suivante peut être utilisée à la place d’une `Shape` classe de base qui a des types dérivés pour Circle, Square, etc.</span><span class="sxs-lookup"><span data-stu-id="8732e-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="8732e-160">Au lieu d’une méthode virtuelle pour calculer une zone ou un périmètre, comme vous le feriez dans une implémentation orientée objet, vous pouvez utiliser des critères spéciaux pour créer une branche vers des formules appropriées afin de calculer ces quantités.</span><span class="sxs-lookup"><span data-stu-id="8732e-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="8732e-161">Dans l’exemple suivant, différentes formules sont utilisées pour calculer la zone, en fonction de la forme.</span><span class="sxs-lookup"><span data-stu-id="8732e-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="8732e-162">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="8732e-162">The output is as follows:</span></span>

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="8732e-163">Utilisation d’unions discriminées pour les structures de données d’arborescence</span><span class="sxs-lookup"><span data-stu-id="8732e-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="8732e-164">Les unions discriminées peuvent être récursives, ce qui signifie que l’Union elle-même peut être incluse dans le type d’un ou de plusieurs cas.</span><span class="sxs-lookup"><span data-stu-id="8732e-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="8732e-165">Les unions discriminées récursives peuvent être utilisées pour créer des structures d’arborescence, qui sont utilisées pour modéliser des expressions dans des langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="8732e-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="8732e-166">Dans le code suivant, une union discriminée récursive est utilisée pour créer une structure de données d’arborescence binaire.</span><span class="sxs-lookup"><span data-stu-id="8732e-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="8732e-167">L’Union se compose de deux cas, `Node` , qui est un nœud avec une valeur entière et des sous-arborescences gauche et droite, et `Tip` , qui termine l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="8732e-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="8732e-168">Dans le code précédent, `resultSumTree` a la valeur 10.</span><span class="sxs-lookup"><span data-stu-id="8732e-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="8732e-169">L’illustration suivante montre l’arborescence de `myTree` .</span><span class="sxs-lookup"><span data-stu-id="8732e-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Diagramme qui affiche l’arborescence pour myTree.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="8732e-171">Les unions discriminées fonctionnent bien si les nœuds de l’arborescence sont hétérogènes.</span><span class="sxs-lookup"><span data-stu-id="8732e-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="8732e-172">Dans le code suivant, le type `Expression` représente l’arborescence de syntaxe abstraite d’une expression dans un langage de programmation simple qui prend en charge l’addition et la multiplication de nombres et de variables.</span><span class="sxs-lookup"><span data-stu-id="8732e-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="8732e-173">Certains des cas d’Union ne sont pas récursifs et représentent des nombres ( `Number` ) ou des variables ( `Variable` ).</span><span class="sxs-lookup"><span data-stu-id="8732e-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="8732e-174">D’autres cas sont récursifs et représentent des opérations ( `Add` et `Multiply` ), où les opérandes sont également des expressions.</span><span class="sxs-lookup"><span data-stu-id="8732e-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="8732e-175">La `Evaluate` fonction utilise une expression de correspondance pour traiter de manière récursive l’arborescence de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="8732e-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="8732e-176">Lorsque ce code est exécuté, la valeur de `result` est 5.</span><span class="sxs-lookup"><span data-stu-id="8732e-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="8732e-177">Membres</span><span class="sxs-lookup"><span data-stu-id="8732e-177">Members</span></span>

<span data-ttu-id="8732e-178">Il est possible de définir des membres sur des unions discriminées.</span><span class="sxs-lookup"><span data-stu-id="8732e-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="8732e-179">L’exemple suivant montre comment définir une propriété et implémenter une interface :</span><span class="sxs-lookup"><span data-stu-id="8732e-179">The following example shows how to define a property and implement an interface:</span></span>

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
            | Circle r -> printfn $"Circle with radius %f{r}"
            | EquilateralTriangle s -> printfn $"Equilateral Triangle of side %f{s}"
            | Square s -> printfn $"Square with side %f{s}"
            | Rectangle(l, w) -> printfn $"Rectangle with length %f{l} and width %f{w}"
```

## <a name="common-attributes"></a><span data-ttu-id="8732e-180">Attributs communs</span><span class="sxs-lookup"><span data-stu-id="8732e-180">Common attributes</span></span>

<span data-ttu-id="8732e-181">Les attributs suivants sont généralement affichés dans des unions discriminées :</span><span class="sxs-lookup"><span data-stu-id="8732e-181">The following attributes are commonly seen in discriminated unions:</span></span>

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="8732e-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8732e-182">See also</span></span>

- [<span data-ttu-id="8732e-183">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="8732e-183">F# Language Reference</span></span>](index.md)
