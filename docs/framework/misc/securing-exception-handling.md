---
title: Sécurisation de la gestion des exceptions
description: Découvrez comment sécuriser la gestion des exceptions dans le code .NET. Examinez l’ordre dans lequel le code s’exécute s’il existe des instructions Try, except, catch et finally.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
ms.openlocfilehash: 73597f83d7236cd48a18a891c987b4f5d7e1723d
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309038"
---
# <a name="securing-exception-handling"></a>Sécurisation de la gestion des exceptions
Dans Visual C++ et Visual Basic, une expression de filtre plus haut dans la pile s’exécute avant toute `finally` instruction. Le bloc **catch** associé à ce filtre s’exécute après l' `finally` instruction. Pour plus d’informations, consultez [utilisation d’exceptions filtrées par l’utilisateur](../../standard/exceptions/using-user-filtered-exception-handlers.md). Cette section examine les implications en matière de sécurité de cet ordre. Prenons l’exemple de pseudocode suivant qui illustre l’ordre dans lequel les instructions et les instructions de filtre `finally` s’exécutent.  
  
```cpp  
void Main()
{  
    try
    {  
        Sub();  
    }
    except (Filter())
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()
{  
    try
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }
    finally
    {  
        Console.WriteLine("finally");  
    }  
}
```  
  
 Ce code imprime ce qui suit.  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 Le filtre s’exécute avant l' `finally` instruction, de sorte que les problèmes de sécurité peuvent être introduits par tout ce qui modifie l’état là où l’exécution d’un autre code peut en tirer parti. Par exemple :  
  
```cpp  
try
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and
    // so on) that could be exploited if malicious
    // code ran before state is restored.  
    Do_some_work();  
}
finally
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 Ce pseudocode permet à un filtre situé plus haut dans la pile d’exécuter du code arbitraire. D’autres exemples d’opérations qui auraient un effet similaire sont l’emprunt d’identité temporaire d’une autre identité, la définition d’un indicateur interne qui ignore certaines vérifications de sécurité ou la modification de la culture associée au thread. La solution recommandée consiste à introduire un gestionnaire d’exceptions pour isoler les modifications du code à l’état du thread des blocs de filtre des appelants. Toutefois, il est important d’introduire correctement le gestionnaire d’exceptions, sans quoi ce problème ne sera pas résolu. L’exemple suivant change la culture de l’interface utilisateur, mais tout type de modification de l’état du thread peut être exposé de façon similaire.  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 Dans ce cas, le correctif approprié consiste à encapsuler le bloc **try** / **finally** existant dans un bloc **try** / **catch** . Le simple fait d’introduire une clause **Catch-Throw** dans le bloc **try** / **finally** existant ne résout pas le problème, comme illustré dans l’exemple suivant.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 Cela ne résout pas le problème, car l' `finally` instruction n’a pas été exécutée avant le `FilterFunc` contrôle obtient.  
  
 L’exemple suivant résout le problème en s’assurant que la `finally` clause a été exécutée avant d’offrir une exception aux blocs de filtres d’exception des appelants.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try
    {  
        try
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
