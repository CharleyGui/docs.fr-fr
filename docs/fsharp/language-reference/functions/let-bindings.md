---
title: Liaisons let
description: "Apprenez à utiliser une liaison F # 'Let', qui associe un identificateur à une valeur ou à une fonction."
ms.date: 05/16/2016
ms.openlocfilehash: 6f2396f480c5e6c631d0022f4732419ee5b07db6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812222"
---
# <a name="let-bindings"></a><span data-ttu-id="40ef0-103">Liaisons let</span><span class="sxs-lookup"><span data-stu-id="40ef0-103">let Bindings</span></span>

<span data-ttu-id="40ef0-104">Une *liaison* associe un identificateur à une valeur ou à une fonction.</span><span class="sxs-lookup"><span data-stu-id="40ef0-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="40ef0-105">Vous utilisez le `let` mot clé pour lier un nom à une valeur ou à une fonction.</span><span class="sxs-lookup"><span data-stu-id="40ef0-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="40ef0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40ef0-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="40ef0-107">Notes</span><span class="sxs-lookup"><span data-stu-id="40ef0-107">Remarks</span></span>

<span data-ttu-id="40ef0-108">Le `let` mot clé est utilisé dans les expressions de liaison pour définir des valeurs ou des valeurs de fonction pour un ou plusieurs noms.</span><span class="sxs-lookup"><span data-stu-id="40ef0-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="40ef0-109">La forme la plus simple de l' `let` expression lie un nom à une valeur simple, comme suit.</span><span class="sxs-lookup"><span data-stu-id="40ef0-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="40ef0-110">Si vous séparez l’expression de l’identificateur à l’aide d’une nouvelle ligne, vous devez mettre en retrait chaque ligne de l’expression, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="40ef0-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="40ef0-111">Au lieu d’un simple nom, un modèle qui contient des noms peut être spécifié, par exemple, un tuple, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="40ef0-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="40ef0-112">*Body-expression* est l’expression dans laquelle les noms sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="40ef0-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="40ef0-113">L’expression de corps apparaît sur sa propre ligne, mise en retrait pour s’aligner exactement avec le premier caractère du `let` mot clé :</span><span class="sxs-lookup"><span data-stu-id="40ef0-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="40ef0-114">Une `let` liaison peut apparaître au niveau du module, dans la définition d’un type de classe ou dans des portées locales, comme dans une définition de fonction.</span><span class="sxs-lookup"><span data-stu-id="40ef0-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="40ef0-115">Une `let` liaison au niveau supérieur d’un module ou dans un type de classe n’a pas besoin d’une expression de corps, mais à d’autres niveaux de portée, l’expression de corps est requise.</span><span class="sxs-lookup"><span data-stu-id="40ef0-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="40ef0-116">Les noms liés sont utilisables après le point de définition, mais pas à un moment donné avant que la `let` liaison n’apparaisse, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="40ef0-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="40ef0-117">Liaisons de fonction</span><span class="sxs-lookup"><span data-stu-id="40ef0-117">Function Bindings</span></span>

<span data-ttu-id="40ef0-118">Les liaisons de fonction suivent les règles pour les liaisons de valeur, à ceci près que les liaisons de fonction incluent le nom de la fonction et les paramètres, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="40ef0-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="40ef0-119">En général, les paramètres sont des modèles, tels qu’un modèle de tuple :</span><span class="sxs-lookup"><span data-stu-id="40ef0-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="40ef0-120">Une `let` expression de liaison prend la valeur de la dernière expression.</span><span class="sxs-lookup"><span data-stu-id="40ef0-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="40ef0-121">Par conséquent, dans l’exemple de code suivant, la valeur de `result` est calculée à partir de `100 * function3 (1, 2)` , qui prend la valeur `300` .</span><span class="sxs-lookup"><span data-stu-id="40ef0-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="40ef0-122">Pour plus d’informations, consultez [Fonctions](index.md).</span><span class="sxs-lookup"><span data-stu-id="40ef0-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="40ef0-123">Annotations de type</span><span class="sxs-lookup"><span data-stu-id="40ef0-123">Type Annotations</span></span>

<span data-ttu-id="40ef0-124">Vous pouvez spécifier des types pour les paramètres en incluant un signe deux-points ( :) suivi d’un nom de type, tous mis entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="40ef0-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="40ef0-125">Vous pouvez également spécifier le type de la valeur de retour en ajoutant le signe deux-points et le type après le dernier paramètre.</span><span class="sxs-lookup"><span data-stu-id="40ef0-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="40ef0-126">Les annotations de type complètes pour `function1` , avec des entiers comme types de paramètres, se présenteront comme suit.</span><span class="sxs-lookup"><span data-stu-id="40ef0-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="40ef0-127">Lorsqu’il n’existe aucun paramètre de type explicite, l’inférence de type est utilisée pour déterminer les types de paramètres des fonctions.</span><span class="sxs-lookup"><span data-stu-id="40ef0-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="40ef0-128">Cela peut inclure la généralisation automatique du type d’un paramètre à générique.</span><span class="sxs-lookup"><span data-stu-id="40ef0-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="40ef0-129">Pour plus d’informations, consultez [généralisation automatique](../generics/automatic-generalization.md) et [inférence de type](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="40ef0-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="40ef0-130">Liaisons let dans des classes</span><span class="sxs-lookup"><span data-stu-id="40ef0-130">let Bindings in Classes</span></span>

<span data-ttu-id="40ef0-131">Une `let` liaison peut apparaître dans un type de classe, mais pas dans une structure ou un type d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="40ef0-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="40ef0-132">Pour utiliser une liaison Let dans un type de classe, la classe doit avoir un constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="40ef0-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="40ef0-133">Les paramètres de constructeur doivent apparaître après le nom de type dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="40ef0-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="40ef0-134">Une `let` liaison dans un type de classe définit des champs et des membres privés pour ce type de classe et, ainsi que des `do` liaisons dans le type, forme le code pour le constructeur principal du type.</span><span class="sxs-lookup"><span data-stu-id="40ef0-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="40ef0-135">Les exemples de code suivants illustrent une classe `MyClass` avec des champs privés `field1` et `field2` .</span><span class="sxs-lookup"><span data-stu-id="40ef0-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="40ef0-136">Les portées de `field1` et `field2` sont limitées au type dans lequel elles sont déclarées.</span><span class="sxs-lookup"><span data-stu-id="40ef0-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="40ef0-137">Pour plus d’informations, consultez [ `let` liaisons dans les classes](../members/let-bindings-in-classes.md) et les [classes](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="40ef0-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="40ef0-138">Paramètres de type dans les liaisons Let</span><span class="sxs-lookup"><span data-stu-id="40ef0-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="40ef0-139">Une `let` liaison au niveau du module, dans un type ou dans une expression de calcul peut avoir des paramètres de type explicite.</span><span class="sxs-lookup"><span data-stu-id="40ef0-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="40ef0-140">Une liaison Let dans une expression, telle que dans une définition de fonction, ne peut pas avoir de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="40ef0-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="40ef0-141">Pour plus d’informations, consultez [Génériques](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="40ef0-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="40ef0-142">Attributs sur les liaisons Let</span><span class="sxs-lookup"><span data-stu-id="40ef0-142">Attributes on let Bindings</span></span>

<span data-ttu-id="40ef0-143">Les attributs peuvent être appliqués aux `let` liaisons de niveau supérieur dans un module, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="40ef0-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="40ef0-144">Portée et accessibilité des liaisons Let</span><span class="sxs-lookup"><span data-stu-id="40ef0-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="40ef0-145">La portée d’une entité déclarée avec une liaison Let est limitée à la partie de l’étendue contenante (telle qu’une fonction, un module, un fichier ou une classe) une fois la liaison affichée.</span><span class="sxs-lookup"><span data-stu-id="40ef0-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="40ef0-146">Par conséquent, il peut être dit qu’une liaison Let introduit un nom dans une portée.</span><span class="sxs-lookup"><span data-stu-id="40ef0-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="40ef0-147">Dans un module, une valeur ou une fonction avec liaison Let est accessible aux clients d’un module tant que le module est accessible, puisque les liaisons Let dans un module sont compilées dans les fonctions publiques du module.</span><span class="sxs-lookup"><span data-stu-id="40ef0-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="40ef0-148">En revanche, les liaisons Let dans une classe sont privées pour la classe.</span><span class="sxs-lookup"><span data-stu-id="40ef0-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="40ef0-149">Normalement, les fonctions dans les modules doivent être qualifiées par le nom du module lorsqu’elles sont utilisées par le code client.</span><span class="sxs-lookup"><span data-stu-id="40ef0-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="40ef0-150">Par exemple, si un module `Module1` possède une fonction `function1` , les utilisateurs doivent spécifier `Module1.function1` pour faire référence à la fonction.</span><span class="sxs-lookup"><span data-stu-id="40ef0-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="40ef0-151">Les utilisateurs d’un module peuvent utiliser une déclaration d’importation pour rendre les fonctions contenues dans ce module disponibles pour une utilisation sans être qualifiées par le nom du module.</span><span class="sxs-lookup"><span data-stu-id="40ef0-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="40ef0-152">Dans l’exemple qui vient d’être mentionné, les utilisateurs du module peuvent, dans ce cas, ouvrir le module à l’aide de la déclaration d’importation ouverte `Module1` , puis faire référence `function1` directement à.</span><span class="sxs-lookup"><span data-stu-id="40ef0-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

<span data-ttu-id="40ef0-153">Certains modules ont l’attribut [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), ce qui signifie que les fonctions qu’ils exposent doivent être qualifiées avec le nom du module.</span><span class="sxs-lookup"><span data-stu-id="40ef0-153">Some modules have the attribute [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="40ef0-154">Par exemple, le module de liste F # a cet attribut.</span><span class="sxs-lookup"><span data-stu-id="40ef0-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="40ef0-155">Pour plus d’informations sur les modules et le contrôle d’accès, consultez [modules](../modules.md) et [Access Control](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="40ef0-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40ef0-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40ef0-156">See also</span></span>

- [<span data-ttu-id="40ef0-157">Fonctions</span><span class="sxs-lookup"><span data-stu-id="40ef0-157">Functions</span></span>](index.md)
- [<span data-ttu-id="40ef0-158">`let` Liaisons dans des classes</span><span class="sxs-lookup"><span data-stu-id="40ef0-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
