---
title: <add>d' <scopedCertificates> élément
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: b00a342108beca69a906fbf6212915768e98778f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398347"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="006de-102">\<Ajouter > de \<l’élément de > scopedCertificates</span><span class="sxs-lookup"><span data-stu-id="006de-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="006de-103">Ajoute un certificat X.509 à la collection de certificats étendus.</span><span class="sxs-lookup"><span data-stu-id="006de-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
<span data-ttu-id="006de-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="006de-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="006de-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="006de-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="006de-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="006de-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="006de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="006de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="006de-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="006de-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="006de-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="006de-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="006de-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="006de-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="006de-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<scopedCertificates >** ](scopedcertificates-element.md)</span><span class="sxs-lookup"><span data-stu-id="006de-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)</span></span>\
<span data-ttu-id="006de-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="006de-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="006de-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="006de-113">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="006de-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="006de-114">Attributes and Elements</span></span>  
 <span data-ttu-id="006de-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="006de-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="006de-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="006de-116">Attributes</span></span>  
  
|<span data-ttu-id="006de-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="006de-117">Attribute</span></span>|<span data-ttu-id="006de-118">Description</span><span class="sxs-lookup"><span data-stu-id="006de-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="006de-119">targetUri</span><span class="sxs-lookup"><span data-stu-id="006de-119">targetUri</span></span>|<span data-ttu-id="006de-120">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="006de-120">String.</span></span> <span data-ttu-id="006de-121">Spécifie l'URI du service a associé au certificat.</span><span class="sxs-lookup"><span data-stu-id="006de-121">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="006de-122">findValue</span><span class="sxs-lookup"><span data-stu-id="006de-122">findValue</span></span>|<span data-ttu-id="006de-123">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="006de-123">String.</span></span> <span data-ttu-id="006de-124">La valeur à rechercher.</span><span class="sxs-lookup"><span data-stu-id="006de-124">The value to search for.</span></span>|  
|<span data-ttu-id="006de-125">x509FindType</span><span class="sxs-lookup"><span data-stu-id="006de-125">x509FindType</span></span>|<span data-ttu-id="006de-126">Énumération.</span><span class="sxs-lookup"><span data-stu-id="006de-126">Enumeration.</span></span> <span data-ttu-id="006de-127">L'un des champs de certificat à rechercher.</span><span class="sxs-lookup"><span data-stu-id="006de-127">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="006de-128">storeLocation</span><span class="sxs-lookup"><span data-stu-id="006de-128">storeLocation</span></span>|<span data-ttu-id="006de-129">Énumération.</span><span class="sxs-lookup"><span data-stu-id="006de-129">Enumeration.</span></span> <span data-ttu-id="006de-130">L'un des deux emplacements du magasin dans lequel effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="006de-130">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="006de-131">storeName</span><span class="sxs-lookup"><span data-stu-id="006de-131">storeName</span></span>|<span data-ttu-id="006de-132">Énumération.</span><span class="sxs-lookup"><span data-stu-id="006de-132">Enumeration.</span></span> <span data-ttu-id="006de-133">L'un des magasins de systèmes à rechercher.</span><span class="sxs-lookup"><span data-stu-id="006de-133">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="006de-134">findValue, attribute</span><span class="sxs-lookup"><span data-stu-id="006de-134">findValue Attribute</span></span>  
  
|<span data-ttu-id="006de-135">`Value`</span><span class="sxs-lookup"><span data-stu-id="006de-135">Value</span></span>|<span data-ttu-id="006de-136">Description</span><span class="sxs-lookup"><span data-stu-id="006de-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="006de-137">String</span><span class="sxs-lookup"><span data-stu-id="006de-137">String</span></span>|<span data-ttu-id="006de-138">La valeur dépend du champ (spécifié par l'attribut X509FindType) qui est recherché.</span><span class="sxs-lookup"><span data-stu-id="006de-138">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="006de-139">Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="006de-139">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="006de-140">x509FindType, attribut</span><span class="sxs-lookup"><span data-stu-id="006de-140">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="006de-141">Valeur</span><span class="sxs-lookup"><span data-stu-id="006de-141">Value</span></span>|<span data-ttu-id="006de-142">Description</span><span class="sxs-lookup"><span data-stu-id="006de-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="006de-143">Énumération</span><span class="sxs-lookup"><span data-stu-id="006de-143">Enumeration</span></span>|<span data-ttu-id="006de-144">Les valeurs incluent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="006de-144">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="006de-145">storeLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="006de-145">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="006de-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="006de-146">Value</span></span>|<span data-ttu-id="006de-147">Description</span><span class="sxs-lookup"><span data-stu-id="006de-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="006de-148">Énumération</span><span class="sxs-lookup"><span data-stu-id="006de-148">Enumeration</span></span>|<span data-ttu-id="006de-149">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="006de-149">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="006de-150">storeName, attribut</span><span class="sxs-lookup"><span data-stu-id="006de-150">storeName Attribute</span></span>  
  
|<span data-ttu-id="006de-151">Valeur</span><span class="sxs-lookup"><span data-stu-id="006de-151">Value</span></span>|<span data-ttu-id="006de-152">Description</span><span class="sxs-lookup"><span data-stu-id="006de-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="006de-153">Énumération</span><span class="sxs-lookup"><span data-stu-id="006de-153">Enumeration</span></span>|<span data-ttu-id="006de-154">Les valeurs incluent : AddressBook, AuthRoot, CertificateAuthority, non autorisé, My, root, TrustedPeople et TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="006de-154">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="006de-155">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="006de-155">Child Elements</span></span>  
 <span data-ttu-id="006de-156">Aucun.</span><span class="sxs-lookup"><span data-stu-id="006de-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="006de-157">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="006de-157">Parent Elements</span></span>  
  
|<span data-ttu-id="006de-158">Élément</span><span class="sxs-lookup"><span data-stu-id="006de-158">Element</span></span>|<span data-ttu-id="006de-159">Description</span><span class="sxs-lookup"><span data-stu-id="006de-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="006de-160">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="006de-160">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="006de-161">Représente une collection de certificats X.509 fournie par les services spécifiques (étendus) à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="006de-161">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="006de-162">Notes</span><span class="sxs-lookup"><span data-stu-id="006de-162">Remarks</span></span>  
 <span data-ttu-id="006de-163">Cet élément permet au client de configurer un certificat de service à utiliser en fonction de l'URL du service avec lequel il communique.</span><span class="sxs-lookup"><span data-stu-id="006de-163">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="006de-164">Ceci s'avère particulièrement utile dans les scénarios de jeton émis dans lesquels un client peut communiquer avec plusieurs services (autant le service final que les services de jeton de sécurité intermédiaire).</span><span class="sxs-lookup"><span data-stu-id="006de-164">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="006de-165">Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, ce certificat est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client.</span><span class="sxs-lookup"><span data-stu-id="006de-165">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="006de-166">Le certificat par défaut est utilisé si une liaison requiert un certificat pour le service et qu’aucun certificat spécifique de l’URL du service n’est trouvé dans ScopedCertificates.</span><span class="sxs-lookup"><span data-stu-id="006de-166">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="006de-167">Pour plus d’informations, consultez la section « certificats délimités [» de la rubrique How to : Créez un client](../../../wcf/feature-details/how-to-create-a-federated-client.md)fédéré.</span><span class="sxs-lookup"><span data-stu-id="006de-167">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="006de-168">Exemple</span><span class="sxs-lookup"><span data-stu-id="006de-168">Example</span></span>  
 <span data-ttu-id="006de-169">L'exemple suivant illustre l'ajout d'un certificat X.509 à la collection.</span><span class="sxs-lookup"><span data-stu-id="006de-169">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="006de-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="006de-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="006de-171">Guide pratique pour Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="006de-171">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="006de-172">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="006de-172">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="006de-173">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="006de-173">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="006de-174">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="006de-174">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
