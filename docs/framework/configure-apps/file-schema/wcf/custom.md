---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 4077aacab1c1c4594db76cc6663bfc0245d345d7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555495"
---
# \<custom>
<span data-ttu-id="95ecd-101">Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="95ecd-101">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="95ecd-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95ecd-102">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95ecd-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="95ecd-103">Attributes and Elements</span></span>  
 <span data-ttu-id="95ecd-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="95ecd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95ecd-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="95ecd-105">Attributes</span></span>  
  
|<span data-ttu-id="95ecd-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="95ecd-106">Attribute</span></span>|<span data-ttu-id="95ecd-107">Description</span><span class="sxs-lookup"><span data-stu-id="95ecd-107">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="95ecd-108">URI indiquant l'adresse de point de terminaison du nœud homologue qui héberge le service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="95ecd-108">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="95ecd-109">Chaîne contenant le type du service de programme de résolution d'homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="95ecd-109">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95ecd-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="95ecd-110">Child Elements</span></span>  
  
|<span data-ttu-id="95ecd-111">Élément</span><span class="sxs-lookup"><span data-stu-id="95ecd-111">Element</span></span>|<span data-ttu-id="95ecd-112">Description</span><span class="sxs-lookup"><span data-stu-id="95ecd-112">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="95ecd-113">Indique l'identité des programmes de résolution d'homologue personnalisés configurés avec cet élément.</span><span class="sxs-lookup"><span data-stu-id="95ecd-113">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="95ecd-114">Cet élément est de type <xref:System.ServiceModel.Configuration.IdentityElement>.</span><span class="sxs-lookup"><span data-stu-id="95ecd-114">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="95ecd-115">Collection d’en-têtes d’adresse utilisée pour les messages SOAP gérés par le programme de résolution d’homologue personnalisé.</span><span class="sxs-lookup"><span data-stu-id="95ecd-115">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95ecd-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="95ecd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="95ecd-117">Élément</span><span class="sxs-lookup"><span data-stu-id="95ecd-117">Element</span></span>|<span data-ttu-id="95ecd-118">Description</span><span class="sxs-lookup"><span data-stu-id="95ecd-118">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="95ecd-119">Un programme de résolution d'homologue est utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds homologues représentant plusieurs nœuds faisant partie de la maille.</span><span class="sxs-lookup"><span data-stu-id="95ecd-119">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95ecd-120">Notes</span><span class="sxs-lookup"><span data-stu-id="95ecd-120">Remarks</span></span>  
 <span data-ttu-id="95ecd-121">Cet élément définit les paramètres de base pour un service de programme de résolution d'homologue personnalisé, y compris l'adresse de point de terminaison de l'homologue qui héberge le service et tous les paramètres de liaison spécifiques.</span><span class="sxs-lookup"><span data-stu-id="95ecd-121">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="95ecd-122">Pour plus d’informations sur la création d’un programme de résolution personnalisé, consultez [Ajout d’un programme de résolution personnalisé à une application PeerChannel](/previous-versions/ms730105(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="95ecd-122">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ecd-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95ecd-123">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="95ecd-124">Programmes de résolution d'homologue</span><span class="sxs-lookup"><span data-stu-id="95ecd-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="95ecd-125">[Ajout d'un programme de résolution personnalisé à une application PeerChannel](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="95ecd-125">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
