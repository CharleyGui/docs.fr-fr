---
title: <peer>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400097"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="43c3c-102">\<peer>d' \<clientCredentials> élément</span><span class="sxs-lookup"><span data-stu-id="43c3c-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="43c3c-103">Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="43c3c-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="43c3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43c3c-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43c3c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="43c3c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="43c3c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="43c3c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43c3c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="43c3c-107">Attributes</span></span>  
 <span data-ttu-id="43c3c-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="43c3c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43c3c-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="43c3c-109">Child Elements</span></span>  
  
|<span data-ttu-id="43c3c-110">Élément</span><span class="sxs-lookup"><span data-stu-id="43c3c-110">Element</span></span>|<span data-ttu-id="43c3c-111">Description</span><span class="sxs-lookup"><span data-stu-id="43c3c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="43c3c-112">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="43c3c-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="43c3c-113">.</span><span class="sxs-lookup"><span data-stu-id="43c3c-113">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="43c3c-114">Spécifie les options d'authentification pour les clients du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="43c3c-114">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="43c3c-115">Spécifie les options d'authentification pour les expéditeurs de messages.</span><span class="sxs-lookup"><span data-stu-id="43c3c-115">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43c3c-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="43c3c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="43c3c-117">Élément</span><span class="sxs-lookup"><span data-stu-id="43c3c-117">Element</span></span>|<span data-ttu-id="43c3c-118">Description</span><span class="sxs-lookup"><span data-stu-id="43c3c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="43c3c-119">Spécifie les informations d'identification utilisées pour authentifier un client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="43c3c-119">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43c3c-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="43c3c-120">Remarks</span></span>  
 <span data-ttu-id="43c3c-121">Cet élément de configuration spécifie les informations d'identification qu'un nœud homologue utilise pour s'authentifier sur les autres nœuds de la maille, ainsi que les paramètres d'authentification qu'un nœud homologue utilise pour authentifier les autres nœuds homologues.</span><span class="sxs-lookup"><span data-stu-id="43c3c-121">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="43c3c-122">Pour plus d’informations, consultez [canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) et la [sécurisation des applications canal homologue](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="43c3c-122">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c3c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43c3c-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="43c3c-124">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="43c3c-124">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="43c3c-125">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="43c3c-125">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="43c3c-126">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="43c3c-126">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="43c3c-127">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="43c3c-127">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="43c3c-128">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="43c3c-128">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="43c3c-129">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="43c3c-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
