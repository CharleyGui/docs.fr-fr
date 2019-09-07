---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 598b341e8b09acd11ba215e6add3adf9e44b2b81
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400463"
---
# <a name="custom"></a><span data-ttu-id="75e4a-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="75e4a-101">\<custom></span></span>
<span data-ttu-id="75e4a-102">Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75e4a-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="75e4a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75e4a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75e4a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="75e4a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="75e4a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="75e4a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="75e4a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="75e4a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="75e4a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="75e4a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="75e4a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> du programme de résolution**](resolver.md)</span><span class="sxs-lookup"><span data-stu-id="75e4a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)</span></span>\
<span data-ttu-id="75e4a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> personnalisé**</span><span class="sxs-lookup"><span data-stu-id="75e4a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75e4a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75e4a-110">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75e4a-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="75e4a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="75e4a-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="75e4a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75e4a-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="75e4a-113">Attributes</span></span>  
  
|<span data-ttu-id="75e4a-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="75e4a-114">Attribute</span></span>|<span data-ttu-id="75e4a-115">Description</span><span class="sxs-lookup"><span data-stu-id="75e4a-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="75e4a-116">URI indiquant l'adresse de point de terminaison du nœud homologue qui héberge le service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75e4a-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="75e4a-117">Chaîne contenant le type du service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75e4a-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75e4a-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75e4a-118">Child Elements</span></span>  
  
|<span data-ttu-id="75e4a-119">Élément</span><span class="sxs-lookup"><span data-stu-id="75e4a-119">Element</span></span>|<span data-ttu-id="75e4a-120">Description</span><span class="sxs-lookup"><span data-stu-id="75e4a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75e4a-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="75e4a-121">\<identity></span></span>](identity.md)|<span data-ttu-id="75e4a-122">Indique l'identité des programmes de résolution d'homologue personnalisés configurés avec cet élément.</span><span class="sxs-lookup"><span data-stu-id="75e4a-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="75e4a-123">Cet élément est de type <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="75e4a-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="75e4a-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="75e4a-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="75e4a-125">Collection d’en-têtes d’adresse utilisée pour les messages SOAP gérés par le programme de résolution d’homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="75e4a-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="75e4a-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75e4a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="75e4a-127">Élément</span><span class="sxs-lookup"><span data-stu-id="75e4a-127">Element</span></span>|<span data-ttu-id="75e4a-128">Description</span><span class="sxs-lookup"><span data-stu-id="75e4a-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75e4a-129">\<resolver></span><span class="sxs-lookup"><span data-stu-id="75e4a-129">\<resolver></span></span>](resolver.md)|<span data-ttu-id="75e4a-130">Un programme de résolution d'homologue est utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds homologues représentant plusieurs nœuds faisant partie de la maille.</span><span class="sxs-lookup"><span data-stu-id="75e4a-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75e4a-131">Notes</span><span class="sxs-lookup"><span data-stu-id="75e4a-131">Remarks</span></span>  
 <span data-ttu-id="75e4a-132">Cet élément définit les paramètres de base pour un service de programme de résolution d'homologue personnalisé, y compris l'adresse de point de terminaison de l'homologue qui héberge le service et tous les paramètres de liaison spécifiques.</span><span class="sxs-lookup"><span data-stu-id="75e4a-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="75e4a-133">Pour plus d’informations sur la création d’un programme de résolution personnalisé, consultez [Ajout d’un programme de résolution personnalisé à une application PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="75e4a-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e4a-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75e4a-134">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="75e4a-135">Programmes de résolution d’homologue</span><span class="sxs-lookup"><span data-stu-id="75e4a-135">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="75e4a-136">[Ajout d’un programme de résolution personnalisé à une application PeerChannel](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="75e4a-136">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
