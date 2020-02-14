---
title: Assistant Débogage managé invalidMemberDeclaration
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: 6033cd4178b2bc493794b5dcc527bc543ba24284
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216295"
---
# <a name="invalidmemberdeclaration-mda"></a><span data-ttu-id="45c83-102">Assistant Débogage managé invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="45c83-102">invalidMemberDeclaration MDA</span></span>
<span data-ttu-id="45c83-103">L’Assistant Débogage managé (MDA) `invalidMemberDeclaration` est activé pour signaler une erreur qui se produit lors de la détermination du mode de marshaling approprié pour les paramètres d’un membre à appeler à partir de l’interface COM.</span><span class="sxs-lookup"><span data-stu-id="45c83-103">The `invalidMemberDeclaration` managed debugging assistant (MDA) is activated to report an error that occurs while determining how to marshal the parameters of a member to be called from COM.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="45c83-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="45c83-104">Symptoms</span></span>  
 <span data-ttu-id="45c83-105">Une erreur HRESULT est retournée à COM sans que la méthode managée ait été appelée.</span><span class="sxs-lookup"><span data-stu-id="45c83-105">A failure HRESULT is returned to COM without the managed method having been called.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="45c83-106">Cause :</span><span class="sxs-lookup"><span data-stu-id="45c83-106">Cause</span></span>  
 <span data-ttu-id="45c83-107">Cela est probablement dû à une incompatibilité d'un attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> sur l'un des paramètres.</span><span class="sxs-lookup"><span data-stu-id="45c83-107">This is most likely due to an incompatible <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute on one of the parameters.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="45c83-108">Résolution</span><span class="sxs-lookup"><span data-stu-id="45c83-108">Resolution</span></span>  
 <span data-ttu-id="45c83-109">Spécifiez des attributs <xref:System.Runtime.InteropServices.MarshalAsAttribute> valides sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="45c83-109">Specify valid <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes on the parameters.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="45c83-110">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="45c83-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="45c83-111">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="45c83-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="45c83-112">Output</span><span class="sxs-lookup"><span data-stu-id="45c83-112">Output</span></span>  
 <span data-ttu-id="45c83-113">Message d'information contenant le nom du membre, le nom du type et le message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="45c83-113">An informational message containing the member name, type name, and error message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="45c83-114">Configuration</span><span class="sxs-lookup"><span data-stu-id="45c83-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45c83-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45c83-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="45c83-116">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="45c83-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="45c83-117">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="45c83-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
