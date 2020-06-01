---
title: Création d’interfaces génériques de type variant (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 27760fd73c8c40fc108106b87b2102ab5e07263c
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241381"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="4d15a-102">Création d’interfaces génériques de type variant (C#)</span><span class="sxs-lookup"><span data-stu-id="4d15a-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="4d15a-103">Vous pouvez déclarer des paramètres de type générique dans les interfaces comme covariant ou contravariant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="4d15a-104">La *covariance* permet aux méthodes d’interface d’avoir des types de retour plus dérivés que ceux définis par les paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="4d15a-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="4d15a-105">La *contravariance* permet aux méthodes d’interface d’avoir des types d’argument moins dérivés que ceux spécifiés par les paramètres génériques.</span><span class="sxs-lookup"><span data-stu-id="4d15a-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="4d15a-106">Une interface générique ayant des paramètres de type générique covariant ou contravariant est appelée *variante*.</span><span class="sxs-lookup"><span data-stu-id="4d15a-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="4d15a-107">.NET Framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes.</span><span class="sxs-lookup"><span data-stu-id="4d15a-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="4d15a-108">Pour obtenir la liste des interfaces de type Variant dans .NET, consultez [variance dans les interfaces génériques (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="4d15a-108">For the list of the variant interfaces in .NET, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="4d15a-109">Déclaration d’interfaces génériques de type variant</span><span class="sxs-lookup"><span data-stu-id="4d15a-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="4d15a-110">Vous pouvez déclarer des interfaces génériques de type variant à l’aide des mots clés `in` et `out` pour les paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="4d15a-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d15a-111">En C#, les paramètres `ref`, `in` et `out` ne peuvent pas être de type variant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="4d15a-112">Les types valeur ne prennent pas non plus en charge la variance.</span><span class="sxs-lookup"><span data-stu-id="4d15a-112">Value types also do not support variance.</span></span>

<span data-ttu-id="4d15a-113">Vous pouvez déclarer un covariant de paramètre de type générique à l’aide du mot clé `out`.</span><span class="sxs-lookup"><span data-stu-id="4d15a-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="4d15a-114">Le type covariant doit remplir les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="4d15a-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="4d15a-115">Le type est utilisé uniquement comme un type de retour de méthodes d’interface, et non pas comme un type d’arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="4d15a-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="4d15a-116">L’exemple suivant en fournit une illustration dans laquelle le type `R` est déclaré covariant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="4d15a-117">Il existe une exception à cette règle.</span><span class="sxs-lookup"><span data-stu-id="4d15a-117">There is one exception to this rule.</span></span> <span data-ttu-id="4d15a-118">Si vous avez un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type comme paramètre de type générique pour le délégué.</span><span class="sxs-lookup"><span data-stu-id="4d15a-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="4d15a-119">L’exemple suivant du type `R` illustre ce principe.</span><span class="sxs-lookup"><span data-stu-id="4d15a-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="4d15a-120">Pour plus d’informations, consultez [Variance dans les délégués (C#)](./variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4d15a-120">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="4d15a-121">Le type n’est pas utilisé comme contrainte générique pour les méthodes d’interface.</span><span class="sxs-lookup"><span data-stu-id="4d15a-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="4d15a-122">C’est ce que montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="4d15a-123">Vous pouvez déclarer un contravariant de paramètre de type générique à l’aide du mot clé `in`.</span><span class="sxs-lookup"><span data-stu-id="4d15a-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="4d15a-124">Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode, et non comme type de retour de méthodes d’interface.</span><span class="sxs-lookup"><span data-stu-id="4d15a-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="4d15a-125">Le type contravariant peut également être utilisé pour les contraintes génériques.</span><span class="sxs-lookup"><span data-stu-id="4d15a-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="4d15a-126">Le code suivant montre comment déclarer une interface de type contravariant et utiliser une contrainte générique pour l’une de ses méthodes.</span><span class="sxs-lookup"><span data-stu-id="4d15a-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="4d15a-127">Il est également possible de prendre en charge à la fois la covariance et la contravariance dans la même interface, mais pour des paramètres de type différent, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="4d15a-128">Implémentation d’interfaces génériques de type variant</span><span class="sxs-lookup"><span data-stu-id="4d15a-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="4d15a-129">Vous implémentez des interfaces génériques de type variant dans les classes en utilisant la même syntaxe que celle utilisée pour les interfaces invariantes.</span><span class="sxs-lookup"><span data-stu-id="4d15a-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="4d15a-130">L’exemple de code suivant montre comment implémenter une interface de type covariant dans une classe générique.</span><span class="sxs-lookup"><span data-stu-id="4d15a-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

```csharp
interface ICovariant<out R>
{
    R GetSomething();
}
class SampleImplementation<R> : ICovariant<R>
{
    public R GetSomething()
    {
        // Some code.
        return default(R);
    }
}
```

<span data-ttu-id="4d15a-131">Les classes qui implémentent des interfaces de type variant sont invariantes.</span><span class="sxs-lookup"><span data-stu-id="4d15a-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="4d15a-132">Par exemple, prenons le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-132">For example, consider the following code.</span></span>

```csharp
// The interface is covariant.
ICovariant<Button> ibutton = new SampleImplementation<Button>();
ICovariant<Object> iobj = ibutton;

// The class is invariant.
SampleImplementation<Button> button = new SampleImplementation<Button>();
// The following statement generates a compiler error
// because classes are invariant.
// SampleImplementation<Object> obj = button;
```

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="4d15a-133">Extension d’interfaces génériques de type variant</span><span class="sxs-lookup"><span data-stu-id="4d15a-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="4d15a-134">Quand vous étendez une interface générique de type variant, vous devez utiliser les mots clés `in` et `out` pour spécifier explicitement si l’interface dérivée prend en charge la variance.</span><span class="sxs-lookup"><span data-stu-id="4d15a-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="4d15a-135">Le compilateur ne déduit pas la variance de l’interface étendue.</span><span class="sxs-lookup"><span data-stu-id="4d15a-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="4d15a-136">Observons, par exemple, les interfaces suivantes.</span><span class="sxs-lookup"><span data-stu-id="4d15a-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="4d15a-137">Dans l’interface `IInvariant<T>`, le paramètre de type générique `T` est invariant, alors que dans `IExtCovariant<out T>`, le paramètre de type est covariant, bien que les deux interfaces étendent la même interface.</span><span class="sxs-lookup"><span data-stu-id="4d15a-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="4d15a-138">La même règle est appliquée aux paramètres de type générique contravariant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="4d15a-139">Vous pouvez créer une interface qui étend à la fois l’interface dans laquelle le paramètre de type générique `T` est covariant et l’interface dans laquelle il est contravariant si, dans l’interface étendue, le paramètre de type générique `T` est invariant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="4d15a-140">En voici une illustration dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="4d15a-141">Toutefois, si un paramètre de type générique `T` est déclaré covariant dans une interface, vous ne pouvez pas le déclarer contravariant dans l’interface étendue, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="4d15a-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="4d15a-142">En voici une illustration dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="4d15a-143">Éviter l’ambiguïté</span><span class="sxs-lookup"><span data-stu-id="4d15a-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="4d15a-144">Quand vous implémentez des interfaces génériques de type variant, la variance peut parfois mener à une certaine ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="4d15a-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="4d15a-145">Cela doit être évité.</span><span class="sxs-lookup"><span data-stu-id="4d15a-145">This should be avoided.</span></span>

<span data-ttu-id="4d15a-146">Par exemple, si vous implémentez explicitement la même interface générique de type variant avec des paramètres de type générique différents dans une classe, cela peut être source d’ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="4d15a-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="4d15a-147">Le compilateur ne génère pas d’erreur dans ce cas, mais l’implémentation d’interface qui sera choisie lors de l’exécution ne lui est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4d15a-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="4d15a-148">Des bogues subtils peuvent alors apparaître dans votre code.</span><span class="sxs-lookup"><span data-stu-id="4d15a-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="4d15a-149">Prenons l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d15a-149">Consider the following code example.</span></span>

```csharp
// Simple class hierarchy.
class Animal { }
class Cat : Animal { }
class Dog : Animal { }

// This class introduces ambiguity
// because IEnumerable<out T> is covariant.
class Pets : IEnumerable<Cat>, IEnumerable<Dog>
{
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()
    {
        Console.WriteLine("Cat");
        // Some code.
        return null;
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        // Some code.
        return null;
    }

    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()
    {
        Console.WriteLine("Dog");
        // Some code.
        return null;
    }
}
class Program
{
    public static void Test()
    {
        IEnumerable<Animal> pets = new Pets();
        pets.GetEnumerator();
    }
}
```

<span data-ttu-id="4d15a-150">Dans cet exemple, la façon dont la méthode `pets.GetEnumerator` choisit entre `Cat` et `Dog` n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4d15a-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="4d15a-151">Cela peut provoquer des problèmes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="4d15a-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d15a-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d15a-152">See also</span></span>

- [<span data-ttu-id="4d15a-153">Variance dans les interfaces génériques (C#)</span><span class="sxs-lookup"><span data-stu-id="4d15a-153">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
- [<span data-ttu-id="4d15a-154">Utilisation de la variance pour les délégués génériques Func et Action (C#)</span><span class="sxs-lookup"><span data-stu-id="4d15a-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
