---
title: <security> de <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 6c07d1ca18837f66548411262b84b9a326f5ec4a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399729"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="d6417-102">\<> de sécurité \<de wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d6417-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="d6417-103">Définit les paramètres de sécurité de l' [ \<> WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d6417-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="d6417-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d6417-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d6417-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d6417-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d6417-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d6417-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d6417-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d6417-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d6417-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="d6417-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d6417-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de sécurité**</span><span class="sxs-lookup"><span data-stu-id="d6417-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6417-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6417-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6417-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d6417-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6417-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d6417-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6417-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="d6417-113">Attributes</span></span>  
  
|<span data-ttu-id="d6417-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="d6417-114">Attribute</span></span>|<span data-ttu-id="d6417-115">Description</span><span class="sxs-lookup"><span data-stu-id="d6417-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6417-116">Mode</span><span class="sxs-lookup"><span data-stu-id="d6417-116">Mode</span></span>|<span data-ttu-id="d6417-117">facultatif.</span><span class="sxs-lookup"><span data-stu-id="d6417-117">Optional.</span></span> <span data-ttu-id="d6417-118">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="d6417-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d6417-119">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="d6417-119">The default value is `Message`.</span></span> <span data-ttu-id="d6417-120">Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d6417-120">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d6417-121">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="d6417-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="d6417-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="d6417-122">Value</span></span>|<span data-ttu-id="d6417-123">Description</span><span class="sxs-lookup"><span data-stu-id="d6417-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6417-124">Aucun</span><span class="sxs-lookup"><span data-stu-id="d6417-124">None</span></span>|<span data-ttu-id="d6417-125">Le message SOAP n'est pas sécurisé pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="d6417-125">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="d6417-126">Message</span><span class="sxs-lookup"><span data-stu-id="d6417-126">Message</span></span>|<span data-ttu-id="d6417-127">L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="d6417-127">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="d6417-128">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="d6417-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="d6417-129">Le service doit être configuré avec un certificat.</span><span class="sxs-lookup"><span data-stu-id="d6417-129">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="d6417-130">L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité</span><span class="sxs-lookup"><span data-stu-id="d6417-130">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="d6417-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d6417-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="d6417-132">L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d6417-132">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="d6417-133">Le service doit être configuré avec un certificat.</span><span class="sxs-lookup"><span data-stu-id="d6417-133">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="d6417-134">L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d6417-134">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6417-135">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d6417-135">Child Elements</span></span>  
  
|<span data-ttu-id="d6417-136">Élément</span><span class="sxs-lookup"><span data-stu-id="d6417-136">Element</span></span>|<span data-ttu-id="d6417-137">Description</span><span class="sxs-lookup"><span data-stu-id="d6417-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6417-138">\<message></span><span class="sxs-lookup"><span data-stu-id="d6417-138">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="d6417-139">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="d6417-139">Defines the settings for the message-level security.</span></span> <span data-ttu-id="d6417-140">Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="d6417-140">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6417-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d6417-141">Parent Elements</span></span>  
  
|<span data-ttu-id="d6417-142">Élément</span><span class="sxs-lookup"><span data-stu-id="d6417-142">Element</span></span>|<span data-ttu-id="d6417-143">Description</span><span class="sxs-lookup"><span data-stu-id="d6417-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6417-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="d6417-144">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="d6417-145">Définit toutes les fonctions de liaison de l' [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d6417-145">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6417-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6417-146">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="d6417-147">Guide pratique : Créer un WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d6417-147">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="d6417-148">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d6417-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d6417-149">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="d6417-149">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="d6417-150">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d6417-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d6417-151">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="d6417-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d6417-152">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d6417-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d6417-153">\<binding></span><span class="sxs-lookup"><span data-stu-id="d6417-153">\<binding></span></span>](../../../misc/binding.md)
