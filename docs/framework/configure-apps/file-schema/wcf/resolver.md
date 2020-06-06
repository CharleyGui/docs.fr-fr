---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738741"
---
# \<resolver>
<span data-ttu-id="be01b-101">Spécifie un programme de résolution d'homologue utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds d'homologues représentant plusieurs nœuds faisant partie de la maille.</span><span class="sxs-lookup"><span data-stu-id="be01b-101">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="be01b-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be01b-102">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be01b-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="be01b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="be01b-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="be01b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be01b-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="be01b-105">Attributes</span></span>  
  
|<span data-ttu-id="be01b-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="be01b-106">Attribute</span></span>|<span data-ttu-id="be01b-107">Description</span><span class="sxs-lookup"><span data-stu-id="be01b-107">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="be01b-108">Chaîne qui spécifie si l'instance du programme de résolution d'homologue associée à ce service est spécifique au PNRP, à un programme de résolution personnalisé ou si elle est déterminée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="be01b-108">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="be01b-109">Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span><span class="sxs-lookup"><span data-stu-id="be01b-109">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="be01b-110">Chaîne qui spécifie la manière dont les références sont partagées parmi des homologues.</span><span class="sxs-lookup"><span data-stu-id="be01b-110">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="be01b-111">Cet attribut est de type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span><span class="sxs-lookup"><span data-stu-id="be01b-111">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be01b-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="be01b-112">Child Elements</span></span>  
  
|<span data-ttu-id="be01b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="be01b-113">Element</span></span>|<span data-ttu-id="be01b-114">Description</span><span class="sxs-lookup"><span data-stu-id="be01b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="be01b-115">Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="be01b-115">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be01b-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="be01b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="be01b-117">Élément</span><span class="sxs-lookup"><span data-stu-id="be01b-117">Element</span></span>|<span data-ttu-id="be01b-118">Description</span><span class="sxs-lookup"><span data-stu-id="be01b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="be01b-119">Définit toutes les fonctions de liaison de [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="be01b-119">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be01b-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="be01b-120">Remarks</span></span>  
 <span data-ttu-id="be01b-121">Un programme de résolution de nom d'homologue est un service de découverte utilisé par les canaux homologues afin de rechercher des nœuds d'homologues faisant partie d'une maille d'homologues.</span><span class="sxs-lookup"><span data-stu-id="be01b-121">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="be01b-122">Il est également utilisé pour « inscrire » un nœud avec un maillage d'homologue, le mécanisme par lequel le nœud homologue est connu et disponible à partir du maillage d'homologue.</span><span class="sxs-lookup"><span data-stu-id="be01b-122">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="be01b-123">Pour plus d’informations sur les programmes de résolution d’homologue, consultez programmes de [résolution d’homologue](../../../wcf/feature-details/peer-resolvers.md).</span><span class="sxs-lookup"><span data-stu-id="be01b-123">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be01b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be01b-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="be01b-125">Programmes de résolution d'homologue</span><span class="sxs-lookup"><span data-stu-id="be01b-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="be01b-126">[Ajout d'un programme de résolution personnalisé à une application PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="be01b-126">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
