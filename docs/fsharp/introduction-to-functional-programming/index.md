---
title: Introduction à la programmation fonctionnelle en F#
description: 'Découvrez les principes de base de la programmation fonctionnelle en F #.'
ms.date: 10/29/2018
ms.openlocfilehash: fc2aebe80de16b92942c3557c0e03c198883dde1
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740326"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="4f63e-103">Présentation de la programmation fonctionnelle en F\#</span><span class="sxs-lookup"><span data-stu-id="4f63e-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="4f63e-104">La programmation fonctionnelle est un style de programmation qui met l’accent sur l’utilisation de fonctions et de données immuables.</span><span class="sxs-lookup"><span data-stu-id="4f63e-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="4f63e-105">La programmation fonctionnelle typée est lorsque la programmation fonctionnelle est combinée à des types statiques, tels que F #.</span><span class="sxs-lookup"><span data-stu-id="4f63e-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="4f63e-106">En général, les concepts suivants sont mis en évidence dans la programmation fonctionnelle :</span><span class="sxs-lookup"><span data-stu-id="4f63e-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="4f63e-107">Fonctionne comme les constructions principales que vous utilisez</span><span class="sxs-lookup"><span data-stu-id="4f63e-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="4f63e-108">Expressions au lieu d’instructions</span><span class="sxs-lookup"><span data-stu-id="4f63e-108">Expressions instead of statements</span></span>
* <span data-ttu-id="4f63e-109">Valeurs immuables sur les variables</span><span class="sxs-lookup"><span data-stu-id="4f63e-109">Immutable values over variables</span></span>
* <span data-ttu-id="4f63e-110">Programmation déclarative sur la programmation impérative</span><span class="sxs-lookup"><span data-stu-id="4f63e-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="4f63e-111">Tout au long de cette série, vous allez explorer les concepts et les modèles de la programmation fonctionnelle à l’aide de F #.</span><span class="sxs-lookup"><span data-stu-id="4f63e-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="4f63e-112">En cours de route, vous apprendrez également un F #.</span><span class="sxs-lookup"><span data-stu-id="4f63e-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="4f63e-113">Terminologie</span><span class="sxs-lookup"><span data-stu-id="4f63e-113">Terminology</span></span>

<span data-ttu-id="4f63e-114">La programmation fonctionnelle, comme d’autres paradigmes de programmation, est fournie avec un vocabulaire que vous devrez finalement apprendre.</span><span class="sxs-lookup"><span data-stu-id="4f63e-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="4f63e-115">Voici quelques termes courants que vous verrez tout le temps :</span><span class="sxs-lookup"><span data-stu-id="4f63e-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="4f63e-116">**Function** : une fonction est une construction qui produit une sortie quand une entrée est fournie.</span><span class="sxs-lookup"><span data-stu-id="4f63e-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="4f63e-117">Plus formellement, il _mappe_ un élément d’un jeu à un autre jeu.</span><span class="sxs-lookup"><span data-stu-id="4f63e-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="4f63e-118">Ce formalisme est intégré au béton de nombreuses façons, en particulier lors de l’utilisation de fonctions qui opèrent sur des collections de données.</span><span class="sxs-lookup"><span data-stu-id="4f63e-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="4f63e-119">Il s’agit du concept le plus simple (et le plus important) de la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="4f63e-119">It is the most basic (and important) concept in functional programming.</span></span>
* <span data-ttu-id="4f63e-120">**Expression** : une expression est une construction dans le code qui produit une valeur.</span><span class="sxs-lookup"><span data-stu-id="4f63e-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="4f63e-121">En F #, cette valeur doit être liée ou explicitement ignorée.</span><span class="sxs-lookup"><span data-stu-id="4f63e-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="4f63e-122">Une expression peut être remplacée par un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="4f63e-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="4f63e-123">**Pureté** -pureté est une propriété d’une fonction de telle sorte que sa valeur de retour est toujours la même pour les mêmes arguments, et que son évaluation n’a aucun effet secondaire.</span><span class="sxs-lookup"><span data-stu-id="4f63e-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="4f63e-124">Une fonction pure dépend entièrement de ses arguments.</span><span class="sxs-lookup"><span data-stu-id="4f63e-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="4f63e-125">**Transparence référentielle** : la transparence référentielle est une propriété d’expressions telle qu’elles peuvent être remplacées par leur sortie sans affecter le comportement d’un programme.</span><span class="sxs-lookup"><span data-stu-id="4f63e-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="4f63e-126">**Immuabilité** -immuabilité signifie qu’une valeur ne peut pas être modifiée sur place.</span><span class="sxs-lookup"><span data-stu-id="4f63e-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="4f63e-127">Cela diffère avec les variables, qui peuvent changer en place.</span><span class="sxs-lookup"><span data-stu-id="4f63e-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="4f63e-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="4f63e-128">Examples</span></span>

<span data-ttu-id="4f63e-129">Les exemples suivants illustrent ces concepts fondamentaux.</span><span class="sxs-lookup"><span data-stu-id="4f63e-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="4f63e-130">Fonctions</span><span class="sxs-lookup"><span data-stu-id="4f63e-130">Functions</span></span>

<span data-ttu-id="4f63e-131">La construction la plus courante et la plus fondamentale de la programmation fonctionnelle est la fonction.</span><span class="sxs-lookup"><span data-stu-id="4f63e-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="4f63e-132">Voici une fonction simple qui ajoute 1 à un entier :</span><span class="sxs-lookup"><span data-stu-id="4f63e-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="4f63e-133">Sa signature de type est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4f63e-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="4f63e-134">La signature peut être lue en tant que, « `addOne` accepte un `int` nommé `x` et produira un `int` ».</span><span class="sxs-lookup"><span data-stu-id="4f63e-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="4f63e-135">Plus formellement `addOne` , _mappe_ une valeur de l’ensemble d’entiers à l’ensemble d’entiers.</span><span class="sxs-lookup"><span data-stu-id="4f63e-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="4f63e-136">Le `->` jeton désigne ce mappage.</span><span class="sxs-lookup"><span data-stu-id="4f63e-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="4f63e-137">En F #, vous pouvez généralement examiner la signature de la fonction pour avoir une idée de ce qu’elle fait.</span><span class="sxs-lookup"><span data-stu-id="4f63e-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="4f63e-138">Pourquoi la signature est-elle importante ?</span><span class="sxs-lookup"><span data-stu-id="4f63e-138">So, why is the signature important?</span></span> <span data-ttu-id="4f63e-139">Dans la programmation fonctionnelle typée, l’implémentation d’une fonction est souvent moins importante que la signature de type réelle !</span><span class="sxs-lookup"><span data-stu-id="4f63e-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="4f63e-140">Le fait `addOne` d’ajouter la valeur 1 à un entier est intéressant lors de l’exécution, mais lorsque vous construisez un programme, le fait qu’il accepte et retourne un `int` est ce qui indique comment vous allez utiliser cette fonction.</span><span class="sxs-lookup"><span data-stu-id="4f63e-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="4f63e-141">En outre, une fois que vous utilisez cette fonction correctement (par rapport à sa signature de type), le diagnostic de tout problème peut être effectué uniquement dans le corps de la `addOne` fonction.</span><span class="sxs-lookup"><span data-stu-id="4f63e-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="4f63e-142">Il s’agit de l’impulsion derrière la programmation fonctionnelle typée.</span><span class="sxs-lookup"><span data-stu-id="4f63e-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="4f63e-143">Expressions</span><span class="sxs-lookup"><span data-stu-id="4f63e-143">Expressions</span></span>

<span data-ttu-id="4f63e-144">Les expressions sont des constructions qui évaluent une valeur.</span><span class="sxs-lookup"><span data-stu-id="4f63e-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="4f63e-145">Contrairement aux instructions qui exécutent une action, les expressions peuvent être considérées comme effectuant une action qui renvoie une valeur.</span><span class="sxs-lookup"><span data-stu-id="4f63e-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="4f63e-146">Les expressions sont presque toujours utilisées en faveur des instructions dans la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="4f63e-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="4f63e-147">Examinez la fonction précédente, `addOne` .</span><span class="sxs-lookup"><span data-stu-id="4f63e-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="4f63e-148">Le corps de `addOne` est une expression :</span><span class="sxs-lookup"><span data-stu-id="4f63e-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="4f63e-149">C’est le résultat de cette expression qui définit le type de résultat de la `addOne` fonction.</span><span class="sxs-lookup"><span data-stu-id="4f63e-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="4f63e-150">Par exemple, l’expression qui compose cette fonction peut être changée en un type différent, tel que `string` :</span><span class="sxs-lookup"><span data-stu-id="4f63e-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="4f63e-151">La signature de la fonction est désormais :</span><span class="sxs-lookup"><span data-stu-id="4f63e-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="4f63e-152">Étant donné que tout type en F # peut avoir `ToString()` été appelé sur celui-ci, le type de `x` a été rendu générique (appelé [généralisation automatique](../language-reference/generics/automatic-generalization.md)) et le type résultant est un `string` .</span><span class="sxs-lookup"><span data-stu-id="4f63e-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="4f63e-153">Les expressions ne sont pas uniquement les corps des fonctions.</span><span class="sxs-lookup"><span data-stu-id="4f63e-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="4f63e-154">Vous pouvez avoir des expressions qui produisent une valeur que vous utilisez ailleurs.</span><span class="sxs-lookup"><span data-stu-id="4f63e-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="4f63e-155">La première est la `if` suivante :</span><span class="sxs-lookup"><span data-stu-id="4f63e-155">A common one is `if`:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

<span data-ttu-id="4f63e-156">L' `if` expression produit une valeur appelée `result` .</span><span class="sxs-lookup"><span data-stu-id="4f63e-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="4f63e-157">Notez que vous pouvez omettre `result` complètement, en faisant de l' `if` expression le corps de la `addOneIfOdd` fonction.</span><span class="sxs-lookup"><span data-stu-id="4f63e-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="4f63e-158">La principale chose à savoir sur les expressions est qu’elles produisent une valeur.</span><span class="sxs-lookup"><span data-stu-id="4f63e-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="4f63e-159">Il existe un type spécial, `unit` , qui est utilisé lorsqu’il n’y a rien à retourner.</span><span class="sxs-lookup"><span data-stu-id="4f63e-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="4f63e-160">Par exemple, considérez cette fonction simple :</span><span class="sxs-lookup"><span data-stu-id="4f63e-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn $"String is: {str}"
```

<span data-ttu-id="4f63e-161">La signature ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="4f63e-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="4f63e-162">Le `unit` type indique qu’aucune valeur réelle n’est retournée.</span><span class="sxs-lookup"><span data-stu-id="4f63e-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="4f63e-163">Cela est utile lorsque vous avez une routine qui doit « faire fonctionner » malgré l’absence de valeur à retourner à la suite de ce travail.</span><span class="sxs-lookup"><span data-stu-id="4f63e-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="4f63e-164">Cela contraste nettement avec la programmation impérative, où la construction équivalente `if` est une instruction, et la production de valeurs est souvent effectuée avec des variables mutantes.</span><span class="sxs-lookup"><span data-stu-id="4f63e-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="4f63e-165">Par exemple, en C#, le code peut être écrit comme suit :</span><span class="sxs-lookup"><span data-stu-id="4f63e-165">For example, in C#, the code might be written like this:</span></span>

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

<span data-ttu-id="4f63e-166">Il est à noter que C# et d’autres langages de style C prennent en charge l' [expression ternaire](../../csharp/language-reference/operators/conditional-operator.md), qui permet la programmation conditionnelle basée sur une expression.</span><span class="sxs-lookup"><span data-stu-id="4f63e-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="4f63e-167">Dans la programmation fonctionnelle, il est rare de faire muter des valeurs avec des instructions.</span><span class="sxs-lookup"><span data-stu-id="4f63e-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="4f63e-168">Bien que certains langages fonctionnels prennent en charge les instructions et la mutation, il n’est pas courant d’utiliser ces concepts dans la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="4f63e-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="4f63e-169">Fonctions pures</span><span class="sxs-lookup"><span data-stu-id="4f63e-169">Pure functions</span></span>

<span data-ttu-id="4f63e-170">Comme mentionné précédemment, les fonctions pures sont des fonctions qui :</span><span class="sxs-lookup"><span data-stu-id="4f63e-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="4f63e-171">Évaluez toujours à la même valeur pour la même entrée.</span><span class="sxs-lookup"><span data-stu-id="4f63e-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="4f63e-172">N’ont pas d’effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="4f63e-172">Have no side effects.</span></span>

<span data-ttu-id="4f63e-173">Il est utile de considérer les fonctions mathématiques dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="4f63e-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="4f63e-174">En mathématiques, les fonctions dépendent uniquement de leurs arguments et n’ont pas d’effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="4f63e-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="4f63e-175">Dans la fonction mathématique `f(x) = x + 1` , la valeur de `f(x)` dépend uniquement de la valeur de `x` .</span><span class="sxs-lookup"><span data-stu-id="4f63e-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="4f63e-176">Les fonctions pures de la programmation fonctionnelle sont de la même façon.</span><span class="sxs-lookup"><span data-stu-id="4f63e-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="4f63e-177">Lors de l’écriture d’une fonction pure, la fonction doit dépendre uniquement de ses arguments et n’exécute aucune action qui produit un effet secondaire.</span><span class="sxs-lookup"><span data-stu-id="4f63e-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="4f63e-178">Voici un exemple de fonction non pure, car elle dépend de l’état global et mutable :</span><span class="sxs-lookup"><span data-stu-id="4f63e-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="4f63e-179">La `addOneToValue` fonction est clairement impure, car `value` peut être modifiée à tout moment pour avoir une valeur différente de 1.</span><span class="sxs-lookup"><span data-stu-id="4f63e-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="4f63e-180">Ce modèle de selon une valeur globale doit être évité dans la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="4f63e-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="4f63e-181">Voici un autre exemple de fonction non pure, car elle effectue un effet secondaire :</span><span class="sxs-lookup"><span data-stu-id="4f63e-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x =
    printfn $"x is %d{x}"
    x + 1
```

<span data-ttu-id="4f63e-182">Bien que cette fonction ne dépende pas d’une valeur globale, elle écrit la valeur de `x` dans la sortie du programme.</span><span class="sxs-lookup"><span data-stu-id="4f63e-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="4f63e-183">Bien qu’il n’y ait rien de mal à faire, cela signifie que la fonction n’est pas pure.</span><span class="sxs-lookup"><span data-stu-id="4f63e-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="4f63e-184">Si une autre partie de votre programme dépend d’un élément externe au programme, tel que la mémoire tampon de sortie, l’appel de cette fonction peut affecter l’autre partie de votre programme.</span><span class="sxs-lookup"><span data-stu-id="4f63e-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="4f63e-185">La suppression de l' `printfn` instruction rend la fonction pure :</span><span class="sxs-lookup"><span data-stu-id="4f63e-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="4f63e-186">Même si cette fonction n’est pas fondamentalement _meilleure_ que la version précédente avec l' `printfn` instruction, elle garantit que toutes les fonctions retournent une valeur.</span><span class="sxs-lookup"><span data-stu-id="4f63e-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="4f63e-187">L’appel de cette fonction un nombre quelconque de fois génère le même résultat : elle produit simplement une valeur.</span><span class="sxs-lookup"><span data-stu-id="4f63e-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="4f63e-188">La prévisibilité donnée par la pureté est un grand nombre de programmeurs fonctionnels.</span><span class="sxs-lookup"><span data-stu-id="4f63e-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="4f63e-189">Immuabilité</span><span class="sxs-lookup"><span data-stu-id="4f63e-189">Immutability</span></span>

<span data-ttu-id="4f63e-190">Enfin, l’un des concepts les plus fondamentaux de la programmation fonctionnelle typée est l’immuabilité.</span><span class="sxs-lookup"><span data-stu-id="4f63e-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="4f63e-191">En F #, toutes les valeurs sont immuables par défaut.</span><span class="sxs-lookup"><span data-stu-id="4f63e-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="4f63e-192">Cela signifie qu’ils ne peuvent pas être mutés sur place, à moins que vous les Marquez explicitement comme mutable.</span><span class="sxs-lookup"><span data-stu-id="4f63e-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="4f63e-193">En pratique, l’utilisation de valeurs immuables signifie que vous modifiez votre approche de programmation à partir de, « je dois modifier un nom » en « je dois produire une nouvelle valeur ».</span><span class="sxs-lookup"><span data-stu-id="4f63e-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="4f63e-194">Par exemple, l’ajout de 1 à une valeur signifie produire une nouvelle valeur, sans muter la valeur existante :</span><span class="sxs-lookup"><span data-stu-id="4f63e-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="4f63e-195">En F #, le code suivant ne fait **pas** muter la `value` fonction ; à la place, il effectue une vérification d’égalité :</span><span class="sxs-lookup"><span data-stu-id="4f63e-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="4f63e-196">Certains langages de programmation fonctionnelle ne prennent pas du tout en charge la mutation.</span><span class="sxs-lookup"><span data-stu-id="4f63e-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="4f63e-197">En F #, il est pris en charge, mais il ne s’agit pas du comportement par défaut pour les valeurs.</span><span class="sxs-lookup"><span data-stu-id="4f63e-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="4f63e-198">Ce concept s’étend encore davantage aux structures de données.</span><span class="sxs-lookup"><span data-stu-id="4f63e-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="4f63e-199">Dans la programmation fonctionnelle, les structures de données immuables, telles que les ensembles (et bien d’autres), ont une implémentation différente de celle que vous pourriez attendre initialement.</span><span class="sxs-lookup"><span data-stu-id="4f63e-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="4f63e-200">D’un point de vue conceptuel, un élément tel que l’ajout d’un élément à un ensemble ne change pas le jeu, il produit un _nouvel_ ensemble avec la valeur ajoutée.</span><span class="sxs-lookup"><span data-stu-id="4f63e-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="4f63e-201">En coulisses, il s’agit souvent d’une structure de données différente qui permet de suivre efficacement une valeur afin que la représentation appropriée des données puisse être donnée en conséquence.</span><span class="sxs-lookup"><span data-stu-id="4f63e-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="4f63e-202">Ce style de travail avec les valeurs et les structures de données est essentiel, car il vous oblige à traiter toute opération qui modifie quelque chose comme si elle crée une nouvelle version de cette chose.</span><span class="sxs-lookup"><span data-stu-id="4f63e-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="4f63e-203">Cela permet d’assurer la cohérence de l’égalité et de la comparabilité dans vos programmes.</span><span class="sxs-lookup"><span data-stu-id="4f63e-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4f63e-204">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4f63e-204">Next steps</span></span>

<span data-ttu-id="4f63e-205">La section suivante traite en détail les fonctions, en explorant les différentes façons de les utiliser dans la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="4f63e-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="4f63e-206">Les [fonctions de première classe](first-class-functions.md) explorent les fonctions en profondeur, en vous expliquant comment vous pouvez les utiliser dans différents contextes.</span><span class="sxs-lookup"><span data-stu-id="4f63e-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="4f63e-207">Pour aller plus loin</span><span class="sxs-lookup"><span data-stu-id="4f63e-207">Further reading</span></span>

<span data-ttu-id="4f63e-208">La série de [réflexion](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) fonctionnelle est une autre formidable ressource pour en savoir plus sur la programmation fonctionnelle avec F #.</span><span class="sxs-lookup"><span data-stu-id="4f63e-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="4f63e-209">Il couvre les principes fondamentaux de la programmation fonctionnelle de manière pragmatique et facile à lire, en utilisant les fonctionnalités F # pour illustrer les concepts.</span><span class="sxs-lookup"><span data-stu-id="4f63e-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
