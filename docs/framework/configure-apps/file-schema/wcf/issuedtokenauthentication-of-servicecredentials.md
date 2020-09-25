---
title: <issuedTokenAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 88657b6982108596c8d9030161390f76fcff6609
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202472"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="7e174-102">\<issuedTokenAuthentication> de \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7e174-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>

<span data-ttu-id="7e174-103">Indique un jeton personnalisé émis en tant qu'informations d'identification du service.</span><span class="sxs-lookup"><span data-stu-id="7e174-103">Specifies a custom token issued as a service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="7e174-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e174-104">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e174-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7e174-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7e174-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7e174-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e174-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="7e174-107">Attributes</span></span>  
  
|<span data-ttu-id="7e174-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7e174-108">Attribute</span></span>|<span data-ttu-id="7e174-109">Description</span><span class="sxs-lookup"><span data-stu-id="7e174-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="7e174-110">Obtient le jeu d'URI cibles pour lesquels le jeton de sécurité <xref:System.IdentityModel.Tokens.SamlSecurityToken> peut être visé pour être considéré comme valide par une instance de <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="7e174-110">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="7e174-111">Pour plus d'informations sur l'utilisation de cet attribut, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e174-111">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="7e174-112">Valeur booléenne indiquant si les émetteurs de certificats RSA non fiables sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7e174-112">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="7e174-113">Les certificats sont signés par des autorités de certification (CA) pour en assurer l'authenticité.</span><span class="sxs-lookup"><span data-stu-id="7e174-113">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="7e174-114">Un émetteur non fiable est une autorité de certification qui n'est pas spécifiée comme étant approuvée pour signer des certificats.</span><span class="sxs-lookup"><span data-stu-id="7e174-114">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="7e174-115">Obtient une valeur indiquant si le <xref:System.IdentityModel.Tokens.SamlSecurityToken> du jeton de sécurité <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> doit être validé.</span><span class="sxs-lookup"><span data-stu-id="7e174-115">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="7e174-116">Cette valeur est de type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="7e174-116">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="7e174-117">Pour plus d'informations sur l'utilisation de cet attribut, consultez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e174-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="7e174-118">Définit le mode de validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="7e174-118">Sets the certificate validation mode.</span></span> <span data-ttu-id="7e174-119">L'une des valeurs valides du <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="7e174-119">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="7e174-120">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="7e174-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="7e174-121">La valeur par défaut est `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7e174-121">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="7e174-122">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="7e174-122">Optional string.</span></span> <span data-ttu-id="7e174-123">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7e174-123">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="7e174-124">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="7e174-124">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="7e174-125">Définit le mode de révocation qui spécifie si un contrôle de révocation a lieu et s'il est effectué en ligne ou hors connexion.</span><span class="sxs-lookup"><span data-stu-id="7e174-125">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="7e174-126">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="7e174-126">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="7e174-127">Attribut de chaîne facultatif indiquant le type de SamlSerializer utilisé pour les informations d'identification du service.</span><span class="sxs-lookup"><span data-stu-id="7e174-127">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="7e174-128">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="7e174-128">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="7e174-129">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="7e174-129">Optional enumeration.</span></span> <span data-ttu-id="7e174-130">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7e174-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e174-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7e174-131">Child Elements</span></span>  
  
|<span data-ttu-id="7e174-132">Élément</span><span class="sxs-lookup"><span data-stu-id="7e174-132">Element</span></span>|<span data-ttu-id="7e174-133">Description</span><span class="sxs-lookup"><span data-stu-id="7e174-133">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="7e174-134">Indique une collection d’éléments <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> qui spécifient des émetteurs approuvés au niveau des informations d’identification du service.</span><span class="sxs-lookup"><span data-stu-id="7e174-134">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e174-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7e174-135">Parent Elements</span></span>  
  
|<span data-ttu-id="7e174-136">Élément</span><span class="sxs-lookup"><span data-stu-id="7e174-136">Element</span></span>|<span data-ttu-id="7e174-137">Description</span><span class="sxs-lookup"><span data-stu-id="7e174-137">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="7e174-138">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="7e174-138">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e174-139">Notes</span><span class="sxs-lookup"><span data-stu-id="7e174-139">Remarks</span></span>  

 <span data-ttu-id="7e174-140">Le scénario de jeton émis comporte trois étapes.</span><span class="sxs-lookup"><span data-stu-id="7e174-140">The issued token scenario has three stages.</span></span> <span data-ttu-id="7e174-141">Lors de la première phase, un client qui tente d’accéder à un service est appelé *service de jeton sécurisé*.</span><span class="sxs-lookup"><span data-stu-id="7e174-141">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="7e174-142">Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language).</span><span class="sxs-lookup"><span data-stu-id="7e174-142">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="7e174-143">Le client retourne ensuite au service avec le jeton.</span><span class="sxs-lookup"><span data-stu-id="7e174-143">The client then returns to the service with the token.</span></span> <span data-ttu-id="7e174-144">Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="7e174-144">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="7e174-145">Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="7e174-145">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="7e174-146">Cet élément est le référentiel pour les certificats de service d'émission de jeton sécurisé de ce type.</span><span class="sxs-lookup"><span data-stu-id="7e174-146">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="7e174-147">Pour ajouter des certificats, utilisez le [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="7e174-147">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="7e174-148">Insérez un [\<add>](add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7e174-148">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="7e174-149">Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="7e174-149">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="7e174-150">Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.</span><span class="sxs-lookup"><span data-stu-id="7e174-150">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="7e174-151">Pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : configurer des informations d’identification sur un service FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="7e174-151">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e174-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e174-152">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="7e174-153">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7e174-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7e174-154">Procédure : configurer des informations d’identification sur un service de fédération</span><span class="sxs-lookup"><span data-stu-id="7e174-154">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
