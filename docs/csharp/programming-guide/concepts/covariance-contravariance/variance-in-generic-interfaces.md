---
title: Variance dans les interfaces génériques (C#)
description: Affichez les informations de prise en charge de la variance pour les interfaces génériques, y compris les informations mises à jour pour les interfaces existantes dans .NET Framework 4 et 4,5.
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 91218742c01eeb6e65ea26d9dc41ed7c98827377
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105633"
---
# <a name="variance-in-generic-interfaces-c"></a>Variance dans les interfaces génériques (C#)

.NET Framework 4 a introduit la prise en charge de la variance pour plusieurs interfaces génériques existantes. La prise en charge de la variance permet la conversion implicite des classes qui implémentent ces interfaces.

À partir de .NET Framework 4, les interfaces suivantes sont des variantes :

- <xref:System.Collections.Generic.IEnumerable%601> (T est covariant)

- <xref:System.Collections.Generic.IEnumerator%601> (T est covariant)

- <xref:System.Linq.IQueryable%601> (T est covariant)

- <xref:System.Linq.IGrouping%602> (`TKey` et `TElement` sont covariants)

- <xref:System.Collections.Generic.IComparer%601> (T est contravariant)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T est contravariant)

- <xref:System.IComparable%601> (T est contravariant)

À compter de .NET Framework 4.5, les interfaces suivantes sont des variants :

- <xref:System.Collections.Generic.IReadOnlyList%601> (T est covariant)

- <xref:System.Collections.Generic.IReadOnlyCollection%601> (T est covariant)

La covariance permet à une méthode d’avoir un type de retour plus dérivé que celui défini par le paramètre de type générique de l’interface. Pour illustrer la fonctionnalité de covariance, considérez ces interfaces génériques : `IEnumerable<Object>` et `IEnumerable<String>`. L’interface `IEnumerable<String>` n’hérite pas de l’interface `IEnumerable<Object>`. Toutefois, le type `String` hérite du type `Object` et, dans certains cas, vous pouvez assigner des objets de ces interfaces de l’un à l’autre. Ce cas de figure est présenté dans l’exemple de code suivant :

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

Dans les versions antérieures de .NET Framework, ce code provoque une erreur de compilation en C# et, si `Option Strict` est activé, dans Visual Basic. Cependant, vous pouvez désormais utiliser `strings` au lieu d’`objects`, comme illustré dans l’exemple précédent, parce que l’interface <xref:System.Collections.Generic.IEnumerable%601> est covariante.

La contravariance permet à une méthode d’avoir des types d’argument moins dérivés que ceux spécifiés par le paramètre générique de l’interface. Pour illustrer la contravariance, supposez que vous avez créé une classe `BaseComparer` pour comparer des instances de la classe `BaseClass`. La classe `BaseComparer` implémente l’interface `IEqualityComparer<BaseClass>`. Étant donné que l’interface <xref:System.Collections.Generic.IEqualityComparer%601> est maintenant contravariante, vous pouvez utiliser `BaseComparer` pour comparer des instances des classes qui héritent de la classe `BaseClass`. Ce cas de figure est présenté dans l’exemple de code suivant :

```csharp
// Simple hierarchy of classes.
class BaseClass { }
class DerivedClass : BaseClass { }

// Comparer class.
class BaseComparer : IEqualityComparer<BaseClass>
{
    public int GetHashCode(BaseClass baseInstance)
    {
        return baseInstance.GetHashCode();
    }
    public bool Equals(BaseClass x, BaseClass y)
    {
        return x == y;
    }
}
class Program
{
    static void Test()
    {
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();

        // Implicit conversion of IEqualityComparer<BaseClass> to
        // IEqualityComparer<DerivedClass>.
        IEqualityComparer<DerivedClass> childComparer = baseComparer;
    }
}
```

Pour obtenir d’autres exemples, consultez [Utilisation de la variance dans les interfaces pour les collections génériques (C#)](./using-variance-in-interfaces-for-generic-collections.md).

La variance dans les interfaces génériques est prise en charge uniquement pour les types référence. Les types valeur ne prennent pas en charge la variance. Par exemple, `IEnumerable<int>` ne peut pas être converti implicitement en `IEnumerable<object>`, car les entiers sont représentés par un type valeur.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Il est également important de se souvenir que les classes qui implémentent des interfaces variantes sont toujours invariantes. Par exemple, même si <xref:System.Collections.Generic.List%601> implémente l’interface covariante <xref:System.Collections.Generic.IEnumerable%601>, vous ne pouvez pas convertir implicitement `List<String>` en `List<Object>`. En voici une illustration dans l’exemple de code suivant.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Voir aussi

- [Utilisation de la variance dans les interfaces pour les collections génériques (C#)](./using-variance-in-interfaces-for-generic-collections.md)
- [Création d’interfaces génériques de type variant (C#)](./creating-variant-generic-interfaces.md)
- [Interfaces génériques](../../../../standard/generics/interfaces.md)
- [Variance dans les délégués (C#)](./variance-in-delegates.md)
