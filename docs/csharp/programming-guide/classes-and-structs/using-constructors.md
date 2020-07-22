---
title: Utilisation de constructeurs - Guide de programmation C#
description: Cet exemple montre comment une classe est instanciée à l’aide de l’opérateur New en C#. Le constructeur simple est appelé après que la mémoire a été allouée pour le nouvel objet.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 6b441b04bd6bfcb5564f40a90718e822f56ac21e
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863953"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="bff0a-104">Utilisation de constructeurs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="bff0a-104">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="bff0a-105">Quand une [classe](../../language-reference/keywords/class.md) ou un [struct](../../language-reference/builtin-types/struct.md) est créé, son constructeur est appelé.</span><span class="sxs-lookup"><span data-stu-id="bff0a-105">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="bff0a-106">Les constructeurs portent le même nom que la classe ou le struct, et ils initialisent généralement les membres de données du nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="bff0a-106">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="bff0a-107">Dans l’exemple suivant, une classe nommée `Taxi` est définie en utilisant un constructeur simple.</span><span class="sxs-lookup"><span data-stu-id="bff0a-107">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="bff0a-108">Cette classe est ensuite instanciée à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-108">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="bff0a-109">Le constructeur `Taxi` est appelé par l’opérateur `new` immédiatement après l’allocation de la mémoire pour le nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="bff0a-109">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="bff0a-110">Un constructeur qui ne prend pas de paramètres est appelé *constructeur sans paramètre*.</span><span class="sxs-lookup"><span data-stu-id="bff0a-110">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="bff0a-111">Les constructeurs sans paramètre sont appelés chaque fois qu’un objet est instancié à l’aide de l’opérateur `new` et qu’aucun argument n’est fourni à `new`.</span><span class="sxs-lookup"><span data-stu-id="bff0a-111">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="bff0a-112">Pour plus d’informations, consultez [Constructeurs d’instances](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-112">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="bff0a-113">À moins d’être [statiques](../../language-reference/keywords/static.md), les classes sans constructeur se voient attribuer un constructeur public sans paramètre par le compilateur C#, afin d’activer l’instanciation de classe.</span><span class="sxs-lookup"><span data-stu-id="bff0a-113">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="bff0a-114">Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-114">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="bff0a-115">Vous pouvez empêcher qu’une classe soit instanciée en rendant le constructeur privé, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bff0a-115">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="bff0a-116">Pour plus d’informations, consultez [Constructeurs privés](./private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-116">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="bff0a-117">Les constructeurs des types [struct](../../language-reference/builtin-types/struct.md) ressemblent aux constructeurs de classe, mais les `structs` ne peuvent pas contenir de constructeur explicite sans paramètre, car le compilateur en fournit automatiquement un.</span><span class="sxs-lookup"><span data-stu-id="bff0a-117">Constructors for [struct](../../language-reference/builtin-types/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="bff0a-118">Ce constructeur initialise chaque champ du `struct` à la [valeur par défaut](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-118">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="bff0a-119">Toutefois, ce constructeur sans paramètre est appelé uniquement si le `struct` est instancié avec `new`.</span><span class="sxs-lookup"><span data-stu-id="bff0a-119">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="bff0a-120">Par exemple, ce code utilise le constructeur sans paramètre pour <xref:System.Int32>. Vous avez ainsi la garantie que l’entier est initialisé :</span><span class="sxs-lookup"><span data-stu-id="bff0a-120">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="bff0a-121">Toutefois, le code suivant provoque une erreur de compilateur, car il n’utilise pas `new` et il essaie d’utiliser un objet qui n’a pas été initialisé :</span><span class="sxs-lookup"><span data-stu-id="bff0a-121">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="bff0a-122">Les objets basés sur des `structs` (notamment tous les types numériques intégrés) peuvent également être initialisés ou assignés, puis utilisés, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bff0a-122">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="bff0a-123">L’appel du constructeur sans paramètre pour un type valeur n’est donc pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bff0a-123">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="bff0a-124">Les classes et les `structs` peuvent tous les deux définir des constructeurs qui prennent des paramètres.</span><span class="sxs-lookup"><span data-stu-id="bff0a-124">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="bff0a-125">Les constructeurs qui prennent des paramètres doivent être appelés à l’aide d’une instruction `new` ou d’une instruction [base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-125">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="bff0a-126">Les classes et les `structs` peuvent également définir plusieurs constructeurs, et ni les classes ni les structs ne sont nécessaires pour définir un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="bff0a-126">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="bff0a-127">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="bff0a-127">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="bff0a-128">Cette classe peut être créée à l’aide de l’une ou l’autre des instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="bff0a-128">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="bff0a-129">Un constructeur peut utiliser le mot clé `base` pour appeler le constructeur d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="bff0a-129">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="bff0a-130">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="bff0a-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="bff0a-131">Dans cet exemple, le constructeur de la classe de base est appelé avant que le bloc du constructeur ne soit exécuté.</span><span class="sxs-lookup"><span data-stu-id="bff0a-131">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="bff0a-132">Le mot clé `base` peut être utilisé avec ou sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="bff0a-132">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="bff0a-133">Tous les paramètres du constructeur peuvent être utilisés comme paramètres pour `base` ou comme partie d’une expression.</span><span class="sxs-lookup"><span data-stu-id="bff0a-133">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="bff0a-134">Pour plus d’informations, consultez [base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-134">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="bff0a-135">Dans une classe dérivée, si un constructeur de classe de base n’est pas appelé explicitement à l’aide du mot clé `base`, le constructeur sans paramètre, s’il existe, est appelé implicitement.</span><span class="sxs-lookup"><span data-stu-id="bff0a-135">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="bff0a-136">Cela signifie que les déclarations de constructeur suivantes sont en fait les mêmes :</span><span class="sxs-lookup"><span data-stu-id="bff0a-136">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="bff0a-137">Si une classe de base n’offre pas de constructeur sans paramètre, la classe dérivée doit faire un appel explicite à un constructeur de base à l’aide de `base`.</span><span class="sxs-lookup"><span data-stu-id="bff0a-137">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="bff0a-138">Un constructeur peut appeler un autre constructeur dans le même objet à l’aide du mot clé [this](../../language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-138">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="bff0a-139">Comme `base`, `this` peut être utilisé avec ou sans paramètres, et tous les paramètres dans le constructeur sont disponibles comme paramètres pour `this` ou comme partie d’une expression.</span><span class="sxs-lookup"><span data-stu-id="bff0a-139">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="bff0a-140">Par exemple, le deuxième constructeur de l’exemple précédent peut être récrit à l’aide de `this` :</span><span class="sxs-lookup"><span data-stu-id="bff0a-140">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="bff0a-141">L’utilisation du mot clé `this` dans l’exemple précédent provoque l’appel de ce constructeur :</span><span class="sxs-lookup"><span data-stu-id="bff0a-141">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="bff0a-142">Les constructeurs peuvent être marqués comme [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) ou [private protected](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-142">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="bff0a-143">Ces modificateurs d’accès définissent la façon dont les utilisateurs de la classe peuvent construire la classe.</span><span class="sxs-lookup"><span data-stu-id="bff0a-143">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="bff0a-144">Pour plus d’informations, consultez [Modificateurs d’accès](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-144">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="bff0a-145">Un constructeur peut être déclaré statique à l’aide du mot clé [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-145">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="bff0a-146">Les constructeurs statiques sont appelés automatiquement, juste avant que des champs statiques soient accessibles, et ils sont généralement utilisés pour initialiser des membres de classe statique.</span><span class="sxs-lookup"><span data-stu-id="bff0a-146">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="bff0a-147">Pour plus d’informations, consultez [Constructeurs statiques](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="bff0a-147">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bff0a-148">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bff0a-148">C# Language Specification</span></span>  

<span data-ttu-id="bff0a-149">Pour plus d’informations, consultez [Constructeurs d’instances](~/_csharplang/spec/classes.md#instance-constructors) et [Constructeurs statiques](~/_csharplang/spec/classes.md#static-constructors) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="bff0a-149">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="bff0a-150">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="bff0a-150">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bff0a-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bff0a-151">See also</span></span>

- [<span data-ttu-id="bff0a-152">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bff0a-152">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bff0a-153">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="bff0a-153">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="bff0a-154">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="bff0a-154">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="bff0a-155">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="bff0a-155">Finalizers</span></span>](./destructors.md)
