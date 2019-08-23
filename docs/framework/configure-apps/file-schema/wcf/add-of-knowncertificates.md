---
title: <add> de <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 939718e8dacca2698b6f71a3bdc1262a5dc3ee20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926681"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="faaed-102">\<Ajouter > de \<la > knownCertificates</span><span class="sxs-lookup"><span data-stu-id="faaed-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="faaed-103">Ajoute un certificat X.509 à la collection de certificats connus.</span><span class="sxs-lookup"><span data-stu-id="faaed-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="faaed-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="faaed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="faaed-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="faaed-105">\<behaviors></span></span>  
<span data-ttu-id="faaed-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="faaed-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="faaed-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="faaed-107">\<behavior></span></span>  
<span data-ttu-id="faaed-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="faaed-108">\<serviceCredentials></span></span>  
<span data-ttu-id="faaed-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="faaed-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="faaed-110">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="faaed-110">\<knownCertificates></span></span>  
<span data-ttu-id="faaed-111">\<add></span><span class="sxs-lookup"><span data-stu-id="faaed-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faaed-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faaed-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faaed-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="faaed-113">Attributes and Elements</span></span>  
 <span data-ttu-id="faaed-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="faaed-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faaed-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="faaed-115">Attributes</span></span>  
  
|<span data-ttu-id="faaed-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="faaed-116">Attribute</span></span>|<span data-ttu-id="faaed-117">Description</span><span class="sxs-lookup"><span data-stu-id="faaed-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="faaed-118">findValue</span><span class="sxs-lookup"><span data-stu-id="faaed-118">findValue</span></span>|<span data-ttu-id="faaed-119">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="faaed-119">String.</span></span> <span data-ttu-id="faaed-120">La valeur à rechercher.</span><span class="sxs-lookup"><span data-stu-id="faaed-120">The value to search for.</span></span>|  
|<span data-ttu-id="faaed-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="faaed-121">storeLocation</span></span>|<span data-ttu-id="faaed-122">Énumération.</span><span class="sxs-lookup"><span data-stu-id="faaed-122">Enumeration.</span></span> <span data-ttu-id="faaed-123">L'un des deux emplacements du magasin dans lequel effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="faaed-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="faaed-124">storeName</span><span class="sxs-lookup"><span data-stu-id="faaed-124">storeName</span></span>|<span data-ttu-id="faaed-125">Énumération.</span><span class="sxs-lookup"><span data-stu-id="faaed-125">Enumeration.</span></span> <span data-ttu-id="faaed-126">L'un des magasins de systèmes à rechercher.</span><span class="sxs-lookup"><span data-stu-id="faaed-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="faaed-127">x509FindType</span><span class="sxs-lookup"><span data-stu-id="faaed-127">x509FindType</span></span>|<span data-ttu-id="faaed-128">Énumération.</span><span class="sxs-lookup"><span data-stu-id="faaed-128">Enumeration.</span></span> <span data-ttu-id="faaed-129">L'un des champs de certificat à rechercher.</span><span class="sxs-lookup"><span data-stu-id="faaed-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="faaed-130">findValue, attribute</span><span class="sxs-lookup"><span data-stu-id="faaed-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="faaed-131">`Value`</span><span class="sxs-lookup"><span data-stu-id="faaed-131">Value</span></span>|<span data-ttu-id="faaed-132">Description</span><span class="sxs-lookup"><span data-stu-id="faaed-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="faaed-133">String</span><span class="sxs-lookup"><span data-stu-id="faaed-133">String</span></span>|<span data-ttu-id="faaed-134">La valeur dépend du champ (spécifié par l'attribut X509FindType) qui est recherché.</span><span class="sxs-lookup"><span data-stu-id="faaed-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="faaed-135">Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="faaed-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="faaed-136">x509FindType, attribut</span><span class="sxs-lookup"><span data-stu-id="faaed-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="faaed-137">`Value`</span><span class="sxs-lookup"><span data-stu-id="faaed-137">Value</span></span>|<span data-ttu-id="faaed-138">Description</span><span class="sxs-lookup"><span data-stu-id="faaed-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="faaed-139">Énumération</span><span class="sxs-lookup"><span data-stu-id="faaed-139">Enumeration</span></span>|<span data-ttu-id="faaed-140">Les valeurs incluent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="faaed-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="faaed-141">storeLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="faaed-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="faaed-142">`Value`</span><span class="sxs-lookup"><span data-stu-id="faaed-142">Value</span></span>|<span data-ttu-id="faaed-143">Description</span><span class="sxs-lookup"><span data-stu-id="faaed-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="faaed-144">Énumération</span><span class="sxs-lookup"><span data-stu-id="faaed-144">Enumeration</span></span>|<span data-ttu-id="faaed-145">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="faaed-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="faaed-146">storeName, attribut</span><span class="sxs-lookup"><span data-stu-id="faaed-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="faaed-147">Valeur</span><span class="sxs-lookup"><span data-stu-id="faaed-147">Value</span></span>|<span data-ttu-id="faaed-148">Description</span><span class="sxs-lookup"><span data-stu-id="faaed-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="faaed-149">Énumération</span><span class="sxs-lookup"><span data-stu-id="faaed-149">Enumeration</span></span>|<span data-ttu-id="faaed-150">Les valeurs incluent : AddressBook, AuthRoot, CertificateAuthority, non autorisé, My, root, TrustedPeople et TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="faaed-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="faaed-151">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="faaed-151">Child Elements</span></span>  
 <span data-ttu-id="faaed-152">Aucun.</span><span class="sxs-lookup"><span data-stu-id="faaed-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="faaed-153">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="faaed-153">Parent Elements</span></span>  
  
|<span data-ttu-id="faaed-154">Élément</span><span class="sxs-lookup"><span data-stu-id="faaed-154">Element</span></span>|<span data-ttu-id="faaed-155">Description</span><span class="sxs-lookup"><span data-stu-id="faaed-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="faaed-156">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="faaed-156">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="faaed-157">Représente une collection des certificats X.509 fournis par un service d’émission de jetons de sécurité (STS) pour valider les jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="faaed-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faaed-158">Notes</span><span class="sxs-lookup"><span data-stu-id="faaed-158">Remarks</span></span>  
 <span data-ttu-id="faaed-159">Le scénario de jeton émis comporte trois étapes.</span><span class="sxs-lookup"><span data-stu-id="faaed-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="faaed-160">Lors de la première phase, un client qui tente d’accéder à un service est appelé *service de jeton sécurisé*.</span><span class="sxs-lookup"><span data-stu-id="faaed-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="faaed-161">Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language).</span><span class="sxs-lookup"><span data-stu-id="faaed-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="faaed-162">Le client retourne ensuite au service avec le jeton.</span><span class="sxs-lookup"><span data-stu-id="faaed-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="faaed-163">Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="faaed-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="faaed-164">Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="faaed-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="faaed-165">L’élément IssuedTokenAuthentication > est le référentiel de tels certificats de service de jeton sécurisé. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="faaed-165">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="faaed-166">Pour ajouter des certificats, utilisez la [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="faaed-166">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="faaed-167">Insérez un [ \<élément Add > \<Element knownCertificates >](add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="faaed-167">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="faaed-168">Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="faaed-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="faaed-169">Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.</span><span class="sxs-lookup"><span data-stu-id="faaed-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="faaed-170">Pour passer en revue les conditions requises pour qu’un client soit authentifié par un service fédéré, et pour plus d’informations sur l’utilisation de cet [élément de configuration, consultez Procédure: Configurez les informations d'](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)identification sur un service FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="faaed-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="faaed-171">Pour plus d’informations sur les scénarios fédérés, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="faaed-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="faaed-172">Exemple</span><span class="sxs-lookup"><span data-stu-id="faaed-172">Example</span></span>  
 <span data-ttu-id="faaed-173">L'exemple suivant ajoute un certificat au référentiel pour tous les certificats STS.</span><span class="sxs-lookup"><span data-stu-id="faaed-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="faaed-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faaed-174">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="faaed-175">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="faaed-175">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="faaed-176">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="faaed-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="faaed-177">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="faaed-177">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="faaed-178">Guide pratique pour Configurer les informations d’identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="faaed-178">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="faaed-179">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="faaed-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
