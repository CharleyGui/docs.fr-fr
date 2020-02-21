---
title: Chiffrement et sécurité réseau-gRPC pour les développeurs WCF
description: Quelques remarques sur la sécurité réseau et le chiffrement dans gRPC
ms.date: 09/02/2019
ms.openlocfilehash: f8a7aeaf2a65e4ff56ac33d728e40f09a436f7a6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542766"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="5e2ce-103">Chiffrement et sécurité réseau</span><span class="sxs-lookup"><span data-stu-id="5e2ce-103">Encryption and network security</span></span>

<span data-ttu-id="5e2ce-104">Le modèle de sécurité réseau pour Windows Communication Foundation (WCF) est étendu et complexe.</span><span class="sxs-lookup"><span data-stu-id="5e2ce-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="5e2ce-105">Il comprend la sécurité au niveau du transport à l’aide de HTTPs ou TLS sur TCP, ainsi que la sécurité au niveau du message à l’aide de la spécification WS-Security pour chiffrer les messages individuels.</span><span class="sxs-lookup"><span data-stu-id="5e2ce-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="5e2ce-106">gRPC laisse un réseau sécurisé au protocole HTTP/2 sous-jacent, que vous pouvez sécuriser à l’aide de certificats TLS.</span><span class="sxs-lookup"><span data-stu-id="5e2ce-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="5e2ce-107">Les navigateurs Web insistent sur l’utilisation des connexions TLS pour HTTP/2, mais la plupart des clients de programmation, y compris. Le `HttpClient`du réseau peut utiliser le protocole HTTP/2 sur des connexions non chiffrées.</span><span class="sxs-lookup"><span data-stu-id="5e2ce-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="5e2ce-108">`HttpClient` nécessite un chiffrement par défaut, mais vous pouvez le remplacer à l’aide d’un commutateur <xref:System.AppContext>.</span><span class="sxs-lookup"><span data-stu-id="5e2ce-108">`HttpClient` does require encryption by default, but you can override this by using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="5e2ce-109">Pour les API publiques, vous devez toujours utiliser des connexions TLS et fournir des certificats valides pour vos services à partir d’une autorité SSL appropriée.</span><span class="sxs-lookup"><span data-stu-id="5e2ce-109">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="5e2ce-110">[LetsEncrypt](https://letsencrypt.org) fournit des certificats SSL gratuits et automatisés, et la plupart des infrastructures d’hébergement prennent aujourd’hui en charge la norme LetsEncrypt avec les plug-ins ou extensions courants.</span><span class="sxs-lookup"><span data-stu-id="5e2ce-110">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="5e2ce-111">Pour les services internes sur un réseau d’entreprise, vous devez toujours envisager d’utiliser TLS pour sécuriser le trafic réseau vers et à partir de vos services gRPC.</span><span class="sxs-lookup"><span data-stu-id="5e2ce-111">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="5e2ce-112">Si vous devez utiliser un TLS explicite entre des services s’exécutant dans Kubernetes, envisagez d’utiliser une autorité de certification en cluster et un contrôleur de gestionnaire de certificats comme [CERT-Manager](https://docs.cert-manager.io/en/latest/).</span><span class="sxs-lookup"><span data-stu-id="5e2ce-112">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="5e2ce-113">Vous pouvez ensuite attribuer automatiquement des certificats aux services au moment du déploiement.</span><span class="sxs-lookup"><span data-stu-id="5e2ce-113">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5e2ce-114">[Précédent](channel-credentials.md)
>[Suivant](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="5e2ce-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
