---
title: Utilisation de la variance pour les délégués génériques Func et Action (C#)
description: En savoir plus sur l’utilisation de la covariance et de la contravariance dans les délégués génériques Func et action pour vous offrir davantage de flexibilité dans votre code.
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: d7174b0f734d10ab69d0936cb5ca4aa2f4fafdf7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105709"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="67e9a-103">Utilisation de la variance pour les délégués génériques Func et Action (C#)</span><span class="sxs-lookup"><span data-stu-id="67e9a-103">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="67e9a-104">Ces exemples montrent comment utiliser la covariance et la contravariance dans les délégués génériques `Func` et `Action` pour permettre de réutiliser des méthodes et fournir davantage de flexibilité dans votre code.</span><span class="sxs-lookup"><span data-stu-id="67e9a-104">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="67e9a-105">Pour plus d’informations sur la covariance et la contravariance, consultez [Variance dans les délégués (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="67e9a-105">For more information about covariance and contravariance, see [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="67e9a-106">Utilisation des délégués avec les paramètres de type covariant</span><span class="sxs-lookup"><span data-stu-id="67e9a-106">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="67e9a-107">L’exemple suivant illustre les avantages de la prise en charge de la covariance dans les délégués génériques `Func`.</span><span class="sxs-lookup"><span data-stu-id="67e9a-107">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="67e9a-108">La méthode `FindByTitle` prend un paramètre de type `String` et retourne un objet de type `Employee`.</span><span class="sxs-lookup"><span data-stu-id="67e9a-108">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="67e9a-109">Toutefois, vous pouvez assigner cette méthode au délégué `Func<String, Person>`, car `Employee` hérite de `Person`.</span><span class="sxs-lookup"><span data-stu-id="67e9a-109">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static Employee FindByTitle(String title)  
    {  
        // This is a stub for a method that returns  
        // an employee that has the specified title.  
        return new Employee();  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Func<String, Employee> findEmployee = FindByTitle;  
  
        // The delegate expects a method to return Person,  
        // but you can assign it a method that returns Employee.  
        Func<String, Person> findPerson = FindByTitle;  
  
        // You can also assign a delegate
        // that returns a more derived type
        // to a delegate that returns a less derived type.  
        findPerson = findEmployee;  
  
    }  
}  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="67e9a-110">Utilisation des délégués avec les paramètres de type contravariant</span><span class="sxs-lookup"><span data-stu-id="67e9a-110">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="67e9a-111">L’exemple suivant illustre les avantages de la prise en charge de la contravariance dans les délégués génériques `Action`.</span><span class="sxs-lookup"><span data-stu-id="67e9a-111">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="67e9a-112">La méthode `AddToContacts` prend un paramètre de type `Person`.</span><span class="sxs-lookup"><span data-stu-id="67e9a-112">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="67e9a-113">Toutefois, vous pouvez assigner cette méthode au délégué `Action<Employee>`, car `Employee` hérite de `Person`.</span><span class="sxs-lookup"><span data-stu-id="67e9a-113">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
```csharp  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static void AddToContacts(Person person)  
    {  
        // This method adds a Person object  
        // to a contact list.  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Action<Person> addPersonToContacts = AddToContacts;  
  
        // The Action delegate expects
        // a method that has an Employee parameter,  
        // but you can assign it a method that has a Person parameter  
        // because Employee derives from Person.  
        Action<Employee> addEmployeeToContacts = AddToContacts;  
  
        // You can also assign a delegate
        // that accepts a less derived parameter to a delegate
        // that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="67e9a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67e9a-114">See also</span></span>

- [<span data-ttu-id="67e9a-115">Covariance et contravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="67e9a-115">Covariance and Contravariance (C#)</span></span>](./index.md)
- [<span data-ttu-id="67e9a-116">Génériques</span><span class="sxs-lookup"><span data-stu-id="67e9a-116">Generics</span></span>](../../../../standard/generics/index.md)
