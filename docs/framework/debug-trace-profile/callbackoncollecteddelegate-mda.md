---
title: callbackOnCollectedDelegate (MDA)
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
ms.openlocfilehash: eb14e0df5396d92eb223dde2e562684c4c318295
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217569"
---
# <a name="callbackoncollecteddelegate-mda"></a><span data-ttu-id="4088b-102">callbackOnCollectedDelegate (MDA)</span><span class="sxs-lookup"><span data-stu-id="4088b-102">callbackOnCollectedDelegate MDA</span></span>
<span data-ttu-id="4088b-103">L'Assistant Débogage managé (MDA) `callbackOnCollectedDelegate` est activé si un délégué est marshalé du code managé vers du code non managé en tant que pointeur de fonction et si un rappel est placé sur ce pointeur de fonction après la récupération du délégué par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="4088b-103">The `callbackOnCollectedDelegate` managed debugging assistant (MDA) is activated if a delegate is marshaled from managed to unmanaged code as a function pointer and a callback is placed on that function pointer after the delegate has been garbage collected.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4088b-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="4088b-104">Symptoms</span></span>  
 <span data-ttu-id="4088b-105">Des violations d'accès se produisent lors des tentatives d'appel de code managé par les pointeurs de fonction obtenus par des délégués managés.</span><span class="sxs-lookup"><span data-stu-id="4088b-105">Access violations occur when attempting to call into managed code through function pointers that were obtained from managed delegates.</span></span> <span data-ttu-id="4088b-106">Ces échecs, qui ne sont pas des bogues du common language runtime (CLR), peuvent pourtant y ressembler, car la violation d'accès se produit dans le code CLR.</span><span class="sxs-lookup"><span data-stu-id="4088b-106">These failures, while not common language runtime (CLR) bugs, may appear to be so because the access violation occurs in the CLR code.</span></span>  
  
 <span data-ttu-id="4088b-107">Les échecs ne surviennent pas de façon cohérente : tantôt l'appel sur le pointeur de fonction aboutit, tantôt il échoue.</span><span class="sxs-lookup"><span data-stu-id="4088b-107">The failure is not consistent; sometimes the call on the function pointer succeeds and sometimes it fails.</span></span> <span data-ttu-id="4088b-108">Un échec peut se produire dans une situation de surcharge uniquement ou sur un nombre aléatoire de tentatives.</span><span class="sxs-lookup"><span data-stu-id="4088b-108">The failure might occur only under heavy load or on a random number of attempts.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4088b-109">Cause :</span><span class="sxs-lookup"><span data-stu-id="4088b-109">Cause</span></span>  
 <span data-ttu-id="4088b-110">Le délégué à partir duquel le pointeur de fonction a été créé et ensuite exposé au code non managé a été récupéré par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="4088b-110">The delegate from which the function pointer was created and exposed to unmanaged code was garbage collected.</span></span> <span data-ttu-id="4088b-111">Quand le composant non managé tente d'appeler sur le pointeur de fonction, il génère une violation d'accès.</span><span class="sxs-lookup"><span data-stu-id="4088b-111">When the unmanaged component tries to call on the function pointer, it generates an access violation.</span></span>  
  
 <span data-ttu-id="4088b-112">L'échec est aléatoire, car il dépend du moment où l'opération garbage collection se produit.</span><span class="sxs-lookup"><span data-stu-id="4088b-112">The failure appears random because it depends on when garbage collection occurs.</span></span> <span data-ttu-id="4088b-113">Si un délégué peut faire l'objet d'une opération garbage collection, celle-ci peut avoir lieu après le rappel et, dans ce cas, l'appel aboutit.</span><span class="sxs-lookup"><span data-stu-id="4088b-113">If a delegate is eligible for collection, the garbage collection can occur after the callback and the call succeeds.</span></span> <span data-ttu-id="4088b-114">Dans d'autres cas où l'opération garbage collection se produit avant le rappel, le rappel génère une violation d'accès et le programme s'arrête.</span><span class="sxs-lookup"><span data-stu-id="4088b-114">At other times, the garbage collection occurs before the callback, the callback generates an access violation, and the program stops.</span></span>  
  
 <span data-ttu-id="4088b-115">La probabilité d’avoir un échec dépend du laps de temps entre le marshaling du délégué et le rappel sur le pointeur de fonction, ainsi que de la fréquence des opérations garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4088b-115">The probability of the failure depends on the time between marshaling the delegate and the callback on the function pointer as well as the frequency of garbage collections.</span></span> <span data-ttu-id="4088b-116">L’échec est sporadique si le laps de temps entre le marshaling du délégué et le rappel résultant est court.</span><span class="sxs-lookup"><span data-stu-id="4088b-116">The failure is sporadic if the time between marshaling the delegate and the ensuing callback is short.</span></span> <span data-ttu-id="4088b-117">Cela est généralement le cas si la méthode non managée qui reçoit le pointeur de fonction ne l'enregistre pas pour une utilisation ultérieure, mais le rappelle immédiatement pour terminer son opération avant d'être retournée.</span><span class="sxs-lookup"><span data-stu-id="4088b-117">This is usually the case if the unmanaged method receiving the function pointer does not save the function pointer for later use but instead calls back on the function pointer immediately to complete its operation before returning.</span></span> <span data-ttu-id="4088b-118">De la même façon, davantage d'opérations garbage collection se produisent quand un système est en surcharge, ce qui rend plus probable l'exécution d'une opération garbage collection avant le rappel.</span><span class="sxs-lookup"><span data-stu-id="4088b-118">Similarly, more garbage collections occur when a system is under heavy load, which makes it more likely that a garbage collection will occur before the callback.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4088b-119">Résolution</span><span class="sxs-lookup"><span data-stu-id="4088b-119">Resolution</span></span>  
 <span data-ttu-id="4088b-120">Quand un délégué a été marshalé en tant que pointeur de fonction non managé, le garbage collector ne peut pas effectuer le suivi de sa durée de vie.</span><span class="sxs-lookup"><span data-stu-id="4088b-120">Once a delegate has been marshaled out as an unmanaged function pointer, the garbage collector cannot track its lifetime.</span></span> <span data-ttu-id="4088b-121">Votre code doit alors conserver une référence au délégué pendant toute la durée de vie du pointeur de fonction non managé.</span><span class="sxs-lookup"><span data-stu-id="4088b-121">Instead, your code must keep a reference to the delegate for the lifetime of the unmanaged function pointer.</span></span> <span data-ttu-id="4088b-122">Pour cela, vous devez d'abord identifier le délégué qui a été collecté.</span><span class="sxs-lookup"><span data-stu-id="4088b-122">But before you can do that, you first must identify which delegate was collected.</span></span> <span data-ttu-id="4088b-123">Si l'Assistant Débogage managé est activé, il fournit le nom de type du délégué.</span><span class="sxs-lookup"><span data-stu-id="4088b-123">When the MDA is activated, it provides the type name of the delegate.</span></span> <span data-ttu-id="4088b-124">Utilisez ce nom pour rechercher votre code d'appel de code non managé ou les signatures COM qui transmettent ce délégué au code non managé.</span><span class="sxs-lookup"><span data-stu-id="4088b-124">Use this name to search your code for platform invoke or COM signatures that pass that delegate out to unmanaged code.</span></span> <span data-ttu-id="4088b-125">Le délégué incriminé est transmis par l'un de ces sites d'appel.</span><span class="sxs-lookup"><span data-stu-id="4088b-125">The offending delegate is passed out through one of these call sites.</span></span> <span data-ttu-id="4088b-126">Vous pouvez également activer l’Assistant Débogage managé `gcUnmanagedToManaged` pour forcer une opération garbage collection avant chaque rappel dans le runtime.</span><span class="sxs-lookup"><span data-stu-id="4088b-126">You can also enable the `gcUnmanagedToManaged` MDA to force a garbage collection before every callback into the runtime.</span></span> <span data-ttu-id="4088b-127">Vous êtes ainsi certain qu’une opération garbage collection se produit toujours avant le rappel.</span><span class="sxs-lookup"><span data-stu-id="4088b-127">This will remove the uncertainty introduced by the garbage collection by ensuring that a garbage collection always occurs before the callback.</span></span> <span data-ttu-id="4088b-128">Une fois que vous savez quel délégué a été collecté, modifiez votre code pour conserver une référence à ce délégué dans le code managé pendant toute la durée de vie du pointeur de fonction non managé ayant été marshalé.</span><span class="sxs-lookup"><span data-stu-id="4088b-128">Once you know what delegate was collected, change your code to keep a reference to that delegate on the managed side for the lifetime of the marshaled unmanaged function pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4088b-129">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="4088b-129">Effect on the Runtime</span></span>  
 <span data-ttu-id="4088b-130">Quand les délégués sont marshalés en tant que pointeurs de fonction, le runtime alloue un thunk qui effectue la transition du code non managé au code managé.</span><span class="sxs-lookup"><span data-stu-id="4088b-130">When delegates are marshaled as function pointers, the runtime allocates a thunk that does the transition from unmanaged to managed.</span></span> <span data-ttu-id="4088b-131">Ce thunk est en fait ce que le code non managé appelle avant que le délégué managé soit finalement appelé.</span><span class="sxs-lookup"><span data-stu-id="4088b-131">This thunk is what the unmanaged code actually calls before the managed delegate is finally invoked.</span></span> <span data-ttu-id="4088b-132">Si l’Assistant Débogage managé `callbackOnCollectedDelegate` n’est pas activé, le code de marshaling non managé est supprimé quand le délégué est collecté.</span><span class="sxs-lookup"><span data-stu-id="4088b-132">Without the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is deleted when the delegate is collected.</span></span> <span data-ttu-id="4088b-133">Si l’Assistant Débogage managé `callbackOnCollectedDelegate` est activé, le code de marshaling non managé n’est pas immédiatement supprimé quand le délégué est collecté.</span><span class="sxs-lookup"><span data-stu-id="4088b-133">With the `callbackOnCollectedDelegate` MDA enabled, the unmanaged marshaling code is not immediately deleted when the delegate is collected.</span></span> <span data-ttu-id="4088b-134">Au lieu de cela, les 1 000 dernières instances restent actives par défaut et sont modifiées pour activer l'Assistant Débogage managé au moment de l'appel.</span><span class="sxs-lookup"><span data-stu-id="4088b-134">Instead, the last 1,000 instances are kept alive by default and changed to activate the MDA when called.</span></span> <span data-ttu-id="4088b-135">Le thunk est finalement supprimé après la collecte de 1 001 délégués marshalés supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="4088b-135">The thunk is eventually deleted after 1,001 more marshaled delegates are collected.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4088b-136">Output</span><span class="sxs-lookup"><span data-stu-id="4088b-136">Output</span></span>  
 <span data-ttu-id="4088b-137">L'Assistant Débogage managé signale le nom de type du délégué qui a été collecté avant une tentative de rappel sur son pointeur de fonction non managé.</span><span class="sxs-lookup"><span data-stu-id="4088b-137">The MDA reports the type name of the delegate that was collected before a callback was attempted on its unmanaged function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4088b-138">Configuration</span><span class="sxs-lookup"><span data-stu-id="4088b-138">Configuration</span></span>  
 <span data-ttu-id="4088b-139">L'exemple suivant montre les options de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="4088b-139">The following example shows the application configuration options.</span></span> <span data-ttu-id="4088b-140">Il définit le nombre des thunks que l'Assistant Débogage managé garde actifs à 1 500.</span><span class="sxs-lookup"><span data-stu-id="4088b-140">It sets the number of thunks the MDA keeps alive to 1,500.</span></span> <span data-ttu-id="4088b-141">La valeur `listSize` par défaut est 1 000, le minimum 50 et le maximum 2 000.</span><span class="sxs-lookup"><span data-stu-id="4088b-141">The default `listSize` value is 1,000, the minimum is 50, and the maximum is 2,000.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="4088b-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="4088b-142">Example</span></span>  
 <span data-ttu-id="4088b-143">L'exemple suivant illustre une situation qui peut activer cet Assistant Débogage managé :</span><span class="sxs-lookup"><span data-stu-id="4088b-143">The following example demonstrates a situation that can activate this MDA:</span></span>  
  
```cpp
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}
```

```csharp
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {          
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4088b-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4088b-144">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="4088b-145">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="4088b-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4088b-146">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="4088b-146">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
- [<span data-ttu-id="4088b-147">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="4088b-147">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)
