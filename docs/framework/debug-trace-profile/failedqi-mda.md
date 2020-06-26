---
title: Assistant Débogage managé failedQI
description: Passez en revue l’Assistant Débogage managé (MDA) failedQI dans .NET, qui peut être activé lorsqu’un cast sur un appel COM ou un appel COM à partir d’un wrapper RCW (Runtime Callable Wrapper) échoue.
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 2d7f14c67d47e58bcb88eab4621df63d7c598a7a
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415938"
---
# <a name="failedqi-mda"></a><span data-ttu-id="4ca8a-103">Assistant Débogage managé failedQI</span><span class="sxs-lookup"><span data-stu-id="4ca8a-103">failedQI MDA</span></span>
<span data-ttu-id="4ca8a-104">L'Assistant Débogage managé (MDA) `failedQI` est activé quand le runtime appelle `QueryInterface` sur un pointeur d'interface COM au nom d'un wrapper RCW et que l'appel à `QueryInterface` échoue.</span><span class="sxs-lookup"><span data-stu-id="4ca8a-104">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4ca8a-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="4ca8a-105">Symptoms</span></span>  
 <span data-ttu-id="4ca8a-106">Un cast sur un RCW échoue ou un appel à COM à partir d'un RCW échoue de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="4ca8a-106">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4ca8a-107">Cause</span><span class="sxs-lookup"><span data-stu-id="4ca8a-107">Cause</span></span>  
  
- <span data-ttu-id="4ca8a-108">L'appel est effectué à partir du contexte incorrect.</span><span class="sxs-lookup"><span data-stu-id="4ca8a-108">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="4ca8a-109">Le proxy inscrit fait échouer l'appel à `QueryInterface`, car la tentative d'appel a été effectuée dans le contexte incorrect.</span><span class="sxs-lookup"><span data-stu-id="4ca8a-109">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="4ca8a-110">Un proxy détenu par OLE a retourné une erreur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="4ca8a-110">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4ca8a-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="4ca8a-111">Resolution</span></span>  
 <span data-ttu-id="4ca8a-112">Consultez la documentation MSDN sur les règles COM.</span><span class="sxs-lookup"><span data-stu-id="4ca8a-112">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4ca8a-113">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="4ca8a-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="4ca8a-114">Si un appel à `QueryInterface` échoue, le contexte est changé et une nouvelle tentative d'appel à `QueryInterface` est effectuée pour déterminer si un contexte incorrect était en cause.</span><span class="sxs-lookup"><span data-stu-id="4ca8a-114">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4ca8a-115">Output</span><span class="sxs-lookup"><span data-stu-id="4ca8a-115">Output</span></span>  
 <span data-ttu-id="4ca8a-116">Nom managé de l'interface, GUID de l'interface et valeur HRESULT de l'échec.</span><span class="sxs-lookup"><span data-stu-id="4ca8a-116">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4ca8a-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="4ca8a-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ca8a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ca8a-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="4ca8a-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="4ca8a-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4ca8a-120">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="4ca8a-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
