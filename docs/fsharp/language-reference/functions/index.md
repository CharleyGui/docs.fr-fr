---
title: Fonctions
description: 'En savoir plus sur les fonctions en F # et sur la façon dont F # prend en charge les constructions de programmation fonctionnelle courantes.'
ms.date: 05/16/2016
ms.openlocfilehash: e49183e0634dee1750757abadbfe9e9c824f51a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596472"
---
# <a name="functions"></a><span data-ttu-id="3fa10-103">Fonctions</span><span class="sxs-lookup"><span data-stu-id="3fa10-103">Functions</span></span>

<span data-ttu-id="3fa10-104">Les fonctions sont l’unité fondamentale de l’exécution d’un programme dans tout langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="3fa10-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="3fa10-105">Comme dans d’autres langages, une fonction F# a un nom, peut avoir des paramètres et accepter des arguments, et contient un corps.</span><span class="sxs-lookup"><span data-stu-id="3fa10-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="3fa10-106">F# prend également en charge des constructions de programmation fonctionnelle, telles que le traitement des fonctions comme valeurs, l’utilisation de fonctions sans nom dans les expressions, la composition de fonctions pour former de nouvelles fonctions, les fonctions curryfiées et la définition implicite de fonctions par l’intermédiaire de l’application partielle d’arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="3fa10-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="3fa10-107">Pour définir des fonctions, utilisez le mot clé `let` ou, si la fonction est récursive, la combinaison de mots clés `let rec`.</span><span class="sxs-lookup"><span data-stu-id="3fa10-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="3fa10-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fa10-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="3fa10-109">Notes</span><span class="sxs-lookup"><span data-stu-id="3fa10-109">Remarks</span></span>

<span data-ttu-id="3fa10-110">*function-name* est un identificateur qui représente la fonction.</span><span class="sxs-lookup"><span data-stu-id="3fa10-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="3fa10-111">*parameter-list* se compose de paramètres consécutifs séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="3fa10-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="3fa10-112">Vous pouvez spécifier un type explicite pour chaque paramètre, comme décrit dans la section Paramètres.</span><span class="sxs-lookup"><span data-stu-id="3fa10-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="3fa10-113">Si vous ne spécifiez pas un type d’argument spécifique, le compilateur tente de déduire le type du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3fa10-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="3fa10-114">*function-body* se compose d’une expression.</span><span class="sxs-lookup"><span data-stu-id="3fa10-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="3fa10-115">L’expression qui constitue le corps de la fonction est en général une expression composée comprenant plusieurs expressions qui débouchent sur une expression finale, c’est-à-dire la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="3fa10-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="3fa10-116">*return-type* est un signe deux-points suivi par un type ; son utilisation est facultative.</span><span class="sxs-lookup"><span data-stu-id="3fa10-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="3fa10-117">Si vous ne spécifiez pas explicitement le type de la valeur de retour, le compilateur détermine le type de retour à partir de l’expression finale.</span><span class="sxs-lookup"><span data-stu-id="3fa10-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="3fa10-118">Une définition de fonction simple se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="3fa10-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="3fa10-119">Dans l’exemple précédent, le nom de la fonction est `f`, l’argument est `x`, dont le type est `int`, le corps de la fonction est `x + 1`, et la valeur de retour est de type `int`.</span><span class="sxs-lookup"><span data-stu-id="3fa10-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="3fa10-120">Les fonctions peuvent être marquées comme étant `inline`.</span><span class="sxs-lookup"><span data-stu-id="3fa10-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="3fa10-121">Pour plus d’informations sur `inline`, consultez [Fonctions inline](inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3fa10-121">For information about `inline`, see [Inline Functions](inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="3fa10-122">Étendue</span><span class="sxs-lookup"><span data-stu-id="3fa10-122">Scope</span></span>

<span data-ttu-id="3fa10-123">À tout niveau de la portée, sauf dans la portée de module, la réutilisation d’une valeur ou d’un nom de fonction ne constitue pas une erreur.</span><span class="sxs-lookup"><span data-stu-id="3fa10-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="3fa10-124">Si vous réutilisez un nom, le nom déclaré en second lieu occulte le nom précédemment déclaré.</span><span class="sxs-lookup"><span data-stu-id="3fa10-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="3fa10-125">Toutefois, à la portée de niveau supérieur dans un module, les noms doivent être uniques.</span><span class="sxs-lookup"><span data-stu-id="3fa10-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="3fa10-126">Par exemple, le code suivant produit une erreur quand il apparaît au niveau de la portée de module, mais pas quand il apparaît à l’intérieur d’une fonction :</span><span class="sxs-lookup"><span data-stu-id="3fa10-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="3fa10-127">Mais le code suivant est acceptable à tout niveau de la portée :</span><span class="sxs-lookup"><span data-stu-id="3fa10-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="3fa10-128">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3fa10-128">Parameters</span></span>

<span data-ttu-id="3fa10-129">Les noms des paramètres sont répertoriés après le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3fa10-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="3fa10-130">Vous pouvez spécifier un type pour un paramètre, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3fa10-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="3fa10-131">Si vous spécifiez un type, celui-ci suit le nom du paramètre et est séparé du nom par un signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="3fa10-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="3fa10-132">Si vous omettez le type du paramètre, celui-ci est déduit par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="3fa10-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="3fa10-133">Par exemple, dans la définition de fonction suivante, le type déduit pour l’argument `x` est `int`, car 1 est de type `int`.</span><span class="sxs-lookup"><span data-stu-id="3fa10-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="3fa10-134">Toutefois, le compilateur tente de rendre la fonction aussi générique que possible.</span><span class="sxs-lookup"><span data-stu-id="3fa10-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="3fa10-135">Observez par exemple le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3fa10-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="3fa10-136">La fonction crée un tuple à partir d’un argument de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="3fa10-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="3fa10-137">Le type n’étant pas spécifié, la fonction peut être utilisée avec n’importe quel type d’argument.</span><span class="sxs-lookup"><span data-stu-id="3fa10-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="3fa10-138">Pour plus d’informations, consultez [Généralisation automatique](../generics/automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="3fa10-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="3fa10-139">Corps de fonction</span><span class="sxs-lookup"><span data-stu-id="3fa10-139">Function Bodies</span></span>

<span data-ttu-id="3fa10-140">Un corps de fonction peut contenir des définitions de variables et de fonctions locales.</span><span class="sxs-lookup"><span data-stu-id="3fa10-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="3fa10-141">Ces variables et fonctions sont dans la portée du corps de la fonction active, et non à l’extérieur.</span><span class="sxs-lookup"><span data-stu-id="3fa10-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="3fa10-142">Si l’option de syntaxe simplifiée est activée, vous devez utiliser la mise en retrait pour indiquer qu’une définition se trouve dans un corps de fonction, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3fa10-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="3fa10-143">Pour plus d’informations, consultez [Indications pour la mise en forme du code](../../style-guide/formatting.md) et [Syntaxe détaillée](../verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="3fa10-143">For more information, see [Code Formatting Guidelines](../../style-guide/formatting.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="3fa10-144">Valeurs de retour</span><span class="sxs-lookup"><span data-stu-id="3fa10-144">Return Values</span></span>

<span data-ttu-id="3fa10-145">Le compilateur utilise l’expression finale dans un corps de fonction pour déterminer la valeur et le type de retour.</span><span class="sxs-lookup"><span data-stu-id="3fa10-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="3fa10-146">Il peut déduire le type de l’expression finale à partir d’expressions précédentes.</span><span class="sxs-lookup"><span data-stu-id="3fa10-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="3fa10-147">Dans la fonction `cylinderVolume` présentée dans la section précédente, le type de `pi` est déterminé à partir du type du littéral `3.14159` comme étant `float`.</span><span class="sxs-lookup"><span data-stu-id="3fa10-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="3fa10-148">Le compilateur utilise le type de `pi` pour déterminer le type de l’expression `h * pi * r * r` comme étant `float`.</span><span class="sxs-lookup"><span data-stu-id="3fa10-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="3fa10-149">Par conséquent, le type de retour global de la fonction est `float`.</span><span class="sxs-lookup"><span data-stu-id="3fa10-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="3fa10-150">Pour spécifier la valeur de retour explicitement, écrivez le code comme suit :</span><span class="sxs-lookup"><span data-stu-id="3fa10-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="3fa10-151">Selon le code ci-dessus, le compilateur applique **float** à la fonction entière ; si vous souhaitez l’appliquer également aux types de paramètre, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3fa10-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="3fa10-152">Appel d’une fonction</span><span class="sxs-lookup"><span data-stu-id="3fa10-152">Calling a Function</span></span>

<span data-ttu-id="3fa10-153">Pour appeler des fonctions, spécifiez le nom de la fonction, suivi d’un espace et des arguments séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="3fa10-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="3fa10-154">Par exemple, pour appeler la fonction **cylinderVolume** et assigner le résultat à la valeur **vol**, écrivez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3fa10-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="3fa10-155">Application partielle d’arguments</span><span class="sxs-lookup"><span data-stu-id="3fa10-155">Partial Application of Arguments</span></span>

<span data-ttu-id="3fa10-156">Si vous fournissez un nombre d’arguments inférieur à celui spécifié, vous créez une fonction qui attend les arguments restants.</span><span class="sxs-lookup"><span data-stu-id="3fa10-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="3fa10-157">Cette méthode de gestion d’arguments, appelée *curryfication*, est une caractéristique des langages de programmation fonctionnelle tels que F#.</span><span class="sxs-lookup"><span data-stu-id="3fa10-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="3fa10-158">Par exemple, supposons que vous travaillez avec des tuyaux de deux tailles : l’un d’un rayon de **2.0** et l’autre de **3.0**.</span><span class="sxs-lookup"><span data-stu-id="3fa10-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="3fa10-159">Vous pouvez créer des fonctions qui déterminent le volume des tuyaux, comme suit :</span><span class="sxs-lookup"><span data-stu-id="3fa10-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="3fa10-160">Vous fournissez ensuite, selon vos besoins, l’argument supplémentaire pour les différentes longueurs de tuyau de chaque taille :</span><span class="sxs-lookup"><span data-stu-id="3fa10-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="3fa10-161">Fonctions récursives</span><span class="sxs-lookup"><span data-stu-id="3fa10-161">Recursive Functions</span></span>

<span data-ttu-id="3fa10-162">Les *fonctions récursives* sont des fonctions qui s’appellent.</span><span class="sxs-lookup"><span data-stu-id="3fa10-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="3fa10-163">Elles nécessitent la spécification du mot clé **rec** après le mot clé **let**.</span><span class="sxs-lookup"><span data-stu-id="3fa10-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="3fa10-164">Appelez la fonction récursive à partir du corps de la fonction, comme vous le feriez pour tout autre appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="3fa10-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="3fa10-165">La fonction récursive suivante calcule le *n*<sup>ième</sup> nombre de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="3fa10-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="3fa10-166">La séquence de nombres de Fibonacci est connue depuis l’antiquité ; il s’agit d’une séquence dans laquelle chaque nombre consécutif est la somme des deux nombres précédents dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="3fa10-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="3fa10-167">Certaines fonctions récursives peuvent entraîner un dépassement de capacité de la pile du programme ou s’exécuter inefficacement si vous ne soignez pas leur écriture ou si vous ne tenez pas compte de techniques spéciales, notamment l’utilisation d’accumulateurs et de continuations.</span><span class="sxs-lookup"><span data-stu-id="3fa10-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="3fa10-168">Valeurs de fonction</span><span class="sxs-lookup"><span data-stu-id="3fa10-168">Function Values</span></span>

<span data-ttu-id="3fa10-169">En F#, toutes les fonctions sont considérées comme des valeurs ; en fait, elles sont appelées *valeurs de fonction*.</span><span class="sxs-lookup"><span data-stu-id="3fa10-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="3fa10-170">Les fonctions étant des valeurs, elles peuvent être utilisées comme arguments d’autres fonctions ou dans d’autres contextes où des valeurs sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="3fa10-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="3fa10-171">L’exemple suivant illustre une fonction qui prend une valeur de fonction comme argument :</span><span class="sxs-lookup"><span data-stu-id="3fa10-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="3fa10-172">Vous spécifiez le type d’une valeur de fonction à l’aide du jeton `->`.</span><span class="sxs-lookup"><span data-stu-id="3fa10-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="3fa10-173">Le type de l’argument se trouve à gauche du jeton, et la valeur de retour à droite.</span><span class="sxs-lookup"><span data-stu-id="3fa10-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="3fa10-174">Dans l’exemple précédent, `apply1` est une fonction qui prend une fonction `transform` comme argument, où `transform` est une fonction qui prend un entier et qui retourne un autre entier.</span><span class="sxs-lookup"><span data-stu-id="3fa10-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="3fa10-175">Le code suivant montre comment utiliser `apply1` :</span><span class="sxs-lookup"><span data-stu-id="3fa10-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="3fa10-176">La valeur de `result` est 101 au terme de l’exécution du code précédent.</span><span class="sxs-lookup"><span data-stu-id="3fa10-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="3fa10-177">Plusieurs arguments sont séparés par des jetons `->` consécutifs, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3fa10-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="3fa10-178">Le résultat est 200.</span><span class="sxs-lookup"><span data-stu-id="3fa10-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="3fa10-179">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="3fa10-179">Lambda Expressions</span></span>

<span data-ttu-id="3fa10-180">Une *expression lambda* est une fonction sans nom.</span><span class="sxs-lookup"><span data-stu-id="3fa10-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="3fa10-181">Dans les exemples précédents, au lieu de définir des fonctions nommées **increment** et **mul**, vous pouvez utiliser des expressions lambda comme suit :</span><span class="sxs-lookup"><span data-stu-id="3fa10-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="3fa10-182">Pour définir des expressions lambda, utilisez le mot clé `fun`.</span><span class="sxs-lookup"><span data-stu-id="3fa10-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="3fa10-183">Une expression lambda ressemble à une définition de fonction, sauf que le jeton `->` est utilisé à la place du jeton `=` pour séparer la liste d’arguments du corps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3fa10-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="3fa10-184">Comme dans une définition de fonction normale, les types d’argument peuvent être déduits ou spécifiés explicitement, et le type de retour de l’expression lambda est déduit du type de la dernière expression dans le corps.</span><span class="sxs-lookup"><span data-stu-id="3fa10-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="3fa10-185">Pour plus d’informations, consultez [Expressions lambda : mot clé `fun`](lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="3fa10-185">For more information, see [Lambda Expressions: The `fun` Keyword](lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="3fa10-186">Composition de fonction et traitement « pipeline »</span><span class="sxs-lookup"><span data-stu-id="3fa10-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="3fa10-187">En F#, des fonctions peuvent être composées d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="3fa10-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="3fa10-188">La composition de deux fonctions **function1** et **function2** est une autre fonction qui représente l’application de **function1**, suivie de l’application de **function2** :</span><span class="sxs-lookup"><span data-stu-id="3fa10-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="3fa10-189">Le résultat est 202.</span><span class="sxs-lookup"><span data-stu-id="3fa10-189">The result is 202.</span></span>

<span data-ttu-id="3fa10-190">Le traitement « pipeline » permet de chaîner des appels de fonction en tant qu’opérations successives.</span><span class="sxs-lookup"><span data-stu-id="3fa10-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="3fa10-191">Le traitement « pipeline » fonctionne comme suit :</span><span class="sxs-lookup"><span data-stu-id="3fa10-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="3fa10-192">Le résultat est encore 202.</span><span class="sxs-lookup"><span data-stu-id="3fa10-192">The result is again 202.</span></span>

<span data-ttu-id="3fa10-193">Les opérateurs de composition prennent deux fonctions et en retournent une, tandis que les opérateurs de pipeline prennent une fonction et un argument et retournent une valeur.</span><span class="sxs-lookup"><span data-stu-id="3fa10-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="3fa10-194">L’exemple de code suivant illustre la différence entre le pipeline et les opérateurs de composition en affichant les différences dans les signatures de la fonction et leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="3fa10-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a><span data-ttu-id="3fa10-195">Surcharge des fonctions</span><span class="sxs-lookup"><span data-stu-id="3fa10-195">Overloading Functions</span></span>

<span data-ttu-id="3fa10-196">Vous pouvez surcharger les méthodes d’un type, mais pas les fonctions.</span><span class="sxs-lookup"><span data-stu-id="3fa10-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="3fa10-197">Pour plus d’informations, consultez [Méthodes](../members/methods.md).</span><span class="sxs-lookup"><span data-stu-id="3fa10-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3fa10-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fa10-198">See also</span></span>

- [<span data-ttu-id="3fa10-199">Valeurs</span><span class="sxs-lookup"><span data-stu-id="3fa10-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="3fa10-200">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="3fa10-200">F# Language Reference</span></span>](../index.md)
