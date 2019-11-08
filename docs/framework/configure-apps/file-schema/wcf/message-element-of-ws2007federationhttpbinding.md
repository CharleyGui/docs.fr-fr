---
title: élément <message> de <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738996"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="98270-102">\<> élément de message de \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="98270-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="98270-103">Définit des paramètres pour la sécurité au niveau du message pour l’élément [\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="98270-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="98270-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="98270-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="98270-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="98270-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="98270-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="98270-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="98270-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**WS2007FederationHttpBinding**](ws2007federationhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="98270-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="98270-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="98270-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="98270-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](security-element-of-ws2007federationhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="98270-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="98270-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="98270-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98270-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98270-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98270-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="98270-112">Attributes and Elements</span></span>  
 <span data-ttu-id="98270-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="98270-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98270-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="98270-114">Attributes</span></span>  
  
|<span data-ttu-id="98270-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="98270-115">Attribute</span></span>|<span data-ttu-id="98270-116">Description</span><span class="sxs-lookup"><span data-stu-id="98270-116">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="98270-117">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="98270-117">Optional.</span></span> <span data-ttu-id="98270-118">Définit les algorithmes de chiffrement de message, de signature et de clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-118">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="98270-119">Les algorithmes et les tailles de clé sont déterminés par la classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="98270-119">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="98270-120">Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="98270-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="98270-121">Consultez le tableau suivant pour connaître les valeurs autorisées.</span><span class="sxs-lookup"><span data-stu-id="98270-121">See the following table for possible values.</span></span> <span data-ttu-id="98270-122">La valeur par défaut est Basic256.</span><span class="sxs-lookup"><span data-stu-id="98270-122">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="98270-123">Spécifie le type de clé à émettre.</span><span class="sxs-lookup"><span data-stu-id="98270-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="98270-124">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="98270-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="98270-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="98270-125">-   SymmetricKey</span></span><br /><span data-ttu-id="98270-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="98270-126">-   PublicKey</span></span><br /><span data-ttu-id="98270-127">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="98270-127">-   BearerKey</span></span><br /><br /> <span data-ttu-id="98270-128">La valeur par défaut est SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="98270-128">The default is SymmetricKey.</span></span> <span data-ttu-id="98270-129">Cet attribut est de type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="98270-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="98270-130">URI qui spécifie le type de jeton à émettre.</span><span class="sxs-lookup"><span data-stu-id="98270-130">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="98270-131">La valeur par défaut est `null`,</span><span class="sxs-lookup"><span data-stu-id="98270-131">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="98270-132">Valeur qui spécifie si les informations d'identification du service doivent être échangées dans le cadre de la négociation ou sont disponibles hors bande.</span><span class="sxs-lookup"><span data-stu-id="98270-132">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="98270-133">La valeur par défaut est `true`, ce qui signifie que les informations d'identification du service sont négociées.</span><span class="sxs-lookup"><span data-stu-id="98270-133">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="98270-134">Attribut algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="98270-134">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="98270-135">valeur</span><span class="sxs-lookup"><span data-stu-id="98270-135">Value</span></span>|<span data-ttu-id="98270-136">Description</span><span class="sxs-lookup"><span data-stu-id="98270-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98270-137">Basic128</span><span class="sxs-lookup"><span data-stu-id="98270-137">Basic128</span></span>|<span data-ttu-id="98270-138">Utilisez le chiffrement Aes128, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-138">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="98270-139">Basic192</span><span class="sxs-lookup"><span data-stu-id="98270-139">Basic192</span></span>|<span data-ttu-id="98270-140">Utilisez le chiffrement Aes192, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-140">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="98270-141">Basic256</span><span class="sxs-lookup"><span data-stu-id="98270-141">Basic256</span></span>|<span data-ttu-id="98270-142">Utilisez le chiffrement Aes256, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-142">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="98270-143">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="98270-143">Basic256Rsa15</span></span>|<span data-ttu-id="98270-144">Utilisez Aes256 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-144">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="98270-145">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="98270-145">Basic192Rsa15</span></span>|<span data-ttu-id="98270-146">Utilisez Aes192 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-146">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="98270-147">TripleDes</span><span class="sxs-lookup"><span data-stu-id="98270-147">TripleDes</span></span>|<span data-ttu-id="98270-148">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-148">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="98270-149">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="98270-149">Basic128Rsa15</span></span>|<span data-ttu-id="98270-150">Utilisez Aes128 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-150">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="98270-151">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="98270-151">TripleDesRsa15</span></span>|<span data-ttu-id="98270-152">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-152">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="98270-153">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="98270-153">Basic128Sha256</span></span>|<span data-ttu-id="98270-154">Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-154">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="98270-155">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="98270-155">Basic192Sha256</span></span>|<span data-ttu-id="98270-156">Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="98270-157">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="98270-157">Basic256Sha256</span></span>|<span data-ttu-id="98270-158">Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="98270-159">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="98270-159">TripleDesSha256</span></span>|<span data-ttu-id="98270-160">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="98270-161">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="98270-161">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="98270-162">Utilisez Aes128 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-162">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="98270-163">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="98270-163">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="98270-164">Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-164">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="98270-165">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="98270-165">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="98270-166">Utilisez Aes256 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-166">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="98270-167">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="98270-167">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="98270-168">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="98270-168">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98270-169">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="98270-169">Child Elements</span></span>  
  
|<span data-ttu-id="98270-170">Élément</span><span class="sxs-lookup"><span data-stu-id="98270-170">Element</span></span>|<span data-ttu-id="98270-171">Description</span><span class="sxs-lookup"><span data-stu-id="98270-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98270-172">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="98270-172">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="98270-173">Spécifie une collection de types de revendication pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="98270-173">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="98270-174">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="98270-174">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="98270-175">émetteur \<</span><span class="sxs-lookup"><span data-stu-id="98270-175">\<issuer></span></span>](issuer.md)|<span data-ttu-id="98270-176">Spécifie un point de terminaison qui publie un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="98270-176">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="98270-177">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="98270-177">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="98270-178">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="98270-178">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="98270-179">Spécifie l'adresse de point de terminaison de l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="98270-179">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="98270-180">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="98270-180">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="98270-181">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="98270-181">A collection of token request parameters.</span></span> <span data-ttu-id="98270-182">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="98270-182">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98270-183">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="98270-183">Parent Elements</span></span>  
  
|<span data-ttu-id="98270-184">Élément</span><span class="sxs-lookup"><span data-stu-id="98270-184">Element</span></span>|<span data-ttu-id="98270-185">Description</span><span class="sxs-lookup"><span data-stu-id="98270-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98270-186">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="98270-186">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="98270-187">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="98270-187">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98270-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98270-188">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="98270-189">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="98270-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="98270-190">Liaisons</span><span class="sxs-lookup"><span data-stu-id="98270-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="98270-191">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="98270-191">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="98270-192">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="98270-192">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="98270-193">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="98270-193">\<binding></span></span>](bindings.md)
