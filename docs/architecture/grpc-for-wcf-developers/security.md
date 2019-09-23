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
# <a name="security-in-grpc-applications"></a><span data-ttu-id="8785b-103">Sécurité dans les applications gRPC</span><span class="sxs-lookup"><span data-stu-id="8785b-103">Security in gRPC applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="8785b-104">Dans tout scénario réel, il est essentiel de sécuriser les applications et les services.</span><span class="sxs-lookup"><span data-stu-id="8785b-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="8785b-105">La sécurité couvre trois domaines clés : le chiffrement du trafic réseau pour empêcher son interception par des acteurs incorrects ; authentification des clients et des serveurs pour établir l’identité et l’approbation ; et d’autoriser les clients à contrôler l’accès aux systèmes et à appliquer des autorisations en fonction de leur identité.</span><span class="sxs-lookup"><span data-stu-id="8785b-105">Security covers three key areas: encrypting network traffic to prevent it from being intercepted by bad actors; authenticating clients and servers to establish identity and trust; and authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="8785b-106">**L’authentification** concerne l’établissement de l’identité d’un client ou d’un serveur.</span><span class="sxs-lookup"><span data-stu-id="8785b-106">**Authentication** is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="8785b-107">L' **autorisation** consiste à déterminer si un client a l’autorisation d’accéder à une ressource ou d’émettre une commande.</span><span class="sxs-lookup"><span data-stu-id="8785b-107">**Authorization** is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="8785b-108">Ce chapitre couvre les fonctionnalités d’authentification et d’autorisation dans gRPC pour ASP.NET Core, et aborde la sécurité réseau à l’aide de connexions chiffrées TLS.</span><span class="sxs-lookup"><span data-stu-id="8785b-108">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core, and discuss network security using TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="8785b-109">Authentification et autorisation WCF</span><span class="sxs-lookup"><span data-stu-id="8785b-109">WCF authentication and authorization</span></span>

<span data-ttu-id="8785b-110">Dans WCF, l’authentification et l’autorisation ont été gérées de différentes façons en fonction des transports et des liaisons utilisés.</span><span class="sxs-lookup"><span data-stu-id="8785b-110">In WCF, authentication and authorization were handled in different ways depending on the transports and bindings being used.</span></span> <span data-ttu-id="8785b-111">WCF prenait en charge différentes\* normes WS-Security, ainsi que l’authentification Windows pour les services http qui s’exécutent dans les services IIS ou NetTcp entre les systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="8785b-111">WCF supported various WS-\* security standards, as well as Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="8785b-112">authentification et autorisation gRPC</span><span class="sxs-lookup"><span data-stu-id="8785b-112">gRPC authentication and authorization</span></span>

<span data-ttu-id="8785b-113">l’authentification et l’autorisation gRPC fonctionnent sur deux niveaux.</span><span class="sxs-lookup"><span data-stu-id="8785b-113">gRPC authentication and authorization works on two levels.</span></span> <span data-ttu-id="8785b-114">L’authentification/autorisation au niveau de l’appel est généralement gérée à l’aide de jetons appliqués dans les métadonnées lorsque l’appel est effectué.</span><span class="sxs-lookup"><span data-stu-id="8785b-114">Call-level authentication/authorization is usually handled using tokens that are applied in metadata when the call is made.</span></span> <span data-ttu-id="8785b-115">L’authentification au niveau du canal utilise un certificat client qui est appliqué au niveau de la connexion et peut également inclure des informations d’authentification/autorisation au niveau de l’appel à appliquer automatiquement à chaque appel sur le canal.</span><span class="sxs-lookup"><span data-stu-id="8785b-115">Channel-level authentication uses a client certificate that is applied at the connection level, and can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span> <span data-ttu-id="8785b-116">Vous pouvez utiliser l’un ou l’autre de ces mécanismes ou les deux pour sécuriser votre service.</span><span class="sxs-lookup"><span data-stu-id="8785b-116">You can use either or both of these mechanisms to secure your service.</span></span>

<span data-ttu-id="8785b-117">La ASP.NET Core implémentation de gRPC prend en charge l’authentification et l’autorisation à l’aide de la plupart des mécanismes de ASP.NET Core standard :</span><span class="sxs-lookup"><span data-stu-id="8785b-117">The ASP.NET Core implementation of gRPC supports authentication and authorization using most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="8785b-118">Appeler l’authentification</span><span class="sxs-lookup"><span data-stu-id="8785b-118">Call authentication</span></span>
  - <span data-ttu-id="8785b-119">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="8785b-119">Azure Active Directory</span></span>
  - <span data-ttu-id="8785b-120">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="8785b-120">IdentityServer</span></span>
  - <span data-ttu-id="8785b-121">Jeton du porteur JWT</span><span class="sxs-lookup"><span data-stu-id="8785b-121">JWT Bearer Token</span></span>
  - <span data-ttu-id="8785b-122">OAuth 2,0</span><span class="sxs-lookup"><span data-stu-id="8785b-122">OAuth 2.0</span></span>
  - <span data-ttu-id="8785b-123">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="8785b-123">OpenID Connect</span></span>
  - <span data-ttu-id="8785b-124">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="8785b-124">WS-Federation</span></span>
- <span data-ttu-id="8785b-125">Authentification de canal</span><span class="sxs-lookup"><span data-stu-id="8785b-125">Channel authentication</span></span>
  - <span data-ttu-id="8785b-126">Certificat client</span><span class="sxs-lookup"><span data-stu-id="8785b-126">Client Certificate</span></span>

<span data-ttu-id="8785b-127">Les méthodes d’authentification d’appel sont toutes basées sur des *jetons*.</span><span class="sxs-lookup"><span data-stu-id="8785b-127">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="8785b-128">La seule différence réelle est la façon dont le jeton est généré et les bibliothèques utilisées pour valider les jetons dans le service ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8785b-128">The only real difference is how the token is generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="8785b-129">Pour plus d’informations, consultez la [documentation sur l’authentification et l’autorisation sur Microsoft docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="8785b-129">For more information, see the [Authentication and authorization documentation on Microsoft Docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span></span>

> [!NOTE]
> <span data-ttu-id="8785b-130">Lors de l’utilisation de gRPC sur une connexion HTTP/2 chiffrée TLS, tout le trafic entre les clients et les serveurs est chiffré, même si vous n’utilisez pas l’authentification au niveau du canal.</span><span class="sxs-lookup"><span data-stu-id="8785b-130">When using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="8785b-131">Ce chapitre explique comment appliquer les informations d’identification d’appel et les informations d’identification de canal à un service gRPC, et comment utiliser les informations d’identification d’un client .NET Core gRPC pour s’authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="8785b-131">This chapter will show how to apply call credentials and channel credentials to a gRPC service, and how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8785b-132">[Précédent](client-libraries.md)
>[Suivant](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="8785b-132">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
