---
title: <peer> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 50415cb9b35d2a2053efa3313a415de518b7e36e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933775"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="3edf6-102">\<> homologue \<de la > ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="3edf6-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="3edf6-103">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="3edf6-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="3edf6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3edf6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3edf6-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="3edf6-105">\<behaviors></span></span>  
<span data-ttu-id="3edf6-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3edf6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3edf6-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="3edf6-107">\<behavior></span></span>  
<span data-ttu-id="3edf6-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3edf6-108">\<serviceCredentials></span></span>  
<span data-ttu-id="3edf6-109">\<> homologues</span><span class="sxs-lookup"><span data-stu-id="3edf6-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3edf6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3edf6-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3edf6-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3edf6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3edf6-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3edf6-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3edf6-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="3edf6-113">Attributes</span></span>  
 <span data-ttu-id="3edf6-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3edf6-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3edf6-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3edf6-115">Child Elements</span></span>  
  
|<span data-ttu-id="3edf6-116">Élément</span><span class="sxs-lookup"><span data-stu-id="3edf6-116">Element</span></span>|<span data-ttu-id="3edf6-117">Description</span><span class="sxs-lookup"><span data-stu-id="3edf6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3edf6-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="3edf6-118">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="3edf6-119">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les services de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="3edf6-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="3edf6-120">.</span><span class="sxs-lookup"><span data-stu-id="3edf6-120">.</span></span>|  
|[<span data-ttu-id="3edf6-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="3edf6-121">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="3edf6-122">Spécifie les options d'authentification pour les expéditeurs de messages.</span><span class="sxs-lookup"><span data-stu-id="3edf6-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="3edf6-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="3edf6-123">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="3edf6-124">Spécifie les options d'authentification pour les services du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="3edf6-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3edf6-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3edf6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3edf6-126">Élément</span><span class="sxs-lookup"><span data-stu-id="3edf6-126">Element</span></span>|<span data-ttu-id="3edf6-127">Description</span><span class="sxs-lookup"><span data-stu-id="3edf6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3edf6-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3edf6-128">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="3edf6-129">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="3edf6-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3edf6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3edf6-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="3edf6-131">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="3edf6-131">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="3edf6-132">[canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3edf6-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="3edf6-133">[canal homologue l’authentification personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3edf6-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="3edf6-134">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="3edf6-134">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="3edf6-135">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="3edf6-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
