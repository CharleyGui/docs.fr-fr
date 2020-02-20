---
title: Sécurité dans les applications gRPC-gRPC pour les développeurs WCF
description: Vue d’ensemble de l’authentification et de l’autorisation de l’appel et du canal dans gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: d5804ad5de4a834eb81b90fa1ea7a61969a0b42f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503411"
---
# <a name="security-in-grpc-applications"></a>Sécurité dans les applications gRPC

Dans tout scénario réel, il est essentiel de sécuriser les applications et les services. La sécurité couvre trois domaines clés : 

* Chiffrement du trafic réseau pour empêcher les pirates malveillants de les intercepter.
* Authentification des clients et des serveurs pour établir l’identité et l’approbation.
* Autoriser les clients à contrôler l’accès aux systèmes et appliquer des autorisations en fonction de leur identité.

> [!NOTE]
> *L’authentification* concerne l’établissement de l’identité d’un client ou d’un serveur. L' *autorisation* consiste à déterminer si un client a l’autorisation d’accéder à une ressource ou d’émettre une commande.

Ce chapitre aborde les fonctionnalités d’authentification et d’autorisation dans gRPC pour ASP.NET Core. Il aborde également la sécurité réseau via des connexions chiffrées TLS.

## <a name="wcf-authentication-and-authorization"></a>Authentification et autorisation WCF

Dans Windows Communication Foundation (WCF), l’authentification et l’autorisation ont été gérées de différentes façons, en fonction des transports et des liaisons utilisés. WCF prenait en charge différentes normes de sécurité WS-\*. Il prend également en charge l’authentification Windows pour les services HTTP qui s’exécutent dans les services IIS ou NetTCP entre les systèmes Windows.

## <a name="grpc-authentication-and-authorization"></a>authentification et autorisation gRPC

l’authentification et l’autorisation gRPC fonctionnent sur deux niveaux :

* L’authentification/autorisation au niveau de l’appel est généralement gérée par le biais de jetons appliqués dans les métadonnées lorsque l’appel est effectué. 
* L’authentification au niveau du canal utilise un certificat client qui est appliqué au niveau de la connexion. Il peut également inclure des informations d’authentification/autorisation au niveau de l’appel à appliquer automatiquement à chaque appel sur le canal. 

Vous pouvez utiliser l’un ou l’autre de ces mécanismes, ou les deux, pour vous aider à sécuriser votre service.

La ASP.NET Core implémentation de gRPC prend en charge l’authentification et l’autorisation via la plupart des mécanismes de ASP.NET Core standard :

- Appeler l’authentification
  - Azure Active Directory
  - IdentityServer
  - Jeton du porteur JWT
  - OAuth 2.0
  - OpenID Connect
  - Un certificat de fournisseur d'identité WS-Federation
- Authentification de canal
  - Certificat client

Les méthodes d’authentification d’appel sont toutes basées sur des *jetons*. La seule différence réelle est la façon dont les jetons sont générés et les bibliothèques utilisées pour valider les jetons dans le service ASP.NET Core.

Pour plus d’informations, consultez l’article [authentification et autorisation](/aspnet/core/grpc/authn-and-authz) .

> [!NOTE]
> Lorsque vous utilisez gRPC sur une connexion HTTP/2 chiffrée TLS, tout le trafic entre les clients et les serveurs est chiffré, même si vous n’utilisez pas l’authentification au niveau du canal.

Ce chapitre explique comment appliquer des informations d’identification d’appel et des informations d’identification de canal à un service gRPC. Il indique également comment utiliser les informations d’identification d’un client gRPC .NET Core pour s’authentifier auprès du service.

>[!div class="step-by-step"]
>[Précédent](client-libraries.md)
>[Suivant](call-credentials.md)
