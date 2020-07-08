---
title: Assistant Débogage managé invalidIUnknown
description: Passez en revue l’Assistant Débogage managé invalidIUnknown (MDA) qui est activé quand un pointeur IUnknown non valide est passé au code managé à partir du code natif.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 65d704463ed746390ff1710b590bf080013bf53d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051725"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="7e8d2-103">Assistant Débogage managé invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="7e8d2-103">invalidIUnknown MDA</span></span>
<span data-ttu-id="7e8d2-104">L'Assistant Débogage managé (MDA) `invalidIUnknown` est activé quand un pointeur `IUnknown` non valide est passé au code managé à partir du code natif.</span><span class="sxs-lookup"><span data-stu-id="7e8d2-104">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="7e8d2-105">Le pointeur `IUnknown` ne peut pas retourner un succès quand il est interrogé sur l'interface `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="7e8d2-105">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7e8d2-106">Symptômes</span><span class="sxs-lookup"><span data-stu-id="7e8d2-106">Symptoms</span></span>  
 <span data-ttu-id="7e8d2-107">Une erreur inattendue se produit quand un pointeur d'interface COM est marshalé pendant le marshaling d'argument.</span><span class="sxs-lookup"><span data-stu-id="7e8d2-107">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7e8d2-108">Cause</span><span class="sxs-lookup"><span data-stu-id="7e8d2-108">Cause</span></span>  
 <span data-ttu-id="7e8d2-109">Une implémentation incorrecte de `QueryInterface` sur l'interface COM a été passée au CLR.</span><span class="sxs-lookup"><span data-stu-id="7e8d2-109">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7e8d2-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="7e8d2-110">Resolution</span></span>  
 <span data-ttu-id="7e8d2-111">Corrigez l'implémentation de `QueryInterface`.</span><span class="sxs-lookup"><span data-stu-id="7e8d2-111">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7e8d2-112">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="7e8d2-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="7e8d2-113">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="7e8d2-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7e8d2-114">Sortie</span><span class="sxs-lookup"><span data-stu-id="7e8d2-114">Output</span></span>  
 <span data-ttu-id="7e8d2-115">Description de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="7e8d2-115">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7e8d2-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="7e8d2-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e8d2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e8d2-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7e8d2-118">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="7e8d2-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7e8d2-119">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="7e8d2-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
