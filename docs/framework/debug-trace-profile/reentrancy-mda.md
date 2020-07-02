---
title: réentrance (MDA)
description: Examinez l’Assistant Débogage managé de réentrance, qui peut être activé si le tas d’objets est endommagé ou si d’autres erreurs graves se produisent lors de la transition du code natif au code managé.
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
ms.openlocfilehash: f666e505b8382b0bec8dcfdb34c775850e46c429
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803103"
---
# <a name="reentrancy-mda"></a><span data-ttu-id="86eca-103">réentrance (MDA)</span><span class="sxs-lookup"><span data-stu-id="86eca-103">reentrancy MDA</span></span>
<span data-ttu-id="86eca-104">L’Assistant Débogage managé (MDA) `reentrancy` est activé en cas de tentative de transition du code natif au code managé dans les cas où un basculement antérieur du code managé au mode natif n’a pas été effectué par le biais d’une transition ordonnée.</span><span class="sxs-lookup"><span data-stu-id="86eca-104">The `reentrancy` managed debugging assistant (MDA) is activated when an attempt is made to transition from native to managed code in cases where a prior switch from managed to native code was not performed through an orderly transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="86eca-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="86eca-105">Symptoms</span></span>  
 <span data-ttu-id="86eca-106">Le tas d’objets est endommagé ou d’autres erreurs graves se produisent lors de la transition du code natif au code managé.</span><span class="sxs-lookup"><span data-stu-id="86eca-106">The object heap is corrupted or other serious errors are occurring when transitioning from native to managed code.</span></span>  
  
 <span data-ttu-id="86eca-107">Les threads qui basculent entre le code managé et le code natif dans les deux sens doivent effectuer une transition de façon ordonnée.</span><span class="sxs-lookup"><span data-stu-id="86eca-107">Threads that switch between native and managed code in either direction must perform an orderly transition.</span></span> <span data-ttu-id="86eca-108">Toutefois, certains points d’extensibilité de bas niveau dans le système d’exploitation, tels que le gestionnaire d’exceptions vectorisées, permettent de basculer entre le code managé et le code natif sans exécuter de transition ordonnée.</span><span class="sxs-lookup"><span data-stu-id="86eca-108">However, certain low-level extensibility points in the operating system, such as the vectored exception handler, allow switches from managed to native code without performing an orderly transition.</span></span>  <span data-ttu-id="86eca-109">Ces basculement sont sous le contrôle du système d’exploitation, et non sous le contrôle du Commun Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="86eca-109">These switches are under operating system control, rather than under common language runtime (CLR) control.</span></span>  <span data-ttu-id="86eca-110">Tout code natif qui s’exécute à l’intérieur de ces points d’extensibilité doit éviter de rappeler le code managé.</span><span class="sxs-lookup"><span data-stu-id="86eca-110">Any native code that executes inside these extensibility points must avoid calling back into managed code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="86eca-111">Cause</span><span class="sxs-lookup"><span data-stu-id="86eca-111">Cause</span></span>  
 <span data-ttu-id="86eca-112">Un point d’extensibilité de bas niveau du système d’exploitation, tel que le gestionnaire d’exceptions vectorisées, a été activé pendant l’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="86eca-112">A low-level operating system extensibility point, such as the vectored exception handler, has activated while executing managed code.</span></span>  <span data-ttu-id="86eca-113">Le code d’application appelé par le biais de ce point d’extensibilité tente d’effectuer un rappel dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="86eca-113">The application code that is invoked through that extensibility point is attempting to call back into managed code.</span></span>  
  
 <span data-ttu-id="86eca-114">Ce problème est toujours dû au code d’application.</span><span class="sxs-lookup"><span data-stu-id="86eca-114">This problem is always caused by application code.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="86eca-115">Résolution</span><span class="sxs-lookup"><span data-stu-id="86eca-115">Resolution</span></span>  
 <span data-ttu-id="86eca-116">Recherchez dans l’arborescence des appels de procédure le thread qui a activé cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="86eca-116">Examine the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="86eca-117">Le thread tente d’appeler illégalement du code managé.</span><span class="sxs-lookup"><span data-stu-id="86eca-117">The thread is attempting to illegally call into managed code.</span></span>  <span data-ttu-id="86eca-118">La trace de pile doit révéler le code d’application qui utilise ce point d’extensibilité, le code du système d’exploitation qui fournit ce point d’extensibilité et le code managé qui a été interrompu par le point d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="86eca-118">The stack trace should reveal the application code using this extensibility point, the operating system code that provides this extensibility point, and the managed code that was interrupted by the extensibility point.</span></span>  
  
 <span data-ttu-id="86eca-119">Vous constaterez par exemple que l’Assistant Débogage managé a été activé lors d’une tentative d’appel de code managé à l’intérieur d’un gestionnaire d’exceptions vectorisées.</span><span class="sxs-lookup"><span data-stu-id="86eca-119">For example, you will see the MDA activated in an attempt to call managed code from inside a vectored exception handler.</span></span>  <span data-ttu-id="86eca-120">Sur la pile, vous verrez le code de gestion des exceptions du système d’exploitation et le code managé qui déclenche une exception comme <xref:System.DivideByZeroException> ou <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="86eca-120">On the stack you will see the operating system exception handling code and some managed code triggering an exception such as a <xref:System.DivideByZeroException> or an <xref:System.AccessViolationException>.</span></span>  
  
 <span data-ttu-id="86eca-121">Dans cet exemple, la solution consiste à implémenter le gestionnaire d’exceptions vectorisées entièrement dans le code non managé.</span><span class="sxs-lookup"><span data-stu-id="86eca-121">In this example, the correct resolution is to implement the vectored exception handler completely in unmanaged code.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="86eca-122">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="86eca-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="86eca-123">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="86eca-123">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="86eca-124">Output</span><span class="sxs-lookup"><span data-stu-id="86eca-124">Output</span></span>  
 <span data-ttu-id="86eca-125">L’Assistant Débogage managé signale les tentatives de réentrance non conformes.</span><span class="sxs-lookup"><span data-stu-id="86eca-125">The MDA reports that illegal reentrancy is being attempted.</span></span>  <span data-ttu-id="86eca-126">Examinez la pile du thread pour déterminer pourquoi cela se produit et comment résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="86eca-126">Examine the thread's stack to determine why this is happening and how to correct the problem.</span></span> <span data-ttu-id="86eca-127">Voici un exemple de sortie.</span><span class="sxs-lookup"><span data-stu-id="86eca-127">The following is sample output.</span></span>  
  
```output
Additional Information: Attempting to call into managed code without
transitioning out first.  Do not attempt to run managed code inside
low-level native extensibility points. Managed Debugging Assistant
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a><span data-ttu-id="86eca-128">Configuration</span><span class="sxs-lookup"><span data-stu-id="86eca-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="86eca-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="86eca-129">Example</span></span>  
 <span data-ttu-id="86eca-130">L’exemple de code suivant provoque la levée de <xref:System.AccessViolationException>.</span><span class="sxs-lookup"><span data-stu-id="86eca-130">The following code example causes an <xref:System.AccessViolationException> to be thrown.</span></span>  <span data-ttu-id="86eca-131">Dans les versions de Windows qui prennent en charge la gestion des exceptions vectorisées, cela entraîne l’appel du gestionnaire d’exceptions vectorisées managé.</span><span class="sxs-lookup"><span data-stu-id="86eca-131">On versions of Windows that support vectored exception handling, this will cause the managed vectored exception handler to be called.</span></span>  <span data-ttu-id="86eca-132">Si l’Assistant Débogage managé `reentrancy` est activé, il sera déclenché pendant la tentative d’appel à `MyHandler` à partir du code de prise en charge de gestion des exceptions vectorisées du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="86eca-132">If the `reentrancy` MDA is enabled, the MDA will activate during the attempted call to `MyHandler` from the operating system's vectored exception handling support code.</span></span>  
  
```csharp
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try
        {  
            // Dispatch on null should AV.  
            Reenter r = null;
            r.Run();  
        }
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="86eca-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86eca-133">See also</span></span>

- [<span data-ttu-id="86eca-134">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="86eca-134">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
