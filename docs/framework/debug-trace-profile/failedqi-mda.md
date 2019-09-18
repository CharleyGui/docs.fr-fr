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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fec1bfb402f3b394ceb36590c3a880f82c5cb101
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052792"
---
# <a name="failedqi-mda"></a><span data-ttu-id="a6c59-102">Assistant Débogage managé failedQI</span><span class="sxs-lookup"><span data-stu-id="a6c59-102">failedQI MDA</span></span>
<span data-ttu-id="a6c59-103">L'Assistant Débogage managé (MDA) `failedQI` est activé quand le runtime appelle `QueryInterface` sur un pointeur d'interface COM au nom d'un wrapper RCW et que l'appel à `QueryInterface` échoue.</span><span class="sxs-lookup"><span data-stu-id="a6c59-103">The `failedQI` managed debugging assistant (MDA) is activated when the runtime calls `QueryInterface` on a COM interface pointer on behalf of a runtime callable wrapper (RCW), and the `QueryInterface` call fails.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a6c59-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="a6c59-104">Symptoms</span></span>  
 <span data-ttu-id="a6c59-105">Un cast sur un RCW échoue ou un appel à COM à partir d'un RCW échoue de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="a6c59-105">A cast on an RCW fails, or a call to COM from an RCW fails unexpectedly.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a6c59-106">Cause</span><span class="sxs-lookup"><span data-stu-id="a6c59-106">Cause</span></span>  
  
- <span data-ttu-id="a6c59-107">L'appel est effectué à partir du contexte incorrect.</span><span class="sxs-lookup"><span data-stu-id="a6c59-107">The call is made from the wrong context.</span></span>  
  
- <span data-ttu-id="a6c59-108">Le proxy inscrit fait échouer l'appel à `QueryInterface`, car la tentative d'appel a été effectuée dans le contexte incorrect.</span><span class="sxs-lookup"><span data-stu-id="a6c59-108">The registered proxy is failing the `QueryInterface` call because the call was attempted in the wrong context.</span></span>  
  
- <span data-ttu-id="a6c59-109">Un proxy détenu par OLE a retourné une erreur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a6c59-109">An OLE-owned proxy returned a failure HRESULT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a6c59-110">Résolution :</span><span class="sxs-lookup"><span data-stu-id="a6c59-110">Resolution</span></span>  
 <span data-ttu-id="a6c59-111">Consultez la documentation MSDN sur les règles COM.</span><span class="sxs-lookup"><span data-stu-id="a6c59-111">See the MSDN documentation on COM rules.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a6c59-112">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="a6c59-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="a6c59-113">Si un appel à `QueryInterface` échoue, le contexte est changé et une nouvelle tentative d'appel à `QueryInterface` est effectuée pour déterminer si un contexte incorrect était en cause.</span><span class="sxs-lookup"><span data-stu-id="a6c59-113">If a `QueryInterface` call fails, the context is switched and the `QueryInterface` call is attempted again to see if an incorrect context was at fault.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a6c59-114">Sortie</span><span class="sxs-lookup"><span data-stu-id="a6c59-114">Output</span></span>  
 <span data-ttu-id="a6c59-115">Nom managé de l'interface, GUID de l'interface et valeur HRESULT de l'échec.</span><span class="sxs-lookup"><span data-stu-id="a6c59-115">The managed name of the interface, the GUID of the interface, and the HRESULT of the failure.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a6c59-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="a6c59-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6c59-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6c59-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a6c59-118">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="a6c59-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a6c59-119">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="a6c59-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
