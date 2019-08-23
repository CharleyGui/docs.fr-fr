---
title: <security> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: bdd3b236c9bae198f8027c4ca0c0fa5b70d30342
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936640"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="d43f2-102">\<> de sécurité \<de peerTransport ></span><span class="sxs-lookup"><span data-stu-id="d43f2-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="d43f2-103">Contient les paramètres de sécurité associés à un canal homologue, y compris le type d'authentification utilisé et la sécurité utilisée pour le transport de messages.</span><span class="sxs-lookup"><span data-stu-id="d43f2-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="d43f2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d43f2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d43f2-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d43f2-105">\<bindings></span></span>  
<span data-ttu-id="d43f2-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d43f2-106">\<customBinding></span></span>  
<span data-ttu-id="d43f2-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="d43f2-107">\<binding></span></span>  
<span data-ttu-id="d43f2-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="d43f2-108">\<peerTransport></span></span>  
<span data-ttu-id="d43f2-109">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="d43f2-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d43f2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d43f2-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d43f2-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d43f2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d43f2-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d43f2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d43f2-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="d43f2-113">Attributes</span></span>  
  
|<span data-ttu-id="d43f2-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="d43f2-114">Attribute</span></span>|<span data-ttu-id="d43f2-115">Description</span><span class="sxs-lookup"><span data-stu-id="d43f2-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d43f2-116">Spécifie le type de sécurité à appliquer.</span><span class="sxs-lookup"><span data-stu-id="d43f2-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="d43f2-117">La valeur par défaut est Message.</span><span class="sxs-lookup"><span data-stu-id="d43f2-117">The default value is Message.</span></span> <span data-ttu-id="d43f2-118">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d43f2-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d43f2-119">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="d43f2-119">mode Attribute</span></span>  
  
|<span data-ttu-id="d43f2-120">`Value`</span><span class="sxs-lookup"><span data-stu-id="d43f2-120">Value</span></span>|<span data-ttu-id="d43f2-121">Description</span><span class="sxs-lookup"><span data-stu-id="d43f2-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="d43f2-122">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="d43f2-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="d43f2-123">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d43f2-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="d43f2-124">La sécurité SOAP assure l'authentification, l'intégrité et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="d43f2-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="d43f2-125">Le protocole HTTPS assure l'authentification et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="d43f2-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="d43f2-126">Les messages SOAP fournissent des types d'informations d'identification enrichies.</span><span class="sxs-lookup"><span data-stu-id="d43f2-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d43f2-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d43f2-127">Child Elements</span></span>  
  
|<span data-ttu-id="d43f2-128">Élément</span><span class="sxs-lookup"><span data-stu-id="d43f2-128">Element</span></span>|<span data-ttu-id="d43f2-129">Description</span><span class="sxs-lookup"><span data-stu-id="d43f2-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d43f2-130">\<transport></span><span class="sxs-lookup"><span data-stu-id="d43f2-130">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="d43f2-131">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d43f2-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="d43f2-132">Cet élément dispose d'un attribut `clientCredentialType` qui spécifie les informations d'identification à utiliser lors de l'interaction avec un service.</span><span class="sxs-lookup"><span data-stu-id="d43f2-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="d43f2-133">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d43f2-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="d43f2-134">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="d43f2-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d43f2-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d43f2-135">Parent Elements</span></span>  
  
|<span data-ttu-id="d43f2-136">Élément</span><span class="sxs-lookup"><span data-stu-id="d43f2-136">Element</span></span>|<span data-ttu-id="d43f2-137">Description</span><span class="sxs-lookup"><span data-stu-id="d43f2-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d43f2-138">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="d43f2-138">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="d43f2-139">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d43f2-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d43f2-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d43f2-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d43f2-141">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="d43f2-141">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="d43f2-142">Transports</span><span class="sxs-lookup"><span data-stu-id="d43f2-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="d43f2-143">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="d43f2-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="d43f2-144">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d43f2-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d43f2-145">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="d43f2-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d43f2-146">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="d43f2-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d43f2-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d43f2-147">\<customBinding></span></span>](custombinding.md)
