---
title: <security>élément de<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 61b56ca1fae5c328cda0bbebef4026f0784095a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936823"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="0eba1-102">\<élément Security > de \<WS2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0eba1-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="0eba1-103">Définit les paramètres de sécurité de l' [ \<élément WS2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0eba1-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="0eba1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0eba1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0eba1-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0eba1-105">\<bindings></span></span>  
<span data-ttu-id="0eba1-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0eba1-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="0eba1-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="0eba1-107">\<binding></span></span>  
<span data-ttu-id="0eba1-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="0eba1-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eba1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eba1-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eba1-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0eba1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0eba1-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0eba1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eba1-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="0eba1-112">Attributes</span></span>  
  
|<span data-ttu-id="0eba1-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="0eba1-113">Attribute</span></span>|<span data-ttu-id="0eba1-114">Description</span><span class="sxs-lookup"><span data-stu-id="0eba1-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="0eba1-115">facultatif.</span><span class="sxs-lookup"><span data-stu-id="0eba1-115">Optional.</span></span> <span data-ttu-id="0eba1-116">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="0eba1-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="0eba1-117">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="0eba1-117">The default value is `Message`.</span></span> <span data-ttu-id="0eba1-118">Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0eba1-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0eba1-119">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="0eba1-119">mode Attribute</span></span>  
  
|<span data-ttu-id="0eba1-120">`Value`</span><span class="sxs-lookup"><span data-stu-id="0eba1-120">Value</span></span>|<span data-ttu-id="0eba1-121">Description</span><span class="sxs-lookup"><span data-stu-id="0eba1-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0eba1-122">Aucun</span><span class="sxs-lookup"><span data-stu-id="0eba1-122">None</span></span>|<span data-ttu-id="0eba1-123">Le message SOAP n'est pas sécurisé pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="0eba1-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="0eba1-124">Message</span><span class="sxs-lookup"><span data-stu-id="0eba1-124">Message</span></span>|<span data-ttu-id="0eba1-125">L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="0eba1-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="0eba1-126">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="0eba1-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="0eba1-127">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="0eba1-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="0eba1-128">L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0eba1-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="0eba1-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="0eba1-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="0eba1-130">L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0eba1-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="0eba1-131">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="0eba1-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="0eba1-132">L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0eba1-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eba1-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0eba1-133">Child Elements</span></span>  
  
|<span data-ttu-id="0eba1-134">Élément</span><span class="sxs-lookup"><span data-stu-id="0eba1-134">Element</span></span>|<span data-ttu-id="0eba1-135">Description</span><span class="sxs-lookup"><span data-stu-id="0eba1-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eba1-136">\<message></span><span class="sxs-lookup"><span data-stu-id="0eba1-136">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="0eba1-137">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="0eba1-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="0eba1-138">Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="0eba1-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0eba1-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0eba1-139">Parent Elements</span></span>  
  
|<span data-ttu-id="0eba1-140">Élément</span><span class="sxs-lookup"><span data-stu-id="0eba1-140">Element</span></span>|<span data-ttu-id="0eba1-141">Description</span><span class="sxs-lookup"><span data-stu-id="0eba1-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eba1-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="0eba1-142">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="0eba1-143">Définit toutes les fonctions de liaison de l' [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0eba1-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0eba1-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eba1-144">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="0eba1-145">Guide pratique pour Créer un WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0eba1-145">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="0eba1-146">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="0eba1-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0eba1-147">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="0eba1-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="0eba1-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="0eba1-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0eba1-149">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="0eba1-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0eba1-150">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="0eba1-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0eba1-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="0eba1-151">\<binding></span></span>](../../../misc/binding.md)
