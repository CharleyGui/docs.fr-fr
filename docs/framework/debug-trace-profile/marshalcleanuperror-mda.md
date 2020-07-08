---
title: Assistant Débogage managé marshalCleanupError
description: Passez en revue l’Assistant Débogage managé (MDA) marshalCleanupError, qui est appelé car une erreur inattendue s’est produite lors du nettoyage des structures temporaires.
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: 3c7498d6f51484de3a2e84d611a2634f53724ab6
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051608"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="63877-103">Assistant Débogage managé marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="63877-103">marshalCleanupError MDA</span></span>
<span data-ttu-id="63877-104">L’Assistant Débogage managé `marshalCleanupError` est activé quand le Common Language Runtime (CLR) rencontre une erreur pendant une tentative de nettoyage de la mémoire et des structures temporaires utilisées pour le marshaling de types de données entre des limites de code native et managé.</span><span class="sxs-lookup"><span data-stu-id="63877-104">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="63877-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="63877-105">Symptoms</span></span>  
 <span data-ttu-id="63877-106">Une fuite de mémoire se produit en cas de transitions de code natif et managé, de non-restauration d'état d'exécution tel que la culture de thread ou d'erreurs de nettoyage <xref:System.Runtime.InteropServices.SafeHandle>.</span><span class="sxs-lookup"><span data-stu-id="63877-106">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="63877-107">Cause</span><span class="sxs-lookup"><span data-stu-id="63877-107">Cause</span></span>  
 <span data-ttu-id="63877-108">Une erreur inattendue s'est produite pendant le nettoyage des structures temporaires.</span><span class="sxs-lookup"><span data-stu-id="63877-108">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="63877-109">Résolution</span><span class="sxs-lookup"><span data-stu-id="63877-109">Resolution</span></span>  
 <span data-ttu-id="63877-110">Examinez toutes les implémentations de marshaleur personnalisé, de finaliseur et de destructeur <xref:System.Runtime.InteropServices.SafeHandle> pour déterminer si elles contiennent des erreurs.</span><span class="sxs-lookup"><span data-stu-id="63877-110">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="63877-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="63877-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="63877-112">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="63877-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="63877-113">Sortie</span><span class="sxs-lookup"><span data-stu-id="63877-113">Output</span></span>  
 <span data-ttu-id="63877-114">Message indiquant l'opération ayant échoué pendant le nettoyage.</span><span class="sxs-lookup"><span data-stu-id="63877-114">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="63877-115">Configuration</span><span class="sxs-lookup"><span data-stu-id="63877-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63877-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63877-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="63877-117">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="63877-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="63877-118">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="63877-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
