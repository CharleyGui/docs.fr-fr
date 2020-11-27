---
title: Assistant Débogage managé invalidVariant
description: Passez en revue l’Assistant Débogage managé invalidVariant, qui est appelé en cas de détection d’un VARIANT non valide dans un appel du code natif/non managé au code managé.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: f0667a54e950ead27000eb6b93ebd547dea1cfb0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281298"
---
# <a name="invalidvariant-mda"></a><span data-ttu-id="f8e20-103">Assistant Débogage managé invalidVariant</span><span class="sxs-lookup"><span data-stu-id="f8e20-103">invalidVariant MDA</span></span>

<span data-ttu-id="f8e20-104">L'Assistant Débogage managé (MDA) `invalidVariant` est activé quand une structure `VARIANT` non valide est rencontrée lors d'un appel du code natif ou non managé au code managé.</span><span class="sxs-lookup"><span data-stu-id="f8e20-104">The `invalidVariant` managed debugging assistant (MDA) is activated when an invalid `VARIANT` structure is encountered during a call from native or unmanaged code to managed code.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f8e20-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="f8e20-105">Symptoms</span></span>  

 <span data-ttu-id="f8e20-106">Comportement inattendu pendant une transition entre du code natif et managé impliquant le marshaling d’une structure `VARIANT` en objet.</span><span class="sxs-lookup"><span data-stu-id="f8e20-106">Unexpected behavior during a transition between native and managed code involving the marshaling of a `VARIANT` to an object.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f8e20-107">Cause</span><span class="sxs-lookup"><span data-stu-id="f8e20-107">Cause</span></span>  

 <span data-ttu-id="f8e20-108">Le code natif passe une structure `VARIANT` incorrecte au code managé.</span><span class="sxs-lookup"><span data-stu-id="f8e20-108">Native code is passing a malformed `VARIANT` structure to managed code.</span></span>  <span data-ttu-id="f8e20-109">Le runtime tente de marshaler cette `VARIANT` en objet et active l'Assistant Débogage managé si la `VARIANT` n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="f8e20-109">The runtime attempts to marshal this `VARIANT` to an object and activates the MDA if the `VARIANT` is not valid.</span></span> <span data-ttu-id="f8e20-110">Exemples de structures `VARIANT` non valides : une structure `VARIANT` avec un `VARTYPE` VT_EMPTY &#124; VT_BYREF ou une structure `VARIANT` avec le `VARTYPE` VT_VARIANT.</span><span class="sxs-lookup"><span data-stu-id="f8e20-110">Examples of invalid `VARIANT`S include a `VARIANT` with `VARTYPE` VT_EMPTY &#124; VT_BYREF or a `VARIANT` with `VARTYPE` VT_VARIANT.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f8e20-111">Résolution</span><span class="sxs-lookup"><span data-stu-id="f8e20-111">Resolution</span></span>  

 <span data-ttu-id="f8e20-112">Le code natif ou non managé qui passe la structure `VARIANT` doit s'assurer que la `VARIANT` est correcte et bien initialisée.</span><span class="sxs-lookup"><span data-stu-id="f8e20-112">The native or unmanaged code passing the `VARIANT` must ensure that the `VARIANT` is correctly formed and initialized.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f8e20-113">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="f8e20-113">Effect on the Runtime</span></span>  

 <span data-ttu-id="f8e20-114">Cet Assistant Débogage managé n'a aucun effet sur le comportement du runtime.</span><span class="sxs-lookup"><span data-stu-id="f8e20-114">The MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f8e20-115">Output</span><span class="sxs-lookup"><span data-stu-id="f8e20-115">Output</span></span>  

 <span data-ttu-id="f8e20-116">Message de l'Assistant Débogage managé indiquant que le runtime a détecté qu'une structure `VARIANT` incorrecte a été passée au code managé par un module non managé.</span><span class="sxs-lookup"><span data-stu-id="f8e20-116">An MDA message indicating that the runtime detected an invalid `VARIANT` passed to managed code by an unmanaged module.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f8e20-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="f8e20-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8e20-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8e20-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f8e20-119">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="f8e20-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f8e20-120">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="f8e20-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
