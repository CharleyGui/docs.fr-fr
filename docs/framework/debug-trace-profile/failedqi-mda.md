---
title: Assistant Débogage managé failedQI
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 4c36ec514645a38ef1228e76bdf6dbd06e886bae
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217508"
---
# <a name="failedqi-mda"></a><span data-ttu-id="0df01-102">Assistant Débogage managé failedQI</span><span class="sxs-lookup"><span data-stu-id="0df01-102">failedQI MDA</span></span>
<span data-ttu-id="0df01-103">L'Assistant Débogage managé (MDA) `failedQI` est activé quand le runtime appelle `QueryInterface` sur un pointeur d'interface COM au nom d'un wrapper RCW et que l'appel à `QueryInterface` échoue.</span><span class="sxs-lookup"><span data-stu-id="0df01-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0df01-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="0df01-104">Symptoms</span></span>  
 <span data-ttu-id="0df01-105">Un cast sur un RCW échoue ou un appel à COM à partir d'un RCW échoue de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="0df01-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0df01-106">Cause :</span><span class="sxs-lookup"><span data-stu-id="0df01-106">Cause</span></span>  
  
- <span data-ttu-id="0df01-107">L'appel est effectué à partir du contexte incorrect.</span><span class="sxs-lookup"><span data-stu-id="0df01-107">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="0df01-108">Le proxy inscrit fait échouer l'appel à `QueryInterface`, car la tentative d'appel a été effectuée dans le contexte incorrect.</span><span class="sxs-lookup"><span data-stu-id="0df01-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="0df01-109">Un proxy détenu par OLE a retourné une erreur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0df01-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0df01-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="0df01-110">Resolution</span></span>  
 <span data-ttu-id="0df01-111">Consultez la documentation MSDN sur les règles COM.</span><span class="sxs-lookup"><span data-stu-id="0df01-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0df01-112">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="0df01-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="0df01-113">Si un appel à `QueryInterface` échoue, le contexte est changé et une nouvelle tentative d'appel à `QueryInterface` est effectuée pour déterminer si un contexte incorrect était en cause.</span><span class="sxs-lookup"><span data-stu-id="0df01-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0df01-114">Output</span><span class="sxs-lookup"><span data-stu-id="0df01-114">Output</span></span>  
 <span data-ttu-id="0df01-115">Nom managé de l'interface, GUID de l'interface et valeur HRESULT de l'échec.</span><span class="sxs-lookup"><span data-stu-id="0df01-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0df01-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="0df01-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0df01-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0df01-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0df01-118">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="0df01-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0df01-119">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="0df01-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
