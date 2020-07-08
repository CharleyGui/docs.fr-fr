---
title: invalidFunctionPointerInDelegate (MDA)
description: Passez en revue l’Assistant Débogage managé (MDA) invalidFunctionPointerInDelegate, qui est appelé si un pointeur fonction non valide est passé pour créer un délégué.
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: a17427d117c62ba782af3c9549c84623a3013b06
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051738"
---
# <a name="invalidfunctionpointerindelegate-mda"></a><span data-ttu-id="5f2b3-103">invalidFunctionPointerInDelegate (MDA)</span><span class="sxs-lookup"><span data-stu-id="5f2b3-103">invalidFunctionPointerInDelegate MDA</span></span>
<span data-ttu-id="5f2b3-104">L'Assistant Débogage managé `invalidFunctionPointerInDelegate` est activé quand un pointeur de fonction non valide est transmis pour créer un délégué sur un pointeur de fonction natif.</span><span class="sxs-lookup"><span data-stu-id="5f2b3-104">The `invalidFunctionPointerInDelegate` managed debugging assistant (MDA) is activated when an invalid function pointer is passed in to construct a delegate over a native function pointer.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5f2b3-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="5f2b3-105">Symptoms</span></span>  
 <span data-ttu-id="5f2b3-106">Violations d'accès ou endommagement de mémoire inattendu pendant l'utilisation d'un délégué sur un pointeur de fonction.</span><span class="sxs-lookup"><span data-stu-id="5f2b3-106">Access violations or unexpected memory corruption when using a delegate over a function pointer.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5f2b3-107">Cause</span><span class="sxs-lookup"><span data-stu-id="5f2b3-107">Cause</span></span>  
 <span data-ttu-id="5f2b3-108">Un pointeur de fonction non valide a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="5f2b3-108">An invalid function pointer was specified.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5f2b3-109">Résolution</span><span class="sxs-lookup"><span data-stu-id="5f2b3-109">Resolution</span></span>  
 <span data-ttu-id="5f2b3-110">Spécifiez un pointeur de fonction valide.</span><span class="sxs-lookup"><span data-stu-id="5f2b3-110">Specify a valid function pointer</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5f2b3-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="5f2b3-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="5f2b3-112">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="5f2b3-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5f2b3-113">Sortie</span><span class="sxs-lookup"><span data-stu-id="5f2b3-113">Output</span></span>  
 <span data-ttu-id="5f2b3-114">Pointeur de fonction non valide.</span><span class="sxs-lookup"><span data-stu-id="5f2b3-114">The invalid function pointer.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5f2b3-115">Configuration</span><span class="sxs-lookup"><span data-stu-id="5f2b3-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f2b3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f2b3-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5f2b3-117">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="5f2b3-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5f2b3-118">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="5f2b3-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
