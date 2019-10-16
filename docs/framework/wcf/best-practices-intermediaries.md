---
title: 'Meilleures pratiques : Intermédiaires'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: a7c037b5942a404b1ff790638979a8e430394151
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320796"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="4fd2a-102">Meilleures pratiques : Intermédiaires</span><span class="sxs-lookup"><span data-stu-id="4fd2a-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="4fd2a-103">La prudence est de mise pour une gestion correcte des erreurs lors de l'appel des intermédiaires afin de s'assurer que les canaux du côté service sur l'intermédiaire sont fermés.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="4fd2a-104">Prenons le scénario suivant :</span><span class="sxs-lookup"><span data-stu-id="4fd2a-104">Consider the following scenario.</span></span> <span data-ttu-id="4fd2a-105">Un client appelle un intermédiaire qui appelle un service principal.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="4fd2a-106">Le service principal ne définit pas de contrat d'erreur ; par conséquent, les erreurs détectées par ce service seront traitées comme une erreur non typée.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="4fd2a-107">Le service principal lève une <xref:System.ApplicationException> et WCF abandonne correctement le canal côté service.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="4fd2a-108"><xref:System.ApplicationException> apparaît ensuite en tant qu'exception <xref:System.ServiceModel.FaultException> levée sur l'intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="4fd2a-109">L'intermédiaire relève l'exception <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="4fd2a-110">WCF interprète cette erreur comme une erreur non typée de l'intermédiaire et la transfère au client.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="4fd2a-111">Lors de la réception de l'erreur, l'intermédiaire et le client entraînent la défaillance de leurs canaux côté client.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="4fd2a-112">Le canal côté service de l'intermédiaire reste cependant ouvert, car WCF ignore que l'erreur est irrécupérable.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="4fd2a-113">La meilleure pratique dans ce scénario consiste à détecter si l'erreur provenant du service est irrécupérable, et le cas échéant, si l'intermédiaire doit provoquer une défaillance de son canal côté service comme l'illustre l'extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4fd2a-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fd2a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fd2a-114">See also</span></span>

- [<span data-ttu-id="4fd2a-115">Gestion des erreurs WCF</span><span class="sxs-lookup"><span data-stu-id="4fd2a-115">WCF Error Handling</span></span>](wcf-error-handling.md)
- [<span data-ttu-id="4fd2a-116">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="4fd2a-116">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
