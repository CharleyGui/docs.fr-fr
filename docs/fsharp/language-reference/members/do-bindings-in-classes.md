---
title: Liaisons do dans les classes
description: Apprenez à utiliser une F# liaison’do’dans une définition de classe, qui effectue des actions lorsque l’objet est construit ou lorsque le type est utilisé pour la première fois.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627589"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="bdc26-103">Liaisons do dans les classes</span><span class="sxs-lookup"><span data-stu-id="bdc26-103">do Bindings in Classes</span></span>

<span data-ttu-id="bdc26-104">Une `do` liaison dans une définition de classe effectue des actions lorsque l’objet est construit ou, pour `do` une liaison statique, lorsque le type est utilisé pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="bdc26-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="bdc26-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdc26-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="bdc26-106">Notes</span><span class="sxs-lookup"><span data-stu-id="bdc26-106">Remarks</span></span>

<span data-ttu-id="bdc26-107">Une `do` liaison s’affiche avec les liaisons `let` or after, mais avant les définitions de membres dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="bdc26-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="bdc26-108">Bien que `do` le mot clé soit `do` facultatif pour les liaisons au niveau du module, il n’est `do` pas facultatif pour les liaisons dans une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="bdc26-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="bdc26-109">Pour la construction de chaque objet d’un type donné, les liaisons non `do` statiques et les liaisons non `let` statiques sont exécutées dans l’ordre dans lequel elles apparaissent dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="bdc26-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="bdc26-110">Plusieurs `do` liaisons peuvent se produire dans un type.</span><span class="sxs-lookup"><span data-stu-id="bdc26-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="bdc26-111">Les liaisons non statiques `let` et les liaisons non statiques `do` deviennent le corps du constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="bdc26-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="bdc26-112">Le code dans la section liaisons non `do` statiques peut référencer les paramètres du constructeur principal et toutes les valeurs ou fonctions qui sont définies `let` dans la section liaisons.</span><span class="sxs-lookup"><span data-stu-id="bdc26-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="bdc26-113">Les liaisons non `do` statiques peuvent accéder aux membres de la classe tant que la classe a un auto-identificateur défini par un `as` mot clé dans l’en-tête de la classe, et tant que toutes les utilisations de ces membres sont qualifiées avec l’auto-identificateur pour la classe.</span><span class="sxs-lookup"><span data-stu-id="bdc26-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="bdc26-114">Étant `let` donné que les liaisons initialisent les champs privés d’une classe, ce qui est souvent nécessaire pour garantir que les membres `do` se comportent comme prévu `let` , les liaisons sont généralement placées `do` après des liaisons afin que le code de la liaison puisse Exécutez avec un objet entièrement initialisé.</span><span class="sxs-lookup"><span data-stu-id="bdc26-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="bdc26-115">Si votre code tente d’utiliser un membre avant la fin de l’initialisation, une exception InvalidOperationException est levée.</span><span class="sxs-lookup"><span data-stu-id="bdc26-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="bdc26-116">Les `do` liaisons statiques peuvent référencer des membres statiques ou des champs de la classe englobante, mais pas des membres d’instance ou des champs.</span><span class="sxs-lookup"><span data-stu-id="bdc26-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="bdc26-117">Les `do` liaisons statiques font partie de l’initialiseur statique de la classe, qui est garantie de s’exécuter avant la première utilisation de la classe.</span><span class="sxs-lookup"><span data-stu-id="bdc26-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="bdc26-118">Les attributs sont ignorés pour les liaisons dans les `do` types.</span><span class="sxs-lookup"><span data-stu-id="bdc26-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="bdc26-119">Si un attribut est requis pour du code qui s’exécute dans `do` une liaison, il doit être appliqué au constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="bdc26-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="bdc26-120">Dans le code suivant, une classe a une liaison `do` statique et une liaison non statique `do` .</span><span class="sxs-lookup"><span data-stu-id="bdc26-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="bdc26-121">L’objet a un constructeur qui a deux paramètres, `a` et `b`, et deux champs privés sont définis dans les `let` liaisons de la classe.</span><span class="sxs-lookup"><span data-stu-id="bdc26-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="bdc26-122">Deux propriétés sont également définies.</span><span class="sxs-lookup"><span data-stu-id="bdc26-122">Two properties are also defined.</span></span> <span data-ttu-id="bdc26-123">Toutes ces valeurs se trouvent dans la portée de la section `do` liaisons non statiques, comme illustré par la ligne qui imprime toutes ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="bdc26-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="bdc26-124">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="bdc26-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="bdc26-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdc26-125">See also</span></span>

- [<span data-ttu-id="bdc26-126">Membres</span><span class="sxs-lookup"><span data-stu-id="bdc26-126">Members</span></span>](index.md)
- [<span data-ttu-id="bdc26-127">Classes</span><span class="sxs-lookup"><span data-stu-id="bdc26-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="bdc26-128">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="bdc26-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="bdc26-129">Liaisons `let` dans des classes</span><span class="sxs-lookup"><span data-stu-id="bdc26-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="bdc26-130">`do`Liaisons</span><span class="sxs-lookup"><span data-stu-id="bdc26-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
