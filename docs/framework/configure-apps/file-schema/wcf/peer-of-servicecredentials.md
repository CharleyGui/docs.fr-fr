---
title: <peer> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 7f6669d3f53a6ee0d189786fa9ca3625fdedd127
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162476"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="8d618-102">\<peer> de \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="8d618-102">\<peer> of \<serviceCredentials></span></span>

<span data-ttu-id="8d618-103">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="8d618-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="8d618-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d618-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d618-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8d618-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8d618-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8d618-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d618-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="8d618-107">Attributes</span></span>  

 <span data-ttu-id="8d618-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8d618-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d618-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8d618-109">Child Elements</span></span>  
  
|<span data-ttu-id="8d618-110">Élément</span><span class="sxs-lookup"><span data-stu-id="8d618-110">Element</span></span>|<span data-ttu-id="8d618-111">Description</span><span class="sxs-lookup"><span data-stu-id="8d618-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="8d618-112">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les services de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="8d618-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="8d618-113">.</span><span class="sxs-lookup"><span data-stu-id="8d618-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="8d618-114">Spécifie les options d'authentification pour les expéditeurs de messages.</span><span class="sxs-lookup"><span data-stu-id="8d618-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="8d618-115">Spécifie les options d'authentification pour les services du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="8d618-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d618-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8d618-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8d618-117">Élément</span><span class="sxs-lookup"><span data-stu-id="8d618-117">Element</span></span>|<span data-ttu-id="8d618-118">Description</span><span class="sxs-lookup"><span data-stu-id="8d618-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="8d618-119">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="8d618-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d618-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d618-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="8d618-121">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="8d618-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="8d618-122">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="8d618-122">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="8d618-123">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="8d618-123">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="8d618-124">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="8d618-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="8d618-125">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="8d618-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
