---
title: élément <security> de <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738726"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="597d1-102">\<> élément de sécurité de \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="597d1-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="597d1-103">Définit les paramètres de sécurité de l’élément [\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="597d1-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="597d1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="597d1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="597d1-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="597d1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="597d1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="597d1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="597d1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**WS2007FederationHttpBinding**](ws2007federationhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="597d1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="597d1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="597d1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="597d1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="597d1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="597d1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="597d1-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="597d1-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="597d1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="597d1-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="597d1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="597d1-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="597d1-113">Attributes</span></span>  
  
|<span data-ttu-id="597d1-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="597d1-114">Attribute</span></span>|<span data-ttu-id="597d1-115">Description</span><span class="sxs-lookup"><span data-stu-id="597d1-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="597d1-116">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="597d1-116">Optional.</span></span> <span data-ttu-id="597d1-117">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="597d1-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="597d1-118">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="597d1-118">The default value is `Message`.</span></span> <span data-ttu-id="597d1-119">Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="597d1-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="597d1-120">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="597d1-120">mode Attribute</span></span>  
  
|<span data-ttu-id="597d1-121">valeur</span><span class="sxs-lookup"><span data-stu-id="597d1-121">Value</span></span>|<span data-ttu-id="597d1-122">Description</span><span class="sxs-lookup"><span data-stu-id="597d1-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="597d1-123">aucune.</span><span class="sxs-lookup"><span data-stu-id="597d1-123">None</span></span>|<span data-ttu-id="597d1-124">Le message SOAP n'est pas sécurisé pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="597d1-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="597d1-125">Message</span><span class="sxs-lookup"><span data-stu-id="597d1-125">Message</span></span>|<span data-ttu-id="597d1-126">L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="597d1-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="597d1-127">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="597d1-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="597d1-128">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="597d1-128">The service must be configured with a certificate.</span></span> <span data-ttu-id="597d1-129">L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="597d1-129">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="597d1-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="597d1-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="597d1-131">L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="597d1-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="597d1-132">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="597d1-132">The service must be configured with a certificate.</span></span> <span data-ttu-id="597d1-133">L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="597d1-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="597d1-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="597d1-134">Child Elements</span></span>  
  
|<span data-ttu-id="597d1-135">Élément</span><span class="sxs-lookup"><span data-stu-id="597d1-135">Element</span></span>|<span data-ttu-id="597d1-136">Description</span><span class="sxs-lookup"><span data-stu-id="597d1-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="597d1-137">message de \<</span><span class="sxs-lookup"><span data-stu-id="597d1-137">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="597d1-138">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="597d1-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="597d1-139">Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="597d1-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="597d1-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="597d1-140">Parent Elements</span></span>  
  
|<span data-ttu-id="597d1-141">Élément</span><span class="sxs-lookup"><span data-stu-id="597d1-141">Element</span></span>|<span data-ttu-id="597d1-142">Description</span><span class="sxs-lookup"><span data-stu-id="597d1-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="597d1-143">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="597d1-143">\<binding></span></span>](bindings.md)|<span data-ttu-id="597d1-144">Définit toutes les fonctions de liaison du [\<WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="597d1-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="597d1-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="597d1-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="597d1-146">Guide pratique pour créer une liaison WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="597d1-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="597d1-147">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="597d1-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="597d1-148">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="597d1-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="597d1-149">Liaisons</span><span class="sxs-lookup"><span data-stu-id="597d1-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="597d1-150">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="597d1-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="597d1-151">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="597d1-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="597d1-152">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="597d1-152">\<binding></span></span>](bindings.md)
