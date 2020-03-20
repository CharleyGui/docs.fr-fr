---
title: Sécurisation de la gestion des exceptions
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
ms.openlocfilehash: ad27e62197f6fdaa6b5e706f4ae02c03fecae9f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181135"
---
# <a name="securing-exception-handling"></a>Sécurisation de la gestion des exceptions
Dans Visual CMD et Visual Basic, une expression de filtre plus haut dans la pile s’exécute avant toute déclaration **finale.** Le bloc **de capture** associé à ce filtre s’exécute après la déclaration **finale.** Pour plus d’informations, voir [à l’aide d’exceptions filtrées par l’utilisateur](../../standard/exceptions/using-user-filtered-exception-handlers.md). Cette section examine les implications en matière de sécurité de cet ordre. Considérez l’exemple pseudocode suivant qui illustre l’ordre dans lequel filtrent les déclarations et **enfin** les déclarations s’exécutent.  
  
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
  
 Le filtre s’exécute avant la déclaration **finale,** de sorte que les questions de sécurité peuvent être introduites par tout ce qui rend un changement d’état où l’exécution d’un autre code pourrait en profiter. Par exemple :  
  
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
  
 Ce pseudocode permet à un filtre plus haut dans la pile d’exécuter le code arbitraire. D’autres exemples d’opérations qui auraient un effet similaire sont l’usurpation d’identité temporaire, la mise en place d’un drapeau interne qui contourne une certaine vérification de sécurité, ou de changer la culture associée au fil. La solution recommandée est d’introduire un gestionnaire d’exception pour isoler les modifications du code à l’état de thread des blocs de filtre des appelants. Cependant, il est important que le gestionnaire d’exception soit correctement introduit ou que ce problème ne soit pas résolu. L’exemple suivant change la culture de l’interface utilisateur, mais tout type de changement d’état de thread pourrait être exposé de la même façon.  
  
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
  
 Le correctif correct dans ce cas est d’envelopper l’essai **try**/existant**finalement** bloquer dans un bloc de capture **d’essai.**/**catch** Le simple fait d’introduire une clause **de lancement de capture** dans l’essai existant **finalement**/**bloquer** ne résout pas le problème, comme le montre l’exemple suivant.  
  
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
  
 Cela ne résout **finally** pas le problème parce `FilterFunc` que la déclaration finale n’a pas couru avant que le contrôle obtient.  
  
 L’exemple suivant résout le problème en veillant à ce que la clause **finale** ait été exécutée avant d’offrir une exception sur les blocs de filtre d’exception des appelants.  
  
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
