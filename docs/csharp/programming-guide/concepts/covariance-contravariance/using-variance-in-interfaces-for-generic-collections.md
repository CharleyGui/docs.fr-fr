---
title: Utilisation de la variance dans les interfaces pour les collections génériques (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 53aaf49ee0802c0d207e0b0a29661cee7c628b4d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595215"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="7281c-102">Utilisation de la variance dans les interfaces pour les collections génériques (C#)</span><span class="sxs-lookup"><span data-stu-id="7281c-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="7281c-103">Une interface covariante permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="7281c-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="7281c-104">Une interface contravariante permet à ses méthodes d’accepter des paramètres de types moins dérivés que ceux spécifiés dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="7281c-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="7281c-105">Dans .NET Framework 4, plusieurs interfaces existantes sont devenues covariantes et contravariantes.</span><span class="sxs-lookup"><span data-stu-id="7281c-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="7281c-106">Celles-ci comprennent <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="7281c-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="7281c-107">Cela vous permet de réutiliser des méthodes qui fonctionnent avec les collections génériques de types de base pour les collections de types dérivés.</span><span class="sxs-lookup"><span data-stu-id="7281c-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="7281c-108">Pour obtenir la liste des interfaces de type variant dans le .NET Framework, consultez [Variance dans les interfaces génériques (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="7281c-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="7281c-109">Conversion de collections génériques</span><span class="sxs-lookup"><span data-stu-id="7281c-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="7281c-110">L’exemple suivant illustre les avantages de la prise en charge de la covariance dans l’interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="7281c-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="7281c-111">La méthode `PrintFullName` accepte une collection de type `IEnumerable<Person>` comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="7281c-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="7281c-112">Toutefois, vous pouvez la réutiliser pour une collection de type `IEnumerable<Employee>`, car `Employee` hérite de `Person`.</span><span class="sxs-lookup"><span data-stu-id="7281c-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,   
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="7281c-113">Comparaison de collections génériques</span><span class="sxs-lookup"><span data-stu-id="7281c-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="7281c-114">L’exemple suivant illustre les avantages de la prise en charge de la contravariance dans l’interface <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="7281c-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="7281c-115">La classe `PersonComparer` implémente l'interface `IComparer<Person>`.</span><span class="sxs-lookup"><span data-stu-id="7281c-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="7281c-116">Toutefois, vous pouvez réutiliser cette classe pour comparer une séquence d’objets de type `Employee`, car `Employee` hérite de `Person`.</span><span class="sxs-lookup"><span data-stu-id="7281c-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {              
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;              
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,   
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7281c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7281c-117">See also</span></span>

- [<span data-ttu-id="7281c-118">Variance dans les interfaces génériques (C#)</span><span class="sxs-lookup"><span data-stu-id="7281c-118">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
