---
title: Assistant Débogage managé exceptionSwallowedOnCallFromCom
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 4ccb03c9a8a473c10f15b00e64810b04f21504c9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217521"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="8c846-102">Assistant Débogage managé exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="8c846-102">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="8c846-103">L'Assistant Débogage managé `exceptionSwallowedOnCallFromCOM` est activé quand une exception est levée à partir d'un code CLR (Common Language Runtime) appelé depuis COM via une méthode dépourvue de type de retour HRESULT non managé.</span><span class="sxs-lookup"><span data-stu-id="8c846-103">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8c846-104">Symptômes</span><span class="sxs-lookup"><span data-stu-id="8c846-104">Symptoms</span></span>  
 <span data-ttu-id="8c846-105">Un appel à un composant managé depuis COM retourne la valeur FALSE ou 0.</span><span class="sxs-lookup"><span data-stu-id="8c846-105">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="8c846-106">Par ailleurs, si la méthode possède un type de retour void, la levée d'une exception pendant l'exécution de la méthode peut passer inaperçue.</span><span class="sxs-lookup"><span data-stu-id="8c846-106">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="8c846-107">Dans ce cas, l'exception est interceptée discrètement et l'appelant COM reprend la main.</span><span class="sxs-lookup"><span data-stu-id="8c846-107">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8c846-108">Cause :</span><span class="sxs-lookup"><span data-stu-id="8c846-108">Cause</span></span>  
 <span data-ttu-id="8c846-109">Une exception a été levée, mais aucune procédure valide ne permet de la signaler.</span><span class="sxs-lookup"><span data-stu-id="8c846-109">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8c846-110">Résolution</span><span class="sxs-lookup"><span data-stu-id="8c846-110">Resolution</span></span>  
 <span data-ttu-id="8c846-111">Le message est purement informatif, et n'indique pas nécessairement la présence d'un bogue.</span><span class="sxs-lookup"><span data-stu-id="8c846-111">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8c846-112">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="8c846-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="8c846-113">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="8c846-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="8c846-114">Il indique uniquement des informations sur les exceptions interceptées discrètement.</span><span class="sxs-lookup"><span data-stu-id="8c846-114">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8c846-115">Output</span><span class="sxs-lookup"><span data-stu-id="8c846-115">Output</span></span>  
 <span data-ttu-id="8c846-116">Message d'information contenant le nom de la méthode, le nom du type et le message de l'exception.</span><span class="sxs-lookup"><span data-stu-id="8c846-116">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8c846-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="8c846-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c846-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c846-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="8c846-119">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="8c846-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8c846-120">Marshaling d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="8c846-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
