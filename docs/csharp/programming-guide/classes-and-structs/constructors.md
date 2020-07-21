---
title: Constructeurs - Guide de programmation C#
description: Un constructeur en C# est appelé lors de la création d’une classe ou d’un struct. Utilisez les constructeurs pour définir les valeurs par défaut, l’instanciation de limite et écrire du code flexible et facile à lire.
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 4a731e648143f5e0ecf8860625962d8baa29fe26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474902"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="9a0c9-104">Constructeurs (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9a0c9-104">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="9a0c9-105">Chaque fois qu’une [classe](../../language-reference/keywords/class.md) ou un [struct](../../language-reference/builtin-types/struct.md) est créé, son constructeur est appelé.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-105">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="9a0c9-106">Une classe ou un struct peut avoir plusieurs constructeurs qui prennent des arguments différents.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-106">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="9a0c9-107">Les constructeurs permettent au programmeur de définir des valeurs par défaut, de limiter l’instanciation et d’écrire un code flexible et facile à lire.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-107">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="9a0c9-108">Pour obtenir plus d’informations et d’exemples, consultez [Utilisation de constructeurs](./using-constructors.md) et [Constructeurs d’instances](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="9a0c9-108">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="9a0c9-109">Constructeurs sans paramètre</span><span class="sxs-lookup"><span data-stu-id="9a0c9-109">Parameterless constructors</span></span>
  
<span data-ttu-id="9a0c9-110">Si vous ne fournissez pas de constructeur pour votre classe, C# en crée un par défaut qui instancie l’objet et définit des variables membres avec les valeurs par défaut, comme indiqué dans l’article [valeurs par défaut des types C#](../../language-reference/builtin-types/default-values.md) .</span><span class="sxs-lookup"><span data-stu-id="9a0c9-110">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="9a0c9-111">Si vous ne fournissez pas de constructeur pour votre struct, C# s’appuie sur un *constructeur sans paramètre implicite* pour initialiser automatiquement chaque champ à sa valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-111">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="9a0c9-112">Pour plus d’informations et d’exemples, consultez [constructeurs d’instances](instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="9a0c9-112">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="9a0c9-113">Syntaxe du constructeur</span><span class="sxs-lookup"><span data-stu-id="9a0c9-113">Constructor syntax</span></span>

<span data-ttu-id="9a0c9-114">Un constructeur est une méthode dont le nom est le même que celui de son type.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-114">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="9a0c9-115">Sa signature de méthode inclut uniquement le nom de la méthode et sa liste de paramètres ; elle n’inclut pas de type de retour.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-115">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="9a0c9-116">L’exemple suivant affiche le constructeur d’une classe nommée `Person`.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-116">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="9a0c9-117">Si un constructeur peut être implémenté comme une seule instruction, vous pouvez utiliser une [définition de corps d’expression](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="9a0c9-117">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="9a0c9-118">L’exemple suivant définit une classe `Location` dont le constructeur a un seul paramètre de chaîne nommé *name*.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-118">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="9a0c9-119">La définition de corps d’expression assigne l’argument au champ `locationName`.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-119">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="9a0c9-120">Constructeurs statiques</span><span class="sxs-lookup"><span data-stu-id="9a0c9-120">Static constructors</span></span>

<span data-ttu-id="9a0c9-121">Les exemples précédents ont tous montré des constructeurs d’instances qui permettent de créer un objet.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-121">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="9a0c9-122">Une classe ou un struct peut également avoir un constructeur statique qui initialise les membres statiques du type.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-122">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="9a0c9-123">Les constructeurs statiques sont sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-123">Static constructors are parameterless.</span></span> <span data-ttu-id="9a0c9-124">Si vous ne fournissez pas de constructeur statique pour initialiser les champs statiques, le compilateur C# initialise les champs statiques à leur valeur par défaut, comme indiqué dans l’article [valeurs par défaut des types C#](../../language-reference/builtin-types/default-values.md) .</span><span class="sxs-lookup"><span data-stu-id="9a0c9-124">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="9a0c9-125">L’exemple suivant utilise un constructeur statique pour initialiser un champ statique.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-125">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="9a0c9-126">Vous pouvez également définir un constructeur statique avec une définition de corps d’expression, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9a0c9-126">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="9a0c9-127">Pour obtenir plus d’informations et d’exemples, consultez [Constructeurs statiques](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="9a0c9-127">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a0c9-128">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9a0c9-128">In This Section</span></span>  
 [<span data-ttu-id="9a0c9-129">Utilisation de constructeurs</span><span class="sxs-lookup"><span data-stu-id="9a0c9-129">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="9a0c9-130">Constructeurs d’instances</span><span class="sxs-lookup"><span data-stu-id="9a0c9-130">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="9a0c9-131">Constructeurs privés</span><span class="sxs-lookup"><span data-stu-id="9a0c9-131">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="9a0c9-132">Constructeurs statiques</span><span class="sxs-lookup"><span data-stu-id="9a0c9-132">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="9a0c9-133">Comment : écrire un constructeur de copie</span><span class="sxs-lookup"><span data-stu-id="9a0c9-133">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="9a0c9-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a0c9-134">See also</span></span>

- [<span data-ttu-id="9a0c9-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9a0c9-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9a0c9-136">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="9a0c9-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9a0c9-137">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="9a0c9-137">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="9a0c9-138">static</span><span class="sxs-lookup"><span data-stu-id="9a0c9-138">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="9a0c9-139">Pourquoi les initialiseurs s’exécutent-ils dans l’ordre inverse en tant que constructeurs ? Première partie</span><span class="sxs-lookup"><span data-stu-id="9a0c9-139">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
