---
title: Sécurité dans les applications gRPC-gRPC pour les développeurs WCF
description: Vue d’ensemble de l’authentification et de l’autorisation de l’appel et du canal dans gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5f3d32817ccb5d9f278d256c0ee135f0e2a17cf2
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184140"
---
# <a name="security-in-grpc-applications"></a>Sécurité dans les applications gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Dans tout scénario réel, il est essentiel de sécuriser les applications et les services. La sécurité couvre trois domaines clés : le chiffrement du trafic réseau pour empêcher son interception par des acteurs incorrects ; authentification des clients et des serveurs pour établir l’identité et l’approbation ; et d’autoriser les clients à contrôler l’accès aux systèmes et à appliquer des autorisations en fonction de leur identité.

> [!NOTE]
> **L’authentification** concerne l’établissement de l’identité d’un client ou d’un serveur. L' **autorisation** consiste à déterminer si un client a l’autorisation d’accéder à une ressource ou d’émettre une commande.

Ce chapitre couvre les fonctionnalités d’authentification et d’autorisation dans gRPC pour ASP.NET Core, et aborde la sécurité réseau à l’aide de connexions chiffrées TLS.

## <a name="wcf-authentication-and-authorization"></a>Authentification et autorisation WCF

Dans WCF, l’authentification et l’autorisation ont été gérées de différentes façons en fonction des transports et des liaisons utilisés. WCF prenait en charge différentes\* normes WS-Security, ainsi que l’authentification Windows pour les services http qui s’exécutent dans les services IIS ou NetTcp entre les systèmes Windows.

## <a name="grpc-authentication-and-authorization"></a>authentification et autorisation gRPC

l’authentification et l’autorisation gRPC fonctionnent sur deux niveaux. L’authentification/autorisation au niveau de l’appel est généralement gérée à l’aide de jetons appliqués dans les métadonnées lorsque l’appel est effectué. L’authentification au niveau du canal utilise un certificat client qui est appliqué au niveau de la connexion et peut également inclure des informations d’authentification/autorisation au niveau de l’appel à appliquer automatiquement à chaque appel sur le canal. Vous pouvez utiliser l’un ou l’autre de ces mécanismes ou les deux pour sécuriser votre service.

La ASP.NET Core implémentation de gRPC prend en charge l’authentification et l’autorisation à l’aide de la plupart des mécanismes de ASP.NET Core standard :

- Appeler l’authentification
  - Azure Active Directory
  - IdentityServer
  - Jeton du porteur JWT
  - OAuth 2,0
  - OpenID Connect
  - WS-Federation
- Authentification de canal
  - Certificat client

Les méthodes d’authentification d’appel sont toutes basées sur des *jetons*. La seule différence réelle est la façon dont le jeton est généré et les bibliothèques utilisées pour valider les jetons dans le service ASP.NET Core.

Pour plus d’informations, consultez la [documentation sur l’authentification et l’autorisation sur Microsoft docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).

> [!NOTE]
> Lors de l’utilisation de gRPC sur une connexion HTTP/2 chiffrée TLS, tout le trafic entre les clients et les serveurs est chiffré, même si vous n’utilisez pas l’authentification au niveau du canal.

Ce chapitre explique comment appliquer les informations d’identification d’appel et les informations d’identification de canal à un service gRPC, et comment utiliser les informations d’identification d’un client .NET Core gRPC pour s’authentifier auprès du service.

>[!div class="step-by-step"]
>[Précédent](client-libraries.md)
>[Suivant](call-credentials.md)
