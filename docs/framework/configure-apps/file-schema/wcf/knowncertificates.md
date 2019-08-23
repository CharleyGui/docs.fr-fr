---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 1210e6282a7dd6c40198693d4948a89efe841d59
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913524"
---
# <a name="knowncertificates"></a><span data-ttu-id="46832-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="46832-101">\<knownCertificates></span></span>
<span data-ttu-id="46832-102">Représente une collection des certificats X.509 fournis pour authentifier des informations d’identification de sécurité publiées à partir d’un service d’émission de jetons de sécurité (STS).</span><span class="sxs-lookup"><span data-stu-id="46832-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="46832-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="46832-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="46832-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="46832-104">\<behaviors></span></span>  
<span data-ttu-id="46832-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="46832-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="46832-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="46832-106">\<behavior></span></span>  
<span data-ttu-id="46832-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="46832-107">\<serviceCredentials></span></span>  
<span data-ttu-id="46832-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="46832-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="46832-109">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="46832-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46832-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46832-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46832-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="46832-111">Attributes and Elements</span></span>  
 <span data-ttu-id="46832-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="46832-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46832-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="46832-113">Attributes</span></span>  
 <span data-ttu-id="46832-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="46832-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="46832-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="46832-115">Child Elements</span></span>  
  
|<span data-ttu-id="46832-116">Élément</span><span class="sxs-lookup"><span data-stu-id="46832-116">Element</span></span>|<span data-ttu-id="46832-117">Description</span><span class="sxs-lookup"><span data-stu-id="46832-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46832-118">\<add></span><span class="sxs-lookup"><span data-stu-id="46832-118">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="46832-119">Ajoute un certificat X.509 à la collection.</span><span class="sxs-lookup"><span data-stu-id="46832-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46832-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="46832-120">Parent Elements</span></span>  
  
|<span data-ttu-id="46832-121">Élément</span><span class="sxs-lookup"><span data-stu-id="46832-121">Element</span></span>|<span data-ttu-id="46832-122">Description</span><span class="sxs-lookup"><span data-stu-id="46832-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46832-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="46832-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="46832-124">Spécifie un jeton émis en guise d'information d'identification du service.</span><span class="sxs-lookup"><span data-stu-id="46832-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46832-125">Notes</span><span class="sxs-lookup"><span data-stu-id="46832-125">Remarks</span></span>  
 <span data-ttu-id="46832-126">Le scénario de jeton émis comporte trois étapes.</span><span class="sxs-lookup"><span data-stu-id="46832-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="46832-127">Lors de la première phase, un client qui tente d’accéder à un service est appelé *service de jeton sécurisé*.</span><span class="sxs-lookup"><span data-stu-id="46832-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="46832-128">Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language).</span><span class="sxs-lookup"><span data-stu-id="46832-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="46832-129">Le client retourne ensuite au service avec le jeton.</span><span class="sxs-lookup"><span data-stu-id="46832-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="46832-130">Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="46832-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="46832-131">Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="46832-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="46832-132">L’élément IssuedTokenAuthentication > est le référentiel de tels certificats de service de jeton sécurisé. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="46832-132">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="46832-133">Pour ajouter des certificats, utilisez l' [ \<élément knownCertificates >](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="46832-133">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="46832-134">Insérez un [ \<> d’ajout](add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="46832-134">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="46832-135">Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="46832-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="46832-136">Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.</span><span class="sxs-lookup"><span data-stu-id="46832-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="46832-137">Pour passer en revue les conditions requises pour qu’un client soit authentifié par un service fédéré, et pour plus d’informations sur l’utilisation de cet [élément de configuration, consultez Procédure: Configurez les informations d'](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)identification sur un service FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="46832-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="46832-138">Pour plus d’informations sur les scénarios fédérés, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="46832-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="46832-139">Pour obtenir un exemple qui montre comment remplir la collection dans la configuration, consultez [ \<ajouter des >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="46832-139">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46832-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46832-140">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="46832-141">\<add></span><span class="sxs-lookup"><span data-stu-id="46832-141">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="46832-142">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="46832-142">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="46832-143">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="46832-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="46832-144">Guide pratique pour Configurer les informations d’identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="46832-144">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="46832-145">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="46832-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="46832-146">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="46832-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="46832-147">\<add></span><span class="sxs-lookup"><span data-stu-id="46832-147">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="46832-148">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="46832-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
