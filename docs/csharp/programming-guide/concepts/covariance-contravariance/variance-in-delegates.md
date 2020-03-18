---
title: Variance dans les délégués (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: fd1b4824dc3d8f12347e01b804a6e39fe2e086c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169712"
---
# <a name="variance-in-delegates-c"></a>Variance dans les délégués (C#)
.NET Framework 3.5 a introduit la prise en charge de la variance pour faire correspondre les signatures de méthode aux types délégués pour tous les délégués dans C#. Cela signifie que vous pouvez assigner aux délégués non seulement les méthodes ayant des signatures correspondantes, mais également des méthodes qui retournent des types plus dérivés (covariance) ou qui acceptent des paramètres ayant des types moins dérivés (contravariance) que ceux spécifiés par le type délégué. Cela inclut à la fois des délégués génériques et non génériques.  
  
 Par exemple, considérez le code suivant, qui a deux classes et deux délégués : génériques et non génériques.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Quand vous créez des délégués des types `SampleDelegate` ou `SampleGenericDelegate<A, R>`, vous pouvez assigner l’une des méthodes suivantes à ces délégués.  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second second)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 L’exemple de code suivant illustre la conversion implicite entre la signature de méthode et le type délégué.  
  
```csharp  
// Assigning a method with a matching signature
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 Pour obtenir d’autres exemples, consultez [Utilisation de la variance dans les délégués (C#)](./using-variance-in-delegates.md) et [Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Variance dans les paramètres de type générique  
 Dans .NET Framework 4 ou version ultérieure, vous pouvez activer la conversion implicite entre les délégués afin que les délégués génériques ayant des types différents spécifiés par les paramètres de type générique puissent être assignés les uns aux autres, si les types sont hérités les uns des autres comme requis par la variance.  
  
 Pour activer la conversion implicite, vous devez déclarer explicitement les paramètres génériques dans un délégué comme covariant ou contravariant à l’aide du mot clé `in` ou `out`.  
  
 L’exemple de code suivant indique comment vous pouvez créer un délégué ayant un paramètre de type générique covariant.  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;
}  
```  
  
 Si vous utilisez uniquement la prise en charge de la variance pour faire correspondre les signatures de méthode aux types délégués et que vous n’utilisez pas les mots clés `in` et `out`, vous pouvez réaliser qu’il est parfois possible d’instancier des délégués avec des expressions ou méthodes lambda identiques, mais que vous ne pouvez pas assigner un délégué à un autre.  
  
 Dans l’exemple de code suivant, `SampleGenericDelegate<String>` ne peut pas être converti explicitement en `SampleGenericDelegate<Object>`, même si `String` hérite de `Object`. Vous pouvez résoudre ce problème en marquant le paramètre générique `T` avec le mot clé `out`.  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Délégués génériques ayant des paramètres de type variant dans le .NET Framework  
 .NET Framework 4 a introduit la prise en charge de la variance pour les paramètres de type générique dans plusieurs délégués génériques existants :  
  
- Les délégués `Action` de l’espace de noms <xref:System>, par exemple, <xref:System.Action%601> et <xref:System.Action%602>  
  
- Les délégués `Func` de l’espace de noms <xref:System>, par exemple, <xref:System.Func%601> et <xref:System.Func%602>  
  
- Le délégué <xref:System.Predicate%601>  
  
- Le délégué <xref:System.Comparison%601>  
  
- Le délégué <xref:System.Converter%602>  
  
 Pour obtenir plus d’informations et d’exemples, consultez [Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Déclaration de paramètres de type variant dans les délégués génériques  
 Si un délégué générique possède des paramètres de type générique covariant ou contravariant, il peut être désigné sous le nom de *délégué générique variant*.  
  
 Vous pouvez déclarer un paramètre de type générique covariant dans un délégué générique à l’aide du mot clé `out`. Le type covariant peut être utilisé uniquement comme type de retour de méthode et non comme type d’arguments de méthode. L’exemple de code suivant indique comment déclarer un délégué générique covariant.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Vous pouvez déclarer un paramètre de type générique contravariant dans un délégué générique à l’aide du mot clé `in`. Le type contravariant peut être utilisé uniquement comme type d’arguments de méthode et non comme type de retour de méthode. L’exemple de code suivant indique comment déclarer un délégué générique contravariant.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> Les paramètres `ref`, `in` et `out` en C# ne peuvent pas être marqués comme étant variants.  
  
 Il est également possible de prendre en charge à la fois la variance et la covariance dans le même délégué, mais pour des paramètres de type différents. Cela est illustré par l'exemple suivant.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Instanciation et appel de délégués génériques variants  
 Vous pouvez instancier et appeler des délégués variants de la même façon que vous instanciez et appelez des délégués invariants. Dans l’exemple suivant, le délégué est instancié par une expression lambda.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Combinaison des délégués génériques variants  
 Vous ne devez pas combiner les délégués variants. La méthode <xref:System.Delegate.Combine%2A> ne prend pas en charge la conversion des délégués variants et nécessite le même type pour tous les délégués. Il peut s’ensuivre une exception runtime quand vous combinez les délégués à l’aide de la méthode <xref:System.Delegate.Combine%2A> ou de l’opérateur `+`, comme dans l’exemple de code suivant.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Variance dans les paramètres de type générique pour les types valeur et référence  
 La variance pour les paramètres de type générique est prise en charge uniquement pour les types référence. Par exemple, `DVariant<int>` ne peut pas être converti implicitement en `DVariant<Object>` ni `DVariant<long>` parce que l’entier est un type valeur.  
  
 L’exemple suivant montre que la variance dans les paramètres de type générique n’est pas prise en charge pour les types valeur.  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Génériques](../../../../standard/generics/index.md)
- [Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)
- [Comment combiner les délégués (délégués multicast)](../../delegates/how-to-combine-delegates-multicast-delegates.md)
