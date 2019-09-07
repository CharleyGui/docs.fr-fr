---
title: Élément <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 3c06159709df0afe2a475de1e186b0114af32bc2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399953"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="14f04-102">\<scopedCertificates >, élément</span><span class="sxs-lookup"><span data-stu-id="14f04-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="14f04-103">Représente une collection de certificats X.509 fournie par les services spécifiques (étendus) à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="14f04-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="14f04-104">Cette collection est utilisée en général pour spécifier les certificats de service pour les services d’émission de jeton de sécurité dans un scénario fédéré.</span><span class="sxs-lookup"><span data-stu-id="14f04-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
<span data-ttu-id="14f04-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="14f04-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="14f04-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="14f04-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="14f04-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="14f04-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="14f04-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="14f04-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="14f04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="14f04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="14f04-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="14f04-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="14f04-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="14f04-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="14f04-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<scopedCertificates >**</span><span class="sxs-lookup"><span data-stu-id="14f04-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14f04-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14f04-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14f04-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="14f04-114">Attributes and Elements</span></span>  
 <span data-ttu-id="14f04-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="14f04-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14f04-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="14f04-116">Attributes</span></span>  
 <span data-ttu-id="14f04-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="14f04-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14f04-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="14f04-118">Child Elements</span></span>  
  
|<span data-ttu-id="14f04-119">Élément</span><span class="sxs-lookup"><span data-stu-id="14f04-119">Element</span></span>|<span data-ttu-id="14f04-120">Description</span><span class="sxs-lookup"><span data-stu-id="14f04-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14f04-121">\<add></span><span class="sxs-lookup"><span data-stu-id="14f04-121">\<add></span></span>](add-of-scopedcertificates-element.md)|<span data-ttu-id="14f04-122">Ajoute un certificat X.509 à la collection de certificats étendus.</span><span class="sxs-lookup"><span data-stu-id="14f04-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14f04-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="14f04-123">Parent Elements</span></span>  
  
|<span data-ttu-id="14f04-124">Élément</span><span class="sxs-lookup"><span data-stu-id="14f04-124">Element</span></span>|<span data-ttu-id="14f04-125">Description</span><span class="sxs-lookup"><span data-stu-id="14f04-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14f04-126">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="14f04-126">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="14f04-127">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="14f04-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14f04-128">Notes</span><span class="sxs-lookup"><span data-stu-id="14f04-128">Remarks</span></span>  
 <span data-ttu-id="14f04-129">Cette collection permet au client de configurer les certificats de service à utiliser en fonction de l’URL du service avec lequel il communique.</span><span class="sxs-lookup"><span data-stu-id="14f04-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="14f04-130">Ceci s'avère particulièrement utile dans les scénarios de jeton émis dans lesquels un client peut communiquer avec plusieurs services (autant le service final que les services de jeton de sécurité intermédiaire).</span><span class="sxs-lookup"><span data-stu-id="14f04-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="14f04-131">Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, ce certificat est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client.</span><span class="sxs-lookup"><span data-stu-id="14f04-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="14f04-132">Le certificat par défaut est utilisé si une liaison requiert un certificat pour le service et qu’aucun certificat spécifique de l’URL du service n’est trouvé dans ScopedCertificates.</span><span class="sxs-lookup"><span data-stu-id="14f04-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="14f04-133">Pour plus d’informations, consultez la section « certificats délimités [» de la rubrique How to : Créez un client](../../../wcf/feature-details/how-to-create-a-federated-client.md)fédéré.</span><span class="sxs-lookup"><span data-stu-id="14f04-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14f04-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="14f04-134">Example</span></span>  
 <span data-ttu-id="14f04-135">L’exemple suivant spécifie un certificat de service que le client doit utiliser lors de la communication avec les points `http://www.contoso.com` de terminaison dont le nom de domaine se trouve sur le protocole http.</span><span class="sxs-lookup"><span data-stu-id="14f04-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="14f04-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14f04-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="14f04-137">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="14f04-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="14f04-138">Guide pratique pour Créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="14f04-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="14f04-139">\<add></span><span class="sxs-lookup"><span data-stu-id="14f04-139">\<add></span></span>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="14f04-140">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="14f04-140">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="14f04-141">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="14f04-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
