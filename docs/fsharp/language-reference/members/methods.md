---
title: Méthodes
description: 'Découvrez comment une méthode F # est une fonction associée à un type qui est utilisé pour exposer et implémenter les fonctionnalités et le comportement d’objets et de types.'
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224103"
---
# <a name="methods"></a><span data-ttu-id="a8b78-103">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a8b78-103">Methods</span></span>

<span data-ttu-id="a8b78-104">Une *méthode* est une fonction associée à un type.</span><span class="sxs-lookup"><span data-stu-id="a8b78-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="a8b78-105">Dans la programmation orientée objet, les méthodes sont utilisées pour exposer et implémenter les fonctionnalités et le comportement des objets et des types.</span><span class="sxs-lookup"><span data-stu-id="a8b78-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8b78-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8b78-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="a8b78-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a8b78-107">Remarks</span></span>

<span data-ttu-id="a8b78-108">Dans la syntaxe précédente, vous pouvez voir les différentes formes de déclarations et de définitions de méthode.</span><span class="sxs-lookup"><span data-stu-id="a8b78-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="a8b78-109">Dans les corps de méthode plus longs, un saut de ligne suit le signe égal (=) et le corps de la méthode entière est mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="a8b78-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="a8b78-110">Les attributs peuvent être appliqués à toute déclaration de méthode.</span><span class="sxs-lookup"><span data-stu-id="a8b78-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="a8b78-111">Elles précèdent la syntaxe d’une définition de méthode et sont généralement listées sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="a8b78-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="a8b78-112">Pour plus d’informations, consultez [Attributs](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a8b78-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="a8b78-113">Les méthodes peuvent être marquées `inline` .</span><span class="sxs-lookup"><span data-stu-id="a8b78-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="a8b78-114">Pour plus d’informations sur `inline`, consultez [Fonctions inline](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="a8b78-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="a8b78-115">Les méthodes non inline peuvent être utilisées de manière récursive dans le type ; Il n’est pas nécessaire d’utiliser explicitement le `rec` mot clé.</span><span class="sxs-lookup"><span data-stu-id="a8b78-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="a8b78-116">Méthodes d’instance</span><span class="sxs-lookup"><span data-stu-id="a8b78-116">Instance Methods</span></span>

<span data-ttu-id="a8b78-117">Les méthodes d’instance sont déclarées avec le `member` mot clé et un *auto-identificateur*, suivis d’un point (.) et du nom et des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a8b78-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="a8b78-118">Comme c’est le cas pour les `let` liaisons, la *liste de paramètres* peut être un modèle.</span><span class="sxs-lookup"><span data-stu-id="a8b78-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="a8b78-119">En général, les paramètres de méthode sont placés entre parenthèses sous forme de tuple, ce qui correspond à la façon dont les méthodes s’affichent en F # lorsqu’elles sont créées dans d’autres langages de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8b78-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="a8b78-120">Toutefois, la forme curryfiée (les paramètres séparés par des espaces) est également courante, et les autres modèles sont également pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a8b78-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="a8b78-121">L’exemple suivant illustre la définition et l’utilisation d’une méthode d’instance non abstraite.</span><span class="sxs-lookup"><span data-stu-id="a8b78-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="a8b78-122">Dans les méthodes d’instance, n’utilisez pas l’auto-identificateur pour accéder aux champs définis à l’aide de liaisons Let.</span><span class="sxs-lookup"><span data-stu-id="a8b78-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="a8b78-123">Utilisez l’auto-identificateur lors de l’accès à d’autres membres et propriétés.</span><span class="sxs-lookup"><span data-stu-id="a8b78-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="a8b78-124">Méthodes statiques</span><span class="sxs-lookup"><span data-stu-id="a8b78-124">Static Methods</span></span>

<span data-ttu-id="a8b78-125">Le mot clé `static` est utilisé pour spécifier qu’une méthode peut être appelée sans instance et qu’elle n’est pas associée à une instance d’objet.</span><span class="sxs-lookup"><span data-stu-id="a8b78-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="a8b78-126">Sinon, les méthodes sont des méthodes d’instance.</span><span class="sxs-lookup"><span data-stu-id="a8b78-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="a8b78-127">L’exemple de la section suivante montre les champs déclarés avec le `let` mot clé, les membres de propriété déclarés avec le `member` mot clé et une méthode statique déclarée avec le `static` mot clé.</span><span class="sxs-lookup"><span data-stu-id="a8b78-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="a8b78-128">L’exemple suivant illustre la définition et l’utilisation de méthodes statiques.</span><span class="sxs-lookup"><span data-stu-id="a8b78-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="a8b78-129">Supposons que ces définitions de méthode se trouvent dans la `SomeType` classe de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="a8b78-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="a8b78-130">Méthodes abstraites et virtuelles</span><span class="sxs-lookup"><span data-stu-id="a8b78-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="a8b78-131">Le mot clé `abstract` indique qu’une méthode a un emplacement de dispatch virtuel et peut ne pas avoir de définition dans la classe.</span><span class="sxs-lookup"><span data-stu-id="a8b78-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="a8b78-132">Un *emplacement de dispatch virtuel* est une entrée dans une table de fonctions gérée en interne qui est utilisée au moment de l’exécution pour rechercher des appels de fonction virtuelle dans un type orienté objet.</span><span class="sxs-lookup"><span data-stu-id="a8b78-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="a8b78-133">Le mécanisme de répartition virtuelle est le mécanisme qui implémente le *polymorphisme*, une fonctionnalité importante de la programmation orientée objet.</span><span class="sxs-lookup"><span data-stu-id="a8b78-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="a8b78-134">Une classe qui a au moins une méthode abstraite sans définition est une *classe abstraite*, ce qui signifie qu’aucune instance de cette classe ne peut être créée.</span><span class="sxs-lookup"><span data-stu-id="a8b78-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="a8b78-135">Pour plus d’informations sur les classes abstraites, consultez [classes abstraites](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a8b78-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="a8b78-136">Les déclarations de méthode abstraite n’incluent pas de corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="a8b78-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="a8b78-137">Au lieu de cela, le nom de la méthode est suivi d’un signe deux-points ( :) et une signature de type pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="a8b78-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="a8b78-138">La signature de type d’une méthode est la même que celle indiquée par IntelliSense lorsque vous placez le pointeur de la souris sur un nom de méthode dans l’éditeur de Visual Studio Code, sauf sans nom de paramètre.</span><span class="sxs-lookup"><span data-stu-id="a8b78-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="a8b78-139">Les signatures de type sont également affichées par l’interpréteur, fsi.exe, quand vous travaillez de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="a8b78-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="a8b78-140">La signature de type d’une méthode est formée en répertoriant les types des paramètres, suivis du type de retour, avec les symboles de séparateur appropriés.</span><span class="sxs-lookup"><span data-stu-id="a8b78-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="a8b78-141">Les paramètres curryfiés sont séparés par `->` et les paramètres de tuple sont séparés par `*` .</span><span class="sxs-lookup"><span data-stu-id="a8b78-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="a8b78-142">La valeur de retour est toujours séparée des arguments par un `->` symbole.</span><span class="sxs-lookup"><span data-stu-id="a8b78-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="a8b78-143">Les parenthèses peuvent être utilisées pour regrouper des paramètres complexes, par exemple lorsqu’un type de fonction est un paramètre, ou pour indiquer quand un tuple est traité comme un paramètre unique plutôt que comme deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="a8b78-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="a8b78-144">Vous pouvez également fournir des méthodes abstraites default Definitions en ajoutant la définition à la classe et en utilisant le `default` mot clé, comme indiqué dans le bloc de syntaxe de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a8b78-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="a8b78-145">Une méthode abstraite qui a une définition dans la même classe est équivalente à une méthode virtuelle dans d’autres langages de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8b78-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="a8b78-146">Qu’une définition existe ou non, le `abstract` mot clé crée un emplacement de dispatch dans la table de fonctions virtuelles pour la classe.</span><span class="sxs-lookup"><span data-stu-id="a8b78-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="a8b78-147">Indépendamment du fait qu’une classe de base implémente ses méthodes abstraites, les classes dérivées peuvent fournir des implémentations de méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="a8b78-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="a8b78-148">Pour implémenter une méthode abstraite dans une classe dérivée, définissez une méthode qui a le même nom et la même signature dans la classe dérivée, à l’exception du `override` `default` mot clé ou, et fournissez le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a8b78-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="a8b78-149">Les mots clés `override` et `default` signifient exactement la même chose.</span><span class="sxs-lookup"><span data-stu-id="a8b78-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="a8b78-150">Utilisez `override` si la nouvelle méthode substitue une implémentation de classe de base ; utilisez `default` lorsque vous créez une implémentation dans la même classe que la déclaration abstraite d’origine.</span><span class="sxs-lookup"><span data-stu-id="a8b78-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="a8b78-151">N’utilisez pas le `abstract` mot clé sur la méthode qui implémente la méthode qui a été déclarée abstraite dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="a8b78-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="a8b78-152">L’exemple suivant illustre une méthode abstraite `Rotate` qui a une implémentation par défaut, l’équivalent d’une .NET Framework méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="a8b78-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="a8b78-153">L’exemple suivant illustre une classe dérivée qui substitue une méthode de classe de base.</span><span class="sxs-lookup"><span data-stu-id="a8b78-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="a8b78-154">Dans ce cas, le remplacement modifie le comportement afin que la méthode ne fasse rien.</span><span class="sxs-lookup"><span data-stu-id="a8b78-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="a8b78-155">Méthodes surchargées</span><span class="sxs-lookup"><span data-stu-id="a8b78-155">Overloaded Methods</span></span>

<span data-ttu-id="a8b78-156">Les méthodes surchargées sont des méthodes qui ont des noms identiques dans un type donné, mais qui ont des arguments différents.</span><span class="sxs-lookup"><span data-stu-id="a8b78-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="a8b78-157">En F #, les arguments facultatifs sont généralement utilisés à la place des méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="a8b78-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="a8b78-158">Toutefois, les méthodes surchargées sont autorisées dans le langage, à condition que les arguments soient sous forme de tuple, et non sous forme curryfiée.</span><span class="sxs-lookup"><span data-stu-id="a8b78-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="a8b78-159">Arguments facultatifs</span><span class="sxs-lookup"><span data-stu-id="a8b78-159">Optional Arguments</span></span>

<span data-ttu-id="a8b78-160">À compter de F # 4,1, vous pouvez également avoir des arguments facultatifs avec une valeur de paramètre par défaut dans les méthodes.</span><span class="sxs-lookup"><span data-stu-id="a8b78-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="a8b78-161">Cela permet de faciliter l’interopérabilité avec le code C#.</span><span class="sxs-lookup"><span data-stu-id="a8b78-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="a8b78-162">L’exemple suivant illustre la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="a8b78-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="a8b78-163">Notez que la valeur passée pour `DefaultParameterValue` doit correspondre au type d’entrée.</span><span class="sxs-lookup"><span data-stu-id="a8b78-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="a8b78-164">Dans l’exemple ci-dessus, il s’agit d’un `int` .</span><span class="sxs-lookup"><span data-stu-id="a8b78-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="a8b78-165">Si vous tentez de passer une valeur non entière dans, `DefaultParameterValue` une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="a8b78-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="a8b78-166">Exemple : propriétés et méthodes</span><span class="sxs-lookup"><span data-stu-id="a8b78-166">Example: Properties and Methods</span></span>

<span data-ttu-id="a8b78-167">L’exemple suivant contient un type qui contient des exemples de champs, de fonctions privées, de propriétés et de méthodes statiques.</span><span class="sxs-lookup"><span data-stu-id="a8b78-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="a8b78-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8b78-168">See also</span></span>

- <span data-ttu-id="a8b78-169">[Members](index.md) (Membres)</span><span class="sxs-lookup"><span data-stu-id="a8b78-169">[Members](index.md)</span></span>
