---
title: <message> élément de <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: d71bce5e94568bdad3c52226fa1029a1dd87bfd9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204916"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="ee202-102">\<message> élément de \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ee202-102">\<message> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="ee202-103">Définit des paramètres pour la sécurité au niveau du message pour l' [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="ee202-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="ee202-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee202-104">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
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
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
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
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee202-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ee202-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ee202-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ee202-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee202-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="ee202-107">Attributes</span></span>  
  
|<span data-ttu-id="ee202-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="ee202-108">Attribute</span></span>|<span data-ttu-id="ee202-109">Description</span><span class="sxs-lookup"><span data-stu-id="ee202-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="ee202-110">facultatif.</span><span class="sxs-lookup"><span data-stu-id="ee202-110">Optional.</span></span> <span data-ttu-id="ee202-111">Définit les algorithmes de chiffrement de message, de signature et de clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-111">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="ee202-112">Les algorithmes et les tailles de clé sont déterminés par la classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="ee202-112">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="ee202-113">Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="ee202-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="ee202-114">Consultez le tableau suivant pour connaître les valeurs autorisées.</span><span class="sxs-lookup"><span data-stu-id="ee202-114">See the following table for possible values.</span></span> <span data-ttu-id="ee202-115">La valeur par défaut est Basic256.</span><span class="sxs-lookup"><span data-stu-id="ee202-115">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="ee202-116">Spécifie le type de clé à émettre.</span><span class="sxs-lookup"><span data-stu-id="ee202-116">Specifies the type of key to be issued.</span></span> <span data-ttu-id="ee202-117">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee202-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee202-118">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="ee202-118">-   SymmetricKey</span></span><br /><span data-ttu-id="ee202-119">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="ee202-119">-   PublicKey</span></span><br /><span data-ttu-id="ee202-120">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="ee202-120">-   BearerKey</span></span><br /><br /> <span data-ttu-id="ee202-121">La valeur par défaut est SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="ee202-121">The default is SymmetricKey.</span></span> <span data-ttu-id="ee202-122">Cet attribut est de type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="ee202-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="ee202-123">URI qui spécifie le type de jeton à émettre.</span><span class="sxs-lookup"><span data-stu-id="ee202-123">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="ee202-124">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="ee202-124">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="ee202-125">Valeur qui spécifie si les informations d'identification du service doivent être échangées dans le cadre de la négociation ou sont disponibles hors bande.</span><span class="sxs-lookup"><span data-stu-id="ee202-125">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="ee202-126">La valeur par défaut est `true`, ce qui signifie que les informations d'identification du service sont négociées.</span><span class="sxs-lookup"><span data-stu-id="ee202-126">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="ee202-127">Attribut algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ee202-127">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="ee202-128">Valeur</span><span class="sxs-lookup"><span data-stu-id="ee202-128">Value</span></span>|<span data-ttu-id="ee202-129">Description</span><span class="sxs-lookup"><span data-stu-id="ee202-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee202-130">Basic128</span><span class="sxs-lookup"><span data-stu-id="ee202-130">Basic128</span></span>|<span data-ttu-id="ee202-131">Utilisez le chiffrement Aes128, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-131">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ee202-132">Basic192</span><span class="sxs-lookup"><span data-stu-id="ee202-132">Basic192</span></span>|<span data-ttu-id="ee202-133">Utilisez le chiffrement Aes192, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-133">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ee202-134">Basic256</span><span class="sxs-lookup"><span data-stu-id="ee202-134">Basic256</span></span>|<span data-ttu-id="ee202-135">Utilisez le chiffrement Aes256, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-135">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ee202-136">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ee202-136">Basic256Rsa15</span></span>|<span data-ttu-id="ee202-137">Utilisez Aes256 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-137">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ee202-138">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="ee202-138">Basic192Rsa15</span></span>|<span data-ttu-id="ee202-139">Utilisez Aes192 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-139">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ee202-140">TripleDes</span><span class="sxs-lookup"><span data-stu-id="ee202-140">TripleDes</span></span>|<span data-ttu-id="ee202-141">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-141">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ee202-142">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="ee202-142">Basic128Rsa15</span></span>|<span data-ttu-id="ee202-143">Utilisez Aes128 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-143">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ee202-144">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="ee202-144">TripleDesRsa15</span></span>|<span data-ttu-id="ee202-145">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-145">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ee202-146">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="ee202-146">Basic128Sha256</span></span>|<span data-ttu-id="ee202-147">Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-147">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ee202-148">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="ee202-148">Basic192Sha256</span></span>|<span data-ttu-id="ee202-149">Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-149">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ee202-150">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="ee202-150">Basic256Sha256</span></span>|<span data-ttu-id="ee202-151">Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-151">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ee202-152">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="ee202-152">TripleDesSha256</span></span>|<span data-ttu-id="ee202-153">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-153">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ee202-154">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ee202-154">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="ee202-155">Utilisez Aes128 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-155">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ee202-156">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ee202-156">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="ee202-157">Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-157">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ee202-158">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ee202-158">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="ee202-159">Utilisez Aes256 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-159">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ee202-160">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ee202-160">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="ee202-161">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="ee202-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee202-162">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ee202-162">Child Elements</span></span>  
  
|<span data-ttu-id="ee202-163">Élément</span><span class="sxs-lookup"><span data-stu-id="ee202-163">Element</span></span>|<span data-ttu-id="ee202-164">Description</span><span class="sxs-lookup"><span data-stu-id="ee202-164">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="ee202-165">Spécifie une collection de types de revendication pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="ee202-165">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="ee202-166">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="ee202-166">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="ee202-167">Spécifie un point de terminaison qui publie un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ee202-167">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="ee202-168">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="ee202-168">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="ee202-169">Spécifie l'adresse de point de terminaison de l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="ee202-169">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="ee202-170">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="ee202-170">A collection of token request parameters.</span></span> <span data-ttu-id="ee202-171">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="ee202-171">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee202-172">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ee202-172">Parent Elements</span></span>  
  
|<span data-ttu-id="ee202-173">Élément</span><span class="sxs-lookup"><span data-stu-id="ee202-173">Element</span></span>|<span data-ttu-id="ee202-174">Description</span><span class="sxs-lookup"><span data-stu-id="ee202-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="ee202-175">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="ee202-175">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee202-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee202-176">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="ee202-177">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ee202-177">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ee202-178">Liaisons</span><span class="sxs-lookup"><span data-stu-id="ee202-178">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ee202-179">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="ee202-179">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ee202-180">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ee202-180">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
