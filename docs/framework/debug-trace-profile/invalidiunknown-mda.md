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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea7f48ab61c16cb0430717074f1b1feab4827763
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052591"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="d72f2-102">Assistant Débogage managé invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="d72f2-102">invalidIUnknown MDA</span></span>
<span data-ttu-id="d72f2-103">L'Assistant Débogage managé (MDA) `invalidIUnknown` est activé quand un pointeur `IUnknown` non valide est passé au code managé à partir du code natif.</span><span class="sxs-lookup"><span data-stu-id="d72f2-103">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="d72f2-104">Le pointeur `IUnknown` ne peut pas retourner un succès quand il est interrogé sur l'interface `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="d72f2-104">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="d72f2-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="d72f2-105">Symptoms</span></span>  
 <span data-ttu-id="d72f2-106">Une erreur inattendue se produit quand un pointeur d'interface COM est marshalé pendant le marshaling d'argument.</span><span class="sxs-lookup"><span data-stu-id="d72f2-106">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="d72f2-107">Cause</span><span class="sxs-lookup"><span data-stu-id="d72f2-107">Cause</span></span>  
 <span data-ttu-id="d72f2-108">Une implémentation incorrecte de `QueryInterface` sur l'interface COM a été passée au CLR.</span><span class="sxs-lookup"><span data-stu-id="d72f2-108">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="d72f2-109">Résolution :</span><span class="sxs-lookup"><span data-stu-id="d72f2-109">Resolution</span></span>  
 <span data-ttu-id="d72f2-110">Corrigez l'implémentation de `QueryInterface`.</span><span class="sxs-lookup"><span data-stu-id="d72f2-110">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d72f2-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="d72f2-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="d72f2-112">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="d72f2-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d72f2-113">Sortie</span><span class="sxs-lookup"><span data-stu-id="d72f2-113">Output</span></span>  
 <span data-ttu-id="d72f2-114">Description de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="d72f2-114">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d72f2-115">Configuration</span><span class="sxs-lookup"><span data-stu-id="d72f2-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d72f2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d72f2-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d72f2-117">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="d72f2-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d72f2-118">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d72f2-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
