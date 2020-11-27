---
title: Assistant Débogage managé invalidGCHandleCookie
description: Passez en revue l’Assistant Débogage managé (MDA) invalidGCHandleCookie, qui est activé lorsqu’une tentative de conversion d’un cookie IntPtr non valide en GCHandle est effectuée.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: 36806498445da78c8d9dd5c51c1903b253a39da0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272603"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="ccbf3-103">Assistant Débogage managé invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="ccbf3-103">invalidGCHandleCookie MDA</span></span>

<span data-ttu-id="ccbf3-104">L’Assistant Débogage managé `invalidGCHandleCookie` est activé quand une tentative de conversion d’un cookie <xref:System.IntPtr> non valide en un <xref:System.Runtime.InteropServices.GCHandle> est effectuée.</span><span class="sxs-lookup"><span data-stu-id="ccbf3-104">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ccbf3-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="ccbf3-105">Symptoms</span></span>  

 <span data-ttu-id="ccbf3-106">Comportement indéfini tel que les violations d’accès et l’altération de la mémoire lors des tentatives d’utilisation ou de récupération d’un <xref:System.Runtime.InteropServices.GCHandle> à partir d’un <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="ccbf3-106">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ccbf3-107">Cause</span><span class="sxs-lookup"><span data-stu-id="ccbf3-107">Cause</span></span>  

 <span data-ttu-id="ccbf3-108">Le cookie est probablement non valide, car il n’a pas été initialement créé à partir d’un <xref:System.Runtime.InteropServices.GCHandle>, représente un <xref:System.Runtime.InteropServices.GCHandle> qui a déjà été libéré, est un cookie pour un <xref:System.Runtime.InteropServices.GCHandle> dans un domaine d’application différent ou a été marshalé en code natif en tant que <xref:System.Runtime.InteropServices.GCHandle>, mais retourné au CLR en tant qu’<xref:System.IntPtr>, où une tentative de cast a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="ccbf3-108">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ccbf3-109">Résolution</span><span class="sxs-lookup"><span data-stu-id="ccbf3-109">Resolution</span></span>  

 <span data-ttu-id="ccbf3-110">Spécifiez un cookie <xref:System.IntPtr> valide pour le <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="ccbf3-110">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ccbf3-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="ccbf3-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="ccbf3-112">Quand cet Assistant Débogage managé est activé, le débogueur n’est plus en mesure de suivre les racines vers leurs objets, car les valeurs du cookie retournées sont différentes de celles retournées lorsque l’Assistant Débogage managé n’est pas activé.</span><span class="sxs-lookup"><span data-stu-id="ccbf3-112">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ccbf3-113">Output</span><span class="sxs-lookup"><span data-stu-id="ccbf3-113">Output</span></span>  

 <span data-ttu-id="ccbf3-114">La valeur du cookie <xref:System.IntPtr> non valide est signalée.</span><span class="sxs-lookup"><span data-stu-id="ccbf3-114">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ccbf3-115">Configuration</span><span class="sxs-lookup"><span data-stu-id="ccbf3-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccbf3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccbf3-116">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="ccbf3-117">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="ccbf3-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
