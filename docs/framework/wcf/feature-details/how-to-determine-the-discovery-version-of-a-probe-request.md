---
title: "Procédure : déterminer la version de découverte d'une demande Probe"
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8fbc3936278a5c6f403f48b59390c69c64378004
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425267"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="f42e4-102">Procédure : déterminer la version de découverte d'une demande Probe</span><span class="sxs-lookup"><span data-stu-id="f42e4-102">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="f42e4-103">Un proxy de découverte peut exposer plusieurs points de terminaison de découverte à l'aide de différentes versions de découverte.</span><span class="sxs-lookup"><span data-stu-id="f42e4-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="f42e4-104">Quand un multidiffusion UDP demande Probe arrive au niveau du proxy, celui-ci doit répondre avec un message de suppression de multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="f42e4-104">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="f42e4-105">Pour ce faire, il devra connaître la version de découverte de la demande.</span><span class="sxs-lookup"><span data-stu-id="f42e4-105">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="f42e4-106">Pour déterminer la version de découverte d'une demande Probe</span><span class="sxs-lookup"><span data-stu-id="f42e4-106">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="f42e4-107">Dans la méthode qui répond à une demande Probe (par exemple <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) utilisez la méthode statique <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> propriété à rechercher un <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f42e4-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="f42e4-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f42e4-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="f42e4-109">Implémentation d’un proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="f42e4-109">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
