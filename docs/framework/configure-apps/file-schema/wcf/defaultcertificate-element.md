---
title: Élément <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400429"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="1d10b-102">\<defaultCertificate >, élément</span><span class="sxs-lookup"><span data-stu-id="1d10b-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="1d10b-103">Spécifie un certificat X.509 à utiliser lorsqu'un service ou un service d'émission de jeton de sécurité n'en fournit pas un via un protocole de négociation.</span><span class="sxs-lookup"><span data-stu-id="1d10b-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
<span data-ttu-id="1d10b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1d10b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1d10b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1d10b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1d10b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1d10b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="1d10b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1d10b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="1d10b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1d10b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="1d10b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="1d10b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="1d10b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="1d10b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="1d10b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultCertificate >**</span><span class="sxs-lookup"><span data-stu-id="1d10b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d10b-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d10b-112">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d10b-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1d10b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1d10b-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1d10b-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d10b-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="1d10b-115">Attributes</span></span>  
  
|<span data-ttu-id="1d10b-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="1d10b-116">Attribute</span></span>|<span data-ttu-id="1d10b-117">Description</span><span class="sxs-lookup"><span data-stu-id="1d10b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d10b-118">findValue</span><span class="sxs-lookup"><span data-stu-id="1d10b-118">findValue</span></span>|<span data-ttu-id="1d10b-119">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="1d10b-119">String.</span></span> <span data-ttu-id="1d10b-120">La valeur à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1d10b-120">The value to search for.</span></span>|  
|<span data-ttu-id="1d10b-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="1d10b-121">x509FindType</span></span>|<span data-ttu-id="1d10b-122">Énumération.</span><span class="sxs-lookup"><span data-stu-id="1d10b-122">Enumeration.</span></span> <span data-ttu-id="1d10b-123">L'un des champs de certificat à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1d10b-123">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="1d10b-124">storeLocation</span><span class="sxs-lookup"><span data-stu-id="1d10b-124">storeLocation</span></span>|<span data-ttu-id="1d10b-125">Énumération.</span><span class="sxs-lookup"><span data-stu-id="1d10b-125">Enumeration.</span></span> <span data-ttu-id="1d10b-126">L'un des deux emplacements du magasin du système à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1d10b-126">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="1d10b-127">storeName</span><span class="sxs-lookup"><span data-stu-id="1d10b-127">storeName</span></span>|<span data-ttu-id="1d10b-128">Énumération.</span><span class="sxs-lookup"><span data-stu-id="1d10b-128">Enumeration.</span></span> <span data-ttu-id="1d10b-129">L'un des magasins de systèmes à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1d10b-129">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="1d10b-130">findValue, attribute</span><span class="sxs-lookup"><span data-stu-id="1d10b-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="1d10b-131">`Value`</span><span class="sxs-lookup"><span data-stu-id="1d10b-131">Value</span></span>|<span data-ttu-id="1d10b-132">Description</span><span class="sxs-lookup"><span data-stu-id="1d10b-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d10b-133">String</span><span class="sxs-lookup"><span data-stu-id="1d10b-133">String</span></span>|<span data-ttu-id="1d10b-134">La valeur dépend du champ (spécifié par l'attribut X509FindType) qui est recherché.</span><span class="sxs-lookup"><span data-stu-id="1d10b-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="1d10b-135">Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="1d10b-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="1d10b-136">x509FindType, attribut</span><span class="sxs-lookup"><span data-stu-id="1d10b-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="1d10b-137">`Value`</span><span class="sxs-lookup"><span data-stu-id="1d10b-137">Value</span></span>|<span data-ttu-id="1d10b-138">Description</span><span class="sxs-lookup"><span data-stu-id="1d10b-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d10b-139">Énumération</span><span class="sxs-lookup"><span data-stu-id="1d10b-139">Enumeration</span></span>|<span data-ttu-id="1d10b-140">Les valeurs incluent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="1d10b-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="1d10b-141">storeLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="1d10b-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="1d10b-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="1d10b-142">Value</span></span>|<span data-ttu-id="1d10b-143">Description</span><span class="sxs-lookup"><span data-stu-id="1d10b-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d10b-144">Énumération</span><span class="sxs-lookup"><span data-stu-id="1d10b-144">Enumeration</span></span>|<span data-ttu-id="1d10b-145">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="1d10b-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="1d10b-146">storeName, attribut</span><span class="sxs-lookup"><span data-stu-id="1d10b-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="1d10b-147">`Value`</span><span class="sxs-lookup"><span data-stu-id="1d10b-147">Value</span></span>|<span data-ttu-id="1d10b-148">Description</span><span class="sxs-lookup"><span data-stu-id="1d10b-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d10b-149">Énumération</span><span class="sxs-lookup"><span data-stu-id="1d10b-149">Enumeration</span></span>|<span data-ttu-id="1d10b-150">Les valeurs incluent : AddressBook, AuthRoot, CertificateAuthority, non autorisé, My, root, TrustedPeople et TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="1d10b-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d10b-151">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1d10b-151">Child Elements</span></span>  
 <span data-ttu-id="1d10b-152">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1d10b-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d10b-153">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1d10b-153">Parent Elements</span></span>  
  
|<span data-ttu-id="1d10b-154">Élément</span><span class="sxs-lookup"><span data-stu-id="1d10b-154">Element</span></span>|<span data-ttu-id="1d10b-155">Description</span><span class="sxs-lookup"><span data-stu-id="1d10b-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d10b-156">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="1d10b-156">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="1d10b-157">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="1d10b-157">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d10b-158">Notes</span><span class="sxs-lookup"><span data-stu-id="1d10b-158">Remarks</span></span>  
 <span data-ttu-id="1d10b-159">Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, le certificat spécifié par cet élément de configuration est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client.</span><span class="sxs-lookup"><span data-stu-id="1d10b-159">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="1d10b-160">Il stocke un certificat unique à utiliser lorsqu'aucun certificat n'est spécifié par un service.</span><span class="sxs-lookup"><span data-stu-id="1d10b-160">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d10b-161">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d10b-161">Example</span></span>  
 <span data-ttu-id="1d10b-162">L’exemple suivant spécifie un certificat à utiliser pour les points de terminaison dont `http://www.contoso.com` l’URI commence par et un certificat à utiliser pour tous les autres points de terminaison qui n’effectuent pas de négociation de certificat.</span><span class="sxs-lookup"><span data-stu-id="1d10b-162">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="1d10b-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d10b-163">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="1d10b-164">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="1d10b-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1d10b-165">\<authentication></span><span class="sxs-lookup"><span data-stu-id="1d10b-165">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="1d10b-166">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="1d10b-166">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="1d10b-167">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="1d10b-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
