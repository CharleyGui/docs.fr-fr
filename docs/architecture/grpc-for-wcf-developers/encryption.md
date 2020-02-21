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
# <a name="encryption-and-network-security"></a>Chiffrement et sécurité réseau

Le modèle de sécurité réseau pour Windows Communication Foundation (WCF) est étendu et complexe. Il comprend la sécurité au niveau du transport à l’aide de HTTPs ou TLS sur TCP, ainsi que la sécurité au niveau du message à l’aide de la spécification WS-Security pour chiffrer les messages individuels.

gRPC laisse un réseau sécurisé au protocole HTTP/2 sous-jacent, que vous pouvez sécuriser à l’aide de certificats TLS.

Les navigateurs Web insistent sur l’utilisation des connexions TLS pour HTTP/2, mais la plupart des clients de programmation, y compris. Le `HttpClient`du réseau peut utiliser le protocole HTTP/2 sur des connexions non chiffrées. `HttpClient` nécessite un chiffrement par défaut, mais vous pouvez le remplacer à l’aide d’un commutateur <xref:System.AppContext>.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Pour les API publiques, vous devez toujours utiliser des connexions TLS et fournir des certificats valides pour vos services à partir d’une autorité SSL appropriée. [LetsEncrypt](https://letsencrypt.org) fournit des certificats SSL gratuits et automatisés, et la plupart des infrastructures d’hébergement prennent aujourd’hui en charge la norme LetsEncrypt avec les plug-ins ou extensions courants.

Pour les services internes sur un réseau d’entreprise, vous devez toujours envisager d’utiliser TLS pour sécuriser le trafic réseau vers et à partir de vos services gRPC.

Si vous devez utiliser un TLS explicite entre des services s’exécutant dans Kubernetes, envisagez d’utiliser une autorité de certification en cluster et un contrôleur de gestionnaire de certificats comme [CERT-Manager](https://docs.cert-manager.io/en/latest/). Vous pouvez ensuite attribuer automatiquement des certificats aux services au moment du déploiement.

>[!div class="step-by-step"]
>[Précédent](channel-credentials.md)
>[Suivant](grpc-in-production.md)
