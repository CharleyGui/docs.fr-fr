---
title: <security> de <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 543c57d6b2dba1ff5934b49e0e219cf2e5cad153
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170023"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="8c813-102">\<security> de \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="8c813-102">\<security> of \<netPeerBinding></span></span>

<span data-ttu-id="8c813-103">Définit les paramètres de sécurité du [\<netPeerTcpBinding>](netpeertcpbinding.md) , y compris le type d’authentification utilisé et la sécurité utilisée pour le transport des messages.</span><span class="sxs-lookup"><span data-stu-id="8c813-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="8c813-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c813-104">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c813-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8c813-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8c813-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8c813-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c813-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="8c813-107">Attributes</span></span>  
  
|<span data-ttu-id="8c813-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="8c813-108">Attribute</span></span>|<span data-ttu-id="8c813-109">Description</span><span class="sxs-lookup"><span data-stu-id="8c813-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c813-110">mode</span><span class="sxs-lookup"><span data-stu-id="8c813-110">mode</span></span>|<span data-ttu-id="8c813-111">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="8c813-111">Optional.</span></span> <span data-ttu-id="8c813-112">Spécifie le type de sécurité utilisé par les homologues configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="8c813-112">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="8c813-113">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="8c813-113">The default value is `Message`.</span></span> <span data-ttu-id="8c813-114">Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="8c813-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8c813-115">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="8c813-115">mode Attribute</span></span>  
  
|<span data-ttu-id="8c813-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="8c813-116">Value</span></span>|<span data-ttu-id="8c813-117">Description</span><span class="sxs-lookup"><span data-stu-id="8c813-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8c813-118">Message</span><span class="sxs-lookup"><span data-stu-id="8c813-118">Message</span></span>|<span data-ttu-id="8c813-119">La sécurité SOAP assure l'authentification, l'intégrité et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="8c813-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="8c813-120">None</span><span class="sxs-lookup"><span data-stu-id="8c813-120">None</span></span>|<span data-ttu-id="8c813-121">La sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="8c813-121">Security is disabled.</span></span>|  
|<span data-ttu-id="8c813-122">Transport</span><span class="sxs-lookup"><span data-stu-id="8c813-122">Transport</span></span>|<span data-ttu-id="8c813-123">La sécurité est fournie à l'aide de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8c813-123">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="8c813-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="8c813-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="8c813-125">Le protocole HTTPS assure l'authentification et la confidentialité.</span><span class="sxs-lookup"><span data-stu-id="8c813-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="8c813-126">Les messages SOAP fournissent des types d'informations d'identification enrichies.</span><span class="sxs-lookup"><span data-stu-id="8c813-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c813-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8c813-127">Child Elements</span></span>  
  
|<span data-ttu-id="8c813-128">Élément</span><span class="sxs-lookup"><span data-stu-id="8c813-128">Element</span></span>|<span data-ttu-id="8c813-129">Description</span><span class="sxs-lookup"><span data-stu-id="8c813-129">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="8c813-130">Définit le type de transport pour les messages sécurisés envoyés par des homologues configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="8c813-130">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="8c813-131">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="8c813-131">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c813-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8c813-132">Parent Elements</span></span>  
  
|<span data-ttu-id="8c813-133">Élément</span><span class="sxs-lookup"><span data-stu-id="8c813-133">Element</span></span>|<span data-ttu-id="8c813-134">Description</span><span class="sxs-lookup"><span data-stu-id="8c813-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8c813-135">Définit toutes les fonctions de liaison de [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8c813-135">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c813-136">Notes</span><span class="sxs-lookup"><span data-stu-id="8c813-136">Remarks</span></span>  

 <span data-ttu-id="8c813-137">La sécurité peut être spécifique au message ou au transport.</span><span class="sxs-lookup"><span data-stu-id="8c813-137">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c813-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c813-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="8c813-139">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="8c813-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8c813-140">Sélection d'un type d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="8c813-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="8c813-141">Liaisons</span><span class="sxs-lookup"><span data-stu-id="8c813-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8c813-142">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="8c813-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8c813-143">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="8c813-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
