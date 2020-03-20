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
# <a name="securing-exception-handling"></a><span data-ttu-id="a5219-102">Sécurisation de la gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="a5219-102">Securing Exception Handling</span></span>
<span data-ttu-id="a5219-103">Dans Visual CMD et Visual Basic, une expression de filtre plus haut dans la pile s’exécute avant toute déclaration **finale.**</span><span class="sxs-lookup"><span data-stu-id="a5219-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="a5219-104">Le bloc **de capture** associé à ce filtre s’exécute après la déclaration **finale.**</span><span class="sxs-lookup"><span data-stu-id="a5219-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="a5219-105">Pour plus d’informations, voir [à l’aide d’exceptions filtrées par l’utilisateur](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="a5219-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="a5219-106">Cette section examine les implications en matière de sécurité de cet ordre.</span><span class="sxs-lookup"><span data-stu-id="a5219-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="a5219-107">Considérez l’exemple pseudocode suivant qui illustre l’ordre dans lequel filtrent les déclarations et **enfin** les déclarations s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="a5219-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="a5219-108">Ce code imprime ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="a5219-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="a5219-109">Le filtre s’exécute avant la déclaration **finale,** de sorte que les questions de sécurité peuvent être introduites par tout ce qui rend un changement d’état où l’exécution d’un autre code pourrait en profiter.</span><span class="sxs-lookup"><span data-stu-id="a5219-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="a5219-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a5219-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="a5219-111">Ce pseudocode permet à un filtre plus haut dans la pile d’exécuter le code arbitraire.</span><span class="sxs-lookup"><span data-stu-id="a5219-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="a5219-112">D’autres exemples d’opérations qui auraient un effet similaire sont l’usurpation d’identité temporaire, la mise en place d’un drapeau interne qui contourne une certaine vérification de sécurité, ou de changer la culture associée au fil.</span><span class="sxs-lookup"><span data-stu-id="a5219-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="a5219-113">La solution recommandée est d’introduire un gestionnaire d’exception pour isoler les modifications du code à l’état de thread des blocs de filtre des appelants.</span><span class="sxs-lookup"><span data-stu-id="a5219-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="a5219-114">Cependant, il est important que le gestionnaire d’exception soit correctement introduit ou que ce problème ne soit pas résolu.</span><span class="sxs-lookup"><span data-stu-id="a5219-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="a5219-115">L’exemple suivant change la culture de l’interface utilisateur, mais tout type de changement d’état de thread pourrait être exposé de la même façon.</span><span class="sxs-lookup"><span data-stu-id="a5219-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="a5219-116">Le correctif correct dans ce cas est d’envelopper l’essai **try**/existant**finalement** bloquer dans un bloc de capture **d’essai.**/**catch**</span><span class="sxs-lookup"><span data-stu-id="a5219-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="a5219-117">Le simple fait d’introduire une clause **de lancement de capture** dans l’essai existant **finalement**/**bloquer** ne résout pas le problème, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a5219-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a5219-118">Cela ne résout **finally** pas le problème parce `FilterFunc` que la déclaration finale n’a pas couru avant que le contrôle obtient.</span><span class="sxs-lookup"><span data-stu-id="a5219-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="a5219-119">L’exemple suivant résout le problème en veillant à ce que la clause **finale** ait été exécutée avant d’offrir une exception sur les blocs de filtre d’exception des appelants.</span><span class="sxs-lookup"><span data-stu-id="a5219-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5219-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5219-120">See also</span></span>

- [<span data-ttu-id="a5219-121">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="a5219-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
