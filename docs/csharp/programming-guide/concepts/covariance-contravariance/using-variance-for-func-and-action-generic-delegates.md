---
title: Utilisation de la variance pour les délégués génériques Func et Action (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: bbfc41fb8ab3e7d800f1eb03098e02056e694872
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659907"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Utilisation de la variance pour les délégués génériques Func et Action (C#)
Ces exemples montrent comment utiliser la covariance et la contravariance dans les délégués génériques `Func` et `Action` pour permettre de réutiliser des méthodes et fournir davantage de flexibilité dans votre code.  
  
 Pour plus d’informations sur la covariance et la contravariance, consultez [Variance dans les délégués (C#)](./variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Utilisation des délégués avec les paramètres de type covariant  
 L’exemple suivant illustre les avantages de la prise en charge de la covariance dans les délégués génériques `Func`. La méthode `FindByTitle` prend un paramètre de type `String` et retourne un objet de type `Employee`. Toutefois, vous pouvez assigner cette méthode au délégué `Func<String, Person>`, car `Employee` hérite de `Person`.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Utilisation des délégués avec les paramètres de type contravariant  
 L’exemple suivant illustre les avantages de la prise en charge de la contravariance dans les délégués génériques `Action`. La méthode `AddToContacts` prend un paramètre de type `Person`. Toutefois, vous pouvez assigner cette méthode au délégué `Action<Employee>`, car `Employee` hérite de `Person`.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Covariance et contravariance (C#)](./index.md)
- [Génériques](../../../../standard/generics/index.md)
