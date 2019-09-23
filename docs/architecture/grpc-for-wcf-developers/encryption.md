---
title: Chiffrement et sécurité réseau-gRPC pour les développeurs WCF
description: Quelques remarques sur la sécurité réseau et le chiffrement dans gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 8a115b59337003669b4e5436edffe239489ca79e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184462"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="03da4-103">Chiffrement et sécurité réseau</span><span class="sxs-lookup"><span data-stu-id="03da4-103">Encryption and network security</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="03da4-104">Le modèle de sécurité réseau de WCF est étendu et complexe, notamment la sécurité au niveau du transport utilisant HTTPs ou TLS sur TCP, et la sécurité au niveau du message à l’aide de la spécification WS-Security pour chiffrer les messages individuels.</span><span class="sxs-lookup"><span data-stu-id="03da4-104">WCF's network security model is extensive and complex, including transport-level security using HTTPS or TLS-over-TCP, and message-level security using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="03da4-105">gRPC laisse un réseau sécurisé au protocole HTTP/2 sous-jacent, qui peut être sécurisé à l’aide de certificats TLS standard.</span><span class="sxs-lookup"><span data-stu-id="03da4-105">gRPC leaves secure networking to the underlying HTTP/2 protocol, which can be secured using regular TLS certificates.</span></span>

<span data-ttu-id="03da4-106">Les navigateurs Web insistent sur l’utilisation des connexions TLS pour HTTP/2, mais la plupart des clients de programmation, y compris. Du `HttpClient`réseau, peut utiliser le protocole http/2 sur des connexions non chiffrées.</span><span class="sxs-lookup"><span data-stu-id="03da4-106">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="03da4-107">`HttpClient`*requiert le* chiffrement par défaut, mais vous pouvez le remplacer à l' <xref:System.AppContext> aide d’un commutateur.</span><span class="sxs-lookup"><span data-stu-id="03da4-107">`HttpClient` *does* require encryption by default, but you can override this using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="03da4-108">Pour les API publiques, vous devez toujours utiliser des connexions TLS et fournir des certificats valides pour vos services à partir d’une autorité SSL appropriée.</span><span class="sxs-lookup"><span data-stu-id="03da4-108">For public APIs, you should always use TLS connections and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="03da4-109">[LetsEncrypt](https://letsencrypt.org) fournissent des certificats SSL gratuits et automatisés, et la plupart des infrastructures d’hébergement prennent aujourd’hui en charge la norme LetsEncrypt avec les plug-ins ou extensions courants.</span><span class="sxs-lookup"><span data-stu-id="03da4-109">[LetsEncrypt](https://letsencrypt.org) provide free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="03da4-110">Pour les services internes sur un réseau d’entreprise, vous devez toujours envisager d’utiliser TLS pour sécuriser le trafic réseau vers et à partir de vos services gRPC.</span><span class="sxs-lookup"><span data-stu-id="03da4-110">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="03da4-111">La communication entre les microservices d’un cluster comme Kubernetes ou l’essaim de l’arrimeur est généralement chiffrée automatiquement par la couche de mise en réseau de conteneurs. par conséquent, il n’est pas nécessaire d’implémenter TLS dans les services exécutés exclusivement dans ce type de cluster.</span><span class="sxs-lookup"><span data-stu-id="03da4-111">Communication between microservices in a cluster like Kubernetes or Docker Swarm is in general automatically encrypted by the container networking layer, so implementing TLS in services running exclusively in such a cluster isn't necessary.</span></span> <span data-ttu-id="03da4-112">Vous trouverez plus d’informations sur ce sujet dans la section « service Mesh » du chapitre suivant.</span><span class="sxs-lookup"><span data-stu-id="03da4-112">There will be more on this subject in the "Service Mesh" section of the next chapter.</span></span>

<span data-ttu-id="03da4-113">Si vous devez utiliser un TLS explicite entre des services s’exécutant dans Kubernetes, envisagez d’utiliser une autorité de certification en cluster et un contrôleur de gestionnaire de certificats comme [CERT-Manager](https://docs.cert-manager.io/en/latest/) pour attribuer automatiquement des certificats aux services au moment du déploiement.</span><span class="sxs-lookup"><span data-stu-id="03da4-113">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster Certificate Authority and a Certificate Manager Controller like [cert-manager](https://docs.cert-manager.io/en/latest/) to assign automatically certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="03da4-114">[Précédent](channel-credentials.md)
>[Suivant](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="03da4-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
