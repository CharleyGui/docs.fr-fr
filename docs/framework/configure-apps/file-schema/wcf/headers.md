---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: a982fa87ab84725e36ee913f00200cd34f0b8f6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925575"
---
# <a name="headers"></a><span data-ttu-id="c8ae2-101">\<headers></span><span class="sxs-lookup"><span data-stu-id="c8ae2-101">\<headers></span></span>
<span data-ttu-id="c8ae2-102">Un point de terminaison peut être adressé par un ou plusieurs en-têtes SOAP en plus de son URI de base.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="c8ae2-103">Le jeu de scénarios où cette opération est utile est un jeu de scénarios intermédiaires SOAP où un point de terminaison requiert que les clients de ce point de terminaison incluent des en-têtes SOAP destinés à des intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="c8ae2-104">Cet élément de configuration peut être utilisé pour définir ces en-têtes d'adresse personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="c8ae2-105">Les entrées de la collection d’en-têtes de points de terminaison sont des éléments XML définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="c8ae2-106">Chaque élément doit être au format XML adéquat.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="c8ae2-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c8ae2-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="c8ae2-108">\<client></span><span class="sxs-lookup"><span data-stu-id="c8ae2-108">\<client></span></span>  
<span data-ttu-id="c8ae2-109">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="c8ae2-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8ae2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8ae2-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8ae2-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c8ae2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c8ae2-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8ae2-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="c8ae2-113">Attributes</span></span>  
 <span data-ttu-id="c8ae2-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c8ae2-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c8ae2-115">Child Elements</span></span>  
 <span data-ttu-id="c8ae2-116">Éléments XML définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8ae2-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c8ae2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c8ae2-118">Élément</span><span class="sxs-lookup"><span data-stu-id="c8ae2-118">Element</span></span>|<span data-ttu-id="c8ae2-119">Description</span><span class="sxs-lookup"><span data-stu-id="c8ae2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8ae2-120">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="c8ae2-120">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="c8ae2-121">Configure différents types de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8ae2-122">Notes</span><span class="sxs-lookup"><span data-stu-id="c8ae2-122">Remarks</span></span>  
 <span data-ttu-id="c8ae2-123">Les en-têtes facultatifs fournissent des informations d'adressage plus détaillées pour identifier ou interagir avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="c8ae2-124">Par exemple, les en-tête peuvent indiquer comment traiter un message entrant, où le point de terminaison doit envoyer un message de réponse ou quelle instance d'un service utiliser pour traiter un message entrant d'un utilisateur particulier lorsque plusieurs instances sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="c8ae2-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ae2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8ae2-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="c8ae2-126">Terminaison Adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="c8ae2-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
