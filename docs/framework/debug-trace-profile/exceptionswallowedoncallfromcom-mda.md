---
title: Assistant Débogage managé exceptionSwallowedOnCallFromCom
description: Passez en revue l’Assistant Débogage managé exceptionSwallowedOnCallFromCOM dans .NET. Cet Assistant Débogage managé se produit si une exception a été levée, mais qu’il n’existe aucun moyen de le signaler.
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 434f06cf953147d5c245e625db997bed6dbef700
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415951"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="97e83-104">Assistant Débogage managé exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="97e83-104">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="97e83-105">L'Assistant Débogage managé `exceptionSwallowedOnCallFromCOM` est activé quand une exception est levée à partir d'un code CLR (Common Language Runtime) appelé depuis COM via une méthode dépourvue de type de retour HRESULT non managé.</span><span class="sxs-lookup"><span data-stu-id="97e83-105">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="97e83-106">Symptômes</span><span class="sxs-lookup"><span data-stu-id="97e83-106">Symptoms</span></span>  
 <span data-ttu-id="97e83-107">Un appel à un composant managé depuis COM retourne la valeur FALSE ou 0.</span><span class="sxs-lookup"><span data-stu-id="97e83-107">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="97e83-108">Par ailleurs, si la méthode possède un type de retour void, la levée d'une exception pendant l'exécution de la méthode peut passer inaperçue.</span><span class="sxs-lookup"><span data-stu-id="97e83-108">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="97e83-109">Dans ce cas, l'exception est interceptée discrètement et l'appelant COM reprend la main.</span><span class="sxs-lookup"><span data-stu-id="97e83-109">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="97e83-110">Cause</span><span class="sxs-lookup"><span data-stu-id="97e83-110">Cause</span></span>  
 <span data-ttu-id="97e83-111">Une exception a été levée, mais aucune procédure valide ne permet de la signaler.</span><span class="sxs-lookup"><span data-stu-id="97e83-111">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="97e83-112">Résolution</span><span class="sxs-lookup"><span data-stu-id="97e83-112">Resolution</span></span>  
 <span data-ttu-id="97e83-113">Le message est purement informatif, et n'indique pas nécessairement la présence d'un bogue.</span><span class="sxs-lookup"><span data-stu-id="97e83-113">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="97e83-114">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="97e83-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="97e83-115">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="97e83-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="97e83-116">Il indique uniquement des informations sur les exceptions interceptées discrètement.</span><span class="sxs-lookup"><span data-stu-id="97e83-116">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="97e83-117">Output</span><span class="sxs-lookup"><span data-stu-id="97e83-117">Output</span></span>  
 <span data-ttu-id="97e83-118">Message d'information contenant le nom de la méthode, le nom du type et le message de l'exception.</span><span class="sxs-lookup"><span data-stu-id="97e83-118">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="97e83-119">Configuration</span><span class="sxs-lookup"><span data-stu-id="97e83-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97e83-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97e83-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="97e83-121">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="97e83-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="97e83-122">Marshaling d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="97e83-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
