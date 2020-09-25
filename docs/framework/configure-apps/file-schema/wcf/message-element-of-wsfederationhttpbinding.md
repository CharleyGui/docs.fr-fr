---
title: <message> élément de <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: ea320b1d97e742d4f90ec55502f3bd429803283d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204890"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="7d992-102">\<message> élément de \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7d992-102">\<message> element of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="7d992-103">Définit les paramètres pour la sécurité au niveau du message pour [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="7d992-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="7d992-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d992-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d992-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7d992-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7d992-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7d992-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d992-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="7d992-107">Attributes</span></span>  
  
|<span data-ttu-id="7d992-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7d992-108">Attribute</span></span>|<span data-ttu-id="7d992-109">Description</span><span class="sxs-lookup"><span data-stu-id="7d992-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d992-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="7d992-110">algorithmSuite</span></span>|<span data-ttu-id="7d992-111">Définit les algorithmes de chiffrement de message et de clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="7d992-112">Consultez le tableau « attribut algorithmSuite » pour des valeurs valides de cet attribut.</span><span class="sxs-lookup"><span data-stu-id="7d992-112">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="7d992-113">La valeur par défaut est `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="7d992-113">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="7d992-114">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="7d992-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="7d992-115">Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="7d992-115">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="7d992-116">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="7d992-116">issuedKeyType</span></span>|<span data-ttu-id="7d992-117">Spécifie le type de clé à émettre.</span><span class="sxs-lookup"><span data-stu-id="7d992-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="7d992-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7d992-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7d992-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="7d992-119">-   SymmetricKey</span></span><br /><span data-ttu-id="7d992-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="7d992-120">-   PublicKey</span></span><br /><br /> <span data-ttu-id="7d992-121">Par défaut, il s’agit de `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="7d992-121">The default is `SymmetricKey`.</span></span> <span data-ttu-id="7d992-122">Cet attribut est de type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="7d992-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="7d992-123">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="7d992-123">issuedTokenType</span></span>|<span data-ttu-id="7d992-124">Chaîne qui contient un URI qui spécifie le type de jeton à publier.</span><span class="sxs-lookup"><span data-stu-id="7d992-124">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="7d992-125">Par défaut, il s’agit de `null`.</span><span class="sxs-lookup"><span data-stu-id="7d992-125">The default is `null`.</span></span>|  
|<span data-ttu-id="7d992-126">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="7d992-126">negotiateServiceCredential</span></span>|<span data-ttu-id="7d992-127">Valeur booléenne qui spécifie si les informations d'identification du service doivent être échangées dans le cadre de la négociation ou si elles sont disponibles hors bande.</span><span class="sxs-lookup"><span data-stu-id="7d992-127">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="7d992-128">La valeur par défaut est `true`, ce qui signifie que les informations d'identification du service sont négociées.</span><span class="sxs-lookup"><span data-stu-id="7d992-128">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="7d992-129">Attribut algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="7d992-129">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="7d992-130">Valeur</span><span class="sxs-lookup"><span data-stu-id="7d992-130">Value</span></span>|<span data-ttu-id="7d992-131">Description</span><span class="sxs-lookup"><span data-stu-id="7d992-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7d992-132">Basic128</span><span class="sxs-lookup"><span data-stu-id="7d992-132">Basic128</span></span>|<span data-ttu-id="7d992-133">Utilisez le chiffrement Basic128, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-133">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7d992-134">Basic192</span><span class="sxs-lookup"><span data-stu-id="7d992-134">Basic192</span></span>|<span data-ttu-id="7d992-135">Utilisez le chiffrement Basic192, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-135">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7d992-136">Basic256</span><span class="sxs-lookup"><span data-stu-id="7d992-136">Basic256</span></span>|<span data-ttu-id="7d992-137">Utilisez le chiffrement Basic256, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-137">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7d992-138">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7d992-138">Basic256Rsa15</span></span>|<span data-ttu-id="7d992-139">Utilisez Basic256 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-139">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7d992-140">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="7d992-140">Basic192Rsa15</span></span>|<span data-ttu-id="7d992-141">Utilisez Basic192 pour le chiffrement du message, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-141">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7d992-142">TripleDes</span><span class="sxs-lookup"><span data-stu-id="7d992-142">TripleDes</span></span>|<span data-ttu-id="7d992-143">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-143">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7d992-144">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="7d992-144">Basic128Rsa15</span></span>|<span data-ttu-id="7d992-145">Utilisez Basic128 pour le chiffrement du message, Sha1 pour le résumé du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-145">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7d992-146">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="7d992-146">TripleDesRsa15</span></span>|<span data-ttu-id="7d992-147">Utilisez le chiffrement TripleDes, Sha1 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-147">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7d992-148">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="7d992-148">Basic128Sha256</span></span>|<span data-ttu-id="7d992-149">Utilisez Basic128 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-149">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7d992-150">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="7d992-150">Basic192Sha256</span></span>|<span data-ttu-id="7d992-151">Utilisez Basic192 pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-151">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7d992-152">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="7d992-152">Basic256Sha256</span></span>|<span data-ttu-id="7d992-153">Utilisez Basic256 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-153">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7d992-154">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="7d992-154">TripleDesSha256</span></span>|<span data-ttu-id="7d992-155">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le résumé du message et Rsa-oaep-mgf1p pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7d992-156">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7d992-156">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="7d992-157">Utilisez Basic128 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-157">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7d992-158">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7d992-158">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="7d992-159">Utilisez Aes192 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-159">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7d992-160">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7d992-160">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="7d992-161">Utilisez Basic256 pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-161">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7d992-162">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7d992-162">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="7d992-163">Utilisez TripleDes pour le chiffrement du message, Sha256 pour le condensat du message et Rsa15 pour la clé de type WRAP.</span><span class="sxs-lookup"><span data-stu-id="7d992-163">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d992-164">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7d992-164">Child Elements</span></span>  
  
|<span data-ttu-id="7d992-165">Élément</span><span class="sxs-lookup"><span data-stu-id="7d992-165">Element</span></span>|<span data-ttu-id="7d992-166">Description</span><span class="sxs-lookup"><span data-stu-id="7d992-166">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="7d992-167">Spécifie une collection de types de revendication pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="7d992-167">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="7d992-168">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="7d992-168">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="7d992-169">émetteur</span><span class="sxs-lookup"><span data-stu-id="7d992-169">issuer</span></span>|<span data-ttu-id="7d992-170">Spécifie un point de terminaison qui publie un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7d992-170">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="7d992-171">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="7d992-171">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="7d992-172">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="7d992-172">issuerMetadata</span></span>|<span data-ttu-id="7d992-173">Spécifie l'adresse de point de terminaison de l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="7d992-173">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="7d992-174">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="7d992-174">A collection of token request parameters.</span></span> <span data-ttu-id="7d992-175">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="7d992-175">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d992-176">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7d992-176">Parent Elements</span></span>  
  
|<span data-ttu-id="7d992-177">Élément</span><span class="sxs-lookup"><span data-stu-id="7d992-177">Element</span></span>|<span data-ttu-id="7d992-178">Description</span><span class="sxs-lookup"><span data-stu-id="7d992-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="7d992-179">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="7d992-179">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d992-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d992-180">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="7d992-181">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7d992-181">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7d992-182">Liaisons</span><span class="sxs-lookup"><span data-stu-id="7d992-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7d992-183">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="7d992-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7d992-184">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7d992-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
