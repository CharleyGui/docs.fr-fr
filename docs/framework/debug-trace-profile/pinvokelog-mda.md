---
title: Assistant Débogage managé pInvokeLog
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: 12d7f60bcaedc5a97a7718610f40188547f87050
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216132"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="f8cb2-102">Assistant Débogage managé pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="f8cb2-102">pInvokeLog MDA</span></span>
<span data-ttu-id="f8cb2-103">L’Assistant Débogage managé (MDA) `pInvokeLog` est activé pour chaque signature d’appel de code non managé unique utilisée pendant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f8cb2-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f8cb2-104">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="f8cb2-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="f8cb2-105">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="f8cb2-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f8cb2-106">Output</span><span class="sxs-lookup"><span data-stu-id="f8cb2-106">Output</span></span>  
 <span data-ttu-id="f8cb2-107">Message indiquant la signature d’appel de code non managé utilisée lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f8cb2-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f8cb2-108">Configuration</span><span class="sxs-lookup"><span data-stu-id="f8cb2-108">Configuration</span></span>  
 <span data-ttu-id="f8cb2-109">Chaque élément de correspondance filtre les fichiers .dll en fonction des appels de code non managé effectués.</span><span class="sxs-lookup"><span data-stu-id="f8cb2-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8cb2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8cb2-110">See also</span></span>

- [<span data-ttu-id="f8cb2-111">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="f8cb2-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f8cb2-112">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="f8cb2-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
