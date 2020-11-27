---
title: Assistant Débogage managé invalidMemberDeclaration
description: Passez en revue l’Assistant Débogage managé invalidMemberDeclaration, appelé si un HRESULT d’échec est retourné à COM sans appeler la méthode managée.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: c8d6c69fc6eb4f5f690b02809fdc492da675c3b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272551"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="18739-103">Assistant Débogage managé invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="18739-103">invalidMemberDeclaration MDA</span></span>

<span data-ttu-id="18739-104">L’Assistant Débogage managé (MDA) `invalidMemberDeclaration` est activé pour signaler une erreur qui se produit lors de la détermination du mode de marshaling approprié pour les paramètres d’un membre à appeler à partir de l’interface COM.</span><span class="sxs-lookup"><span data-stu-id="18739-104">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="18739-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="18739-105">Symptoms</span></span>  

 <span data-ttu-id="18739-106">Une erreur HRESULT est retournée à COM sans que la méthode managée ait été appelée.</span><span class="sxs-lookup"><span data-stu-id="18739-106">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="18739-107">Cause</span><span class="sxs-lookup"><span data-stu-id="18739-107">Cause</span></span>  

 <span data-ttu-id="18739-108">Cela est probablement dû à une incompatibilité d'un attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> sur l'un des paramètres.</span><span class="sxs-lookup"><span data-stu-id="18739-108">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="18739-109">Résolution</span><span class="sxs-lookup"><span data-stu-id="18739-109">Resolution</span></span>  

 <span data-ttu-id="18739-110">Spécifiez des attributs <xref:System.Runtime.InteropServices.MarshalAsAttribute> valides sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="18739-110">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="18739-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="18739-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="18739-112">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="18739-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="18739-113">Output</span><span class="sxs-lookup"><span data-stu-id="18739-113">Output</span></span>  

 <span data-ttu-id="18739-114">Message d'information contenant le nom du membre, le nom du type et le message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="18739-114">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="18739-115">Configuration</span><span class="sxs-lookup"><span data-stu-id="18739-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18739-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18739-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="18739-117">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="18739-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="18739-118">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="18739-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
