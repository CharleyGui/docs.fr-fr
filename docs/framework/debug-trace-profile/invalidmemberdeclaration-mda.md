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
ms.openlocfilehash: 5dbfba2baec3263d91746c06379438e97a81f005
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051712"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="bc1a7-103">Assistant Débogage managé invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="bc1a7-103">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="bc1a7-104">L’Assistant Débogage managé (MDA) `invalidMemberDeclaration` est activé pour signaler une erreur qui se produit lors de la détermination du mode de marshaling approprié pour les paramètres d’un membre à appeler à partir de l’interface COM.</span><span class="sxs-lookup"><span data-stu-id="bc1a7-104">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bc1a7-105">Symptômes</span><span class="sxs-lookup"><span data-stu-id="bc1a7-105">Symptoms</span></span>  
 <span data-ttu-id="bc1a7-106">Une erreur HRESULT est retournée à COM sans que la méthode managée ait été appelée.</span><span class="sxs-lookup"><span data-stu-id="bc1a7-106">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bc1a7-107">Cause</span><span class="sxs-lookup"><span data-stu-id="bc1a7-107">Cause</span></span>  
 <span data-ttu-id="bc1a7-108">Cela est probablement dû à une incompatibilité d'un attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> sur l'un des paramètres.</span><span class="sxs-lookup"><span data-stu-id="bc1a7-108">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bc1a7-109">Résolution</span><span class="sxs-lookup"><span data-stu-id="bc1a7-109">Resolution</span></span>  
 <span data-ttu-id="bc1a7-110">Spécifiez des attributs <xref:System.Runtime.InteropServices.MarshalAsAttribute> valides sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="bc1a7-110">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bc1a7-111">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="bc1a7-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="bc1a7-112">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="bc1a7-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bc1a7-113">Sortie</span><span class="sxs-lookup"><span data-stu-id="bc1a7-113">Output</span></span>  
 <span data-ttu-id="bc1a7-114">Message d'information contenant le nom du membre, le nom du type et le message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="bc1a7-114">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bc1a7-115">Configuration</span><span class="sxs-lookup"><span data-stu-id="bc1a7-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc1a7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc1a7-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="bc1a7-117">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="bc1a7-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="bc1a7-118">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="bc1a7-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
