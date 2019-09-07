---
title: <security> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399771"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="00698-102">\<> de sécurité \<de peerTransport ></span><span class="sxs-lookup"><span data-stu-id="00698-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="00698-103">Contient les paramètres de sécurité associés à un canal homologue, y compris le type d'authentification utilisé et la sécurité utilisée pour le transport de messages.</span><span class="sxs-lookup"><span data-stu-id="00698-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="00698-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="00698-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="00698-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="00698-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="00698-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="00698-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="00698-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="00698-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="00698-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="00698-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="00698-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="00698-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="00698-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de sécurité**</span><span class="sxs-lookup"><span data-stu-id="00698-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00698-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00698-111">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00698-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="00698-112">Attributes and Elements</span></span>  
 <span data-ttu-id="00698-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="00698-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00698-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="00698-114">Attributes</span></span>  
  
|<span data-ttu-id="00698-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="00698-115">Attribute</span></span>|<span data-ttu-id="00698-116">Description</span><span class="sxs-lookup"><span data-stu-id="00698-116">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="00698-117">Spécifie le type de sécurité à appliquer.</span><span class="sxs-lookup"><span data-stu-id="00698-117">Specifies the type of security to be applied.</span></span> <span data-ttu-id="00698-118">La valeur par défaut est Message.</span><span class="sxs-lookup"><span data-stu-id="00698-118">The default value is Message.</span></span> <span data-ttu-id="00698-119">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="00698-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="00698-120">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="00698-120">mode Attribute</span></span>  
  
|<span data-ttu-id="00698-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="00698-121">Value</span></span>|<span data-ttu-id="00698-122">Description</span><span class="sxs-lookup"><span data-stu-id="00698-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="00698-123">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="00698-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="00698-124">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="00698-124">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="00698-125">La sécurité SOAP assure l'authentification, l'intégrité et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="00698-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="00698-126">Le protocole HTTPS assure l'authentification et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="00698-126">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="00698-127">Les messages SOAP fournissent des types d'informations d'identification enrichies.</span><span class="sxs-lookup"><span data-stu-id="00698-127">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00698-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="00698-128">Child Elements</span></span>  
  
|<span data-ttu-id="00698-129">Élément</span><span class="sxs-lookup"><span data-stu-id="00698-129">Element</span></span>|<span data-ttu-id="00698-130">Description</span><span class="sxs-lookup"><span data-stu-id="00698-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00698-131">\<transport></span><span class="sxs-lookup"><span data-stu-id="00698-131">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="00698-132">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="00698-132">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="00698-133">Cet élément dispose d'un attribut `clientCredentialType` qui spécifie les informations d'identification à utiliser lors de l'interaction avec un service.</span><span class="sxs-lookup"><span data-stu-id="00698-133">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="00698-134">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="00698-134">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="00698-135">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="00698-135">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00698-136">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="00698-136">Parent Elements</span></span>  
  
|<span data-ttu-id="00698-137">Élément</span><span class="sxs-lookup"><span data-stu-id="00698-137">Element</span></span>|<span data-ttu-id="00698-138">Description</span><span class="sxs-lookup"><span data-stu-id="00698-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00698-139">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="00698-139">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="00698-140">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="00698-140">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00698-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00698-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="00698-142">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="00698-142">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="00698-143">Transports</span><span class="sxs-lookup"><span data-stu-id="00698-143">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="00698-144">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="00698-144">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="00698-145">Liaisons</span><span class="sxs-lookup"><span data-stu-id="00698-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="00698-146">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="00698-146">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="00698-147">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="00698-147">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="00698-148">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="00698-148">\<customBinding></span></span>](custombinding.md)
