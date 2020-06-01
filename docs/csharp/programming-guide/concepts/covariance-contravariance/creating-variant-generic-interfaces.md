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
# <a name="creating-variant-generic-interfaces-c"></a>Création d’interfaces génériques de type variant (C#)

Vous pouvez déclarer des paramètres de type générique dans les interfaces comme covariant ou contravariant. La *covariance* permet aux méthodes d’interface d’avoir des types de retour plus dérivés que ceux définis par les paramètres de type générique. La *contravariance* permet aux méthodes d’interface d’avoir des types d’argument moins dérivés que ceux spécifiés par les paramètres génériques. Une interface générique ayant des paramètres de type générique covariant ou contravariant est appelée *variante*.

> [!NOTE]
> .NET Framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes. Pour obtenir la liste des interfaces de type Variant dans .NET, consultez [variance dans les interfaces génériques (C#)](./variance-in-generic-interfaces.md).

## <a name="declaring-variant-generic-interfaces"></a>Déclaration d’interfaces génériques de type variant

Vous pouvez déclarer des interfaces génériques de type variant à l’aide des mots clés `in` et `out` pour les paramètres de type générique.

> [!IMPORTANT]
> En C#, les paramètres `ref`, `in` et `out` ne peuvent pas être de type variant. Les types valeur ne prennent pas non plus en charge la variance.

Vous pouvez déclarer un covariant de paramètre de type générique à l’aide du mot clé `out`. Le type covariant doit remplir les conditions suivantes :

- Le type est utilisé uniquement comme un type de retour de méthodes d’interface, et non pas comme un type d’arguments de méthode. L’exemple suivant en fournit une illustration dans laquelle le type `R` est déclaré covariant.

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    Il existe une exception à cette règle. Si vous avez un délégué générique contravariant comme paramètre de méthode, vous pouvez utiliser le type comme paramètre de type générique pour le délégué. L’exemple suivant du type `R` illustre ce principe. Pour plus d’informations, consultez [Variance dans les délégués (C#)](./variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md).

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- Le type n’est pas utilisé comme contrainte générique pour les méthodes d’interface. C’est ce que montre le code suivant.

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

Vous pouvez déclarer un contravariant de paramètre de type générique à l’aide du mot clé `in`. Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode, et non comme type de retour de méthodes d’interface. Le type contravariant peut également être utilisé pour les contraintes génériques. Le code suivant montre comment déclarer une interface de type contravariant et utiliser une contrainte générique pour l’une de ses méthodes.

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

Il est également possible de prendre en charge à la fois la covariance et la contravariance dans la même interface, mais pour des paramètres de type différent, comme indiqué dans l’exemple de code suivant.

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a>Implémentation d’interfaces génériques de type variant

Vous implémentez des interfaces génériques de type variant dans les classes en utilisant la même syntaxe que celle utilisée pour les interfaces invariantes. L’exemple de code suivant montre comment implémenter une interface de type covariant dans une classe générique.

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

Les classes qui implémentent des interfaces de type variant sont invariantes. Par exemple, prenons le code suivant.

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

## <a name="extending-variant-generic-interfaces"></a>Extension d’interfaces génériques de type variant

Quand vous étendez une interface générique de type variant, vous devez utiliser les mots clés `in` et `out` pour spécifier explicitement si l’interface dérivée prend en charge la variance. Le compilateur ne déduit pas la variance de l’interface étendue. Observons, par exemple, les interfaces suivantes.

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

Dans l’interface `IInvariant<T>`, le paramètre de type générique `T` est invariant, alors que dans `IExtCovariant<out T>`, le paramètre de type est covariant, bien que les deux interfaces étendent la même interface. La même règle est appliquée aux paramètres de type générique contravariant.

Vous pouvez créer une interface qui étend à la fois l’interface dans laquelle le paramètre de type générique `T` est covariant et l’interface dans laquelle il est contravariant si, dans l’interface étendue, le paramètre de type générique `T` est invariant. En voici une illustration dans l’exemple de code suivant.

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

Toutefois, si un paramètre de type générique `T` est déclaré covariant dans une interface, vous ne pouvez pas le déclarer contravariant dans l’interface étendue, ou vice versa. En voici une illustration dans l’exemple de code suivant.

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a>Éviter l’ambiguïté

Quand vous implémentez des interfaces génériques de type variant, la variance peut parfois mener à une certaine ambiguïté. Cela doit être évité.

Par exemple, si vous implémentez explicitement la même interface générique de type variant avec des paramètres de type générique différents dans une classe, cela peut être source d’ambiguïté. Le compilateur ne génère pas d’erreur dans ce cas, mais l’implémentation d’interface qui sera choisie lors de l’exécution ne lui est pas spécifiée. Des bogues subtils peuvent alors apparaître dans votre code. Prenons l’exemple de code suivant.

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

Dans cet exemple, la façon dont la méthode `pets.GetEnumerator` choisit entre `Cat` et `Dog` n’est pas spécifiée. Cela peut provoquer des problèmes dans votre code.

## <a name="see-also"></a>Voir aussi

- [Variance dans les interfaces génériques (C#)](./variance-in-generic-interfaces.md)
- [Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)
