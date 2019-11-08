---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738741"
---
# <a name="resolver"></a><span data-ttu-id="061c4-101">> de résolution de \<</span><span class="sxs-lookup"><span data-stu-id="061c4-101">\<resolver></span></span>
<span data-ttu-id="061c4-102">Spécifie un programme de résolution d'homologue utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds d'homologues représentant plusieurs nœuds faisant partie de la maille.</span><span class="sxs-lookup"><span data-stu-id="061c4-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
<span data-ttu-id="061c4-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="061c4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="061c4-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="061c4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="061c4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="061c4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="061c4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**NetPeerTcpBinding**](netpeertcpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="061c4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="061c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="061c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="061c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="061c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="061c4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="061c4-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="061c4-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="061c4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="061c4-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="061c4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="061c4-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="061c4-112">Attributes</span></span>  
  
|<span data-ttu-id="061c4-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="061c4-113">Attribute</span></span>|<span data-ttu-id="061c4-114">Description</span><span class="sxs-lookup"><span data-stu-id="061c4-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="061c4-115">Chaîne qui spécifie si l'instance du programme de résolution d'homologue associée à ce service est spécifique au PNRP, à un programme de résolution personnalisé ou si elle est déterminée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="061c4-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="061c4-116">Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="061c4-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="061c4-117">Chaîne qui spécifie la manière dont les références sont partagées parmi des homologues.</span><span class="sxs-lookup"><span data-stu-id="061c4-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="061c4-118">Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="061c4-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="061c4-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="061c4-119">Child Elements</span></span>  
  
|<span data-ttu-id="061c4-120">Élément</span><span class="sxs-lookup"><span data-stu-id="061c4-120">Element</span></span>|<span data-ttu-id="061c4-121">Description</span><span class="sxs-lookup"><span data-stu-id="061c4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="061c4-122">en-têtes de \<</span><span class="sxs-lookup"><span data-stu-id="061c4-122">\<headers></span></span>](headers.md)|<span data-ttu-id="061c4-123">Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="061c4-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="061c4-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="061c4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="061c4-125">Élément</span><span class="sxs-lookup"><span data-stu-id="061c4-125">Element</span></span>|<span data-ttu-id="061c4-126">Description</span><span class="sxs-lookup"><span data-stu-id="061c4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="061c4-127">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="061c4-127">\<binding></span></span>](bindings.md)|<span data-ttu-id="061c4-128">Définit toutes les fonctions de liaison du [\<NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="061c4-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="061c4-129">Notes</span><span class="sxs-lookup"><span data-stu-id="061c4-129">Remarks</span></span>  
 <span data-ttu-id="061c4-130">Un programme de résolution de nom d'homologue est un service de découverte utilisé par les canaux homologues afin de rechercher des nœuds d'homologues faisant partie d'une maille d'homologues.</span><span class="sxs-lookup"><span data-stu-id="061c4-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="061c4-131">Il est également utilisé pour « inscrire » un nœud avec un maillage d'homologue, le mécanisme par lequel le nœud homologue est connu et disponible à partir du maillage d'homologue.</span><span class="sxs-lookup"><span data-stu-id="061c4-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="061c4-132">Pour plus d’informations sur les programmes de résolution d’homologue, consultez programmes de [résolution d’homologue](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="061c4-132">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="061c4-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="061c4-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="061c4-134">Programmes de résolution d’homologue</span><span class="sxs-lookup"><span data-stu-id="061c4-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="061c4-135">[Ajout d’un programme de résolution personnalisé à une application PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="061c4-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
