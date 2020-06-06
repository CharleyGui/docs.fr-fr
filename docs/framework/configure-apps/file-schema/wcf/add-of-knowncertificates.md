---
title: <add> de <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400624"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="fd7bf-102">\<add> de \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="fd7bf-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="fd7bf-103">Ajoute un certificat X.509 à la collection de certificats connus.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="fd7bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd7bf-104">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd7bf-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fd7bf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fd7bf-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd7bf-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="fd7bf-107">Attributes</span></span>  
  
|<span data-ttu-id="fd7bf-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="fd7bf-108">Attribute</span></span>|<span data-ttu-id="fd7bf-109">Description</span><span class="sxs-lookup"><span data-stu-id="fd7bf-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd7bf-110">findValue</span><span class="sxs-lookup"><span data-stu-id="fd7bf-110">findValue</span></span>|<span data-ttu-id="fd7bf-111">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-111">String.</span></span> <span data-ttu-id="fd7bf-112">La valeur à rechercher.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-112">The value to search for.</span></span>|  
|<span data-ttu-id="fd7bf-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="fd7bf-113">storeLocation</span></span>|<span data-ttu-id="fd7bf-114">Énumération.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-114">Enumeration.</span></span> <span data-ttu-id="fd7bf-115">L'un des deux emplacements du magasin dans lequel effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-115">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="fd7bf-116">storeName</span><span class="sxs-lookup"><span data-stu-id="fd7bf-116">storeName</span></span>|<span data-ttu-id="fd7bf-117">Énumération.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-117">Enumeration.</span></span> <span data-ttu-id="fd7bf-118">L'un des magasins de systèmes à rechercher.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-118">One of the system stores to search.</span></span>|  
|<span data-ttu-id="fd7bf-119">x509FindType</span><span class="sxs-lookup"><span data-stu-id="fd7bf-119">x509FindType</span></span>|<span data-ttu-id="fd7bf-120">Énumération.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-120">Enumeration.</span></span> <span data-ttu-id="fd7bf-121">L'un des champs de certificat à rechercher.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-121">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="fd7bf-122">findValue, attribute</span><span class="sxs-lookup"><span data-stu-id="fd7bf-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="fd7bf-123">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd7bf-123">Value</span></span>|<span data-ttu-id="fd7bf-124">Description</span><span class="sxs-lookup"><span data-stu-id="fd7bf-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd7bf-125">String</span><span class="sxs-lookup"><span data-stu-id="fd7bf-125">String</span></span>|<span data-ttu-id="fd7bf-126">La valeur dépend du champ (spécifié par l'attribut X509FindType) qui est recherché.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="fd7bf-127">Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="fd7bf-128">x509FindType, attribut</span><span class="sxs-lookup"><span data-stu-id="fd7bf-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="fd7bf-129">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd7bf-129">Value</span></span>|<span data-ttu-id="fd7bf-130">Description</span><span class="sxs-lookup"><span data-stu-id="fd7bf-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd7bf-131">Énumération</span><span class="sxs-lookup"><span data-stu-id="fd7bf-131">Enumeration</span></span>|<span data-ttu-id="fd7bf-132">Les valeurs comprennent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="fd7bf-133">storeLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="fd7bf-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="fd7bf-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd7bf-134">Value</span></span>|<span data-ttu-id="fd7bf-135">Description</span><span class="sxs-lookup"><span data-stu-id="fd7bf-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd7bf-136">Énumération</span><span class="sxs-lookup"><span data-stu-id="fd7bf-136">Enumeration</span></span>|<span data-ttu-id="fd7bf-137">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="fd7bf-138">storeName, attribut</span><span class="sxs-lookup"><span data-stu-id="fd7bf-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="fd7bf-139">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd7bf-139">Value</span></span>|<span data-ttu-id="fd7bf-140">Description</span><span class="sxs-lookup"><span data-stu-id="fd7bf-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd7bf-141">Énumération</span><span class="sxs-lookup"><span data-stu-id="fd7bf-141">Enumeration</span></span>|<span data-ttu-id="fd7bf-142">Les valeurs comprennent : AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople et TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd7bf-143">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd7bf-143">Child Elements</span></span>  
 <span data-ttu-id="fd7bf-144">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd7bf-145">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd7bf-145">Parent Elements</span></span>  
  
|<span data-ttu-id="fd7bf-146">Élément</span><span class="sxs-lookup"><span data-stu-id="fd7bf-146">Element</span></span>|<span data-ttu-id="fd7bf-147">Description</span><span class="sxs-lookup"><span data-stu-id="fd7bf-147">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="fd7bf-148">Représente une collection des certificats X.509 fournis par un service d’émission de jetons de sécurité (STS) pour valider les jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-148">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd7bf-149">Remarques</span><span class="sxs-lookup"><span data-stu-id="fd7bf-149">Remarks</span></span>  
 <span data-ttu-id="fd7bf-150">Le scénario de jeton émis comporte trois étapes.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="fd7bf-151">Lors de la première phase, un client qui tente d’accéder à un service est appelé *service de jeton sécurisé*.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-151">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="fd7bf-152">Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language).</span><span class="sxs-lookup"><span data-stu-id="fd7bf-152">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="fd7bf-153">Le client retourne ensuite au service avec le jeton.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="fd7bf-154">Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="fd7bf-155">Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-155">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="fd7bf-156">L' [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) élément est le référentiel de tels certificats de service de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-156">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="fd7bf-157">Pour ajouter des certificats, utilisez le [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="fd7bf-157">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="fd7bf-158">Insérez un [ \<add> \<knownCertificates> élément element](add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-158">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="fd7bf-159">Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="fd7bf-160">Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="fd7bf-161">Pour passer en revue les conditions requises pour qu’un client soit authentifié par un service fédéré, et pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Comment : configurer des informations d’identification sur un service FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="fd7bf-161">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="fd7bf-162">Pour plus d’informations sur les scénarios fédérés, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="fd7bf-162">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd7bf-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd7bf-163">Example</span></span>  
 <span data-ttu-id="fd7bf-164">L'exemple suivant ajoute un certificat au référentiel pour tous les certificats STS.</span><span class="sxs-lookup"><span data-stu-id="fd7bf-164">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="fd7bf-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd7bf-165">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="fd7bf-166">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="fd7bf-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="fd7bf-167">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="fd7bf-167">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fd7bf-168">Comment : configurer des informations d'identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="fd7bf-168">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="fd7bf-169">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="fd7bf-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
