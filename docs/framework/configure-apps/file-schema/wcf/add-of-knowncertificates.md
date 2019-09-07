---
title: <add> de <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400624"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="20be4-102">\<Ajouter > de \<la > knownCertificates</span><span class="sxs-lookup"><span data-stu-id="20be4-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="20be4-103">Ajoute un certificat X.509 à la collection de certificats connus.</span><span class="sxs-lookup"><span data-stu-id="20be4-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
<span data-ttu-id="20be4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="20be4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="20be4-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="20be4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="20be4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="20be4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="20be4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="20be4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="20be4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="20be4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="20be4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="20be4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="20be4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="20be4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="20be4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<knownCertificates >** ](knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="20be4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)</span></span>\
<span data-ttu-id="20be4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="20be4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20be4-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20be4-113">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20be4-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="20be4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="20be4-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="20be4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20be4-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="20be4-116">Attributes</span></span>  
  
|<span data-ttu-id="20be4-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="20be4-117">Attribute</span></span>|<span data-ttu-id="20be4-118">Description</span><span class="sxs-lookup"><span data-stu-id="20be4-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20be4-119">findValue</span><span class="sxs-lookup"><span data-stu-id="20be4-119">findValue</span></span>|<span data-ttu-id="20be4-120">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="20be4-120">String.</span></span> <span data-ttu-id="20be4-121">La valeur à rechercher.</span><span class="sxs-lookup"><span data-stu-id="20be4-121">The value to search for.</span></span>|  
|<span data-ttu-id="20be4-122">storeLocation</span><span class="sxs-lookup"><span data-stu-id="20be4-122">storeLocation</span></span>|<span data-ttu-id="20be4-123">Énumération.</span><span class="sxs-lookup"><span data-stu-id="20be4-123">Enumeration.</span></span> <span data-ttu-id="20be4-124">L'un des deux emplacements du magasin dans lequel effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="20be4-124">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="20be4-125">storeName</span><span class="sxs-lookup"><span data-stu-id="20be4-125">storeName</span></span>|<span data-ttu-id="20be4-126">Énumération.</span><span class="sxs-lookup"><span data-stu-id="20be4-126">Enumeration.</span></span> <span data-ttu-id="20be4-127">L'un des magasins de systèmes à rechercher.</span><span class="sxs-lookup"><span data-stu-id="20be4-127">One of the system stores to search.</span></span>|  
|<span data-ttu-id="20be4-128">x509FindType</span><span class="sxs-lookup"><span data-stu-id="20be4-128">x509FindType</span></span>|<span data-ttu-id="20be4-129">Énumération.</span><span class="sxs-lookup"><span data-stu-id="20be4-129">Enumeration.</span></span> <span data-ttu-id="20be4-130">L'un des champs de certificat à rechercher.</span><span class="sxs-lookup"><span data-stu-id="20be4-130">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="20be4-131">findValue, attribute</span><span class="sxs-lookup"><span data-stu-id="20be4-131">findValue Attribute</span></span>  
  
|<span data-ttu-id="20be4-132">Valeur</span><span class="sxs-lookup"><span data-stu-id="20be4-132">Value</span></span>|<span data-ttu-id="20be4-133">Description</span><span class="sxs-lookup"><span data-stu-id="20be4-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20be4-134">String</span><span class="sxs-lookup"><span data-stu-id="20be4-134">String</span></span>|<span data-ttu-id="20be4-135">La valeur dépend du champ (spécifié par l'attribut X509FindType) qui est recherché.</span><span class="sxs-lookup"><span data-stu-id="20be4-135">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="20be4-136">Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="20be4-136">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="20be4-137">x509FindType, attribut</span><span class="sxs-lookup"><span data-stu-id="20be4-137">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="20be4-138">Valeur</span><span class="sxs-lookup"><span data-stu-id="20be4-138">Value</span></span>|<span data-ttu-id="20be4-139">Description</span><span class="sxs-lookup"><span data-stu-id="20be4-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20be4-140">Énumération</span><span class="sxs-lookup"><span data-stu-id="20be4-140">Enumeration</span></span>|<span data-ttu-id="20be4-141">Les valeurs incluent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="20be4-141">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="20be4-142">storeLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="20be4-142">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="20be4-143">Valeur</span><span class="sxs-lookup"><span data-stu-id="20be4-143">Value</span></span>|<span data-ttu-id="20be4-144">Description</span><span class="sxs-lookup"><span data-stu-id="20be4-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20be4-145">Énumération</span><span class="sxs-lookup"><span data-stu-id="20be4-145">Enumeration</span></span>|<span data-ttu-id="20be4-146">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="20be4-146">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="20be4-147">storeName, attribut</span><span class="sxs-lookup"><span data-stu-id="20be4-147">storeName Attribute</span></span>  
  
|<span data-ttu-id="20be4-148">Valeur</span><span class="sxs-lookup"><span data-stu-id="20be4-148">Value</span></span>|<span data-ttu-id="20be4-149">Description</span><span class="sxs-lookup"><span data-stu-id="20be4-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20be4-150">Énumération</span><span class="sxs-lookup"><span data-stu-id="20be4-150">Enumeration</span></span>|<span data-ttu-id="20be4-151">Les valeurs incluent : AddressBook, AuthRoot, CertificateAuthority, non autorisé, My, root, TrustedPeople et TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="20be4-151">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20be4-152">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="20be4-152">Child Elements</span></span>  
 <span data-ttu-id="20be4-153">Aucun.</span><span class="sxs-lookup"><span data-stu-id="20be4-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20be4-154">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="20be4-154">Parent Elements</span></span>  
  
|<span data-ttu-id="20be4-155">Élément</span><span class="sxs-lookup"><span data-stu-id="20be4-155">Element</span></span>|<span data-ttu-id="20be4-156">Description</span><span class="sxs-lookup"><span data-stu-id="20be4-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20be4-157">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="20be4-157">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="20be4-158">Représente une collection des certificats X.509 fournis par un service d’émission de jetons de sécurité (STS) pour valider les jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="20be4-158">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20be4-159">Notes</span><span class="sxs-lookup"><span data-stu-id="20be4-159">Remarks</span></span>  
 <span data-ttu-id="20be4-160">Le scénario de jeton émis comporte trois étapes.</span><span class="sxs-lookup"><span data-stu-id="20be4-160">The issued token scenario has three stages.</span></span> <span data-ttu-id="20be4-161">Lors de la première phase, un client qui tente d’accéder à un service est appelé *service de jeton sécurisé*.</span><span class="sxs-lookup"><span data-stu-id="20be4-161">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="20be4-162">Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language).</span><span class="sxs-lookup"><span data-stu-id="20be4-162">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="20be4-163">Le client retourne ensuite au service avec le jeton.</span><span class="sxs-lookup"><span data-stu-id="20be4-163">The client then returns to the service with the token.</span></span> <span data-ttu-id="20be4-164">Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="20be4-164">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="20be4-165">Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="20be4-165">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="20be4-166">L’élément IssuedTokenAuthentication > est le référentiel de tels certificats de service de jeton sécurisé. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="20be4-166">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="20be4-167">Pour ajouter des certificats, utilisez la [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="20be4-167">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="20be4-168">Insérez un [ \<élément Add > \<Element knownCertificates >](add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="20be4-168">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="20be4-169">Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="20be4-169">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="20be4-170">Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.</span><span class="sxs-lookup"><span data-stu-id="20be4-170">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="20be4-171">Pour passer en revue les conditions requises pour qu’un client soit authentifié par un service fédéré, et pour plus d’informations sur l’utilisation de cet [élément de configuration, consultez Procédure : Configurez les informations d'](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)identification sur un service FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="20be4-171">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="20be4-172">Pour plus d’informations sur les scénarios fédérés, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="20be4-172">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20be4-173">Exemple</span><span class="sxs-lookup"><span data-stu-id="20be4-173">Example</span></span>  
 <span data-ttu-id="20be4-174">L'exemple suivant ajoute un certificat au référentiel pour tous les certificats STS.</span><span class="sxs-lookup"><span data-stu-id="20be4-174">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20be4-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20be4-175">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="20be4-176">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="20be4-176">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="20be4-177">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="20be4-177">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="20be4-178">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="20be4-178">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="20be4-179">Guide pratique pour Configurer les informations d’identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="20be4-179">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="20be4-180">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="20be4-180">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
