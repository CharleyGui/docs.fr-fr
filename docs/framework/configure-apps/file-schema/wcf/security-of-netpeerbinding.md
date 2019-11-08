---
title: <security> de <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738663"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="1eae7-102">\<> de sécurité de \<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="1eae7-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="1eae7-103">Définit les paramètres de sécurité de l' [\<NetPeerTcpBinding](netpeertcpbinding.md), y compris le type d’authentification utilisé et la sécurité utilisée pour le transport de messages.</span><span class="sxs-lookup"><span data-stu-id="1eae7-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="1eae7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1eae7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1eae7-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="1eae7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1eae7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="1eae7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="1eae7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**NetPeerTcpBinding**](netpeertcpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="1eae7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="1eae7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="1eae7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="1eae7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="1eae7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eae7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1eae7-110">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1eae7-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1eae7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1eae7-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1eae7-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1eae7-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="1eae7-113">Attributes</span></span>  
  
|<span data-ttu-id="1eae7-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="1eae7-114">Attribute</span></span>|<span data-ttu-id="1eae7-115">Description</span><span class="sxs-lookup"><span data-stu-id="1eae7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1eae7-116">mode</span><span class="sxs-lookup"><span data-stu-id="1eae7-116">mode</span></span>|<span data-ttu-id="1eae7-117">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="1eae7-117">Optional.</span></span> <span data-ttu-id="1eae7-118">Spécifie le type de sécurité utilisé par les homologues configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="1eae7-118">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="1eae7-119">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="1eae7-119">The default value is `Message`.</span></span> <span data-ttu-id="1eae7-120">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="1eae7-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="1eae7-121">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="1eae7-121">mode Attribute</span></span>  
  
|<span data-ttu-id="1eae7-122">valeur</span><span class="sxs-lookup"><span data-stu-id="1eae7-122">Value</span></span>|<span data-ttu-id="1eae7-123">Description</span><span class="sxs-lookup"><span data-stu-id="1eae7-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1eae7-124">Message</span><span class="sxs-lookup"><span data-stu-id="1eae7-124">Message</span></span>|<span data-ttu-id="1eae7-125">La sécurité SOAP assure l'authentification, l'intégrité et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="1eae7-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="1eae7-126">aucune.</span><span class="sxs-lookup"><span data-stu-id="1eae7-126">None</span></span>|<span data-ttu-id="1eae7-127">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="1eae7-127">Security is disabled.</span></span>|  
|<span data-ttu-id="1eae7-128">Transport</span><span class="sxs-lookup"><span data-stu-id="1eae7-128">Transport</span></span>|<span data-ttu-id="1eae7-129">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1eae7-129">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="1eae7-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="1eae7-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="1eae7-131">Le protocole HTTPS assure l'authentification et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="1eae7-131">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="1eae7-132">Les messages SOAP fournissent des types d'informations d'identification enrichies.</span><span class="sxs-lookup"><span data-stu-id="1eae7-132">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1eae7-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1eae7-133">Child Elements</span></span>  
  
|<span data-ttu-id="1eae7-134">Élément</span><span class="sxs-lookup"><span data-stu-id="1eae7-134">Element</span></span>|<span data-ttu-id="1eae7-135">Description</span><span class="sxs-lookup"><span data-stu-id="1eae7-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1eae7-136">> de transport \<</span><span class="sxs-lookup"><span data-stu-id="1eae7-136">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="1eae7-137">Définit le type de transport pour les messages sécurisés envoyés par des homologues configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="1eae7-137">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="1eae7-138">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1eae7-138">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1eae7-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1eae7-139">Parent Elements</span></span>  
  
|<span data-ttu-id="1eae7-140">Élément</span><span class="sxs-lookup"><span data-stu-id="1eae7-140">Element</span></span>|<span data-ttu-id="1eae7-141">Description</span><span class="sxs-lookup"><span data-stu-id="1eae7-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1eae7-142">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="1eae7-142">\<binding></span></span>](bindings.md)|<span data-ttu-id="1eae7-143">Définit toutes les fonctions de liaison du [\<NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1eae7-143">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eae7-144">Notes</span><span class="sxs-lookup"><span data-stu-id="1eae7-144">Remarks</span></span>  
 <span data-ttu-id="1eae7-145">La sécurité peut être spécifique au message ou au transport.</span><span class="sxs-lookup"><span data-stu-id="1eae7-145">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eae7-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1eae7-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="1eae7-147">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="1eae7-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1eae7-148">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="1eae7-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="1eae7-149">Liaisons</span><span class="sxs-lookup"><span data-stu-id="1eae7-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1eae7-150">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="1eae7-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1eae7-151">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="1eae7-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1eae7-152">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="1eae7-152">\<binding></span></span>](bindings.md)
