---
title: Critères spéciaux
description: Découvrez comment les modèles sont utilisées dans F# pour comparer des données avec les structures logiques, décomposer des données en parties constituantes ou extraire des informations à partir des données.
ms.date: 05/16/2016
ms.openlocfilehash: f76a5fb675f83df87dd896f471a3552495f39e7e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641767"
---
# <a name="pattern-matching"></a><span data-ttu-id="1ccc8-103">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="1ccc8-103">Pattern Matching</span></span>

<span data-ttu-id="1ccc8-104">Les modèles sont des règles de transformation des données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="1ccc8-105">Ils sont utilisés tout au long de la F# langage pour comparer des données avec une structure logique ou des structures, décomposer des données en parties constituantes ou extraire des informations à partir des données de différentes manières.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ccc8-106">Notes</span><span class="sxs-lookup"><span data-stu-id="1ccc8-106">Remarks</span></span>

<span data-ttu-id="1ccc8-107">Modèles utilisés dans de nombreuses constructions de langage, tels que le `match` expression.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="1ccc8-108">Ils sont utilisés lorsque vous traitez des arguments pour les fonctions dans `let` liaisons, des expressions lambda et gestionnaires d’exceptions associés à la `try...with` expression.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="1ccc8-109">Pour plus d’informations, consultez [Expressions de correspondance](match-expressions.md), [liaisons let](functions/let-bindings.md), [Expressions Lambda : Le `fun` mot clé](functions/lambda-expressions-the-fun-keyword.md), et [Exceptions : Le `try...with` Expression](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="1ccc8-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="1ccc8-110">Par exemple, dans le `match` expression, le *modèle* est ce qui suit le symbole de barre verticale.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="1ccc8-111">Chaque modèle agit comme une règle transforme l’entrée d’une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="1ccc8-112">Dans le `match` expression, chaque modèle est examinée tour à tour pour voir si les données d’entrée sont compatibles avec le modèle.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="1ccc8-113">Si une correspondance est trouvée, l’expression de résultat est exécutée.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="1ccc8-114">Si une correspondance est introuvable, la règle de modèle suivante est testée.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="1ccc8-115">When facultatif *condition* partie est expliquée dans [Expressions de correspondance](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1ccc8-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="1ccc8-116">Modèles pris en charge sont affichés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="1ccc8-117">Au moment de l’exécution, l’entrée est testée par rapport à chacun des modèles suivants dans l’ordre indiqué dans la table, et modèles sont appliquées de manière récursive, à partir de tout d’abord au dernier telles qu’elles apparaissent dans votre code et de gauche à droite pour les modèles sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="1ccc8-118">Nom</span><span class="sxs-lookup"><span data-stu-id="1ccc8-118">Name</span></span>|<span data-ttu-id="1ccc8-119">Description</span><span class="sxs-lookup"><span data-stu-id="1ccc8-119">Description</span></span>|<span data-ttu-id="1ccc8-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ccc8-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="1ccc8-121">Modèle de constante</span><span class="sxs-lookup"><span data-stu-id="1ccc8-121">Constant pattern</span></span>|<span data-ttu-id="1ccc8-122">Toute numérique, caractère, ou littéral de chaîne, une constante d’énumération ou identificateur littéral défini</span><span class="sxs-lookup"><span data-stu-id="1ccc8-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="1ccc8-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="1ccc8-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="1ccc8-124">Modèle d’identificateur</span><span class="sxs-lookup"><span data-stu-id="1ccc8-124">Identifier pattern</span></span>|<span data-ttu-id="1ccc8-125">Valeur de cas d’une union discriminée, étiquette d’exception ou cas de modèle actif</span><span class="sxs-lookup"><span data-stu-id="1ccc8-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="1ccc8-126">Modèle de variable</span><span class="sxs-lookup"><span data-stu-id="1ccc8-126">Variable pattern</span></span>|<span data-ttu-id="1ccc8-127">*identifier*</span><span class="sxs-lookup"><span data-stu-id="1ccc8-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="1ccc8-128">`as` Modèle</span><span class="sxs-lookup"><span data-stu-id="1ccc8-128">`as` pattern</span></span>|<span data-ttu-id="1ccc8-129">*modèle* comme *identificateur*</span><span class="sxs-lookup"><span data-stu-id="1ccc8-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="1ccc8-130">OU un modèle</span><span class="sxs-lookup"><span data-stu-id="1ccc8-130">OR pattern</span></span>|<span data-ttu-id="1ccc8-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="1ccc8-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="1ccc8-132">ET le modèle</span><span class="sxs-lookup"><span data-stu-id="1ccc8-132">AND pattern</span></span>|<span data-ttu-id="1ccc8-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="1ccc8-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="1ccc8-134">Modèle Cons</span><span class="sxs-lookup"><span data-stu-id="1ccc8-134">Cons pattern</span></span>|<span data-ttu-id="1ccc8-135">*identificateur* :: *identificateur de la liste*</span><span class="sxs-lookup"><span data-stu-id="1ccc8-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="1ccc8-136">Modèle de liste</span><span class="sxs-lookup"><span data-stu-id="1ccc8-136">List pattern</span></span>|<span data-ttu-id="1ccc8-137">[ *modèle_1*;... ; *modèle_n* ]</span><span class="sxs-lookup"><span data-stu-id="1ccc8-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="1ccc8-138">Modèle de tableau</span><span class="sxs-lookup"><span data-stu-id="1ccc8-138">Array pattern</span></span>|<span data-ttu-id="1ccc8-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="1ccc8-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="1ccc8-140">Modèle entre parenthèses</span><span class="sxs-lookup"><span data-stu-id="1ccc8-140">Parenthesized pattern</span></span>|<span data-ttu-id="1ccc8-141">( *pattern* )</span><span class="sxs-lookup"><span data-stu-id="1ccc8-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="1ccc8-142">Modèle de tuple</span><span class="sxs-lookup"><span data-stu-id="1ccc8-142">Tuple pattern</span></span>|<span data-ttu-id="1ccc8-143">( *modèle_1*,..., *modèle_n* )</span><span class="sxs-lookup"><span data-stu-id="1ccc8-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="1ccc8-144">Modèle d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="1ccc8-144">Record pattern</span></span>|<span data-ttu-id="1ccc8-145">{ *identificateur1* = *modèle_1*;... ; *identificateur_n* = *modèle_n* }</span><span class="sxs-lookup"><span data-stu-id="1ccc8-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="1ccc8-146">Modèle de caractère générique</span><span class="sxs-lookup"><span data-stu-id="1ccc8-146">Wildcard pattern</span></span>|<span data-ttu-id="1ccc8-147">_</span><span class="sxs-lookup"><span data-stu-id="1ccc8-147">_</span></span>|`_`|
|<span data-ttu-id="1ccc8-148">Modèle avec une annotation de type</span><span class="sxs-lookup"><span data-stu-id="1ccc8-148">Pattern together with type annotation</span></span>|<span data-ttu-id="1ccc8-149">*modèle* : *type*</span><span class="sxs-lookup"><span data-stu-id="1ccc8-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="1ccc8-150">Modèle de test de type</span><span class="sxs-lookup"><span data-stu-id="1ccc8-150">Type test pattern</span></span>|<span data-ttu-id="1ccc8-151">:?</span><span class="sxs-lookup"><span data-stu-id="1ccc8-151">:?</span></span> <span data-ttu-id="1ccc8-152">*type* [comme *identificateur* ]</span><span class="sxs-lookup"><span data-stu-id="1ccc8-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="1ccc8-153">Modèle Null</span><span class="sxs-lookup"><span data-stu-id="1ccc8-153">Null pattern</span></span>|<span data-ttu-id="1ccc8-154">null</span><span class="sxs-lookup"><span data-stu-id="1ccc8-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="1ccc8-155">Modèles de constante</span><span class="sxs-lookup"><span data-stu-id="1ccc8-155">Constant Patterns</span></span>

<span data-ttu-id="1ccc8-156">Modèles de constante sont numériques, de caractère et de littéraux de chaîne, des constantes d’énumération (avec le nom de type d’énumération inclus).</span><span class="sxs-lookup"><span data-stu-id="1ccc8-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="1ccc8-157">Un `match` expression qui a uniquement les modèles de constante peut être comparée à une instruction case dans d’autres langages.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="1ccc8-158">L’entrée est comparée à la valeur littérale et le modèle correspond à si les valeurs sont égales.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="1ccc8-159">Le type du littéral doit être compatible avec le type de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="1ccc8-160">L’exemple suivant illustre l’utilisation de modèles de littéral et utilise également un modèle de variable et un modèle OR.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="1ccc8-161">Un autre exemple de modèle de littéral est un modèle basé sur des constantes d’énumération.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="1ccc8-162">Vous devez spécifier le nom de type énumération lorsque vous utilisez des constantes d’énumération.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="1ccc8-163">Modèles d’identificateur</span><span class="sxs-lookup"><span data-stu-id="1ccc8-163">Identifier Patterns</span></span>

<span data-ttu-id="1ccc8-164">Si le modèle est une chaîne de caractères qui forme un identificateur valide, le format de l’identificateur détermine comment le modèle est mis en correspondance.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="1ccc8-165">Si l’identificateur est plus long qu’un caractère unique et commence par un caractère majuscule, le compilateur tente d’établir une correspondance avec le modèle d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="1ccc8-166">L’identificateur pour ce modèle peut être une valeur marquée avec l’attribut littéral, un cas d’union discriminée, un identificateur d’exception ou cas de modèle actif.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="1ccc8-167">Si aucun identificateur correspondant n’est trouvé, la correspondance échoue et la règle de modèle suivante, le modèle de variable, est comparée à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="1ccc8-168">Modèles d’union discriminée peuvent être simples cas nommés, ou ils peuvent avoir une valeur ou un tuple contenant plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="1ccc8-169">S’il existe une valeur, vous devez spécifier un identificateur pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="1ccc8-170">Dans le cas d’un tuple, vous devez fournir un modèle de tuple avec un identificateur pour chaque élément du tuple ou un identificateur avec un nom de champ pour l’une ou plusieurs champs d’union nommés.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="1ccc8-171">Consultez les exemples de code dans cette section pour obtenir des exemples.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="1ccc8-172">Le `option` type est une union discriminée qui a deux cas, `Some` et `None`.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="1ccc8-173">Un cas (`Some`) a une valeur, mais l’autre (`None`) est simplement un cas nommé.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="1ccc8-174">Par conséquent, `Some` doit avoir une variable pour la valeur associée à la `Some` , mais `None` doit apparaître seul.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="1ccc8-175">Dans le code suivant, la variable `var1` se voit attribuer la valeur est obtenue en faisant correspondre à la `Some` cas.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="1ccc8-176">Dans l’exemple suivant, le `PersonName` union discriminée contient un mélange de chaînes et des caractères qui représentent différentes formes possibles de noms.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="1ccc8-177">Les cas de l’union discriminée sont `FirstOnly`, `LastOnly`, et `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="1ccc8-178">Pour les unions discriminées qui ont des champs nommés, vous utilisez le signe égal (=) pour extraire la valeur d’un champ nommé.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="1ccc8-179">Par exemple, considérez une union discriminée avec une déclaration similaire à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="1ccc8-180">Vous pouvez utiliser les champs nommés dans une expression de critères spéciaux comme suit.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="1ccc8-181">L’utilisation du champ nommé est facultative, de sorte que dans l’exemple précédent, les deux `Circle(r)` et `Circle(radius = r)` ont le même effet.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="1ccc8-182">Lorsque vous spécifiez plusieurs champs, utilisez le point-virgule ( ;) comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="1ccc8-183">Modèles actifs permettent de définir des critères spéciaux personnalisés plus complexes.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="1ccc8-184">Pour plus d’informations sur les modèles actifs, consultez [modèles actifs](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="1ccc8-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="1ccc8-185">Le cas dans lequel l’identificateur est une exception est utilisé dans les critères spéciaux dans le contexte de gestionnaires d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="1ccc8-186">Pour plus d’informations sur les critères spéciaux dans la gestion des exceptions, consultez [Exceptions : Le `try...with` Expression](exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="1ccc8-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="1ccc8-187">Modèles de variable</span><span class="sxs-lookup"><span data-stu-id="1ccc8-187">Variable Patterns</span></span>

<span data-ttu-id="1ccc8-188">Le modèle de variable assigne la valeur mise en correspondance à un nom de variable, qui est ensuite disponible pour une utilisation dans l’expression d’exécution à droite de la `->` symbole.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="1ccc8-189">Un modèle de variable seul correspond à n’importe quelle entrée, mais les modèles de variable apparaissent souvent dans d’autres modèles, ce qui permet à des structures plus complexes telles que les tuples et des tableaux pour être décomposé en variables.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="1ccc8-190">L’exemple suivant montre un modèle de variable dans un modèle de tuple.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="1ccc8-191">en tant que modèle</span><span class="sxs-lookup"><span data-stu-id="1ccc8-191">as Pattern</span></span>

<span data-ttu-id="1ccc8-192">Le `as` modèle est un modèle qui a un `as` clause est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="1ccc8-193">Le `as` clause lie la valeur correspondante à un nom qui peut être utilisé dans l’expression de l’exécution d’un `match` expression, ou, dans le cas où ce modèle est utilisé dans un `let` de liaison, le nom est ajouté en tant que liaison à la portée locale.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="1ccc8-194">L’exemple suivant utilise un `as` modèle.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="1ccc8-195">OU un modèle</span><span class="sxs-lookup"><span data-stu-id="1ccc8-195">OR Pattern</span></span>

<span data-ttu-id="1ccc8-196">Le modèle OR est utilisé lorsque les données d’entrée peuvent correspondre à plusieurs modèles, et que vous souhaitez exécuter le même code en conséquence.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="1ccc8-197">Les types des deux côtés du modèle OR doivent être compatibles.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="1ccc8-198">L’exemple suivant illustre le modèle OR.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="1ccc8-199">ET le modèle</span><span class="sxs-lookup"><span data-stu-id="1ccc8-199">AND Pattern</span></span>

<span data-ttu-id="1ccc8-200">Le modèle AND requiert que l’entrée corresponde à deux modèles.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="1ccc8-201">Les types des deux côtés du modèle AND doivent être compatibles.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="1ccc8-202">L’exemple suivant est semblable `detectZeroTuple` indiqué dans le [modèle de Tuple](https://msdn.microsoft.com/library/#tuple) section plus loin dans cette rubrique, mais ici `var1` et `var2` sont obtenus en tant que valeurs à l’aide du modèle AND.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="1ccc8-203">Modèle Cons</span><span class="sxs-lookup"><span data-stu-id="1ccc8-203">Cons Pattern</span></span>

<span data-ttu-id="1ccc8-204">Le modèle cons est utilisé pour décomposer une liste comme le premier élément, le *head*et une liste qui contient les éléments restants, le *fin*.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="1ccc8-205">Modèle de liste</span><span class="sxs-lookup"><span data-stu-id="1ccc8-205">List Pattern</span></span>

<span data-ttu-id="1ccc8-206">Le modèle de liste permet la décomposition en un nombre d’éléments de listes.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="1ccc8-207">Le modèle de liste proprement dit peut correspondre uniquement les listes d’un nombre spécifique d’éléments.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="1ccc8-208">Modèle de tableau</span><span class="sxs-lookup"><span data-stu-id="1ccc8-208">Array Pattern</span></span>

<span data-ttu-id="1ccc8-209">Le modèle de tableau est semblable au modèle de liste et peut être utilisé pour décomposer des tableaux de longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="1ccc8-210">Modèle entre parenthèses</span><span class="sxs-lookup"><span data-stu-id="1ccc8-210">Parenthesized Pattern</span></span>

<span data-ttu-id="1ccc8-211">Parenthèses peuvent être groupées autour de modèles pour obtenir l’associativité désirée.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="1ccc8-212">Dans l’exemple suivant, les parenthèses sont utilisées pour contrôler l’associativité entre un modèle AND et un modèle cons.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="1ccc8-213">Modèle de tuple</span><span class="sxs-lookup"><span data-stu-id="1ccc8-213">Tuple Pattern</span></span>

<span data-ttu-id="1ccc8-214">Le modèle de tuple correspond à l’entrée sous forme de tuple et permet le tuple à décomposer en éléments constituants à l’aide de critères spéciaux de variables pour chaque position dans le tuple.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="1ccc8-215">L’exemple suivant illustre le modèle de tuple et utilise également des modèles de littéral, des modèles de variable et le modèle de caractère générique.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="1ccc8-216">Modèle d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="1ccc8-216">Record Pattern</span></span>

<span data-ttu-id="1ccc8-217">Le modèle d’enregistrement est utilisé pour décomposer des enregistrements pour extraire les valeurs des champs.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="1ccc8-218">Le modèle n’a pas référencer tous les champs de l’enregistrement. tout champ omis ne participe pas mise en correspondance uniquement et n’est pas extraits.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="1ccc8-219">Modèle de caractère générique</span><span class="sxs-lookup"><span data-stu-id="1ccc8-219">Wildcard Pattern</span></span>

<span data-ttu-id="1ccc8-220">Le modèle de caractère générique est représenté par un trait de soulignement (`_`) de caractères et correspond à une entrée, comme le modèle de variable, à ceci près que l’entrée est ignorée au lieu d’assigné à une variable.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="1ccc8-221">Le modèle de caractère générique est souvent utilisé dans d’autres modèles comme un espace réservé pour les valeurs qui ne sont pas nécessaires dans l’expression à droite de la `->` symbole.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="1ccc8-222">Le modèle de caractère générique est aussi fréquemment utilisé à la fin d’une liste de modèles pour faire correspondre n’importe quelle entrée sans correspondance.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="1ccc8-223">Le modèle de caractère générique est illustré dans de nombreux exemples de code dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="1ccc8-224">Consultez le code précédent pour obtenir un exemple.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="1ccc8-225">Modèles avec des Annotations de Type</span><span class="sxs-lookup"><span data-stu-id="1ccc8-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="1ccc8-226">Les modèles peuvent avoir des annotations de type.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-226">Patterns can have type annotations.</span></span> <span data-ttu-id="1ccc8-227">Celles-ci se comportent comme les autres annotations de type et guident l’inférence comme d’autres annotations de type.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="1ccc8-228">Parenthèses sont obligatoires autour des annotations de type dans les modèles.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="1ccc8-229">Le code suivant illustre un modèle qui a une annotation de type.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="1ccc8-230">Modèle de Test de type</span><span class="sxs-lookup"><span data-stu-id="1ccc8-230">Type Test Pattern</span></span>

<span data-ttu-id="1ccc8-231">Le modèle de test de type est utilisé pour faire correspondre l’entrée par rapport à un type.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="1ccc8-232">Si le type d’entrée est une recherche de correspondance (ou un type dérivé de) le type spécifié dans le modèle, la correspondance réussit.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="1ccc8-233">L’exemple suivant illustre le modèle de test de type.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="1ccc8-234">Modèle Null</span><span class="sxs-lookup"><span data-stu-id="1ccc8-234">Null Pattern</span></span>

<span data-ttu-id="1ccc8-235">Le modèle null correspond à la valeur null qui peut s’afficher lorsque vous travaillez avec des types qui autorisent une valeur null.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="1ccc8-236">Modèles null sont fréquemment utilisés lors de l’interaction avec le code .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="1ccc8-237">Par exemple, la valeur de retour d’une API .NET peut être l’entrée à un `match` expression.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="1ccc8-238">Vous pouvez contrôler le flux du programme selon si la valeur de retour est null, ainsi que d’autres caractéristiques de la valeur retournée.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="1ccc8-239">Vous pouvez utiliser le modèle null pour empêcher la propagation pour le reste de votre programme de valeurs null.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="1ccc8-240">L’exemple suivant utilise le modèle null et le modèle de variable.</span><span class="sxs-lookup"><span data-stu-id="1ccc8-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="1ccc8-241">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ccc8-241">See also</span></span>

- [<span data-ttu-id="1ccc8-242">Expressions match</span><span class="sxs-lookup"><span data-stu-id="1ccc8-242">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="1ccc8-243">Modèles actifs</span><span class="sxs-lookup"><span data-stu-id="1ccc8-243">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="1ccc8-244">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="1ccc8-244">F# Language Reference</span></span>](index.md)
