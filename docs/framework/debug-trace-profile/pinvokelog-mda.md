---
title: Assistant Débogage managé pInvokeLog
description: Comprenez l’Assistant Débogage managé (MDA) pInvokeLog, qui est activé pour chaque signature d’appel de code non managé unique utilisée pendant l’exécution dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: 05af4e17a91f7c0d8f3576a86d3d784ef6666aed
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803688"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="888ca-103">Assistant Débogage managé pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="888ca-103">pInvokeLog MDA</span></span>
<span data-ttu-id="888ca-104">L’Assistant Débogage managé (MDA) `pInvokeLog` est activé pour chaque signature d’appel de code non managé unique utilisée pendant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="888ca-104">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="888ca-105">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="888ca-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="888ca-106">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="888ca-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="888ca-107">Output</span><span class="sxs-lookup"><span data-stu-id="888ca-107">Output</span></span>  
 <span data-ttu-id="888ca-108">Message indiquant la signature d’appel de code non managé utilisée lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="888ca-108">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="888ca-109">Configuration</span><span class="sxs-lookup"><span data-stu-id="888ca-109">Configuration</span></span>  
 <span data-ttu-id="888ca-110">Chaque élément de correspondance filtre les fichiers .dll en fonction des appels de code non managé effectués.</span><span class="sxs-lookup"><span data-stu-id="888ca-110">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="888ca-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="888ca-111">See also</span></span>

- [<span data-ttu-id="888ca-112">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="888ca-112">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="888ca-113">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="888ca-113">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
