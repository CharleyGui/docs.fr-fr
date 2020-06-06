---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855172"
---
# \<headers>
<span data-ttu-id="a9ad9-101">Un point de terminaison peut être adressé par un ou plusieurs en-têtes SOAP en plus de son URI de base.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-101">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="a9ad9-102">Le jeu de scénarios où cette opération est utile est un jeu de scénarios intermédiaires SOAP où un point de terminaison requiert que les clients de ce point de terminaison incluent des en-têtes SOAP destinés à des intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-102">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="a9ad9-103">Cet élément de configuration peut être utilisé pour définir ces en-têtes d'adresse personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-103">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="a9ad9-104">Les entrées de la collection d’en-têtes de points de terminaison sont des éléments XML définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-104">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="a9ad9-105">Chaque élément doit être au format XML adéquat.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-105">Each element has to be well-formed XML.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a><span data-ttu-id="a9ad9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9ad9-106">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9ad9-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a9ad9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a9ad9-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9ad9-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="a9ad9-109">Attributes</span></span>  
 <span data-ttu-id="a9ad9-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a9ad9-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a9ad9-111">Child Elements</span></span>  
 <span data-ttu-id="a9ad9-112">Éléments XML définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-112">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9ad9-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a9ad9-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a9ad9-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a9ad9-114">Element</span></span>|<span data-ttu-id="a9ad9-115">Description</span><span class="sxs-lookup"><span data-stu-id="a9ad9-115">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="a9ad9-116">Configure différents types de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-116">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9ad9-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="a9ad9-117">Remarks</span></span>  
 <span data-ttu-id="a9ad9-118">Les en-têtes facultatifs fournissent des informations d'adressage plus détaillées pour identifier ou interagir avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-118">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="a9ad9-119">Par exemple, les en-tête peuvent indiquer comment traiter un message entrant, où le point de terminaison doit envoyer un message de réponse ou quelle instance d'un service utiliser pour traiter un message entrant d'un utilisateur particulier lorsque plusieurs instances sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="a9ad9-119">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ad9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9ad9-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="a9ad9-121">Points de terminaison : adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="a9ad9-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
