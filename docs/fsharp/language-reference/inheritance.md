---
title: Héritage
description: Apprenez à spécifier les relations d’héritage de F à l’aide du mot clé « héritez ».
ms.date: 05/16/2016
ms.openlocfilehash: 5ab891a93528427a66e4eb8f7bfeccbf6e4d2c7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400287"
---
# <a name="inheritance"></a><span data-ttu-id="326cf-103">Héritage</span><span class="sxs-lookup"><span data-stu-id="326cf-103">Inheritance</span></span>

<span data-ttu-id="326cf-104">L’héritage est utilisé pour modéliser la relation « est-a », ou sous-typage, dans la programmation orientée objet.</span><span class="sxs-lookup"><span data-stu-id="326cf-104">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>

## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="326cf-105">Spécifier les relations d’héritage</span><span class="sxs-lookup"><span data-stu-id="326cf-105">Specifying Inheritance Relationships</span></span>

<span data-ttu-id="326cf-106">Vous spécifiez `inherit` les relations d’héritage en utilisant le mot clé dans une déclaration de classe.</span><span class="sxs-lookup"><span data-stu-id="326cf-106">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="326cf-107">La forme syntaxique de base est indiquée dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="326cf-107">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="326cf-108">Une classe peut avoir au plus une classe de base directe.</span><span class="sxs-lookup"><span data-stu-id="326cf-108">A class can have at most one direct base class.</span></span> <span data-ttu-id="326cf-109">Si vous ne spécifiez `inherit` pas une classe de `System.Object`base en utilisant le mot clé, la classe hérite implicitement de .</span><span class="sxs-lookup"><span data-stu-id="326cf-109">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>

## <a name="inherited-members"></a><span data-ttu-id="326cf-110">Membres hérités</span><span class="sxs-lookup"><span data-stu-id="326cf-110">Inherited Members</span></span>

<span data-ttu-id="326cf-111">Si une classe hérite d’une autre classe, les méthodes et les membres de la classe de base sont disponibles pour les utilisateurs de la classe dérivée comme s’ils étaient des membres directs de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="326cf-111">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="326cf-112">Les fixations de laisser et les paramètres constructor sont privés d’une classe et, par conséquent, ne peuvent pas être consultées à partir de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="326cf-112">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="326cf-113">Le `base` mot clé est disponible dans les classes dérivées et se réfère à l’instance de classe de base.</span><span class="sxs-lookup"><span data-stu-id="326cf-113">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="326cf-114">Il est utilisé comme l’auto-identifiant.</span><span class="sxs-lookup"><span data-stu-id="326cf-114">It is used like the self-identifier.</span></span>

## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="326cf-115">Méthodes et remplacements virtuels</span><span class="sxs-lookup"><span data-stu-id="326cf-115">Virtual Methods and Overrides</span></span>

<span data-ttu-id="326cf-116">Les méthodes virtuelles (et les propriétés) fonctionnent un peu différemment en F par rapport à d’autres langues .NET.</span><span class="sxs-lookup"><span data-stu-id="326cf-116">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="326cf-117">Pour déclarer un nouveau membre `abstract` virtuel, vous utilisez le mot clé.</span><span class="sxs-lookup"><span data-stu-id="326cf-117">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="326cf-118">Vous le faites indépendamment du fait que vous fournissiez une implémentation par défaut pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="326cf-118">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="326cf-119">Ainsi, une définition complète d’une méthode virtuelle dans une classe de base suit ce modèle :</span><span class="sxs-lookup"><span data-stu-id="326cf-119">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="326cf-120">Et dans une classe dérivée, un remplacement de cette méthode virtuelle suit ce modèle :</span><span class="sxs-lookup"><span data-stu-id="326cf-120">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="326cf-121">Si vous ometez l’implémentation par défaut dans la classe de base, la classe de base devient une classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="326cf-121">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="326cf-122">L’exemple de code suivant illustre la `function1` déclaration d’une nouvelle méthode virtuelle dans une classe de base et comment la remplacer dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="326cf-122">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]

## <a name="constructors-and-inheritance"></a><span data-ttu-id="326cf-123">Constructeurs et héritage</span><span class="sxs-lookup"><span data-stu-id="326cf-123">Constructors and Inheritance</span></span>

<span data-ttu-id="326cf-124">Le constructeur de la classe de base doit être appelé dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="326cf-124">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="326cf-125">Les arguments en faveur du constructeur de la `inherit` catégorie de base figurent dans la liste d’arguments de la clause.</span><span class="sxs-lookup"><span data-stu-id="326cf-125">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="326cf-126">Les valeurs utilisées doivent être déterminées à partir des arguments fournis au constructeur de classe dérivé.</span><span class="sxs-lookup"><span data-stu-id="326cf-126">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="326cf-127">Le code suivant montre une classe de base et une classe dérivée, où la classe dérivée appelle le constructeur de classe de base dans la clause d’hériter :</span><span class="sxs-lookup"><span data-stu-id="326cf-127">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="326cf-128">Dans le cas de plusieurs constructeurs, le code suivant peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="326cf-128">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="326cf-129">La première ligne des constructeurs `inherit` de classe dérivés est la clause, `val` et les champs apparaissent comme des champs explicites qui sont déclarés avec le mot clé.</span><span class="sxs-lookup"><span data-stu-id="326cf-129">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="326cf-130">Pour plus d’informations, voir [Champs explicites: `val` Le mot clé](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="326cf-130">For more information, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="326cf-131">Alternatives à l’héritage</span><span class="sxs-lookup"><span data-stu-id="326cf-131">Alternatives to Inheritance</span></span>

<span data-ttu-id="326cf-132">Dans les cas où une modification mineure d’un type est nécessaire, envisagez d’utiliser une expression d’objet comme alternative à l’héritage.</span><span class="sxs-lookup"><span data-stu-id="326cf-132">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="326cf-133">L’exemple suivant illustre l’utilisation d’une expression d’objet comme alternative à la création d’un nouveau type dérivé :</span><span class="sxs-lookup"><span data-stu-id="326cf-133">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="326cf-134">Pour plus d’informations sur les expressions d’objets, voir [Expressions d’objets](object-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="326cf-134">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="326cf-135">Lorsque vous créez des hiérarchies d’objets, envisagez d’utiliser une union discriminée au lieu de l’héritage.</span><span class="sxs-lookup"><span data-stu-id="326cf-135">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="326cf-136">Les unions discriminées peuvent également modéliser le comportement varié de différents objets qui partagent un type global commun.</span><span class="sxs-lookup"><span data-stu-id="326cf-136">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="326cf-137">Une union seule et discriminée peut souvent éliminer la nécessité d’un certain nombre de classes dérivées qui sont des variations mineures les unes des autres.</span><span class="sxs-lookup"><span data-stu-id="326cf-137">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="326cf-138">Pour plus d’informations sur les syndicats discriminés, voir [Discriminated Unions](discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="326cf-138">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="326cf-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="326cf-139">See also</span></span>

- [<span data-ttu-id="326cf-140">Expressions d'objet</span><span class="sxs-lookup"><span data-stu-id="326cf-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="326cf-141">Référence linguistique F</span><span class="sxs-lookup"><span data-stu-id="326cf-141">F# Language Reference</span></span>](index.md)
