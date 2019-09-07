---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400337"
---
# <a name="knowncertificates"></a><span data-ttu-id="434b2-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="434b2-101">\<knownCertificates></span></span>
<span data-ttu-id="434b2-102">Représente une collection des certificats X.509 fournis pour authentifier des informations d’identification de sécurité publiées à partir d’un service d’émission de jetons de sécurité (STS).</span><span class="sxs-lookup"><span data-stu-id="434b2-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
<span data-ttu-id="434b2-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="434b2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="434b2-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="434b2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="434b2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="434b2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="434b2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="434b2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="434b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="434b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="434b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="434b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="434b2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="434b2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="434b2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownCertificates >**</span><span class="sxs-lookup"><span data-stu-id="434b2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="434b2-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="434b2-111">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="434b2-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="434b2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="434b2-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="434b2-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="434b2-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="434b2-114">Attributes</span></span>  
 <span data-ttu-id="434b2-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="434b2-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="434b2-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="434b2-116">Child Elements</span></span>  
  
|<span data-ttu-id="434b2-117">Élément</span><span class="sxs-lookup"><span data-stu-id="434b2-117">Element</span></span>|<span data-ttu-id="434b2-118">Description</span><span class="sxs-lookup"><span data-stu-id="434b2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="434b2-119">\<add></span><span class="sxs-lookup"><span data-stu-id="434b2-119">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="434b2-120">Ajoute un certificat X.509 à la collection.</span><span class="sxs-lookup"><span data-stu-id="434b2-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="434b2-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="434b2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="434b2-122">Élément</span><span class="sxs-lookup"><span data-stu-id="434b2-122">Element</span></span>|<span data-ttu-id="434b2-123">Description</span><span class="sxs-lookup"><span data-stu-id="434b2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="434b2-124">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="434b2-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="434b2-125">Spécifie un jeton émis en guise d'information d'identification du service.</span><span class="sxs-lookup"><span data-stu-id="434b2-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="434b2-126">Notes</span><span class="sxs-lookup"><span data-stu-id="434b2-126">Remarks</span></span>  
 <span data-ttu-id="434b2-127">Le scénario de jeton émis comporte trois étapes.</span><span class="sxs-lookup"><span data-stu-id="434b2-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="434b2-128">Lors de la première phase, un client qui tente d’accéder à un service est appelé *service de jeton sécurisé*.</span><span class="sxs-lookup"><span data-stu-id="434b2-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="434b2-129">Le service d'émission de jeton sécurisé authentifie ensuite le client et émet par la suite un jeton au client, généralement un jeton SAML (Security Assertions Markup Language).</span><span class="sxs-lookup"><span data-stu-id="434b2-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="434b2-130">Le client retourne ensuite au service avec le jeton.</span><span class="sxs-lookup"><span data-stu-id="434b2-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="434b2-131">Le service recherche dans le jeton les données lui permettant de l'authentifier, et par conséquent d'authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="434b2-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="434b2-132">Pour authentifier le jeton, le service doit connaître le certificat utilisé par le service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="434b2-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="434b2-133">L’élément IssuedTokenAuthentication > est le référentiel de tels certificats de service de jeton sécurisé. [ \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="434b2-133">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="434b2-134">Pour ajouter des certificats, utilisez l' [ \<élément knownCertificates >](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="434b2-134">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="434b2-135">Insérez un [ \<> d’ajout](add-of-knowncertificates.md) pour chaque certificat, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="434b2-135">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="434b2-136">Par défaut, les certificats doivent être obtenus auprès d'un service d'émission de jeton sécurisé.</span><span class="sxs-lookup"><span data-stu-id="434b2-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="434b2-137">Ces certificats « connus » garantissent que seuls les clients légitimes peuvent accéder à un service.</span><span class="sxs-lookup"><span data-stu-id="434b2-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="434b2-138">Pour passer en revue les conditions requises pour qu’un client soit authentifié par un service fédéré, et pour plus d’informations sur l’utilisation de cet [élément de configuration, consultez Procédure : Configurez les informations d'](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)identification sur un service FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="434b2-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="434b2-139">Pour plus d’informations sur les scénarios fédérés, consultez [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="434b2-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="434b2-140">Pour obtenir un exemple qui montre comment remplir la collection dans la configuration, consultez [ \<ajouter des >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="434b2-140">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434b2-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="434b2-141">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="434b2-142">\<add></span><span class="sxs-lookup"><span data-stu-id="434b2-142">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="434b2-143">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="434b2-143">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="434b2-144">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="434b2-144">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="434b2-145">Guide pratique : Configurer les informations d’identification sur un service FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="434b2-145">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="434b2-146">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="434b2-146">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="434b2-147">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="434b2-147">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="434b2-148">\<add></span><span class="sxs-lookup"><span data-stu-id="434b2-148">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="434b2-149">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="434b2-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
