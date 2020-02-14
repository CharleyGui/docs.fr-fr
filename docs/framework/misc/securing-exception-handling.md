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
ms.openlocfilehash: e0465f2eb6be61e161f5e6b8cadf629a53f11906
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215785"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="f00ee-102">Sécurisation de la gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="f00ee-102">Securing Exception Handling</span></span>
<span data-ttu-id="f00ee-103">Dans Visual C++ et Visual Basic, une expression de filtre plus haut dans la pile s’exécute avant toute instruction **finally** .</span><span class="sxs-lookup"><span data-stu-id="f00ee-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="f00ee-104">Le bloc **catch** associé à ce filtre s’exécute après l’instruction **finally** .</span><span class="sxs-lookup"><span data-stu-id="f00ee-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="f00ee-105">Pour plus d’informations, consultez [utilisation d’exceptions filtrées par l’utilisateur](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="f00ee-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="f00ee-106">Cette section examine les implications en matière de sécurité de cet ordre.</span><span class="sxs-lookup"><span data-stu-id="f00ee-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="f00ee-107">Prenons l’exemple de pseudocode suivant qui illustre l’ordre dans lequel les instructions de filtre et les instructions **finally** s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="f00ee-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="f00ee-108">Ce code imprime ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="f00ee-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="f00ee-109">Le filtre s’exécute avant l’instruction **finally** , de sorte que les problèmes de sécurité peuvent être introduits par tout ce qui modifie l’État à l’endroit où l’exécution d’un autre code peut en tirer parti.</span><span class="sxs-lookup"><span data-stu-id="f00ee-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="f00ee-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f00ee-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="f00ee-111">Ce pseudocode permet à un filtre situé plus haut dans la pile d’exécuter du code arbitraire.</span><span class="sxs-lookup"><span data-stu-id="f00ee-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="f00ee-112">D’autres exemples d’opérations qui auraient un effet similaire sont l’emprunt d’identité temporaire d’une autre identité, la définition d’un indicateur interne qui ignore certaines vérifications de sécurité ou la modification de la culture associée au thread.</span><span class="sxs-lookup"><span data-stu-id="f00ee-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="f00ee-113">La solution recommandée consiste à introduire un gestionnaire d’exceptions pour isoler les modifications du code à l’état du thread des blocs de filtre des appelants.</span><span class="sxs-lookup"><span data-stu-id="f00ee-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="f00ee-114">Toutefois, il est important que le gestionnaire d’exceptions soit correctement introduit ou que ce problème ne soit pas résolu.</span><span class="sxs-lookup"><span data-stu-id="f00ee-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="f00ee-115">L’exemple suivant change la culture de l’interface utilisateur, mais tout type de modification de l’état du thread peut être exposé de façon similaire.</span><span class="sxs-lookup"><span data-stu-id="f00ee-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="f00ee-116">Dans ce cas, le correctif approprié consiste à encapsuler le bloc **try**/**finally** existant dans un bloc **try**/**catch** .</span><span class="sxs-lookup"><span data-stu-id="f00ee-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="f00ee-117">Le simple fait d’introduire une clause **Catch-Throw** dans le bloc **try**/**finally** existant ne résout pas le problème, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f00ee-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="f00ee-118">Cela ne résout pas le problème, car l’instruction **finally** n’a pas été exécutée avant que le `FilterFunc` soit le contrôle.</span><span class="sxs-lookup"><span data-stu-id="f00ee-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="f00ee-119">L’exemple suivant résout le problème en s’assurant que la clause **finally** a été exécutée avant d’offrir une exception aux blocs de filtres d’exception des appelants.</span><span class="sxs-lookup"><span data-stu-id="f00ee-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f00ee-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f00ee-120">See also</span></span>

- [<span data-ttu-id="f00ee-121">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="f00ee-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
