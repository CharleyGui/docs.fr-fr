---
title: Assistant Débogage managé reportAvOnComRelease
description: Passez en revue l’Assistant Débogage managé (MDA) reportAvOnComRelease, qui peut être activé en raison de violations d’accès et d’une altération de la mémoire dans .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
ms.openlocfilehash: c5047aa4005cdaa9ae6aabe8dcd7ee838ee13f58
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267115"
---
# <a name="reportavoncomrelease-mda"></a><span data-ttu-id="c1b53-103">Assistant Débogage managé reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="c1b53-103">reportAvOnComRelease MDA</span></span>

<span data-ttu-id="c1b53-104">L'Assistant Débogage managé `reportAvOnComRelease` est activé quand des exceptions sont levées en raison d'erreurs de comptage de références utilisateur pendant une opération COM Interop et l'utilisation de la méthode <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinée avec des appels COM bruts.</span><span class="sxs-lookup"><span data-stu-id="c1b53-104">The `reportAvOnComRelease` managed debugging assistant (MDA) is activated when exceptions are thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c1b53-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="c1b53-105">Symptoms</span></span>  

 <span data-ttu-id="c1b53-106">Violations d'accès et endommagement de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="c1b53-106">Access violations and memory corruption.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c1b53-107">Cause</span><span class="sxs-lookup"><span data-stu-id="c1b53-107">Cause</span></span>  

 <span data-ttu-id="c1b53-108">Parfois, une exception est levée en raison d'erreurs de comptage de références utilisateur pendant une opération COM Interop et l'utilisation de la méthode <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinée avec des appels COM bruts.</span><span class="sxs-lookup"><span data-stu-id="c1b53-108">Occasionally, an exception is thrown due to user reference counting errors while performing COM interop and using the <xref:System.Runtime.InteropServices.Marshal.Release%2A> or <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> method combined with raw COM calls.</span></span> <span data-ttu-id="c1b53-109">Normalement, cette exception est ignorée, car elle entraînerait une violation d'accès dans le CLR et l'arrêt de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="c1b53-109">Normally, this exception is discarded because not doing so would cause an access violation in the CLR, bringing it down.</span></span> <span data-ttu-id="c1b53-110">Quand cet Assistant est activé, les exceptions de ce type peuvent être détectées et signalées au lieu d'être simplement ignorées.</span><span class="sxs-lookup"><span data-stu-id="c1b53-110">When this assistant is enabled, such exceptions can be detected and reported instead of being simply discarded.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c1b53-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="c1b53-111">Resolution</span></span>  

 <span data-ttu-id="c1b53-112">Examinez votre code de comptage de références, ainsi que les clients natifs de votre objet pour déterminer s'ils contiennent des erreurs de comptage.</span><span class="sxs-lookup"><span data-stu-id="c1b53-112">Examine your reference counting code and search for errors as well as examining the native clients of your object for reference counting errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c1b53-113">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="c1b53-113">Effect on the Runtime</span></span>  

 <span data-ttu-id="c1b53-114">Deux modes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="c1b53-114">Two modes are available.</span></span> <span data-ttu-id="c1b53-115">Si l'attribut `allowAv` a pour valeur `true`, l'Assistant empêche le runtime d'ignorer la violation d'accès.</span><span class="sxs-lookup"><span data-stu-id="c1b53-115">If the `allowAv` attribute is `true`, the assistant prevents the runtime from discarding the access violation.</span></span> <span data-ttu-id="c1b53-116">Si l'attribut `allowAv` est défini sur `false` (valeur par défaut), le runtime ignore la violation d'accès, mais un message d'avertissement est présenté à l'utilisateur pour indiquer qu'une exception a été levée et ignorée.</span><span class="sxs-lookup"><span data-stu-id="c1b53-116">If `allowAv` is `false`, which is the default, the runtime discards the access violation, but a warning message is reported to the user to indicate that an exception was thrown and discarded.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c1b53-117">Output</span><span class="sxs-lookup"><span data-stu-id="c1b53-117">Output</span></span>  

 <span data-ttu-id="c1b53-118">Si possible, la sortie contient le vtable d'origine du pointeur d'interface COM.</span><span class="sxs-lookup"><span data-stu-id="c1b53-118">If possible, the output contains the COM interface pointer's original vtable.</span></span> <span data-ttu-id="c1b53-119">Sinon, un message d'information apparaît.</span><span class="sxs-lookup"><span data-stu-id="c1b53-119">Otherwise, an informational message is displayed.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c1b53-120">Configuration</span><span class="sxs-lookup"><span data-stu-id="c1b53-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1b53-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1b53-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c1b53-122">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="c1b53-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c1b53-123">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="c1b53-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
