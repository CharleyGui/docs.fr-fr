---
title: "Procédure : déterminer la version de découverte d'une demande Probe"
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 2b7e42714ae1d16a84bcb6f0fc79cf5b376a7a16
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595412"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="51a92-102">Procédure : déterminer la version de découverte d'une demande Probe</span><span class="sxs-lookup"><span data-stu-id="51a92-102">How to:Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="51a92-103">Un proxy de découverte peut exposer plusieurs points de terminaison de découverte à l'aide de différentes versions de découverte.</span><span class="sxs-lookup"><span data-stu-id="51a92-103">A discovery proxy may expose multiple discovery endpoints using different discovery versions.</span></span> <span data-ttu-id="51a92-104">Quand une demande de sonde de multidiffusion UDP arrive au proxy, le proxy doit répondre par un message de suppression de la multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="51a92-104">When a UDP multicast Probe request arrives at the proxy, the proxy should respond with a multicast suppression message.</span></span> <span data-ttu-id="51a92-105">Pour ce faire, il doit connaître la version de découverte de la demande.</span><span class="sxs-lookup"><span data-stu-id="51a92-105">In order to do this, it would have to know the discovery version of the request.</span></span>

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a><span data-ttu-id="51a92-106">Pour déterminer la version de découverte d'une demande Probe</span><span class="sxs-lookup"><span data-stu-id="51a92-106">To Determine the Discovery Version of a Probe Request</span></span>

<span data-ttu-id="51a92-107">Dans la méthode qui répond à une demande de sondage (par exemple <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> ), utilisez la <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> propriété statique pour rechercher un <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension> , comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="51a92-107">In the method that responds to a Probe request (for example <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>) use the static <xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType> property to search for a <xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>, as shown in the following code.</span></span>

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a><span data-ttu-id="51a92-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51a92-108">See also</span></span>

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [<span data-ttu-id="51a92-109">Implémentation d'un proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="51a92-109">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)
