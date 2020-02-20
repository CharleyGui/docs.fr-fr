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
# <a name="security-in-grpc-applications"></a><span data-ttu-id="b97e7-103">Sécurité dans les applications gRPC</span><span class="sxs-lookup"><span data-stu-id="b97e7-103">Security in gRPC applications</span></span>

<span data-ttu-id="b97e7-104">Dans tout scénario réel, il est essentiel de sécuriser les applications et les services.</span><span class="sxs-lookup"><span data-stu-id="b97e7-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="b97e7-105">La sécurité couvre trois domaines clés :</span><span class="sxs-lookup"><span data-stu-id="b97e7-105">Security covers three key areas:</span></span> 

* <span data-ttu-id="b97e7-106">Chiffrement du trafic réseau pour empêcher les pirates malveillants de les intercepter.</span><span class="sxs-lookup"><span data-stu-id="b97e7-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="b97e7-107">Authentification des clients et des serveurs pour établir l’identité et l’approbation.</span><span class="sxs-lookup"><span data-stu-id="b97e7-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="b97e7-108">Autoriser les clients à contrôler l’accès aux systèmes et appliquer des autorisations en fonction de leur identité.</span><span class="sxs-lookup"><span data-stu-id="b97e7-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="b97e7-109">*L’authentification* concerne l’établissement de l’identité d’un client ou d’un serveur.</span><span class="sxs-lookup"><span data-stu-id="b97e7-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="b97e7-110">L' *autorisation* consiste à déterminer si un client a l’autorisation d’accéder à une ressource ou d’émettre une commande.</span><span class="sxs-lookup"><span data-stu-id="b97e7-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="b97e7-111">Ce chapitre aborde les fonctionnalités d’authentification et d’autorisation dans gRPC pour ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b97e7-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="b97e7-112">Il aborde également la sécurité réseau via des connexions chiffrées TLS.</span><span class="sxs-lookup"><span data-stu-id="b97e7-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="b97e7-113">Authentification et autorisation WCF</span><span class="sxs-lookup"><span data-stu-id="b97e7-113">WCF authentication and authorization</span></span>

<span data-ttu-id="b97e7-114">Dans Windows Communication Foundation (WCF), l’authentification et l’autorisation ont été gérées de différentes façons, en fonction des transports et des liaisons utilisés.</span><span class="sxs-lookup"><span data-stu-id="b97e7-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="b97e7-115">WCF prenait en charge différentes normes de sécurité WS-\*.</span><span class="sxs-lookup"><span data-stu-id="b97e7-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="b97e7-116">Il prend également en charge l’authentification Windows pour les services HTTP qui s’exécutent dans les services IIS ou NetTCP entre les systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="b97e7-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="b97e7-117">authentification et autorisation gRPC</span><span class="sxs-lookup"><span data-stu-id="b97e7-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="b97e7-118">l’authentification et l’autorisation gRPC fonctionnent sur deux niveaux :</span><span class="sxs-lookup"><span data-stu-id="b97e7-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="b97e7-119">L’authentification/autorisation au niveau de l’appel est généralement gérée par le biais de jetons appliqués dans les métadonnées lorsque l’appel est effectué.</span><span class="sxs-lookup"><span data-stu-id="b97e7-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span> 
* <span data-ttu-id="b97e7-120">L’authentification au niveau du canal utilise un certificat client qui est appliqué au niveau de la connexion.</span><span class="sxs-lookup"><span data-stu-id="b97e7-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="b97e7-121">Il peut également inclure des informations d’authentification/autorisation au niveau de l’appel à appliquer automatiquement à chaque appel sur le canal.</span><span class="sxs-lookup"><span data-stu-id="b97e7-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span> 

<span data-ttu-id="b97e7-122">Vous pouvez utiliser l’un ou l’autre de ces mécanismes, ou les deux, pour vous aider à sécuriser votre service.</span><span class="sxs-lookup"><span data-stu-id="b97e7-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="b97e7-123">La ASP.NET Core implémentation de gRPC prend en charge l’authentification et l’autorisation via la plupart des mécanismes de ASP.NET Core standard :</span><span class="sxs-lookup"><span data-stu-id="b97e7-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="b97e7-124">Appeler l’authentification</span><span class="sxs-lookup"><span data-stu-id="b97e7-124">Call authentication</span></span>
  - <span data-ttu-id="b97e7-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="b97e7-125">Azure Active Directory</span></span>
  - <span data-ttu-id="b97e7-126">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="b97e7-126">IdentityServer</span></span>
  - <span data-ttu-id="b97e7-127">Jeton du porteur JWT</span><span class="sxs-lookup"><span data-stu-id="b97e7-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="b97e7-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="b97e7-128">OAuth 2.0</span></span>
  - <span data-ttu-id="b97e7-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="b97e7-129">OpenID Connect</span></span>
  - <span data-ttu-id="b97e7-130">Un certificat de fournisseur d'identité WS-Federation</span><span class="sxs-lookup"><span data-stu-id="b97e7-130">WS-Federation</span></span>
- <span data-ttu-id="b97e7-131">Authentification de canal</span><span class="sxs-lookup"><span data-stu-id="b97e7-131">Channel authentication</span></span>
  - <span data-ttu-id="b97e7-132">Certificat client</span><span class="sxs-lookup"><span data-stu-id="b97e7-132">Client certificate</span></span>

<span data-ttu-id="b97e7-133">Les méthodes d’authentification d’appel sont toutes basées sur des *jetons*.</span><span class="sxs-lookup"><span data-stu-id="b97e7-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="b97e7-134">La seule différence réelle est la façon dont les jetons sont générés et les bibliothèques utilisées pour valider les jetons dans le service ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b97e7-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="b97e7-135">Pour plus d’informations, consultez l’article [authentification et autorisation](/aspnet/core/grpc/authn-and-authz) .</span><span class="sxs-lookup"><span data-stu-id="b97e7-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="b97e7-136">Lorsque vous utilisez gRPC sur une connexion HTTP/2 chiffrée TLS, tout le trafic entre les clients et les serveurs est chiffré, même si vous n’utilisez pas l’authentification au niveau du canal.</span><span class="sxs-lookup"><span data-stu-id="b97e7-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="b97e7-137">Ce chapitre explique comment appliquer des informations d’identification d’appel et des informations d’identification de canal à un service gRPC.</span><span class="sxs-lookup"><span data-stu-id="b97e7-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="b97e7-138">Il indique également comment utiliser les informations d’identification d’un client gRPC .NET Core pour s’authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="b97e7-138">It will also show how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b97e7-139">[Précédent](client-libraries.md)
>[Suivant](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="b97e7-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
