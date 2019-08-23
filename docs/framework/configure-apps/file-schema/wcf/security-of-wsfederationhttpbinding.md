---
title: <security> de <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 875ce7d548d59f32465da817e9e956217f346f60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936537"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="7fca8-102">\<> de sécurité \<de wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="7fca8-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="7fca8-103">Définit les paramètres de sécurité de l' [ \<> WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7fca8-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="7fca8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7fca8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7fca8-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7fca8-105">\<bindings></span></span>  
<span data-ttu-id="7fca8-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="7fca8-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="7fca8-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="7fca8-107">\<binding></span></span>  
<span data-ttu-id="7fca8-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="7fca8-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fca8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fca8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fca8-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7fca8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7fca8-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7fca8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fca8-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="7fca8-112">Attributes</span></span>  
  
|<span data-ttu-id="7fca8-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="7fca8-113">Attribute</span></span>|<span data-ttu-id="7fca8-114">Description</span><span class="sxs-lookup"><span data-stu-id="7fca8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fca8-115">Mode</span><span class="sxs-lookup"><span data-stu-id="7fca8-115">Mode</span></span>|<span data-ttu-id="7fca8-116">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7fca8-116">Optional.</span></span> <span data-ttu-id="7fca8-117">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="7fca8-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="7fca8-118">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="7fca8-118">The default value is `Message`.</span></span> <span data-ttu-id="7fca8-119">Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="7fca8-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="7fca8-120">Mode, attribut</span><span class="sxs-lookup"><span data-stu-id="7fca8-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="7fca8-121">`Value`</span><span class="sxs-lookup"><span data-stu-id="7fca8-121">Value</span></span>|<span data-ttu-id="7fca8-122">Description</span><span class="sxs-lookup"><span data-stu-id="7fca8-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7fca8-123">Aucun</span><span class="sxs-lookup"><span data-stu-id="7fca8-123">None</span></span>|<span data-ttu-id="7fca8-124">Le message SOAP n'est pas sécurisé pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="7fca8-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="7fca8-125">Message</span><span class="sxs-lookup"><span data-stu-id="7fca8-125">Message</span></span>|<span data-ttu-id="7fca8-126">L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="7fca8-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="7fca8-127">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="7fca8-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="7fca8-128">Le service doit être configuré avec un certificat.</span><span class="sxs-lookup"><span data-stu-id="7fca8-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="7fca8-129">L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité</span><span class="sxs-lookup"><span data-stu-id="7fca8-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="7fca8-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="7fca8-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="7fca8-131">L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7fca8-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="7fca8-132">Le service doit être configuré avec un certificat.</span><span class="sxs-lookup"><span data-stu-id="7fca8-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="7fca8-133">L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7fca8-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fca8-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7fca8-134">Child Elements</span></span>  
  
|<span data-ttu-id="7fca8-135">Élément</span><span class="sxs-lookup"><span data-stu-id="7fca8-135">Element</span></span>|<span data-ttu-id="7fca8-136">Description</span><span class="sxs-lookup"><span data-stu-id="7fca8-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fca8-137">\<message></span><span class="sxs-lookup"><span data-stu-id="7fca8-137">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="7fca8-138">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="7fca8-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="7fca8-139">Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="7fca8-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7fca8-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7fca8-140">Parent Elements</span></span>  
  
|<span data-ttu-id="7fca8-141">Élément</span><span class="sxs-lookup"><span data-stu-id="7fca8-141">Element</span></span>|<span data-ttu-id="7fca8-142">Description</span><span class="sxs-lookup"><span data-stu-id="7fca8-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fca8-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="7fca8-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="7fca8-144">Définit toutes les fonctions de liaison de l' [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7fca8-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fca8-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fca8-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="7fca8-146">Guide pratique : Créer un WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7fca8-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="7fca8-147">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7fca8-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7fca8-148">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="7fca8-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="7fca8-149">Liaisons</span><span class="sxs-lookup"><span data-stu-id="7fca8-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7fca8-150">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="7fca8-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7fca8-151">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7fca8-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7fca8-152">\<binding></span><span class="sxs-lookup"><span data-stu-id="7fca8-152">\<binding></span></span>](../../../misc/binding.md)
