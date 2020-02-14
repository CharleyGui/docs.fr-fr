---
title: Assistant Débogage managé invalidIUnknown
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 5df9a3f506d8c2de6f1a3125459adc2d59d510bf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217362"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="a06b6-102">Assistant Débogage managé invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="a06b6-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="a06b6-103">L'Assistant Débogage managé (MDA) `invalidIUnknown` est activé quand un pointeur `IUnknown` non valide est passé au code managé à partir du code natif.</span><span class="sxs-lookup"><span data-stu-id="a06b6-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="a06b6-104">Le pointeur `IUnknown` ne peut pas retourner un succès quand il est interrogé sur l'interface `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="a06b6-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a06b6-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="a06b6-105">Symptoms</span></span>  
 <span data-ttu-id="a06b6-106">Une erreur inattendue se produit quand un pointeur d'interface COM est marshalé pendant le marshaling d'argument.</span><span class="sxs-lookup"><span data-stu-id="a06b6-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a06b6-107">Cause :</span><span class="sxs-lookup"><span data-stu-id="a06b6-107">Cause</span></span>  
 <span data-ttu-id="a06b6-108">Une implémentation incorrecte de `QueryInterface` sur l'interface COM a été passée au CLR.</span><span class="sxs-lookup"><span data-stu-id="a06b6-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a06b6-109">Résolution</span><span class="sxs-lookup"><span data-stu-id="a06b6-109">Resolution</span></span>  
 <span data-ttu-id="a06b6-110">Corrigez l'implémentation de `QueryInterface`.</span><span class="sxs-lookup"><span data-stu-id="a06b6-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a06b6-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="a06b6-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="a06b6-112">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="a06b6-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a06b6-113">Output</span><span class="sxs-lookup"><span data-stu-id="a06b6-113">Output</span></span>  
 <span data-ttu-id="a06b6-114">Description de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="a06b6-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a06b6-115">Configuration</span><span class="sxs-lookup"><span data-stu-id="a06b6-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a06b6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a06b6-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a06b6-117">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="a06b6-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a06b6-118">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="a06b6-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
