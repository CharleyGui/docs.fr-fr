---
title: Assistant Débogage managé invalidApartmentStateChange
description: En savoir plus sur l’Assistant Débogage managé (MDA) invalidApartmentStateChange dans .NET, qui est activé en cas de problème avec l’état de cloisonnement COM.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
ms.openlocfilehash: db55e3ac2d6862d008013abef0f09f67213d9faa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272746"
---
# <a name="invalidapartmentstatechange-mda"></a><span data-ttu-id="1ed4b-103">Assistant Débogage managé invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="1ed4b-103">invalidApartmentStateChange MDA</span></span>

<span data-ttu-id="1ed4b-104">L’Assistant Débogage managé `invalidApartmentStateChange` est activé par l’un des deux problèmes suivants :</span><span class="sxs-lookup"><span data-stu-id="1ed4b-104">The `invalidApartmentStateChange` managed debugging assistant (MDS) is activated by either of two problems:</span></span>  
  
- <span data-ttu-id="1ed4b-105">Une tentative est effectuée pour modifier l’état de cloisonnement COM d’un thread qui a déjà été initialisé par COM à un état de cloisonnement différent.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-105">An attempt is made to change the COM apartment state of a thread that has already been initialized by COM to a different apartment state.</span></span>  
  
- <span data-ttu-id="1ed4b-106">L’état de cloisonnement COM d’un thread change de manière inopinée.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-106">The COM apartment state of a thread changes unexpectedly.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1ed4b-107">Symptômes</span><span class="sxs-lookup"><span data-stu-id="1ed4b-107">Symptoms</span></span>  
  
- <span data-ttu-id="1ed4b-108">L’état de cloisonnement COM d’un thread ne correspond pas à ce qui a été demandé.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-108">A thread's COM apartment state is not what was requested.</span></span> <span data-ttu-id="1ed4b-109">Cela peut entraîner l’utilisation de proxies pour des composants COM qui ont un modèle de thread différent du modèle courant.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-109">This may cause proxies to be used for COM components that have a threading model different from the current one.</span></span> <span data-ttu-id="1ed4b-110">Cela peut également provoquer la levée d’une <xref:System.InvalidCastException> lors de l’appel de l’objet COM via des interfaces qui ne sont pas définies pour le marshaling entre cloisonnements.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-110">This in turn may cause an <xref:System.InvalidCastException> to be thrown when calling the COM object through interfaces that are not set up for cross-apartment marshaling.</span></span>  
  
- <span data-ttu-id="1ed4b-111">L’état de cloisonnement COM du thread est différent de celui qui est attendu.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-111">The COM apartment state of the thread is different than expected.</span></span> <span data-ttu-id="1ed4b-112">Cela peut provoquer une <xref:System.Runtime.InteropServices.COMException> avec la valeur HRESULT RPC_E_WRONG_THREAD ainsi qu’une <xref:System.InvalidCastException> quand des appels sont effectués sur un [wrapper RCW (Runtime Callable Wrapper)](../../standard/native-interop/runtime-callable-wrapper.md).</span><span class="sxs-lookup"><span data-stu-id="1ed4b-112">This can cause a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD as well as a <xref:System.InvalidCastException> when making calls on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="1ed4b-113">Cela peut également conduire plusieurs threads à accéder en même temps à certains composants COM à thread unique, ce qui risque d’entraîner une altération ou une perte de données.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-113">This can also cause some single-threaded COM components to be accessed by multiple threads at the same time, which can lead to corruption or data loss.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1ed4b-114">Cause</span><span class="sxs-lookup"><span data-stu-id="1ed4b-114">Cause</span></span>  
  
- <span data-ttu-id="1ed4b-115">Le thread a été précédemment initialisé à un état de cloisonnement COM différent.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-115">The thread was previously initialized to a different COM apartment state.</span></span> <span data-ttu-id="1ed4b-116">Notez que l’état de cloisonnement d’un thread peut être défini explicitement ou implicitement.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-116">Note that the apartment state of a thread can be set either explicitly or implicitly.</span></span> <span data-ttu-id="1ed4b-117">Les opérations explicites incluent la propriété <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> et les méthodes <xref:System.Threading.Thread.SetApartmentState%2A> et <xref:System.Threading.Thread.TrySetApartmentState%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-117">The explicit operations include the <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> property and the <xref:System.Threading.Thread.SetApartmentState%2A> and <xref:System.Threading.Thread.TrySetApartmentState%2A> methods.</span></span> <span data-ttu-id="1ed4b-118"><xref:System.Threading.ApartmentState.MTA> est implicitement affecté à un thread créé à l’aide de la méthode <xref:System.Threading.Thread.Start%2A>, à moins que <xref:System.Threading.Thread.SetApartmentState%2A> ne soit appelé avant le démarrage du thread.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-118">A thread created using the <xref:System.Threading.Thread.Start%2A> method is implicitly set to <xref:System.Threading.ApartmentState.MTA> unless <xref:System.Threading.Thread.SetApartmentState%2A> is called before the thread is started.</span></span> <span data-ttu-id="1ed4b-119">De même, la valeur <xref:System.Threading.ApartmentState.MTA> est implicitement affectée au thread principal de l’application, à moins que l’attribut <xref:System.STAThreadAttribute> ne soit spécifié sur la méthode principale.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-119">The main thread of the application is also implicitly initialized to <xref:System.Threading.ApartmentState.MTA> unless the <xref:System.STAThreadAttribute> attribute is specified on the main method.</span></span>  
  
- <span data-ttu-id="1ed4b-120">La méthode `CoUninitialize` (ou la méthode `CoInitializeEx`) avec un modèle de concurrence différent est appelée sur le thread.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-120">The `CoUninitialize` method (or the `CoInitializeEx` method) with a different concurrency model is called on the thread.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1ed4b-121">Résolution</span><span class="sxs-lookup"><span data-stu-id="1ed4b-121">Resolution</span></span>  

 <span data-ttu-id="1ed4b-122">Définissez l’état de cloisonnement du thread avant que son exécution ne commence ou appliquez l’attribut <xref:System.STAThreadAttribute> ou l’attribut <xref:System.MTAThreadAttribute> à la méthode principale de l’application.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-122">Set the apartment state of the thread before it begins executing, or apply either the <xref:System.STAThreadAttribute> attribute or the <xref:System.MTAThreadAttribute> attribute to the main method of the application.</span></span>  
  
 <span data-ttu-id="1ed4b-123">Dans l’idéal, pour la deuxième cause, le code qui appelle la méthode `CoUninitialize` doit être modifié pour différer l’appel jusqu’à ce que le thread soit sur le point de s’arrêter et qu’aucun des RCW ou de leurs composants COM sous-jacents ne soient encore utilisés par le thread.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-123">For the second cause, ideally, the code that calls the `CoUninitialize` method should be modified to delay the call until the thread is about to terminate and there are no RCWs and their underlying COM components still in use by the thread.</span></span> <span data-ttu-id="1ed4b-124">Toutefois, s’il est impossible de modifier le code qui appelle la méthode `CoUninitialize`, aucun RCW ne doit être utilisé par des threads non initialisés de cette façon.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-124">However, if it is not possible to modify the code that calls the `CoUninitialize` method, then no RCWs should be used from threads that are uninitialized in this way.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1ed4b-125">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="1ed4b-125">Effect on the Runtime</span></span>  

 <span data-ttu-id="1ed4b-126">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-126">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1ed4b-127">Output</span><span class="sxs-lookup"><span data-stu-id="1ed4b-127">Output</span></span>  

 <span data-ttu-id="1ed4b-128">État de cloisonnement COM du thread actuel et état que le code tentait d’appliquer.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-128">The COM apartment state of the current thread, and the state that the code was attempting to apply.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1ed4b-129">Configuration</span><span class="sxs-lookup"><span data-stu-id="1ed4b-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="1ed4b-130"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1ed4b-130">Example</span></span>  

 <span data-ttu-id="1ed4b-131">L’exemple de code suivant illustre une situation qui peut activer cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="1ed4b-131">The following code example demonstrates a situation that can activate this MDA.</span></span>  
  
```csharp
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ed4b-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ed4b-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1ed4b-133">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="1ed4b-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1ed4b-134">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="1ed4b-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
