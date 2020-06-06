---
title: <security> de <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: ea029444cee331a235c7a2fc140b4321d7530063
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736329"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="d6b7b-102">\<security> de \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d6b7b-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="d6b7b-103">Définit les paramètres de sécurité du [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d6b7b-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="d6b7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6b7b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6b7b-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d6b7b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d6b7b-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6b7b-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="d6b7b-107">Attributes</span></span>  
  
|<span data-ttu-id="d6b7b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="d6b7b-108">Attribute</span></span>|<span data-ttu-id="d6b7b-109">Description</span><span class="sxs-lookup"><span data-stu-id="d6b7b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6b7b-110">Mode</span><span class="sxs-lookup"><span data-stu-id="d6b7b-110">Mode</span></span>|<span data-ttu-id="d6b7b-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-111">Optional.</span></span> <span data-ttu-id="d6b7b-112">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d6b7b-113">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-113">The default value is `Message`.</span></span> <span data-ttu-id="d6b7b-114">Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d6b7b-115">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="d6b7b-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="d6b7b-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="d6b7b-116">Value</span></span>|<span data-ttu-id="d6b7b-117">Description</span><span class="sxs-lookup"><span data-stu-id="d6b7b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6b7b-118">None</span><span class="sxs-lookup"><span data-stu-id="d6b7b-118">None</span></span>|<span data-ttu-id="d6b7b-119">Le message SOAP n'est pas sécurisé pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="d6b7b-120">Message</span><span class="sxs-lookup"><span data-stu-id="d6b7b-120">Message</span></span>|<span data-ttu-id="d6b7b-121">L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="d6b7b-122">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="d6b7b-123">Le service doit être configuré avec un certificat.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-123">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="d6b7b-124">L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité</span><span class="sxs-lookup"><span data-stu-id="d6b7b-124">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="d6b7b-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d6b7b-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="d6b7b-126">L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="d6b7b-127">Le service doit être configuré avec un certificat.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-127">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="d6b7b-128">L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6b7b-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d6b7b-129">Child Elements</span></span>  
  
|<span data-ttu-id="d6b7b-130">Élément</span><span class="sxs-lookup"><span data-stu-id="d6b7b-130">Element</span></span>|<span data-ttu-id="d6b7b-131">Description</span><span class="sxs-lookup"><span data-stu-id="d6b7b-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="d6b7b-132">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="d6b7b-133">Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="d6b7b-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6b7b-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d6b7b-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d6b7b-135">Élément</span><span class="sxs-lookup"><span data-stu-id="d6b7b-135">Element</span></span>|<span data-ttu-id="d6b7b-136">Description</span><span class="sxs-lookup"><span data-stu-id="d6b7b-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d6b7b-137">Définit toutes les fonctions de liaison de [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d6b7b-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6b7b-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6b7b-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="d6b7b-139">Guide pratique pour créer une liaison WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d6b7b-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="d6b7b-140">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="d6b7b-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d6b7b-141">Sélection d'un type d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="d6b7b-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="d6b7b-142">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d6b7b-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d6b7b-143">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="d6b7b-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d6b7b-144">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d6b7b-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
