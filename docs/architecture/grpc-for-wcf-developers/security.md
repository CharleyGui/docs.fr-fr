---
title: Sécurité dans les applications gRPC - gRPC pour les développeurs WCF
description: Aperçu de l’authentification et de l’autorisation des appels et des canaux dans gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 70cbf441bbc1b299b997f7d1f02bcd2bf7fde60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147813"
---
# <a name="security-in-grpc-applications"></a>Sécurité dans les applications gRPC

Dans n’importe quel scénario réel, il est essentiel de sécuriser les applications et les services. La sécurité couvre trois domaines clés :

* Chiffrer le trafic réseau pour empêcher les pirates malveillants de l’intercepter.
* Authentifier les clients et les serveurs pour établir l’identité et la confiance.
* Autoriser les clients à contrôler l’accès aux systèmes et à appliquer des autorisations basées sur l’identité.

> [!NOTE]
> *L’authentification* vise à établir l’identité d’un client ou d’un serveur. *L’autorisation* vise à déterminer si un client a la permission d’accéder à une ressource ou d’émettre une commande.

Ce chapitre couvrira les installations d’authentification et d’autorisation en gRPC pour ASP.NET Core. Il discutera également de la sécurité du réseau par le biais de connexions cryptées TLS.

## <a name="wcf-authentication-and-authorization"></a>Authentification et autorisation de la WCF

Dans Windows Communication Foundation (WCF), l’authentification et l’autorisation ont été traitées de différentes manières, en fonction des transports et des liaisons utilisées. WCF a soutenu\* diverses normes de sécurité WS. Il a également pris en charge l’authentification de Windows pour les services HTTP exécutant dans les services IIS ou NetTCP entre les systèmes Windows.

## <a name="grpc-authentication-and-authorization"></a>gRPC authentification et autorisation

gRPC authentification et autorisation fonctionne sur deux niveaux :

* L’authentification/autorisation au niveau des appels est généralement traitée par des jetons qui sont appliqués dans les métadonnées lorsque l’appel est effectué.
* L’authentification au niveau des canaux utilise un certificat client qui est appliqué au niveau de connexion. Il peut également inclure des informations d’authentification/autorisation au niveau des appels à appliquer automatiquement à chaque appel sur le canal.

Vous pouvez utiliser l’un ou l’autre ou les deux de ces mécanismes pour vous aider à sécuriser votre service.

La mise en œuvre de base ASP.NET de gRPC prend en charge l’authentification et l’autorisation par la plupart des mécanismes ASP.NET de base standard :

- Appel authentification
  - Azure Active Directory
  - IdentityServer
  - Jeton de porteur de JWT
  - OAuth 2.0
  - OpenID Connect
  - Un certificat de fournisseur d'identité WS-Federation
- Authentification des canaux
  - Certificat client

Les méthodes d’authentification d’appel sont toutes basées sur *des jetons.* La seule vraie différence est la façon dont les jetons sont générés et les bibliothèques qui sont utilisées pour valider les jetons dans le service ASP.NET Core.

Pour plus d’informations, consultez l’article [d’authentification et d’autorisation.](/aspnet/core/grpc/authn-and-authz)

> [!NOTE]
> Lorsque vous utilisez gRPC sur une connexion HTTP/2 cryptée TLS, tout le trafic entre les clients et les serveurs est crypté, même si vous n’utilisez pas d’authentification au niveau du canal.

Ce chapitre montrera comment appliquer les informations d’identification des appels et canaliser les informations d’identification à un service gRPC. Il montrera également comment utiliser les informations d’identification d’un client .NET Core gRPC pour authentifier avec le service.

>[!div class="step-by-step"]
>[Suivant précédent](client-libraries.md)
>[Next](call-credentials.md)
