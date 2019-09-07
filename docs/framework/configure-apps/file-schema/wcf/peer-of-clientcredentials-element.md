---
title: <peer>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400097"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="1e112-102">\<> homologue \<de l’élément > ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="1e112-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="1e112-103">Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="1e112-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
<span data-ttu-id="1e112-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e112-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e112-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1e112-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1e112-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1e112-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="1e112-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1e112-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="1e112-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1e112-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="1e112-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="1e112-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="1e112-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> homologues**</span><span class="sxs-lookup"><span data-stu-id="1e112-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e112-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e112-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e112-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1e112-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1e112-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1e112-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e112-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="1e112-114">Attributes</span></span>  
 <span data-ttu-id="1e112-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1e112-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e112-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1e112-116">Child Elements</span></span>  
  
|<span data-ttu-id="1e112-117">Élément</span><span class="sxs-lookup"><span data-stu-id="1e112-117">Element</span></span>|<span data-ttu-id="1e112-118">Description</span><span class="sxs-lookup"><span data-stu-id="1e112-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e112-119">\<certificate></span><span class="sxs-lookup"><span data-stu-id="1e112-119">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="1e112-120">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="1e112-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="1e112-121">.</span><span class="sxs-lookup"><span data-stu-id="1e112-121">.</span></span>|  
|[<span data-ttu-id="1e112-122">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="1e112-122">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="1e112-123">Spécifie les options d'authentification pour les clients du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="1e112-123">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="1e112-124">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="1e112-124">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="1e112-125">Spécifie les options d'authentification pour les expéditeurs de messages.</span><span class="sxs-lookup"><span data-stu-id="1e112-125">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e112-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1e112-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1e112-127">Élément</span><span class="sxs-lookup"><span data-stu-id="1e112-127">Element</span></span>|<span data-ttu-id="1e112-128">Description</span><span class="sxs-lookup"><span data-stu-id="1e112-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e112-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="1e112-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="1e112-130">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="1e112-130">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e112-131">Notes</span><span class="sxs-lookup"><span data-stu-id="1e112-131">Remarks</span></span>  
 <span data-ttu-id="1e112-132">Cet élément de configuration spécifie les informations d'identification qu'un nœud homologue utilise pour s'authentifier sur les autres nœuds de la maille, ainsi que les paramètres d'authentification qu'un nœud homologue utilise pour authentifier les autres nœuds homologues.</span><span class="sxs-lookup"><span data-stu-id="1e112-132">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="1e112-133">Pour plus d’informations, consultez [canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) et la [sécurisation des applications canal homologue](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1e112-133">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e112-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e112-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="1e112-135">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="1e112-135">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="1e112-136">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="1e112-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="1e112-137">[canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1e112-137">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="1e112-138">[canal homologue l’authentification personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1e112-138">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="1e112-139">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="1e112-139">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="1e112-140">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="1e112-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
