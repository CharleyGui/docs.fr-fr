---
title: Méthodes
description: Découvrez comment une méthode F est une fonction associée à un type qui sont utilisés pour exposer et mettre en œuvre la fonctionnalité et le comportement des objets et des types.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400210"
---
# <a name="methods"></a><span data-ttu-id="5839b-103">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5839b-103">Methods</span></span>

<span data-ttu-id="5839b-104">Une *méthode* est une fonction qui est associée à un type.</span><span class="sxs-lookup"><span data-stu-id="5839b-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="5839b-105">Dans la programmation orientée objet, des méthodes sont utilisées pour exposer et implémenter la fonctionnalité et le comportement des objets et des types.</span><span class="sxs-lookup"><span data-stu-id="5839b-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="5839b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5839b-106">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="5839b-107">Notes </span><span class="sxs-lookup"><span data-stu-id="5839b-107">Remarks</span></span>

<span data-ttu-id="5839b-108">Dans la syntaxe précédente, vous pouvez voir les différentes formes de déclarations et de définitions de méthode.</span><span class="sxs-lookup"><span data-stu-id="5839b-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="5839b-109">Dans les corps de méthode plus longs, une rupture de ligne suit le signe égal (MD), et tout le corps de méthode est en retrait.</span><span class="sxs-lookup"><span data-stu-id="5839b-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="5839b-110">Les attributs peuvent être appliqués à n’importe quelle déclaration de méthode.</span><span class="sxs-lookup"><span data-stu-id="5839b-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="5839b-111">Ils précèdent la syntaxe pour une définition de méthode et sont généralement répertoriés sur une ligne séparée.</span><span class="sxs-lookup"><span data-stu-id="5839b-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="5839b-112">Pour plus d’informations, consultez [Attributs](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5839b-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="5839b-113">Les méthodes `inline`peuvent être marquées .</span><span class="sxs-lookup"><span data-stu-id="5839b-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="5839b-114">Pour plus d’informations sur `inline`, consultez [Fonctions inline](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="5839b-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="5839b-115">Les méthodes non-inline peuvent être utilisées de façon récursive dans le type; il n’est pas `rec` nécessaire d’utiliser explicitement le mot clé.</span><span class="sxs-lookup"><span data-stu-id="5839b-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="5839b-116">Méthodes d’instance</span><span class="sxs-lookup"><span data-stu-id="5839b-116">Instance Methods</span></span>

<span data-ttu-id="5839b-117">Les méthodes d’instance sont déclarées avec le `member` mot clé et un *auto-identifiant,* suivie d’une période (.) et le nom et les paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5839b-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="5839b-118">Comme c’est `let` le cas pour les fixations, la *liste des paramètres* peut être un modèle.</span><span class="sxs-lookup"><span data-stu-id="5839b-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="5839b-119">Typiquement, vous enfermez les paramètres de méthode entre parenthèses sous une forme de tuple, qui est la façon dont les méthodes apparaissent dans F quand ils sont créés dans d’autres langues cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="5839b-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="5839b-120">Cependant, la forme au curry (paramètres séparés par des espaces) est également commune, et d’autres modèles sont soutenus aussi.</span><span class="sxs-lookup"><span data-stu-id="5839b-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="5839b-121">L’exemple suivant illustre la définition et l’utilisation d’une méthode d’instance non abstraite.</span><span class="sxs-lookup"><span data-stu-id="5839b-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="5839b-122">Dans les méthodes d’instance, n’utilisez pas l’auto-identifiant pour accéder aux champs définis en utilisant des reliures de laisser.</span><span class="sxs-lookup"><span data-stu-id="5839b-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="5839b-123">Utilisez l’auto-identifiant lorsque vous accédez à d’autres membres et propriétés.</span><span class="sxs-lookup"><span data-stu-id="5839b-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="5839b-124">Méthodes statiques</span><span class="sxs-lookup"><span data-stu-id="5839b-124">Static Methods</span></span>

<span data-ttu-id="5839b-125">Le `static` mot clé est utilisé pour spécifier qu’une méthode peut être appelée sans instance et n’est pas associée à une instance d’objet.</span><span class="sxs-lookup"><span data-stu-id="5839b-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="5839b-126">Sinon, les méthodes sont des méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="5839b-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="5839b-127">L’exemple de la section suivante `let` montre les champs `member` déclarés avec le mot-clé, les membres de la propriété déclarés avec le mot clé, et une méthode statique déclarée avec le `static` mot clé.</span><span class="sxs-lookup"><span data-stu-id="5839b-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="5839b-128">L’exemple suivant illustre la définition et l’utilisation de méthodes statiques.</span><span class="sxs-lookup"><span data-stu-id="5839b-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="5839b-129">Supposons que ces définitions `SomeType` de méthode sont dans la classe dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="5839b-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="5839b-130">Méthodes abstraites et virtuelles</span><span class="sxs-lookup"><span data-stu-id="5839b-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="5839b-131">Le `abstract` mot clé indique qu’une méthode a une fente de répartition virtuelle et pourrait ne pas avoir de définition dans la classe.</span><span class="sxs-lookup"><span data-stu-id="5839b-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="5839b-132">Une *fente de répartition virtuelle* est une entrée dans une table interne de fonctions qui est utilisée au moment de l’exécution pour rechercher des appels de fonction virtuelle dans un type orienté objet.</span><span class="sxs-lookup"><span data-stu-id="5839b-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="5839b-133">Le mécanisme de répartition virtuelle est le mécanisme qui met en œuvre le *polymorphisme*, une caractéristique importante de la programmation orientée objet.</span><span class="sxs-lookup"><span data-stu-id="5839b-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="5839b-134">Une classe qui a au moins une méthode abstraite sans définition est une *classe abstraite,* ce qui signifie qu’aucun cas ne peut être créé de cette classe.</span><span class="sxs-lookup"><span data-stu-id="5839b-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="5839b-135">Pour plus d’informations sur les classes abstraites, voir [Classes abstraites](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5839b-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="5839b-136">Les déclarations de méthode abstraites n’incluent pas un corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="5839b-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="5839b-137">Au lieu de cela, le nom de la méthode est suivi d’un côlon (:) et une signature type pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="5839b-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="5839b-138">La signature type d’une méthode est la même que celle montrée par IntelliSense lorsque vous mettez en pause le pointeur de la souris sur un nom de méthode dans l’éditeur de code visual studio, sauf sans noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5839b-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="5839b-139">Les signatures de type sont également affichées par l’interprète, fsi.exe, lorsque vous travaillez de façon interactive.</span><span class="sxs-lookup"><span data-stu-id="5839b-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="5839b-140">La signature type d’une méthode est formée en énumérant les types des paramètres, suivi par le type de retour, avec des symboles de séparateur appropriés.</span><span class="sxs-lookup"><span data-stu-id="5839b-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="5839b-141">Les paramètres au curry `->` sont séparés par et `*`les paramètres de tuple sont séparés par .</span><span class="sxs-lookup"><span data-stu-id="5839b-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="5839b-142">La valeur de retour est toujours `->` séparée des arguments par un symbole.</span><span class="sxs-lookup"><span data-stu-id="5839b-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="5839b-143">Les parenthèses peuvent être utilisées pour regrouper des paramètres complexes, par exemple lorsqu’un type de fonction est un paramètre, ou pour indiquer quand un tuple est traité comme un seul paramètre plutôt que comme deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="5839b-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="5839b-144">Vous pouvez également donner des définitions par défaut de `default` méthodes abstraites en ajoutant la définition à la classe et en utilisant le mot clé, comme indiqué dans le bloc de syntaxe dans ce sujet.</span><span class="sxs-lookup"><span data-stu-id="5839b-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="5839b-145">Une méthode abstraite qui a une définition dans la même classe équivaut à une méthode virtuelle dans d’autres langues cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="5839b-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="5839b-146">Qu’une définition existe ou `abstract` non, le mot clé crée une nouvelle fente de répartition dans le tableau de fonction virtuel pour la classe.</span><span class="sxs-lookup"><span data-stu-id="5839b-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="5839b-147">Qu’une classe de base implémente ses méthodes abstraites, les classes dérivées peuvent fournir des implémentations de méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="5839b-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="5839b-148">Pour implémenter une méthode abstraite dans une classe dérivée, définir une `override` méthode `default` qui a le même nom et la signature dans la classe dérivée, sauf utiliser le ou le mot clé, et fournir le corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="5839b-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="5839b-149">Les mots-clés `override` et `default` signifient exactement la même chose.</span><span class="sxs-lookup"><span data-stu-id="5839b-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="5839b-150">Utiliser `override` si la nouvelle méthode l’emporte sur une mise en œuvre de la classe de base; lorsque `default` vous créez une implémentation dans la même classe que la déclaration abstraite originale.</span><span class="sxs-lookup"><span data-stu-id="5839b-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="5839b-151">N’utilisez `abstract` pas le mot clé sur la méthode qui implémente la méthode qui a été déclarée abstraite dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="5839b-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="5839b-152">L’exemple suivant illustre `Rotate` une méthode abstraite qui a une implémentation par défaut, l’équivalent d’une méthode virtuelle .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5839b-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="5839b-153">L’exemple suivant illustre une classe dérivée qui l’emporte sur une méthode de classe de base.</span><span class="sxs-lookup"><span data-stu-id="5839b-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="5839b-154">Dans ce cas, le remplacement modifie le comportement de sorte que la méthode ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="5839b-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="5839b-155">Méthodes surchargées</span><span class="sxs-lookup"><span data-stu-id="5839b-155">Overloaded Methods</span></span>

<span data-ttu-id="5839b-156">Les méthodes surchargées sont des méthodes qui ont des noms identiques dans un type donné, mais qui ont des arguments différents.</span><span class="sxs-lookup"><span data-stu-id="5839b-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="5839b-157">Dans le F, les arguments facultatifs sont généralement utilisés au lieu de méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="5839b-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="5839b-158">Cependant, les méthodes surchargées sont autorisées dans la langue, à condition que les arguments soient sous forme de tuple, et non sous forme de cari.</span><span class="sxs-lookup"><span data-stu-id="5839b-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="5839b-159">Arguments facultatifs</span><span class="sxs-lookup"><span data-stu-id="5839b-159">Optional Arguments</span></span>

<span data-ttu-id="5839b-160">En commençant par F 4.1, vous pouvez également avoir des arguments facultatifs avec une valeur de paramètre par défaut dans les méthodes.</span><span class="sxs-lookup"><span data-stu-id="5839b-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="5839b-161">Il s’agit d’aider à faciliter l’interopération avec le code C.</span><span class="sxs-lookup"><span data-stu-id="5839b-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="5839b-162">L’exemple suivant montre la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="5839b-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="5839b-163">Notez que la `DefaultParameterValue` valeur transmise pour doit correspondre au type d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5839b-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="5839b-164">Dans l’échantillon ci-dessus, il s’agit d’un `int`.</span><span class="sxs-lookup"><span data-stu-id="5839b-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="5839b-165">Tenter de faire passer une valeur `DefaultParameterValue` non-integer dans entraînerait une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="5839b-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="5839b-166">Exemple : Propriétés et méthodes</span><span class="sxs-lookup"><span data-stu-id="5839b-166">Example: Properties and Methods</span></span>

<span data-ttu-id="5839b-167">L’exemple suivant contient un type qui a des exemples de champs, fonctions privées, propriétés, et une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="5839b-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="5839b-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5839b-168">See also</span></span>

- [<span data-ttu-id="5839b-169">Membres</span><span class="sxs-lookup"><span data-stu-id="5839b-169">Members</span></span>](index.md)
