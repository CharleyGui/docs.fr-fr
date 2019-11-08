---
title: élément <message> de <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738983"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="9432e-102">\<> élément de message de \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9432e-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="9432e-103">Définit les paramètres pour la sécurité au niveau du message pour le [\<WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9432e-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="9432e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9432e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9432e-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="9432e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9432e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="9432e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="9432e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**WSFederationHttpBinding**](wsfederationhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="9432e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="9432e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="9432e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="9432e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](security-of-wsfederationhttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="9432e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="9432e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="9432e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9432e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9432e-111">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
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
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9432e-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9432e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9432e-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9432e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9432e-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="9432e-114">Attributes</span></span>  
  
|<span data-ttu-id="9432e-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="9432e-115">Attribute</span></span>|<span data-ttu-id="9432e-116">Description</span><span class="sxs-lookup"><span data-stu-id="9432e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9432e-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="9432e-117">algorithmSuite</span></span>|<span data-ttu-id="9432e-118">Définit les algorithmes de chiffrement de message et de clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="9432e-119">Consultez le tableau « attribut algorithmSuite » pour des valeurs valides de cet attribut.</span><span class="sxs-lookup"><span data-stu-id="9432e-119">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="9432e-120">La valeur par défaut est `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="9432e-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="9432e-121">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="9432e-121">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="9432e-122">Ces algorithmes se mappent à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="9432e-122">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="9432e-123">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="9432e-123">issuedKeyType</span></span>|<span data-ttu-id="9432e-124">Spécifie le type de clé à émettre.</span><span class="sxs-lookup"><span data-stu-id="9432e-124">Specifies the type of key to be issued.</span></span> <span data-ttu-id="9432e-125">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9432e-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9432e-126">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="9432e-126">-   SymmetricKey</span></span><br /><span data-ttu-id="9432e-127">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="9432e-127">-   PublicKey</span></span><br /><br /> <span data-ttu-id="9432e-128">La valeur par défaut est `SymmetricKey`,</span><span class="sxs-lookup"><span data-stu-id="9432e-128">The default is `SymmetricKey`.</span></span> <span data-ttu-id="9432e-129">Cet attribut est de type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="9432e-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="9432e-130">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="9432e-130">issuedTokenType</span></span>|<span data-ttu-id="9432e-131">Chaîne qui contient un URI qui spécifie le type de jeton à publier.</span><span class="sxs-lookup"><span data-stu-id="9432e-131">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="9432e-132">La valeur par défaut est `null`,</span><span class="sxs-lookup"><span data-stu-id="9432e-132">The default is `null`.</span></span>|  
|<span data-ttu-id="9432e-133">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="9432e-133">negotiateServiceCredential</span></span>|<span data-ttu-id="9432e-134">Valeur booléenne qui spécifie si les informations d'identification du service doivent être échangées dans le cadre de la négociation ou si elles sont disponibles hors bande.</span><span class="sxs-lookup"><span data-stu-id="9432e-134">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="9432e-135">La valeur par défaut est `true`, ce qui signifie que les informations d'identification du service sont négociées.</span><span class="sxs-lookup"><span data-stu-id="9432e-135">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="9432e-136">Attribut algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="9432e-136">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="9432e-137">valeur</span><span class="sxs-lookup"><span data-stu-id="9432e-137">Value</span></span>|<span data-ttu-id="9432e-138">Description</span><span class="sxs-lookup"><span data-stu-id="9432e-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9432e-139">Basic128</span><span class="sxs-lookup"><span data-stu-id="9432e-139">Basic128</span></span>|<span data-ttu-id="9432e-140">Utilisez le chiffrement Basic128, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-140">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9432e-141">Basic192</span><span class="sxs-lookup"><span data-stu-id="9432e-141">Basic192</span></span>|<span data-ttu-id="9432e-142">Utilisez le chiffrement Basic192, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-142">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9432e-143">Basic256</span><span class="sxs-lookup"><span data-stu-id="9432e-143">Basic256</span></span>|<span data-ttu-id="9432e-144">Utilisez le chiffrement Basic256, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-144">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9432e-145">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9432e-145">Basic256Rsa15</span></span>|<span data-ttu-id="9432e-146">Utilisez Basic256 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-146">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9432e-147">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="9432e-147">Basic192Rsa15</span></span>|<span data-ttu-id="9432e-148">Utilisez Basic192 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-148">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9432e-149">TripleDes</span><span class="sxs-lookup"><span data-stu-id="9432e-149">TripleDes</span></span>|<span data-ttu-id="9432e-150">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-150">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9432e-151">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="9432e-151">Basic128Rsa15</span></span>|<span data-ttu-id="9432e-152">Utilisez Basic128 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-152">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9432e-153">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="9432e-153">TripleDesRsa15</span></span>|<span data-ttu-id="9432e-154">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-154">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9432e-155">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="9432e-155">Basic128Sha256</span></span>|<span data-ttu-id="9432e-156">Utilisez Basic128 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-156">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9432e-157">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="9432e-157">Basic192Sha256</span></span>|<span data-ttu-id="9432e-158">Utilisez Basic192 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-158">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9432e-159">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="9432e-159">Basic256Sha256</span></span>|<span data-ttu-id="9432e-160">Utilisez Basic256 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-160">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9432e-161">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="9432e-161">TripleDesSha256</span></span>|<span data-ttu-id="9432e-162">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="9432e-163">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9432e-163">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="9432e-164">Utilisez Basic128 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-164">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9432e-165">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9432e-165">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="9432e-166">Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-166">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9432e-167">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9432e-167">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="9432e-168">Utilisez Basic256 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-168">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="9432e-169">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="9432e-169">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="9432e-170">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="9432e-170">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9432e-171">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9432e-171">Child Elements</span></span>  
  
|<span data-ttu-id="9432e-172">Élément</span><span class="sxs-lookup"><span data-stu-id="9432e-172">Element</span></span>|<span data-ttu-id="9432e-173">Description</span><span class="sxs-lookup"><span data-stu-id="9432e-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9432e-174">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="9432e-174">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="9432e-175">Spécifie une collection de types de revendication pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="9432e-175">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="9432e-176">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="9432e-176">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="9432e-177">issuer</span><span class="sxs-lookup"><span data-stu-id="9432e-177">issuer</span></span>|<span data-ttu-id="9432e-178">Spécifie un point de terminaison qui publie un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9432e-178">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="9432e-179">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="9432e-179">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="9432e-180">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="9432e-180">issuerMetadata</span></span>|<span data-ttu-id="9432e-181">Spécifie l'adresse de point de terminaison de l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="9432e-181">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="9432e-182">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="9432e-182">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="9432e-183">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="9432e-183">A collection of token request parameters.</span></span> <span data-ttu-id="9432e-184">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="9432e-184">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9432e-185">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9432e-185">Parent Elements</span></span>  
  
|<span data-ttu-id="9432e-186">Élément</span><span class="sxs-lookup"><span data-stu-id="9432e-186">Element</span></span>|<span data-ttu-id="9432e-187">Description</span><span class="sxs-lookup"><span data-stu-id="9432e-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9432e-188">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="9432e-188">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="9432e-189">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="9432e-189">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9432e-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9432e-190">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="9432e-191">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="9432e-191">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9432e-192">Liaisons</span><span class="sxs-lookup"><span data-stu-id="9432e-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9432e-193">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="9432e-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9432e-194">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="9432e-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9432e-195">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="9432e-195">\<binding></span></span>](bindings.md)
