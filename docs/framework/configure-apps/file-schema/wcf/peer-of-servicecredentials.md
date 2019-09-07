---
title: <peer> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397639"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="23cec-102">\<> homologue \<de la > ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="23cec-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="23cec-103">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="23cec-103">Specifies the current credentials for a peer node.</span></span>  
  
<span data-ttu-id="23cec-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="23cec-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="23cec-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="23cec-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="23cec-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="23cec-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="23cec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="23cec-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="23cec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="23cec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="23cec-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="23cec-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="23cec-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> homologues**</span><span class="sxs-lookup"><span data-stu-id="23cec-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23cec-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23cec-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23cec-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="23cec-112">Attributes and Elements</span></span>  
 <span data-ttu-id="23cec-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="23cec-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23cec-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="23cec-114">Attributes</span></span>  
 <span data-ttu-id="23cec-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="23cec-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23cec-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="23cec-116">Child Elements</span></span>  
  
|<span data-ttu-id="23cec-117">Élément</span><span class="sxs-lookup"><span data-stu-id="23cec-117">Element</span></span>|<span data-ttu-id="23cec-118">Description</span><span class="sxs-lookup"><span data-stu-id="23cec-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23cec-119">\<certificate></span><span class="sxs-lookup"><span data-stu-id="23cec-119">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="23cec-120">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les services de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="23cec-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="23cec-121">.</span><span class="sxs-lookup"><span data-stu-id="23cec-121">.</span></span>|  
|[<span data-ttu-id="23cec-122">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="23cec-122">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="23cec-123">Spécifie les options d'authentification pour les expéditeurs de messages.</span><span class="sxs-lookup"><span data-stu-id="23cec-123">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="23cec-124">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="23cec-124">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="23cec-125">Spécifie les options d'authentification pour les services du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="23cec-125">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23cec-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="23cec-126">Parent Elements</span></span>  
  
|<span data-ttu-id="23cec-127">Élément</span><span class="sxs-lookup"><span data-stu-id="23cec-127">Element</span></span>|<span data-ttu-id="23cec-128">Description</span><span class="sxs-lookup"><span data-stu-id="23cec-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23cec-129">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="23cec-129">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="23cec-130">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="23cec-130">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23cec-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23cec-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="23cec-132">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="23cec-132">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="23cec-133">[canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="23cec-133">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="23cec-134">[canal homologue l’authentification personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="23cec-134">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="23cec-135">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="23cec-135">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="23cec-136">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="23cec-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
