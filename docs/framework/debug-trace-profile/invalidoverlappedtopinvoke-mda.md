---
title: Assistant Débogage managé invalidOverlappedToPinvoke
description: Passez en revue l’Assistant Débogage managé (MDA) invalidOverlappedToPinvoke dans .NET, qui peut être activé pendant un incident ou une altération inexpliquée du tas.
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
ms.openlocfilehash: 162efd55bf636cf2e8698706bd011379f2f6f11f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051699"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="d7baf-103">Assistant Débogage managé invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="d7baf-103">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="d7baf-104">L’Assistant Débogage managé `invalidOverlappedToPinvoke` est activé quand un pointeur superposé qui n’a pas été créé sur le tas du garbage collection est passé à des fonctions Win32 spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d7baf-104">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7baf-105">Par défaut, cet Assistant Débogage managé est activé uniquement si l’appel de code non managé est défini dans votre code et que le débogueur signale l’état JustMyCode de chaque méthode.</span><span class="sxs-lookup"><span data-stu-id="d7baf-105">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="d7baf-106">Un débogueur qui ne comprend pas JustMyCode (tel que MDbg.exe sans extension) n’activera pas cet Assistant.</span><span class="sxs-lookup"><span data-stu-id="d7baf-106">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="d7baf-107">Il peut être activé pour ces débogueurs en utilisant un fichier de configuration et en définissant explicitement `justMyCode="false"` dans le fichier de configuration .mda `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span><span class="sxs-lookup"><span data-stu-id="d7baf-107">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d7baf-108">Symptômes</span><span class="sxs-lookup"><span data-stu-id="d7baf-108">Symptoms</span></span>  
 <span data-ttu-id="d7baf-109">Incidents ou altérations de tas inexplicables.</span><span class="sxs-lookup"><span data-stu-id="d7baf-109">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d7baf-110">Cause</span><span class="sxs-lookup"><span data-stu-id="d7baf-110">Cause</span></span>  
 <span data-ttu-id="d7baf-111">Un pointeur superposé qui n’a pas été créé sur le tas du garbage collection est passé à des fonctions spécifiques du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="d7baf-111">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="d7baf-112">Le tableau suivant répertorie les fonctions dont cet Assistant Débogage managé assure le suivi.</span><span class="sxs-lookup"><span data-stu-id="d7baf-112">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="d7baf-113">Module</span><span class="sxs-lookup"><span data-stu-id="d7baf-113">Module</span></span>|<span data-ttu-id="d7baf-114">Fonction</span><span class="sxs-lookup"><span data-stu-id="d7baf-114">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="d7baf-115">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-115">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="d7baf-116">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-116">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="d7baf-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-117">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="d7baf-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-118">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="d7baf-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-119">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="d7baf-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-120">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="d7baf-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-121">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="d7baf-122">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-122">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="d7baf-123">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-123">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="d7baf-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-124">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="d7baf-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-125">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="d7baf-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-126">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="d7baf-127">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-127">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="d7baf-128">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="d7baf-128">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="d7baf-129">Le risque d’altération de tas est élevé pour cette condition, car l’<xref:System.AppDomain> effectuant l’appel peut être déchargé.</span><span class="sxs-lookup"><span data-stu-id="d7baf-129">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="d7baf-130">En cas de déchargement d’<xref:System.AppDomain>, soit le code d’application libérera de la mémoire pour le pointeur superposé, donnant lieu à une altération au terme de l’opération, soit le code provoquera une fuite de mémoire, entraînant des problèmes ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="d7baf-130">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d7baf-131">Résolution</span><span class="sxs-lookup"><span data-stu-id="d7baf-131">Resolution</span></span>  
 <span data-ttu-id="d7baf-132">Utilisez un objet <xref:System.Threading.Overlapped>, appelant la méthode <xref:System.Threading.Overlapped.Pack%2A> pour obtenir une structure <xref:System.Threading.NativeOverlapped> qui peut être passée à la fonction.</span><span class="sxs-lookup"><span data-stu-id="d7baf-132">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="d7baf-133">Si l’<xref:System.AppDomain> est déchargé, le CLR (Common Language Runtime) attend la fin de l’opération asynchrone avant de libérer le pointeur.</span><span class="sxs-lookup"><span data-stu-id="d7baf-133">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d7baf-134">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="d7baf-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="d7baf-135">Cet Assistant Débogage managé n’a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="d7baf-135">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d7baf-136">Sortie</span><span class="sxs-lookup"><span data-stu-id="d7baf-136">Output</span></span>  
 <span data-ttu-id="d7baf-137">L’exemple suivant illustre une sortie de cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="d7baf-137">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="d7baf-138">Configuration</span><span class="sxs-lookup"><span data-stu-id="d7baf-138">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7baf-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7baf-139">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d7baf-140">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="d7baf-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d7baf-141">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d7baf-141">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
