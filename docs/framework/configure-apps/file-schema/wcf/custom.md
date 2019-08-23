---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: b5cc522604fa7aca8ca6eae787520265b36fef6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925952"
---
# <a name="custom"></a><span data-ttu-id="bdb96-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="bdb96-101">\<custom></span></span>
<span data-ttu-id="bdb96-102">Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="bdb96-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="bdb96-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bdb96-103">\<system.serviceModel></span></span>  
<span data-ttu-id="bdb96-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bdb96-104">\<bindings></span></span>  
<span data-ttu-id="bdb96-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="bdb96-105">\<netPeerBinding></span></span>  
<span data-ttu-id="bdb96-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="bdb96-106">\<binding></span></span>  
<span data-ttu-id="bdb96-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="bdb96-107">\<resolver></span></span>  
<span data-ttu-id="bdb96-108">\<custom></span><span class="sxs-lookup"><span data-stu-id="bdb96-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb96-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdb96-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdb96-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bdb96-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bdb96-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bdb96-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdb96-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="bdb96-112">Attributes</span></span>  
  
|<span data-ttu-id="bdb96-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="bdb96-113">Attribute</span></span>|<span data-ttu-id="bdb96-114">Description</span><span class="sxs-lookup"><span data-stu-id="bdb96-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="bdb96-115">URI indiquant l'adresse de point de terminaison du nœud homologue qui héberge le service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="bdb96-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="bdb96-116">Chaîne contenant le type du service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="bdb96-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bdb96-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bdb96-117">Child Elements</span></span>  
  
|<span data-ttu-id="bdb96-118">Élément</span><span class="sxs-lookup"><span data-stu-id="bdb96-118">Element</span></span>|<span data-ttu-id="bdb96-119">Description</span><span class="sxs-lookup"><span data-stu-id="bdb96-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdb96-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="bdb96-120">\<identity></span></span>](identity.md)|<span data-ttu-id="bdb96-121">Indique l'identité des programmes de résolution d'homologue personnalisés configurés avec cet élément.</span><span class="sxs-lookup"><span data-stu-id="bdb96-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="bdb96-122">Cet élément est de type <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="bdb96-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="bdb96-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="bdb96-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="bdb96-124">Collection d’en-têtes d’adresse utilisée pour les messages SOAP gérés par le programme de résolution d’homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="bdb96-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bdb96-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bdb96-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bdb96-126">Élément</span><span class="sxs-lookup"><span data-stu-id="bdb96-126">Element</span></span>|<span data-ttu-id="bdb96-127">Description</span><span class="sxs-lookup"><span data-stu-id="bdb96-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdb96-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="bdb96-128">\<resolver></span></span>](resolver.md)|<span data-ttu-id="bdb96-129">Un programme de résolution d'homologue est utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds homologues représentant plusieurs nœuds faisant partie de la maille.</span><span class="sxs-lookup"><span data-stu-id="bdb96-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdb96-130">Notes</span><span class="sxs-lookup"><span data-stu-id="bdb96-130">Remarks</span></span>  
 <span data-ttu-id="bdb96-131">Cet élément définit les paramètres de base pour un service de programme de résolution d'homologue personnalisé, y compris l'adresse de point de terminaison de l'homologue qui héberge le service et tous les paramètres de liaison spécifiques.</span><span class="sxs-lookup"><span data-stu-id="bdb96-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="bdb96-132">Pour plus d’informations sur la création d’un programme de résolution personnalisé, consultez [Ajout d’un programme de résolution personnalisé à une application PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="bdb96-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb96-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdb96-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="bdb96-134">Programmes de résolution d’homologue</span><span class="sxs-lookup"><span data-stu-id="bdb96-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="bdb96-135">[Ajout d’un programme de résolution personnalisé à une application PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bdb96-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
