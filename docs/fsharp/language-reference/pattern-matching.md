---
title: Critères spéciaux
description: 'Découvrez comment les modèles sont utilisés en F # pour comparer des données avec des structures logiques, décomposer des données en parties constituantes ou extraire des informations à partir de données.'
ms.date: 11/12/2020
ms.openlocfilehash: e167712b082b7f587e41a78edcaf0a0db9c7294b
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687803"
---
# <a name="pattern-matching"></a><span data-ttu-id="8cc75-103">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="8cc75-103">Pattern Matching</span></span>

<span data-ttu-id="8cc75-104">Les modèles sont des règles de transformation des données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8cc75-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="8cc75-105">Ils sont utilisés dans le langage F # pour comparer des données avec une structure logique ou des structures, décomposer des données en parties constitutives ou extraire des informations de données de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="8cc75-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cc75-106">Notes</span><span class="sxs-lookup"><span data-stu-id="8cc75-106">Remarks</span></span>

<span data-ttu-id="8cc75-107">Les modèles sont utilisés dans de nombreuses constructions de langage, telles que l' `match` expression.</span><span class="sxs-lookup"><span data-stu-id="8cc75-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="8cc75-108">Elles sont utilisées lorsque vous traitez des arguments pour les fonctions dans `let` les liaisons, les expressions lambda et dans les gestionnaires d’exceptions associés à l' `try...with` expression.</span><span class="sxs-lookup"><span data-stu-id="8cc75-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="8cc75-109">Pour plus d’informations, [consultez expressions de correspondance](match-expressions.md), [liaisons Let](./functions/let-bindings.md), [expressions lambda : le `fun` mot clé](./functions/lambda-expressions-the-fun-keyword.md)et [exceptions : l' `try...with` expression](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="8cc75-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="8cc75-110">Par exemple, dans l' `match` expression, le *modèle* correspond à ce qui suit le symbole de barre verticale.</span><span class="sxs-lookup"><span data-stu-id="8cc75-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="8cc75-111">Chaque modèle agit comme une règle de transformation d’entrée d’une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="8cc75-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="8cc75-112">Dans l' `match` expression, chaque modèle est examiné à son tour pour déterminer si les données d’entrée sont compatibles avec le modèle.</span><span class="sxs-lookup"><span data-stu-id="8cc75-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="8cc75-113">Si une correspondance est trouvée, l’expression de résultat est exécutée.</span><span class="sxs-lookup"><span data-stu-id="8cc75-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="8cc75-114">Si aucune correspondance n’est trouvée, la règle de modèle suivante est testée.</span><span class="sxs-lookup"><span data-stu-id="8cc75-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="8cc75-115">Le composant facultatif when *condition* est expliqué dans [expressions de correspondance](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8cc75-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="8cc75-116">Les modèles pris en charge sont présentés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="8cc75-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="8cc75-117">Au moment de l’exécution, l’entrée est testée par rapport à chacun des modèles suivants dans l’ordre indiqué dans le tableau, et les modèles sont appliqués de manière récursive, de la première à la dernière telle qu’ils apparaissent dans votre code, et de gauche à droite pour les modèles sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="8cc75-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="8cc75-118">Nom</span><span class="sxs-lookup"><span data-stu-id="8cc75-118">Name</span></span>|<span data-ttu-id="8cc75-119">Description</span><span class="sxs-lookup"><span data-stu-id="8cc75-119">Description</span></span>|<span data-ttu-id="8cc75-120"> Exemple</span><span class="sxs-lookup"><span data-stu-id="8cc75-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="8cc75-121">Modèle de constante</span><span class="sxs-lookup"><span data-stu-id="8cc75-121">Constant pattern</span></span>|<span data-ttu-id="8cc75-122">Tout littéral numérique, de caractère ou de chaîne, une constante d’énumération ou un identificateur littéral défini</span><span class="sxs-lookup"><span data-stu-id="8cc75-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="8cc75-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="8cc75-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="8cc75-124">Modèle d’identificateur</span><span class="sxs-lookup"><span data-stu-id="8cc75-124">Identifier pattern</span></span>|<span data-ttu-id="8cc75-125">Une valeur case d’une union discriminée, une étiquette d’exception ou un cas de modèle actif</span><span class="sxs-lookup"><span data-stu-id="8cc75-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="8cc75-126">Modèle de variable</span><span class="sxs-lookup"><span data-stu-id="8cc75-126">Variable pattern</span></span>|<span data-ttu-id="8cc75-127">*identifier*</span><span class="sxs-lookup"><span data-stu-id="8cc75-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="8cc75-128">`as` répétition</span><span class="sxs-lookup"><span data-stu-id="8cc75-128">`as` pattern</span></span>|<span data-ttu-id="8cc75-129">*modèle* en tant qu' *identificateur*</span><span class="sxs-lookup"><span data-stu-id="8cc75-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="8cc75-130">OU modèle</span><span class="sxs-lookup"><span data-stu-id="8cc75-130">OR pattern</span></span>|<span data-ttu-id="8cc75-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="8cc75-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="8cc75-132">ET modèle</span><span class="sxs-lookup"><span data-stu-id="8cc75-132">AND pattern</span></span>|<span data-ttu-id="8cc75-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="8cc75-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="8cc75-134">Modèle cons</span><span class="sxs-lookup"><span data-stu-id="8cc75-134">Cons pattern</span></span>|<span data-ttu-id="8cc75-135">*identificateur* :: *List-identifier*</span><span class="sxs-lookup"><span data-stu-id="8cc75-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="8cc75-136">Modèle de liste</span><span class="sxs-lookup"><span data-stu-id="8cc75-136">List pattern</span></span>|<span data-ttu-id="8cc75-137">[ *pattern_1*;...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="8cc75-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="8cc75-138">Modèle de tableau</span><span class="sxs-lookup"><span data-stu-id="8cc75-138">Array pattern</span></span>|<span data-ttu-id="8cc75-139">[&#124; *pattern_1*;..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="8cc75-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="8cc75-140">Modèle entre parenthèses</span><span class="sxs-lookup"><span data-stu-id="8cc75-140">Parenthesized pattern</span></span>|<span data-ttu-id="8cc75-141">( *modèle* )</span><span class="sxs-lookup"><span data-stu-id="8cc75-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="8cc75-142">Modèle de Tuple</span><span class="sxs-lookup"><span data-stu-id="8cc75-142">Tuple pattern</span></span>|<span data-ttu-id="8cc75-143">( *pattern_1*,..., *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="8cc75-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="8cc75-144">Modèle d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="8cc75-144">Record pattern</span></span>|<span data-ttu-id="8cc75-145">{ *identificateur1*  =  *pattern_1*; ... ; *identifier_n*  =  *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="8cc75-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="8cc75-146">Modèle de caractère générique</span><span class="sxs-lookup"><span data-stu-id="8cc75-146">Wildcard pattern</span></span>|<span data-ttu-id="8cc75-147">_</span><span class="sxs-lookup"><span data-stu-id="8cc75-147">_</span></span>|`_`|
|<span data-ttu-id="8cc75-148">Modèle avec annotation de type</span><span class="sxs-lookup"><span data-stu-id="8cc75-148">Pattern together with type annotation</span></span>|<span data-ttu-id="8cc75-149">*modèle* : *type*</span><span class="sxs-lookup"><span data-stu-id="8cc75-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="8cc75-150">Modèle de test de type</span><span class="sxs-lookup"><span data-stu-id="8cc75-150">Type test pattern</span></span>|<span data-ttu-id="8cc75-151">:?</span><span class="sxs-lookup"><span data-stu-id="8cc75-151">:?</span></span> <span data-ttu-id="8cc75-152">*type* [ *identificateur* ]</span><span class="sxs-lookup"><span data-stu-id="8cc75-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="8cc75-153">Modèle null</span><span class="sxs-lookup"><span data-stu-id="8cc75-153">Null pattern</span></span>|<span data-ttu-id="8cc75-154">null</span><span class="sxs-lookup"><span data-stu-id="8cc75-154">null</span></span>|`null`|
|<span data-ttu-id="8cc75-155">Modèle Nameof</span><span class="sxs-lookup"><span data-stu-id="8cc75-155">Nameof pattern</span></span>|<span data-ttu-id="8cc75-156">*nameof expr*</span><span class="sxs-lookup"><span data-stu-id="8cc75-156">*nameof expr*</span></span>|`nameof str`|

## <a name="constant-patterns"></a><span data-ttu-id="8cc75-157">Modèles de constante</span><span class="sxs-lookup"><span data-stu-id="8cc75-157">Constant Patterns</span></span>

<span data-ttu-id="8cc75-158">Les modèles de constantes sont des littéraux numériques, de caractère et de chaîne, des constantes d’énumération (avec le nom du type d’énumération inclus).</span><span class="sxs-lookup"><span data-stu-id="8cc75-158">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="8cc75-159">Une `match` expression qui possède uniquement des modèles de constantes peut être comparée à une instruction case dans d’autres langages.</span><span class="sxs-lookup"><span data-stu-id="8cc75-159">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="8cc75-160">L’entrée est comparée à la valeur littérale et le modèle correspond si les valeurs sont égales.</span><span class="sxs-lookup"><span data-stu-id="8cc75-160">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="8cc75-161">Le type du littéral doit être compatible avec le type de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="8cc75-161">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="8cc75-162">L’exemple suivant illustre l’utilisation de modèles littéraux et utilise également un modèle de variable et un modèle ou.</span><span class="sxs-lookup"><span data-stu-id="8cc75-162">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="8cc75-163">Un autre exemple de modèle littéral est un modèle basé sur des constantes d’énumération.</span><span class="sxs-lookup"><span data-stu-id="8cc75-163">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="8cc75-164">Vous devez spécifier le nom du type d’énumération lorsque vous utilisez des constantes d’énumération.</span><span class="sxs-lookup"><span data-stu-id="8cc75-164">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="8cc75-165">Modèles d’identificateur</span><span class="sxs-lookup"><span data-stu-id="8cc75-165">Identifier Patterns</span></span>

<span data-ttu-id="8cc75-166">Si le modèle est une chaîne de caractères qui forme un identificateur valide, le formulaire de l’identificateur détermine la façon dont le modèle est mis en correspondance.</span><span class="sxs-lookup"><span data-stu-id="8cc75-166">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="8cc75-167">Si l’identificateur est plus long qu’un caractère unique et commence par un caractère majuscule, le compilateur tente d’établir une correspondance avec le modèle d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="8cc75-167">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="8cc75-168">L’identificateur de ce modèle peut être une valeur marquée avec l’attribut Literal, un cas d’union discriminée, un identificateur d’exception ou un cas de modèle actif.</span><span class="sxs-lookup"><span data-stu-id="8cc75-168">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="8cc75-169">Si aucun identificateur correspondant n’est trouvé, la correspondance échoue et la règle de modèle suivante, le modèle de variable, est comparée à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="8cc75-169">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="8cc75-170">Les modèles d’union discriminée peuvent être des cas nommés simples ou ils peuvent avoir une valeur, ou un tuple contenant plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="8cc75-170">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="8cc75-171">S’il y a une valeur, vous devez spécifier un identificateur pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="8cc75-171">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="8cc75-172">Dans le cas d’un tuple, vous devez fournir un modèle de tuple avec un identificateur pour chaque élément du tuple ou un identificateur avec un nom de champ pour un ou plusieurs champs d’Union nommés.</span><span class="sxs-lookup"><span data-stu-id="8cc75-172">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="8cc75-173">Consultez les exemples de code de cette section pour obtenir des exemples.</span><span class="sxs-lookup"><span data-stu-id="8cc75-173">See the code examples in this section for examples.</span></span>

<span data-ttu-id="8cc75-174">Le `option` type est une union discriminée qui a deux cas, `Some` et `None` .</span><span class="sxs-lookup"><span data-stu-id="8cc75-174">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="8cc75-175">Un cas ( `Some` ) a une valeur, mais l’autre ( `None` ) est simplement un cas nommé.</span><span class="sxs-lookup"><span data-stu-id="8cc75-175">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="8cc75-176">Par conséquent, `Some` doit avoir une variable pour la valeur associée à la `Some` casse, mais `None` doit s’afficher par lui-même.</span><span class="sxs-lookup"><span data-stu-id="8cc75-176">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="8cc75-177">Dans le code suivant, la variable `var1` reçoit la valeur obtenue en faisant correspondre le `Some` cas.</span><span class="sxs-lookup"><span data-stu-id="8cc75-177">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="8cc75-178">Dans l’exemple suivant, l' `PersonName` union discriminée contient un mélange de chaînes et de caractères qui représentent les formes possibles des noms.</span><span class="sxs-lookup"><span data-stu-id="8cc75-178">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="8cc75-179">Les cas de l’union discriminée sont `FirstOnly` , `LastOnly` et `FirstLast` .</span><span class="sxs-lookup"><span data-stu-id="8cc75-179">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="8cc75-180">Pour les unions discriminées qui ont des champs nommés, vous utilisez le signe égal (=) pour extraire la valeur d’un champ nommé.</span><span class="sxs-lookup"><span data-stu-id="8cc75-180">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="8cc75-181">Par exemple, considérez une union discriminée avec une déclaration semblable à la suivante.</span><span class="sxs-lookup"><span data-stu-id="8cc75-181">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="8cc75-182">Vous pouvez utiliser les champs nommés dans une expression de critères spéciaux comme suit.</span><span class="sxs-lookup"><span data-stu-id="8cc75-182">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="8cc75-183">L’utilisation du champ nommé est facultative. par conséquent, dans l’exemple précédent, les deux `Circle(r)` et `Circle(radius = r)` ont le même effet.</span><span class="sxs-lookup"><span data-stu-id="8cc75-183">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="8cc75-184">Lorsque vous spécifiez plusieurs champs, utilisez le point-virgule (;) comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="8cc75-184">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="8cc75-185">Les modèles actifs vous permettent de définir des critères spéciaux personnalisés plus complexes.</span><span class="sxs-lookup"><span data-stu-id="8cc75-185">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="8cc75-186">Pour plus d’informations sur les modèles actifs, consultez [modèles actifs](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="8cc75-186">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="8cc75-187">Le cas dans lequel l’identificateur est une exception est utilisé dans les critères spéciaux dans le contexte des gestionnaires d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="8cc75-187">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="8cc75-188">Pour plus d’informations sur les critères spéciaux dans la gestion des exceptions, consultez [exceptions : l' `try...with` expression](./exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="8cc75-188">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="8cc75-189">Modèles de variables</span><span class="sxs-lookup"><span data-stu-id="8cc75-189">Variable Patterns</span></span>

<span data-ttu-id="8cc75-190">Le modèle de variable affecte la valeur mise en correspondance à un nom de variable, qui peut ensuite être utilisée dans l’expression d’exécution à droite du `->` symbole.</span><span class="sxs-lookup"><span data-stu-id="8cc75-190">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="8cc75-191">Un modèle de variable ne correspond à aucune entrée, mais les modèles de variable apparaissent souvent dans d’autres modèles, ce qui permet de décomposer les structures plus complexes, telles que les tuples et les tableaux, en variables.</span><span class="sxs-lookup"><span data-stu-id="8cc75-191">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="8cc75-192">L’exemple suivant illustre un modèle de variable dans un modèle de Tuple.</span><span class="sxs-lookup"><span data-stu-id="8cc75-192">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="8cc75-193">Modèle As</span><span class="sxs-lookup"><span data-stu-id="8cc75-193">as Pattern</span></span>

<span data-ttu-id="8cc75-194">Le `as` modèle est un modèle auquel une `as` clause est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="8cc75-194">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="8cc75-195">La `as` clause lie la valeur correspondante à un nom qui peut être utilisé dans l’expression d’exécution d’une `match` expression, ou, dans le cas où ce modèle est utilisé dans une `let` liaison, le nom est ajouté en tant que liaison à la portée locale.</span><span class="sxs-lookup"><span data-stu-id="8cc75-195">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="8cc75-196">L’exemple suivant utilise un `as` modèle.</span><span class="sxs-lookup"><span data-stu-id="8cc75-196">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="8cc75-197">OU modèle</span><span class="sxs-lookup"><span data-stu-id="8cc75-197">OR Pattern</span></span>

<span data-ttu-id="8cc75-198">Le modèle ou est utilisé lorsque les données d’entrée peuvent correspondre à plusieurs modèles et que vous souhaitez exécuter le même code en tant que résultat.</span><span class="sxs-lookup"><span data-stu-id="8cc75-198">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="8cc75-199">Les types des deux côtés du modèle ou doivent être compatibles.</span><span class="sxs-lookup"><span data-stu-id="8cc75-199">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="8cc75-200">L’exemple suivant illustre le modèle ou.</span><span class="sxs-lookup"><span data-stu-id="8cc75-200">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="8cc75-201">ET modèle</span><span class="sxs-lookup"><span data-stu-id="8cc75-201">AND Pattern</span></span>

<span data-ttu-id="8cc75-202">Le modèle et requiert que l’entrée corresponde à deux modèles.</span><span class="sxs-lookup"><span data-stu-id="8cc75-202">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="8cc75-203">Les types des deux côtés du modèle et doivent être compatibles.</span><span class="sxs-lookup"><span data-stu-id="8cc75-203">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="8cc75-204">L’exemple suivant est similaire `detectZeroTuple` à celui présenté dans la section modèle de tuple plus loin dans cette rubrique, mais ici `var1` et `var2` sont obtenus comme valeurs à l’aide du modèle et.</span><span class="sxs-lookup"><span data-stu-id="8cc75-204">The following example is like `detectZeroTuple` shown in the Tuple Pattern section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="8cc75-205">Modèle cons</span><span class="sxs-lookup"><span data-stu-id="8cc75-205">Cons Pattern</span></span>

<span data-ttu-id="8cc75-206">Le modèle cons est utilisé pour décomposer une liste en premier élément, l' *en-tête* et une liste qui contient les éléments restants, la *fin*.</span><span class="sxs-lookup"><span data-stu-id="8cc75-206">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="8cc75-207">Modèle de liste</span><span class="sxs-lookup"><span data-stu-id="8cc75-207">List Pattern</span></span>

<span data-ttu-id="8cc75-208">Le modèle de liste permet de décomposer des listes en plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="8cc75-208">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="8cc75-209">Le modèle de liste lui-même peut mettre en correspondance uniquement les listes d’un nombre spécifique d’éléments.</span><span class="sxs-lookup"><span data-stu-id="8cc75-209">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="8cc75-210">Modèle de tableau</span><span class="sxs-lookup"><span data-stu-id="8cc75-210">Array Pattern</span></span>

<span data-ttu-id="8cc75-211">Le modèle de tableau ressemble au modèle de liste et peut être utilisé pour décomposer des tableaux d’une longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="8cc75-211">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="8cc75-212">Modèle entre parenthèses</span><span class="sxs-lookup"><span data-stu-id="8cc75-212">Parenthesized Pattern</span></span>

<span data-ttu-id="8cc75-213">Les parenthèses peuvent être regroupées autour des modèles pour atteindre l’associativité souhaitée.</span><span class="sxs-lookup"><span data-stu-id="8cc75-213">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="8cc75-214">Dans l’exemple suivant, les parenthèses sont utilisées pour contrôler l’associativité entre un modèle et et un modèle cons.</span><span class="sxs-lookup"><span data-stu-id="8cc75-214">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="8cc75-215">Modèle de Tuple</span><span class="sxs-lookup"><span data-stu-id="8cc75-215">Tuple Pattern</span></span>

<span data-ttu-id="8cc75-216">Le modèle de tuple correspond à l’entrée sous forme de tuple et permet de décomposer le tuple en éléments constitutifs à l’aide de variables de critères spéciaux pour chaque position dans le tuple.</span><span class="sxs-lookup"><span data-stu-id="8cc75-216">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="8cc75-217">L’exemple suivant illustre le modèle de tuple et utilise également des modèles de littéral, des modèles de variable et le modèle de caractère générique.</span><span class="sxs-lookup"><span data-stu-id="8cc75-217">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="8cc75-218">Modèle d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="8cc75-218">Record Pattern</span></span>

<span data-ttu-id="8cc75-219">Le modèle d’enregistrement est utilisé pour décomposer les enregistrements afin d’extraire les valeurs des champs.</span><span class="sxs-lookup"><span data-stu-id="8cc75-219">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="8cc75-220">Le modèle n’a pas besoin de référencer tous les champs de l’enregistrement ; tout champ omis ne fait pas partie de la correspondance et n’est pas extrait.</span><span class="sxs-lookup"><span data-stu-id="8cc75-220">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="8cc75-221">Modèle de caractère générique</span><span class="sxs-lookup"><span data-stu-id="8cc75-221">Wildcard Pattern</span></span>

<span data-ttu-id="8cc75-222">Le modèle de caractère générique est représenté par le caractère de soulignement ( `_` ) et correspond à toute entrée, comme le modèle de variable, sauf que l’entrée est ignorée au lieu d’être affectée à une variable.</span><span class="sxs-lookup"><span data-stu-id="8cc75-222">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="8cc75-223">Le modèle de caractère générique est souvent utilisé dans d’autres modèles comme un espace réservé pour les valeurs qui ne sont pas nécessaires dans l’expression à droite du `->` symbole.</span><span class="sxs-lookup"><span data-stu-id="8cc75-223">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="8cc75-224">Le modèle de caractère générique est également fréquemment utilisé à la fin d’une liste de modèles pour faire correspondre n’importe quelle entrée sans correspondance.</span><span class="sxs-lookup"><span data-stu-id="8cc75-224">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="8cc75-225">Le modèle de caractère générique est illustré dans de nombreux exemples de code de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8cc75-225">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="8cc75-226">Pour obtenir un exemple, consultez le code précédent.</span><span class="sxs-lookup"><span data-stu-id="8cc75-226">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="8cc75-227">Modèles avec des annotations de type</span><span class="sxs-lookup"><span data-stu-id="8cc75-227">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="8cc75-228">Les modèles peuvent avoir des annotations de type.</span><span class="sxs-lookup"><span data-stu-id="8cc75-228">Patterns can have type annotations.</span></span> <span data-ttu-id="8cc75-229">Ils se comportent comme d’autres annotations de type et l’inférence de guide comme d’autres annotations de type.</span><span class="sxs-lookup"><span data-stu-id="8cc75-229">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="8cc75-230">Les parenthèses sont requises autour des annotations de type dans les modèles.</span><span class="sxs-lookup"><span data-stu-id="8cc75-230">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="8cc75-231">Le code suivant illustre un modèle qui a une annotation de type.</span><span class="sxs-lookup"><span data-stu-id="8cc75-231">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="8cc75-232">Modèle de test de type</span><span class="sxs-lookup"><span data-stu-id="8cc75-232">Type Test Pattern</span></span>

<span data-ttu-id="8cc75-233">Le modèle de test de type est utilisé pour faire correspondre l’entrée à un type.</span><span class="sxs-lookup"><span data-stu-id="8cc75-233">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="8cc75-234">Si le type d’entrée correspond à (ou à un type dérivé de) le type spécifié dans le modèle, la correspondance est établie.</span><span class="sxs-lookup"><span data-stu-id="8cc75-234">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="8cc75-235">L’exemple suivant illustre le modèle de test de type.</span><span class="sxs-lookup"><span data-stu-id="8cc75-235">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

<span data-ttu-id="8cc75-236">Si vous vérifiez uniquement si un identificateur est d’un type dérivé particulier, vous n’avez pas besoin `as identifier` de la partie du modèle, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8cc75-236">If you're only checking if an identifier is of a particular derived type, you don't need the `as identifier` part of the pattern, as shown in the following example:</span></span>

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a><span data-ttu-id="8cc75-237">Modèle null</span><span class="sxs-lookup"><span data-stu-id="8cc75-237">Null Pattern</span></span>

<span data-ttu-id="8cc75-238">Le modèle null correspond à la valeur null qui peut s’afficher lorsque vous utilisez des types qui autorisent une valeur null.</span><span class="sxs-lookup"><span data-stu-id="8cc75-238">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="8cc75-239">Les modèles NULL sont fréquemment utilisés lors de l’interopérabilité avec .NET Framework code.</span><span class="sxs-lookup"><span data-stu-id="8cc75-239">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="8cc75-240">Par exemple, la valeur de retour d’une API .NET peut être l’entrée d’une `match` expression.</span><span class="sxs-lookup"><span data-stu-id="8cc75-240">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="8cc75-241">Vous pouvez contrôler le déroulement du programme selon que la valeur de retour est null et également d’autres caractéristiques de la valeur retournée.</span><span class="sxs-lookup"><span data-stu-id="8cc75-241">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="8cc75-242">Vous pouvez utiliser le modèle null pour empêcher la propagation de valeurs Null vers le reste de votre programme.</span><span class="sxs-lookup"><span data-stu-id="8cc75-242">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="8cc75-243">L’exemple suivant utilise le modèle null et le modèle de variable.</span><span class="sxs-lookup"><span data-stu-id="8cc75-243">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="nameof-pattern"></a><span data-ttu-id="8cc75-244">Modèle Nameof</span><span class="sxs-lookup"><span data-stu-id="8cc75-244">Nameof pattern</span></span>

<span data-ttu-id="8cc75-245">Le `nameof` modèle correspond à une chaîne lorsque sa valeur est égale à l’expression qui suit le `nameof` mot clé.</span><span class="sxs-lookup"><span data-stu-id="8cc75-245">The `nameof` pattern matches against a string when its value is equal to the expression that follows the `nameof` keyword.</span></span> <span data-ttu-id="8cc75-246">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8cc75-246">for example:</span></span>

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```

<span data-ttu-id="8cc75-247">[`nameof`](nameof.md)Pour plus d’informations sur la façon dont vous pouvez prendre un nom, consultez l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="8cc75-247">See the [`nameof`](nameof.md) operator for information on what you can take a name of.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cc75-248">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cc75-248">See also</span></span>

- [<span data-ttu-id="8cc75-249">Expressions de correspondance</span><span class="sxs-lookup"><span data-stu-id="8cc75-249">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="8cc75-250">Modèles actifs</span><span class="sxs-lookup"><span data-stu-id="8cc75-250">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="8cc75-251">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="8cc75-251">F# Language Reference</span></span>](index.md)
