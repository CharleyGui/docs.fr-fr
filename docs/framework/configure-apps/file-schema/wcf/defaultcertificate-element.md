---
title: Élément <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 2eaec4f4296f90579ca32d817f0a20da4ccc9a37
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153896"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="cbaa7-102">Élément \<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="cbaa7-102">\<defaultCertificate> Element</span></span>

<span data-ttu-id="cbaa7-103">Spécifie un certificat X.509 à utiliser lorsqu'un service ou un service d'émission de jeton de sécurité n'en fournit pas un via un protocole de négociation.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="cbaa7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbaa7-104">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbaa7-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cbaa7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cbaa7-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbaa7-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="cbaa7-107">Attributes</span></span>  
  
|<span data-ttu-id="cbaa7-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="cbaa7-108">Attribute</span></span>|<span data-ttu-id="cbaa7-109">Description</span><span class="sxs-lookup"><span data-stu-id="cbaa7-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbaa7-110">findValue</span><span class="sxs-lookup"><span data-stu-id="cbaa7-110">findValue</span></span>|<span data-ttu-id="cbaa7-111">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-111">String.</span></span> <span data-ttu-id="cbaa7-112">La valeur à rechercher.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-112">The value to search for.</span></span>|  
|<span data-ttu-id="cbaa7-113">x509FindType</span><span class="sxs-lookup"><span data-stu-id="cbaa7-113">x509FindType</span></span>|<span data-ttu-id="cbaa7-114">Énumération.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-114">Enumeration.</span></span> <span data-ttu-id="cbaa7-115">L'un des champs de certificat à rechercher.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-115">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="cbaa7-116">storeLocation</span><span class="sxs-lookup"><span data-stu-id="cbaa7-116">storeLocation</span></span>|<span data-ttu-id="cbaa7-117">Énumération.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-117">Enumeration.</span></span> <span data-ttu-id="cbaa7-118">L'un des deux emplacements du magasin du système à rechercher.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-118">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="cbaa7-119">storeName</span><span class="sxs-lookup"><span data-stu-id="cbaa7-119">storeName</span></span>|<span data-ttu-id="cbaa7-120">Énumération.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-120">Enumeration.</span></span> <span data-ttu-id="cbaa7-121">L'un des magasins de systèmes à rechercher.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-121">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="cbaa7-122">findValue, attribute</span><span class="sxs-lookup"><span data-stu-id="cbaa7-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="cbaa7-123">Valeur</span><span class="sxs-lookup"><span data-stu-id="cbaa7-123">Value</span></span>|<span data-ttu-id="cbaa7-124">Description</span><span class="sxs-lookup"><span data-stu-id="cbaa7-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbaa7-125">String</span><span class="sxs-lookup"><span data-stu-id="cbaa7-125">String</span></span>|<span data-ttu-id="cbaa7-126">La valeur dépend du champ (spécifié par l'attribut X509FindType) qui est recherché.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="cbaa7-127">Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="cbaa7-128">x509FindType, attribut</span><span class="sxs-lookup"><span data-stu-id="cbaa7-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="cbaa7-129">Valeur</span><span class="sxs-lookup"><span data-stu-id="cbaa7-129">Value</span></span>|<span data-ttu-id="cbaa7-130">Description</span><span class="sxs-lookup"><span data-stu-id="cbaa7-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbaa7-131">Énumération</span><span class="sxs-lookup"><span data-stu-id="cbaa7-131">Enumeration</span></span>|<span data-ttu-id="cbaa7-132">Les valeurs comprennent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="cbaa7-133">storeLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="cbaa7-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="cbaa7-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="cbaa7-134">Value</span></span>|<span data-ttu-id="cbaa7-135">Description</span><span class="sxs-lookup"><span data-stu-id="cbaa7-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbaa7-136">Énumération</span><span class="sxs-lookup"><span data-stu-id="cbaa7-136">Enumeration</span></span>|<span data-ttu-id="cbaa7-137">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="cbaa7-138">storeName, attribut</span><span class="sxs-lookup"><span data-stu-id="cbaa7-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="cbaa7-139">Valeur</span><span class="sxs-lookup"><span data-stu-id="cbaa7-139">Value</span></span>|<span data-ttu-id="cbaa7-140">Description</span><span class="sxs-lookup"><span data-stu-id="cbaa7-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbaa7-141">Énumération</span><span class="sxs-lookup"><span data-stu-id="cbaa7-141">Enumeration</span></span>|<span data-ttu-id="cbaa7-142">Les valeurs comprennent : AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople et TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbaa7-143">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cbaa7-143">Child Elements</span></span>  

 <span data-ttu-id="cbaa7-144">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbaa7-145">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cbaa7-145">Parent Elements</span></span>  
  
|<span data-ttu-id="cbaa7-146">Élément</span><span class="sxs-lookup"><span data-stu-id="cbaa7-146">Element</span></span>|<span data-ttu-id="cbaa7-147">Description</span><span class="sxs-lookup"><span data-stu-id="cbaa7-147">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="cbaa7-148">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-148">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbaa7-149">Notes</span><span class="sxs-lookup"><span data-stu-id="cbaa7-149">Remarks</span></span>  

 <span data-ttu-id="cbaa7-150">Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, le certificat spécifié par cet élément de configuration est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-150">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="cbaa7-151">Il stocke un certificat unique à utiliser lorsqu'aucun certificat n'est spécifié par un service.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-151">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbaa7-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="cbaa7-152">Example</span></span>  

 <span data-ttu-id="cbaa7-153">L’exemple suivant spécifie un certificat à utiliser pour les points de terminaison dont l’URI commence par `http://www.contoso.com` et un certificat à utiliser pour tous les autres points de terminaison qui n’effectuent pas de négociation de certificat.</span><span class="sxs-lookup"><span data-stu-id="cbaa7-153">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbaa7-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbaa7-154">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="cbaa7-155">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="cbaa7-155">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="cbaa7-156">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="cbaa7-156">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="cbaa7-157">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="cbaa7-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
