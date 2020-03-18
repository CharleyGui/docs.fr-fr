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
# <a name="security-in-grpc-applications"></a><span data-ttu-id="86511-103">Sécurité dans les applications gRPC</span><span class="sxs-lookup"><span data-stu-id="86511-103">Security in gRPC applications</span></span>

<span data-ttu-id="86511-104">Dans n’importe quel scénario réel, il est essentiel de sécuriser les applications et les services.</span><span class="sxs-lookup"><span data-stu-id="86511-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="86511-105">La sécurité couvre trois domaines clés :</span><span class="sxs-lookup"><span data-stu-id="86511-105">Security covers three key areas:</span></span>

* <span data-ttu-id="86511-106">Chiffrer le trafic réseau pour empêcher les pirates malveillants de l’intercepter.</span><span class="sxs-lookup"><span data-stu-id="86511-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="86511-107">Authentifier les clients et les serveurs pour établir l’identité et la confiance.</span><span class="sxs-lookup"><span data-stu-id="86511-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="86511-108">Autoriser les clients à contrôler l’accès aux systèmes et à appliquer des autorisations basées sur l’identité.</span><span class="sxs-lookup"><span data-stu-id="86511-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="86511-109">*L’authentification* vise à établir l’identité d’un client ou d’un serveur.</span><span class="sxs-lookup"><span data-stu-id="86511-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="86511-110">*L’autorisation* vise à déterminer si un client a la permission d’accéder à une ressource ou d’émettre une commande.</span><span class="sxs-lookup"><span data-stu-id="86511-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="86511-111">Ce chapitre couvrira les installations d’authentification et d’autorisation en gRPC pour ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="86511-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="86511-112">Il discutera également de la sécurité du réseau par le biais de connexions cryptées TLS.</span><span class="sxs-lookup"><span data-stu-id="86511-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="86511-113">Authentification et autorisation de la WCF</span><span class="sxs-lookup"><span data-stu-id="86511-113">WCF authentication and authorization</span></span>

<span data-ttu-id="86511-114">Dans Windows Communication Foundation (WCF), l’authentification et l’autorisation ont été traitées de différentes manières, en fonction des transports et des liaisons utilisées.</span><span class="sxs-lookup"><span data-stu-id="86511-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="86511-115">WCF a soutenu\* diverses normes de sécurité WS.</span><span class="sxs-lookup"><span data-stu-id="86511-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="86511-116">Il a également pris en charge l’authentification de Windows pour les services HTTP exécutant dans les services IIS ou NetTCP entre les systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="86511-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="86511-117">gRPC authentification et autorisation</span><span class="sxs-lookup"><span data-stu-id="86511-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="86511-118">gRPC authentification et autorisation fonctionne sur deux niveaux :</span><span class="sxs-lookup"><span data-stu-id="86511-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="86511-119">L’authentification/autorisation au niveau des appels est généralement traitée par des jetons qui sont appliqués dans les métadonnées lorsque l’appel est effectué.</span><span class="sxs-lookup"><span data-stu-id="86511-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span>
* <span data-ttu-id="86511-120">L’authentification au niveau des canaux utilise un certificat client qui est appliqué au niveau de connexion.</span><span class="sxs-lookup"><span data-stu-id="86511-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="86511-121">Il peut également inclure des informations d’authentification/autorisation au niveau des appels à appliquer automatiquement à chaque appel sur le canal.</span><span class="sxs-lookup"><span data-stu-id="86511-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span>

<span data-ttu-id="86511-122">Vous pouvez utiliser l’un ou l’autre ou les deux de ces mécanismes pour vous aider à sécuriser votre service.</span><span class="sxs-lookup"><span data-stu-id="86511-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="86511-123">La mise en œuvre de base ASP.NET de gRPC prend en charge l’authentification et l’autorisation par la plupart des mécanismes ASP.NET de base standard :</span><span class="sxs-lookup"><span data-stu-id="86511-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="86511-124">Appel authentification</span><span class="sxs-lookup"><span data-stu-id="86511-124">Call authentication</span></span>
  - <span data-ttu-id="86511-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="86511-125">Azure Active Directory</span></span>
  - <span data-ttu-id="86511-126">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="86511-126">IdentityServer</span></span>
  - <span data-ttu-id="86511-127">Jeton de porteur de JWT</span><span class="sxs-lookup"><span data-stu-id="86511-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="86511-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="86511-128">OAuth 2.0</span></span>
  - <span data-ttu-id="86511-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="86511-129">OpenID Connect</span></span>
  - <span data-ttu-id="86511-130">Un certificat de fournisseur d'identité WS-Federation</span><span class="sxs-lookup"><span data-stu-id="86511-130">WS-Federation</span></span>
- <span data-ttu-id="86511-131">Authentification des canaux</span><span class="sxs-lookup"><span data-stu-id="86511-131">Channel authentication</span></span>
  - <span data-ttu-id="86511-132">Certificat client</span><span class="sxs-lookup"><span data-stu-id="86511-132">Client certificate</span></span>

<span data-ttu-id="86511-133">Les méthodes d’authentification d’appel sont toutes basées sur *des jetons.*</span><span class="sxs-lookup"><span data-stu-id="86511-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="86511-134">La seule vraie différence est la façon dont les jetons sont générés et les bibliothèques qui sont utilisées pour valider les jetons dans le service ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="86511-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="86511-135">Pour plus d’informations, consultez l’article [d’authentification et d’autorisation.](/aspnet/core/grpc/authn-and-authz)</span><span class="sxs-lookup"><span data-stu-id="86511-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="86511-136">Lorsque vous utilisez gRPC sur une connexion HTTP/2 cryptée TLS, tout le trafic entre les clients et les serveurs est crypté, même si vous n’utilisez pas d’authentification au niveau du canal.</span><span class="sxs-lookup"><span data-stu-id="86511-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="86511-137">Ce chapitre montrera comment appliquer les informations d’identification des appels et canaliser les informations d’identification à un service gRPC.</span><span class="sxs-lookup"><span data-stu-id="86511-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="86511-138">Il montrera également comment utiliser les informations d’identification d’un client .NET Core gRPC pour authentifier avec le service.</span><span class="sxs-lookup"><span data-stu-id="86511-138">It will also show how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="86511-139">[Suivant précédent](client-libraries.md)
>[Next](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="86511-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
