---
title: <security> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: f37c336b0e42993e1eef3f06e2f919705f425a2e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169958"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="aa2ba-102">\<security> de \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="aa2ba-102">\<security> of \<peerTransport></span></span>

<span data-ttu-id="aa2ba-103">Contient les paramètres de sécurité associés à un canal homologue, y compris le type d'authentification utilisé et la sécurité utilisée pour le transport de messages.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="aa2ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa2ba-104">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa2ba-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="aa2ba-105">Attributes and Elements</span></span>  

 <span data-ttu-id="aa2ba-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa2ba-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="aa2ba-107">Attributes</span></span>  
  
|<span data-ttu-id="aa2ba-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="aa2ba-108">Attribute</span></span>|<span data-ttu-id="aa2ba-109">Description</span><span class="sxs-lookup"><span data-stu-id="aa2ba-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="aa2ba-110">Spécifie le type de sécurité à appliquer.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-110">Specifies the type of security to be applied.</span></span> <span data-ttu-id="aa2ba-111">La valeur par défaut est Message.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-111">The default value is Message.</span></span> <span data-ttu-id="aa2ba-112">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-112">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="aa2ba-113">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="aa2ba-113">mode Attribute</span></span>  
  
|<span data-ttu-id="aa2ba-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="aa2ba-114">Value</span></span>|<span data-ttu-id="aa2ba-115">Description</span><span class="sxs-lookup"><span data-stu-id="aa2ba-115">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="aa2ba-116">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-116">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="aa2ba-117">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-117">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="aa2ba-118">La sécurité SOAP assure l'authentification, l'intégrité et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-118">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="aa2ba-119">Le protocole HTTPS assure l'authentification et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-119">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="aa2ba-120">Les messages SOAP fournissent des types d'informations d'identification enrichies.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-120">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa2ba-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="aa2ba-121">Child Elements</span></span>  
  
|<span data-ttu-id="aa2ba-122">Élément</span><span class="sxs-lookup"><span data-stu-id="aa2ba-122">Element</span></span>|<span data-ttu-id="aa2ba-123">Description</span><span class="sxs-lookup"><span data-stu-id="aa2ba-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="aa2ba-124">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-124">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="aa2ba-125">Cet élément dispose d'un attribut `clientCredentialType` qui spécifie les informations d'identification à utiliser lors de l'interaction avec un service.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-125">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="aa2ba-126">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-126">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="aa2ba-127">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-127">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa2ba-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="aa2ba-128">Parent Elements</span></span>  
  
|<span data-ttu-id="aa2ba-129">Élément</span><span class="sxs-lookup"><span data-stu-id="aa2ba-129">Element</span></span>|<span data-ttu-id="aa2ba-130">Description</span><span class="sxs-lookup"><span data-stu-id="aa2ba-130">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="aa2ba-131">Définit un transport d’homologue pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="aa2ba-131">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa2ba-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa2ba-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="aa2ba-133">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="aa2ba-133">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="aa2ba-134">Transports</span><span class="sxs-lookup"><span data-stu-id="aa2ba-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="aa2ba-135">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="aa2ba-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="aa2ba-136">Liaisons</span><span class="sxs-lookup"><span data-stu-id="aa2ba-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aa2ba-137">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="aa2ba-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="aa2ba-138">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="aa2ba-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
