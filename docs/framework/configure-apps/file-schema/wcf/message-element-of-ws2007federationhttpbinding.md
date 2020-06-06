---
title: <message>élément de<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738996"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="688c7-102">\<message>élément de\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="688c7-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="688c7-103">Définit des paramètres pour la sécurité au niveau du message pour l' [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="688c7-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="688c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="688c7-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="688c7-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="688c7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="688c7-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="688c7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="688c7-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="688c7-107">Attributes</span></span>  
  
|<span data-ttu-id="688c7-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="688c7-108">Attribute</span></span>|<span data-ttu-id="688c7-109">Description</span><span class="sxs-lookup"><span data-stu-id="688c7-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="688c7-110">facultatif.</span><span class="sxs-lookup"><span data-stu-id="688c7-110">Optional.</span></span> <span data-ttu-id="688c7-111">Définit les algorithmes de chiffrement de message, de signature et de clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-111">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="688c7-112">Les algorithmes et les tailles de clé sont déterminés par la classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="688c7-112">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="688c7-113">Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="688c7-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="688c7-114">Consultez le tableau suivant pour connaître les valeurs autorisées.</span><span class="sxs-lookup"><span data-stu-id="688c7-114">See the following table for possible values.</span></span> <span data-ttu-id="688c7-115">La valeur par défaut est Basic256.</span><span class="sxs-lookup"><span data-stu-id="688c7-115">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="688c7-116">Spécifie le type de clé à émettre.</span><span class="sxs-lookup"><span data-stu-id="688c7-116">Specifies the type of key to be issued.</span></span> <span data-ttu-id="688c7-117">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="688c7-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="688c7-118">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="688c7-118">-   SymmetricKey</span></span><br /><span data-ttu-id="688c7-119">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="688c7-119">-   PublicKey</span></span><br /><span data-ttu-id="688c7-120">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="688c7-120">-   BearerKey</span></span><br /><br /> <span data-ttu-id="688c7-121">La valeur par défaut est SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="688c7-121">The default is SymmetricKey.</span></span> <span data-ttu-id="688c7-122">Cet attribut est de type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="688c7-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="688c7-123">URI qui spécifie le type de jeton à émettre.</span><span class="sxs-lookup"><span data-stu-id="688c7-123">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="688c7-124">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="688c7-124">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="688c7-125">Valeur qui spécifie si les informations d'identification du service doivent être échangées dans le cadre de la négociation ou sont disponibles hors bande.</span><span class="sxs-lookup"><span data-stu-id="688c7-125">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="688c7-126">La valeur par défaut est `true`, ce qui signifie que les informations d'identification du service sont négociées.</span><span class="sxs-lookup"><span data-stu-id="688c7-126">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="688c7-127">Attribut algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="688c7-127">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="688c7-128">Valeur</span><span class="sxs-lookup"><span data-stu-id="688c7-128">Value</span></span>|<span data-ttu-id="688c7-129">Description</span><span class="sxs-lookup"><span data-stu-id="688c7-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="688c7-130">Basic128</span><span class="sxs-lookup"><span data-stu-id="688c7-130">Basic128</span></span>|<span data-ttu-id="688c7-131">Utilisez le chiffrement Aes128, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-131">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="688c7-132">Basic192</span><span class="sxs-lookup"><span data-stu-id="688c7-132">Basic192</span></span>|<span data-ttu-id="688c7-133">Utilisez le chiffrement Aes192, Sha1 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-133">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="688c7-134">Basic256</span><span class="sxs-lookup"><span data-stu-id="688c7-134">Basic256</span></span>|<span data-ttu-id="688c7-135">Utilisez le chiffrement Aes256, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-135">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="688c7-136">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="688c7-136">Basic256Rsa15</span></span>|<span data-ttu-id="688c7-137">Utilisez Aes256 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-137">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="688c7-138">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="688c7-138">Basic192Rsa15</span></span>|<span data-ttu-id="688c7-139">Utilisez Aes192 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-139">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="688c7-140">TripleDes</span><span class="sxs-lookup"><span data-stu-id="688c7-140">TripleDes</span></span>|<span data-ttu-id="688c7-141">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-141">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="688c7-142">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="688c7-142">Basic128Rsa15</span></span>|<span data-ttu-id="688c7-143">Utilisez Aes128 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-143">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="688c7-144">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="688c7-144">TripleDesRsa15</span></span>|<span data-ttu-id="688c7-145">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-145">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="688c7-146">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="688c7-146">Basic128Sha256</span></span>|<span data-ttu-id="688c7-147">Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-147">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="688c7-148">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="688c7-148">Basic192Sha256</span></span>|<span data-ttu-id="688c7-149">Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-149">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="688c7-150">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="688c7-150">Basic256Sha256</span></span>|<span data-ttu-id="688c7-151">Utilisez Aes256 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-151">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="688c7-152">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="688c7-152">TripleDesSha256</span></span>|<span data-ttu-id="688c7-153">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-153">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="688c7-154">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="688c7-154">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="688c7-155">Utilisez Aes128 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-155">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="688c7-156">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="688c7-156">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="688c7-157">Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-157">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="688c7-158">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="688c7-158">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="688c7-159">Utilisez Aes256 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-159">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="688c7-160">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="688c7-160">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="688c7-161">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="688c7-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="688c7-162">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="688c7-162">Child Elements</span></span>  
  
|<span data-ttu-id="688c7-163">Élément</span><span class="sxs-lookup"><span data-stu-id="688c7-163">Element</span></span>|<span data-ttu-id="688c7-164">Description</span><span class="sxs-lookup"><span data-stu-id="688c7-164">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="688c7-165">Spécifie une collection de types de revendication pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="688c7-165">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="688c7-166">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="688c7-166">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="688c7-167">Spécifie un point de terminaison qui publie un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="688c7-167">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="688c7-168">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="688c7-168">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="688c7-169">Spécifie l'adresse de point de terminaison de l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="688c7-169">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="688c7-170">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="688c7-170">A collection of token request parameters.</span></span> <span data-ttu-id="688c7-171">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="688c7-171">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="688c7-172">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="688c7-172">Parent Elements</span></span>  
  
|<span data-ttu-id="688c7-173">Élément</span><span class="sxs-lookup"><span data-stu-id="688c7-173">Element</span></span>|<span data-ttu-id="688c7-174">Description</span><span class="sxs-lookup"><span data-stu-id="688c7-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="688c7-175">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="688c7-175">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="688c7-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="688c7-176">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="688c7-177">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="688c7-177">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="688c7-178">Liaisons</span><span class="sxs-lookup"><span data-stu-id="688c7-178">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="688c7-179">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="688c7-179">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="688c7-180">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="688c7-180">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
