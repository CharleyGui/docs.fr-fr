---
title: <add> d' <scopedCertificates> élément
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 28777ecac130295a8ba82a8e4d67cc519d088d8a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195140"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="41c94-102">\<add> d' \<scopedCertificates> élément</span><span class="sxs-lookup"><span data-stu-id="41c94-102">\<add> of \<scopedCertificates> Element</span></span>

<span data-ttu-id="41c94-103">Ajoute un certificat X.509 à la collection de certificats étendus.</span><span class="sxs-lookup"><span data-stu-id="41c94-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="41c94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41c94-104">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41c94-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="41c94-105">Attributes and Elements</span></span>  

 <span data-ttu-id="41c94-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="41c94-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41c94-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="41c94-107">Attributes</span></span>  
  
|<span data-ttu-id="41c94-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="41c94-108">Attribute</span></span>|<span data-ttu-id="41c94-109">Description</span><span class="sxs-lookup"><span data-stu-id="41c94-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41c94-110">targetUri</span><span class="sxs-lookup"><span data-stu-id="41c94-110">targetUri</span></span>|<span data-ttu-id="41c94-111">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="41c94-111">String.</span></span> <span data-ttu-id="41c94-112">Spécifie l'URI du service a associé au certificat.</span><span class="sxs-lookup"><span data-stu-id="41c94-112">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="41c94-113">findValue</span><span class="sxs-lookup"><span data-stu-id="41c94-113">findValue</span></span>|<span data-ttu-id="41c94-114">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="41c94-114">String.</span></span> <span data-ttu-id="41c94-115">La valeur à rechercher.</span><span class="sxs-lookup"><span data-stu-id="41c94-115">The value to search for.</span></span>|  
|<span data-ttu-id="41c94-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="41c94-116">x509FindType</span></span>|<span data-ttu-id="41c94-117">Énumération.</span><span class="sxs-lookup"><span data-stu-id="41c94-117">Enumeration.</span></span> <span data-ttu-id="41c94-118">L'un des champs de certificat à rechercher.</span><span class="sxs-lookup"><span data-stu-id="41c94-118">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="41c94-119">storeLocation</span><span class="sxs-lookup"><span data-stu-id="41c94-119">storeLocation</span></span>|<span data-ttu-id="41c94-120">Énumération.</span><span class="sxs-lookup"><span data-stu-id="41c94-120">Enumeration.</span></span> <span data-ttu-id="41c94-121">L'un des deux emplacements du magasin dans lequel effectuer la recherche.</span><span class="sxs-lookup"><span data-stu-id="41c94-121">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="41c94-122">storeName</span><span class="sxs-lookup"><span data-stu-id="41c94-122">storeName</span></span>|<span data-ttu-id="41c94-123">Énumération.</span><span class="sxs-lookup"><span data-stu-id="41c94-123">Enumeration.</span></span> <span data-ttu-id="41c94-124">L'un des magasins de systèmes à rechercher.</span><span class="sxs-lookup"><span data-stu-id="41c94-124">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="41c94-125">findValue, attribute</span><span class="sxs-lookup"><span data-stu-id="41c94-125">findValue Attribute</span></span>  
  
|<span data-ttu-id="41c94-126">Valeur</span><span class="sxs-lookup"><span data-stu-id="41c94-126">Value</span></span>|<span data-ttu-id="41c94-127">Description</span><span class="sxs-lookup"><span data-stu-id="41c94-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41c94-128">String</span><span class="sxs-lookup"><span data-stu-id="41c94-128">String</span></span>|<span data-ttu-id="41c94-129">La valeur dépend du champ (spécifié par l'attribut X509FindType) qui est recherché.</span><span class="sxs-lookup"><span data-stu-id="41c94-129">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="41c94-130">Par exemple, lors de la recherche d'une empreinte numérique, la valeur doit être une chaîne de nombres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="41c94-130">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="41c94-131">x509FindType, attribut</span><span class="sxs-lookup"><span data-stu-id="41c94-131">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="41c94-132">Valeur</span><span class="sxs-lookup"><span data-stu-id="41c94-132">Value</span></span>|<span data-ttu-id="41c94-133">Description</span><span class="sxs-lookup"><span data-stu-id="41c94-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41c94-134">Énumération</span><span class="sxs-lookup"><span data-stu-id="41c94-134">Enumeration</span></span>|<span data-ttu-id="41c94-135">Les valeurs comprennent : FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="41c94-135">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="41c94-136">storeLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="41c94-136">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="41c94-137">Valeur</span><span class="sxs-lookup"><span data-stu-id="41c94-137">Value</span></span>|<span data-ttu-id="41c94-138">Description</span><span class="sxs-lookup"><span data-stu-id="41c94-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41c94-139">Énumération</span><span class="sxs-lookup"><span data-stu-id="41c94-139">Enumeration</span></span>|<span data-ttu-id="41c94-140">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="41c94-140">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="41c94-141">storeName, attribut</span><span class="sxs-lookup"><span data-stu-id="41c94-141">storeName Attribute</span></span>  
  
|<span data-ttu-id="41c94-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="41c94-142">Value</span></span>|<span data-ttu-id="41c94-143">Description</span><span class="sxs-lookup"><span data-stu-id="41c94-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41c94-144">Énumération</span><span class="sxs-lookup"><span data-stu-id="41c94-144">Enumeration</span></span>|<span data-ttu-id="41c94-145">Les valeurs comprennent : AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople et TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="41c94-145">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41c94-146">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="41c94-146">Child Elements</span></span>  

 <span data-ttu-id="41c94-147">Aucun.</span><span class="sxs-lookup"><span data-stu-id="41c94-147">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41c94-148">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="41c94-148">Parent Elements</span></span>  
  
|<span data-ttu-id="41c94-149">Élément</span><span class="sxs-lookup"><span data-stu-id="41c94-149">Element</span></span>|<span data-ttu-id="41c94-150">Description</span><span class="sxs-lookup"><span data-stu-id="41c94-150">Description</span></span>|  
|-------------|-----------------|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="41c94-151">Représente une collection de certificats X.509 fournie par les services spécifiques (étendus) à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="41c94-151">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41c94-152">Notes</span><span class="sxs-lookup"><span data-stu-id="41c94-152">Remarks</span></span>  

 <span data-ttu-id="41c94-153">Cet élément permet au client de configurer un certificat de service à utiliser en fonction de l'URL du service avec lequel il communique.</span><span class="sxs-lookup"><span data-stu-id="41c94-153">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="41c94-154">Ceci s'avère particulièrement utile dans les scénarios de jeton émis dans lesquels un client peut communiquer avec plusieurs services (autant le service final que les services de jeton de sécurité intermédiaire).</span><span class="sxs-lookup"><span data-stu-id="41c94-154">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="41c94-155">Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, ce certificat est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client.</span><span class="sxs-lookup"><span data-stu-id="41c94-155">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="41c94-156">Le certificat par défaut est utilisé si une liaison requiert un certificat pour le service et qu’aucun certificat spécifique de l’URL du service n’est trouvé dans ScopedCertificates.</span><span class="sxs-lookup"><span data-stu-id="41c94-156">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="41c94-157">Pour plus d’informations, consultez la section « certificats délimités » [dans How to : Create a Federated client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="41c94-157">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41c94-158">Exemple</span><span class="sxs-lookup"><span data-stu-id="41c94-158">Example</span></span>  

 <span data-ttu-id="41c94-159">L'exemple suivant illustre l'ajout d'un certificat X.509 à la collection.</span><span class="sxs-lookup"><span data-stu-id="41c94-159">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41c94-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41c94-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="41c94-161">Procédure : créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="41c94-161">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="41c94-162">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="41c94-162">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="41c94-163">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="41c94-163">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="41c94-164">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="41c94-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
