---
title: Services demande-réponse
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: f58da6f1cdaad1b976659ee2e9febe12cc07726f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991142"
---
# <a name="request-reply-services"></a><span data-ttu-id="9b023-102">Services demande-réponse</span><span class="sxs-lookup"><span data-stu-id="9b023-102">Request-Reply Services</span></span>
<span data-ttu-id="9b023-103">Les services demande-réponse sont le type de contrat d’opération par défaut dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9b023-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="9b023-104">Les clients effectuent des appels aux opérations de service et attendent une réponse du service.</span><span class="sxs-lookup"><span data-stu-id="9b023-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="9b023-105">Vous pouvez effectuer des appels à une opération de service de façon synchrone (le client se bloque jusqu'à ce qu'il reçoive une réponse du service ou que l'appel expire) ou de façon asynchrone (le client effectue un appel à l'opération de service, continue à fonctionner et reçoit la réponse du service sur un autre thread).</span><span class="sxs-lookup"><span data-stu-id="9b023-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="9b023-106">Pour créer un contrat de service demande-réponse, définissez votre contrat de service et appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque opération, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="9b023-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="9b023-107">Il n'est pas nécessaire d'affecter <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> à la propriété `false`car il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b023-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b023-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b023-108">See also</span></span>

- [<span data-ttu-id="9b023-109">Services unidirectionnels</span><span class="sxs-lookup"><span data-stu-id="9b023-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="9b023-110">Services duplex</span><span class="sxs-lookup"><span data-stu-id="9b023-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
