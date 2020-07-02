---
title: notMarshalable (MDA)
description: Passez en revue l’Assistant Débogage managé notMarshalable, qui peut activer si les appels ne sont pas pris en service ou se produire dans le contexte incorrect pour les pointeurs d’interface COM.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
ms.openlocfilehash: b464d914a8d83504daaf4cb276914da7798262dc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803792"
---
# <a name="notmarshalable-mda"></a><span data-ttu-id="6c98f-103">notMarshalable (MDA)</span><span class="sxs-lookup"><span data-stu-id="6c98f-103">notMarshalable MDA</span></span>
<span data-ttu-id="6c98f-104">L’Assistant Débogage managé (MDA) `notMarshalable` est activé lorsque le Common Language Runtime (CLR) rencontre un pointeur d’interface COM sans proxy/stub inscrit valide ou une implémentation d’interface `IMarshal` incorrecte lors d’une tentative de marshaling de l’interface entre plusieurs contextes.</span><span class="sxs-lookup"><span data-stu-id="6c98f-104">The `notMarshalable` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters a COM interface pointer without a valid registered proxy/stub or an incorrect `IMarshal` interface implementation while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6c98f-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="6c98f-105">Symptoms</span></span>  
 <span data-ttu-id="6c98f-106">Les appels ne sont pas traités ou ils se produisent dans le contexte incorrect pour les pointeurs d'interface COM.</span><span class="sxs-lookup"><span data-stu-id="6c98f-106">Calls are not serviced, or calls occur in the wrong context for COM interface pointers.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6c98f-107">Cause</span><span class="sxs-lookup"><span data-stu-id="6c98f-107">Cause</span></span>  
 <span data-ttu-id="6c98f-108">Absence de proxy/stub inscrit valide ou présence d’une interface `IMarshal` incorrecte lors d’une tentative de marshaling de l’interface entre plusieurs contextes.</span><span class="sxs-lookup"><span data-stu-id="6c98f-108">No valid registered proxy/stub or an incorrect `IMarshal` while attempting to marshal the interface across contexts.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6c98f-109">Résolution</span><span class="sxs-lookup"><span data-stu-id="6c98f-109">Resolution</span></span>  
 <span data-ttu-id="6c98f-110">Assurez-vous que vous avez un stub/proxy inscrit et que l'implémentation de `IMarshal` est correcte.</span><span class="sxs-lookup"><span data-stu-id="6c98f-110">Make sure you have a proxy stub registered and that the `IMarshal` implementation is valid.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6c98f-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="6c98f-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="6c98f-112">Cet Assistant Débogage managé n'a aucun effet sur le runtime.</span><span class="sxs-lookup"><span data-stu-id="6c98f-112">This MDA has no effect on the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6c98f-113">Output</span><span class="sxs-lookup"><span data-stu-id="6c98f-113">Output</span></span>  
 <span data-ttu-id="6c98f-114">Message décrivant le problème.</span><span class="sxs-lookup"><span data-stu-id="6c98f-114">A message describing the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6c98f-115">Configuration</span><span class="sxs-lookup"><span data-stu-id="6c98f-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c98f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c98f-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="6c98f-117">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="6c98f-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6c98f-118">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="6c98f-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
