---
title: Unions discriminées
description: Découvrez comment utiliser F# unions discriminées.
ms.date: 05/16/2016
ms.openlocfilehash: 27fb9205f3f216adc435483fd1dcc839a6e13e03
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557970"
---
# <a name="discriminated-unions"></a><span data-ttu-id="ae4b2-103">Unions discriminées</span><span class="sxs-lookup"><span data-stu-id="ae4b2-103">Discriminated Unions</span></span>

<span data-ttu-id="ae4b2-104">Les unions discriminées fournissent la prise en charge pour les valeurs qui peuvent s’agir d’un nombre de cas nommés, chacun avec des types et des valeurs différentes.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="ae4b2-105">Les unions discriminées sont utiles pour les données hétérogènes ; données qui peuvent avoir des cas spéciaux, y compris valides et cas d’erreur ; données qui varie selon le type d’une instance à l’autre ; et comme alternative pour les petites hiérarchies d’objets.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="ae4b2-106">En outre, discriminées récursives unions sont utilisées pour représenter des structures de données d’arborescence.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae4b2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae4b2-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="ae4b2-108">Notes</span><span class="sxs-lookup"><span data-stu-id="ae4b2-108">Remarks</span></span>

<span data-ttu-id="ae4b2-109">Les unions discriminées sont semblables aux types union dans d’autres langages, mais il existe des différences.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="ae4b2-110">Comme avec un type union en C++ ou un type variant en Visual Basic, les données stockées dans la valeur ne sont pas fixe ; Il peut prendre l’une des diverses options distinctes.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="ae4b2-111">Contrairement aux unions de ces autres langages, toutefois, chacune des options possibles reçoit un *identificateur de cas*.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="ae4b2-112">Les identificateurs de cas sont des noms pour les différents types de valeurs susceptibles d’entraîner des objets de ce type ; les valeurs sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="ae4b2-113">Si les valeurs ne sont pas présents, le cas équivaut à un cas d’énumération.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="ae4b2-114">Si les valeurs sont présentes, chaque valeur peut être une valeur unique d’un type spécifié, ou un tuple qui regroupe plusieurs champs des types identiques ou différents.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="ae4b2-115">Vous pouvez donner à un champ individuel un nom, mais le nom est facultatif, même si d’autres champs dans le même cas sont nommés.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="ae4b2-116">Par défaut est d’accessibilité pour les unions discriminées `public`.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="ae4b2-117">Par exemple, considérez la déclaration suivante d’un type de forme.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="ae4b2-118">Le code précédent déclare une union discriminée forme, qui peut avoir des valeurs d’un des trois cas : Rectangle, cercle et prisme.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="ae4b2-119">Chaque cas possède un ensemble de champs différent.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-119">Each case has a different set of fields.</span></span> <span data-ttu-id="ae4b2-120">Le Rectangle a le nom de deux champs, tous deux de type `float`, qui ont le nom largeur et la longueur.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="ae4b2-121">Le cercle a un seul champ nommé, radius.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="ae4b2-122">Le cas de prisme a trois champs, deux (largeur et hauteur) sont des champs nommés.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="ae4b2-123">Les champs sans nom sont appelés des champs anonymes.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="ae4b2-124">Vous construisez des objets en fournissant des valeurs pour les champs nommés et anonymes selon les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="ae4b2-125">Ce code montre que vous pouvez utiliser les champs nommés dans l’initialisation, ou vous pouvez utiliser l’ordre des champs dans la déclaration et fournir uniquement les valeurs pour chaque champ à son tour.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="ae4b2-126">L’appel de constructeur pour `rect` dans le code précédent utilise les champs nommés, mais l’appel de constructeur pour `circ` utilise le classement.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="ae4b2-127">Vous pouvez combiner les champs ordonnés et les champs nommés, comme dans la construction de `prism`.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="ae4b2-128">Le `option` type est une union discriminée simple dans le F# bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="ae4b2-129">Le `option` type est déclaré comme suit.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="ae4b2-130">Le code précédent Spécifie que le type `Option` est une union discriminée qui a deux cas, `Some` et `None`.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="ae4b2-131">Le `Some` cas a une valeur associée qui se compose d’un champ anonyme dont le type est représenté par le paramètre de type `'a`.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="ae4b2-132">Le `None` cas n’a aucune valeur associée.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-132">The `None` case has no associated value.</span></span> <span data-ttu-id="ae4b2-133">Par conséquent, le `option` type spécifie un type générique qui a soit une valeur d’un certain type, soit aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="ae4b2-134">Le type `Option` a également un alias de type en minuscules, `option`, qui est plus couramment utilisé.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="ae4b2-135">Les identificateurs de cas peuvent être utilisés comme constructeurs pour le type d’union discriminée.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="ae4b2-136">Par exemple, le code suivant est utilisé pour créer des valeurs de la `option` type.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="ae4b2-137">Les identificateurs de cas sont également utilisés dans les expressions de critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="ae4b2-138">Dans une expression à critères spéciaux, les identificateurs sont fournis pour les valeurs associées à chaque cas.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="ae4b2-139">Par exemple, dans le code suivant, `x` est l’identificateur qui reçoit la valeur qui est associée à la `Some` cas de la `option` type.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="ae4b2-140">Dans les expressions de critères spéciaux, vous pouvez utiliser des champs nommés pour spécifier des correspondances d’unions discriminées.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="ae4b2-141">Pour le type de forme qui a été déclaré précédemment, vous pouvez utiliser les champs nommés, comme le montre le code suivant pour extraire les valeurs des champs.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="ae4b2-142">Normalement, les identificateurs de cas peuvent être utilisés sans être qualifiés avec le nom de l’union.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="ae4b2-143">Si vous souhaitez que le nom soit toujours qualifié avec le nom de l’union, vous pouvez appliquer le [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribut à la définition de type d’union.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="ae4b2-144">Unions discriminées désencapsuler</span><span class="sxs-lookup"><span data-stu-id="ae4b2-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="ae4b2-145">Dans F# Unions discriminées sont souvent utilisées dans la modélisation de domaine pour l’encapsulation d’un type unique.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="ae4b2-146">Il est facile d’extraire la valeur sous-jacente par le biais de critères spéciaux ainsi.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="ae4b2-147">Vous n’avez pas besoin d’utiliser une expression de correspondance pour un seul cas :</span><span class="sxs-lookup"><span data-stu-id="ae4b2-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="ae4b2-148">Cela est illustré par l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ae4b2-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="ae4b2-149">Critères spéciaux est également autorisée directement dans les paramètres de fonction, donc vous pouvez désencapsuler un cas unique :</span><span class="sxs-lookup"><span data-stu-id="ae4b2-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="ae4b2-150">Unions discriminées de structs</span><span class="sxs-lookup"><span data-stu-id="ae4b2-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="ae4b2-151">En commençant par F# 4.1, vous pouvez également représenter des Unions discriminées en tant que structures.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-151">Starting with F# 4.1, you can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="ae4b2-152">Cette opération est effectuée avec la `[<Struct>]` attribut.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="ae4b2-153">Car celles-ci sont des types valeur et pas les types référencent, voici supplémentaire par rapport à la référence de considérations sur les unions discriminées :</span><span class="sxs-lookup"><span data-stu-id="ae4b2-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="ae4b2-154">Ils sont copiés en tant que types de valeur et ont une sémantique de type valeur.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="ae4b2-155">Vous ne pouvez pas utiliser une définition de type récursive avec un struct multicase discriminées Union.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="ae4b2-156">Vous devez fournir des noms de cas uniques pour un struct multicase discriminées Union.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="ae4b2-157">Utilisation d’Unions discriminées au lieu de hiérarchies d’objets</span><span class="sxs-lookup"><span data-stu-id="ae4b2-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="ae4b2-158">Vous pouvez souvent utiliser une union discriminée comme alternative plus simple à une petite hiérarchie d’objets.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="ae4b2-159">Par exemple, l’union discriminée suivante pourrait être utilisée au lieu d’un `Shape` classe de base qui a des types dérivés pour cercle, carré, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="ae4b2-160">À la place d’une méthode virtuelle pour calculer une zone ou un périmètre, que vous utiliseriez dans une implémentation orientée objet, vous pouvez utiliser des critères spéciaux à la branche vers les formules appropriées pour calculer ces quantités.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="ae4b2-161">Dans l’exemple suivant, différentes formules sont utilisées pour calculer la zone, en fonction de la forme.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="ae4b2-162">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ae4b2-162">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="ae4b2-163">Utilisation d’Unions discriminées pour les Structures de données d’arborescence</span><span class="sxs-lookup"><span data-stu-id="ae4b2-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="ae4b2-164">Les unions discriminées peuvent être récursives, ce qui signifie que l’union elle-même peut être incluse dans le type d’un ou plusieurs cas.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="ae4b2-165">Récursive les unions discriminées peuvent être utilisées pour créer des arborescences, qui sont utilisées pour modeler des expressions dans les langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="ae4b2-166">Dans le code suivant, une récursive discriminées union est utilisée pour créer une structure de données d’arborescence binaire.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="ae4b2-167">L’union se compose de deux cas, `Node`, qui est un nœud avec une valeur entière et des sous-arborescences gauche et droite, et `Tip`, qui termine l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="ae4b2-168">Dans le code précédent, `resultSumTree` a la valeur 10.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="ae4b2-169">L’illustration suivante montre la structure d’arborescence de `myTree`.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Diagramme qui montre l’arborescence pour myTree.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="ae4b2-171">Les unions discriminées fonctionnent bien si les nœuds dans l’arborescence sont hétérogènes.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="ae4b2-172">Dans le code suivant, le type `Expression` représente l’arborescence de syntaxe abstraite d’une expression dans un langage de programmation simple qui prend en charge l’addition et multiplication de nombres et de variables.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="ae4b2-173">Certains cas d’union ne sont pas récursifs et représentent des nombres (`Number`) ou des variables (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="ae4b2-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="ae4b2-174">Autres cas sont récursifs et représentent des opérations (`Add` et `Multiply`), où les opérandes sont également des expressions.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="ae4b2-175">Le `Evaluate` fonction utilise une expression de correspondance pour traiter de manière récursive l’arborescence de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="ae4b2-176">Lorsque ce code est exécuté, la valeur de `result` est 5.</span><span class="sxs-lookup"><span data-stu-id="ae4b2-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="common-attributes"></a><span data-ttu-id="ae4b2-177">Attributs courants</span><span class="sxs-lookup"><span data-stu-id="ae4b2-177">Common Attributes</span></span>

<span data-ttu-id="ae4b2-178">Les attributs suivants sont généralement visibles dans les unions discriminées :</span><span class="sxs-lookup"><span data-stu-id="ae4b2-178">The following attributes are commonly seen in discriminated unions:</span></span>

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a><span data-ttu-id="ae4b2-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae4b2-179">See also</span></span>

- [<span data-ttu-id="ae4b2-180">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="ae4b2-180">F# Language Reference</span></span>](index.md)
