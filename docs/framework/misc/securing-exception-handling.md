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
ms.openlocfilehash: c7643bb34da0cbcbd267fc90e6294bc0b565985e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855775"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="4308d-104">Sécurisation de la gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="4308d-104">Securing Exception Handling</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="4308d-105">Dans Visual C++ et Visual Basic, une expression de filtre plus haut dans la pile s’exécute avant toute `finally` instruction.</span><span class="sxs-lookup"><span data-stu-id="4308d-105">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any `finally` statement.</span></span> <span data-ttu-id="4308d-106">Le bloc **catch** associé à ce filtre s’exécute après l' `finally` instruction.</span><span class="sxs-lookup"><span data-stu-id="4308d-106">The **catch** block associated with that filter runs after the `finally` statement.</span></span> <span data-ttu-id="4308d-107">Pour plus d’informations, consultez [utilisation d’exceptions filtrées par l’utilisateur](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="4308d-107">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="4308d-108">Cette section examine les implications en matière de sécurité de cet ordre.</span><span class="sxs-lookup"><span data-stu-id="4308d-108">This section examines the security implications of this order.</span></span> <span data-ttu-id="4308d-109">Prenons l’exemple de pseudocode suivant qui illustre l’ordre dans lequel les instructions et les instructions de filtre `finally` s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="4308d-109">Consider the following pseudocode example that illustrates the order in which filter statements and `finally` statements run.</span></span>  
  
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
  
 <span data-ttu-id="4308d-110">Ce code imprime ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="4308d-110">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="4308d-111">Le filtre s’exécute avant l' `finally` instruction, de sorte que les problèmes de sécurité peuvent être introduits par tout ce qui modifie l’état là où l’exécution d’un autre code peut en tirer parti.</span><span class="sxs-lookup"><span data-stu-id="4308d-111">The filter runs before the `finally` statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="4308d-112">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="4308d-112">For example:</span></span>  
  
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
  
 <span data-ttu-id="4308d-113">Ce pseudocode permet à un filtre situé plus haut dans la pile d’exécuter du code arbitraire.</span><span class="sxs-lookup"><span data-stu-id="4308d-113">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="4308d-114">D’autres exemples d’opérations qui auraient un effet similaire sont l’emprunt d’identité temporaire d’une autre identité, la définition d’un indicateur interne qui ignore certaines vérifications de sécurité ou la modification de la culture associée au thread.</span><span class="sxs-lookup"><span data-stu-id="4308d-114">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="4308d-115">La solution recommandée consiste à introduire un gestionnaire d’exceptions pour isoler les modifications du code à l’état du thread des blocs de filtre des appelants.</span><span class="sxs-lookup"><span data-stu-id="4308d-115">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="4308d-116">Toutefois, il est important d’introduire correctement le gestionnaire d’exceptions, sans quoi ce problème ne sera pas résolu.</span><span class="sxs-lookup"><span data-stu-id="4308d-116">However, it's important to properly introduce the exception handler or this problem won't be fixed.</span></span> <span data-ttu-id="4308d-117">L’exemple suivant change la culture de l’interface utilisateur, mais tout type de modification de l’état du thread peut être exposé de façon similaire.</span><span class="sxs-lookup"><span data-stu-id="4308d-117">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="4308d-118">Dans ce cas, le correctif approprié consiste à encapsuler le bloc **try** / **finally** existant dans un bloc **try** / **catch** .</span><span class="sxs-lookup"><span data-stu-id="4308d-118">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="4308d-119">Le simple fait d’introduire une clause **Catch-Throw** dans le bloc **try** / **finally** existant ne résout pas le problème, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4308d-119">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="4308d-120">Cela ne résout pas le problème, car l' `finally` instruction n’a pas été exécutée avant le `FilterFunc` contrôle obtient.</span><span class="sxs-lookup"><span data-stu-id="4308d-120">This does not fix the problem because the `finally` statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="4308d-121">L’exemple suivant résout le problème en s’assurant que la `finally` clause a été exécutée avant d’offrir une exception aux blocs de filtres d’exception des appelants.</span><span class="sxs-lookup"><span data-stu-id="4308d-121">The following example fixes the problem by ensuring that the `finally` clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4308d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4308d-122">See also</span></span>

- [<span data-ttu-id="4308d-123">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="4308d-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
