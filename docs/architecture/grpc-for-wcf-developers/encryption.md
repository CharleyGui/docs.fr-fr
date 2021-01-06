---
title: Chiffrement et sécurité réseau-gRPC pour les développeurs WCF
description: Quelques remarques sur la sécurité réseau et le chiffrement dans gRPC
ms.date: 12/15/2020
ms.openlocfilehash: 0735158ed69ce425c4f00eed6c42689b888a1885
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938622"
---
# <a name="encryption-and-network-security"></a>Chiffrement et sécurité réseau

Le modèle de sécurité réseau pour Windows Communication Foundation (WCF) est étendu et complexe. Il comprend la sécurité au niveau du transport à l’aide de HTTPs ou TLS sur TCP, ainsi que la sécurité au niveau du message à l’aide de la spécification WS-Security pour chiffrer les messages individuels.

gRPC laisse un réseau sécurisé au protocole HTTP/2 sous-jacent, que vous pouvez sécuriser à l’aide de certificats TLS.

Les navigateurs Web insistent sur l’utilisation des connexions TLS pour HTTP/2, mais la plupart des clients de programmation, y compris. Du réseau `HttpClient` , peut utiliser le protocole http/2 sur des connexions non chiffrées. `HttpClient` requiert le chiffrement par défaut, mais vous pouvez remplacer ce comportement à l’aide d’un <xref:System.AppContext> commutateur.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Pour les API publiques, vous devez toujours utiliser des connexions TLS et fournir des certificats valides pour vos services à partir d’une autorité SSL appropriée. [LetsEncrypt](https://letsencrypt.org) fournit des certificats SSL gratuits et automatisés, et la plupart des infrastructures d’hébergement prennent aujourd’hui en charge la norme LetsEncrypt avec les plug-ins ou extensions courants.

Pour les services internes sur un réseau d’entreprise, vous devez toujours envisager d’utiliser TLS pour sécuriser le trafic réseau vers et à partir de vos services gRPC.

Si vous devez utiliser un TLS explicite entre des services s’exécutant dans Kubernetes, envisagez d’utiliser une autorité de certification en cluster et un contrôleur de gestionnaire de certificats comme [CERT-Manager](https://docs.cert-manager.io/en/latest/). Vous pouvez ensuite attribuer automatiquement des certificats aux services au moment du déploiement.

>[!div class="step-by-step"]
>[Précédent](channel-credentials.md) 
> [Suivant](grpc-in-production.md)
