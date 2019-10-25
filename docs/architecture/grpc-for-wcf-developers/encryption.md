---
title: Chiffrement et sécurité réseau-gRPC pour les développeurs WCF
description: Quelques remarques sur la sécurité réseau et le chiffrement dans gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 67ee1ffaf00ea0cc6b771ede9f49b6a691af0968
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846675"
---
# <a name="encryption-and-network-security"></a>Chiffrement et sécurité réseau

Le modèle de sécurité réseau de WCF est étendu et complexe, notamment la sécurité au niveau du transport utilisant HTTPs ou TLS sur TCP, et la sécurité au niveau du message à l’aide de la spécification WS-Security pour chiffrer les messages individuels.

gRPC laisse un réseau sécurisé au protocole HTTP/2 sous-jacent, qui peut être sécurisé à l’aide de certificats TLS standard.

Les navigateurs Web insistent sur l’utilisation des connexions TLS pour HTTP/2, mais la plupart des clients de programmation, y compris. Le `HttpClient`du réseau peut utiliser le protocole HTTP/2 sur des connexions non chiffrées. `HttpClient` *nécessite* un chiffrement par défaut, mais vous pouvez le remplacer à l’aide d’un commutateur <xref:System.AppContext>.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Pour les API publiques, vous devez toujours utiliser des connexions TLS et fournir des certificats valides pour vos services à partir d’une autorité SSL appropriée. [LetsEncrypt](https://letsencrypt.org) fournissent des certificats SSL gratuits et automatisés, et la plupart des infrastructures d’hébergement prennent aujourd’hui en charge la norme LetsEncrypt avec les plug-ins ou extensions courants.

Pour les services internes sur un réseau d’entreprise, vous devez toujours envisager d’utiliser TLS pour sécuriser le trafic réseau vers et à partir de vos services gRPC.

La communication entre les microservices d’un cluster comme Kubernetes ou l’essaim de l’arrimeur est généralement chiffrée automatiquement par la couche de mise en réseau de conteneurs. par conséquent, il n’est pas nécessaire d’implémenter TLS dans les services exécutés exclusivement dans ce type de cluster. Vous trouverez plus d’informations sur ce sujet dans la section « service Mesh » du chapitre suivant.

Si vous devez utiliser un TLS explicite entre des services s’exécutant dans Kubernetes, envisagez d’utiliser une autorité de certification en cluster et un contrôleur de gestionnaire de certificats comme [CERT-Manager](https://docs.cert-manager.io/en/latest/) pour attribuer automatiquement des certificats aux services au moment du déploiement.

>[!div class="step-by-step"]
>[Précédent](channel-credentials.md)
>[Suivant](grpc-in-production.md)
