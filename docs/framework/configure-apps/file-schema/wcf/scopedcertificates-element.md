---
title: Élément <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 4bee627fe186ed8dd85c118a37f59f575eb4650e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162255"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="3a1f0-102">Élément \<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="3a1f0-102">\<scopedCertificates> Element</span></span>

<span data-ttu-id="3a1f0-103">Représente une collection de certificats X.509 fournie par les services spécifiques (étendus) à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="3a1f0-104">Cette collection est utilisée en général pour spécifier les certificats de service pour les services d’émission de jeton de sécurité dans un scénario fédéré.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="3a1f0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a1f0-105">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a1f0-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3a1f0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3a1f0-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a1f0-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="3a1f0-108">Attributes</span></span>  

 <span data-ttu-id="3a1f0-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a1f0-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3a1f0-110">Child Elements</span></span>  
  
|<span data-ttu-id="3a1f0-111">Élément</span><span class="sxs-lookup"><span data-stu-id="3a1f0-111">Element</span></span>|<span data-ttu-id="3a1f0-112">Description</span><span class="sxs-lookup"><span data-stu-id="3a1f0-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|<span data-ttu-id="3a1f0-113">Ajoute un certificat X.509 à la collection de certificats étendus.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-113">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a1f0-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3a1f0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="3a1f0-115">Élément</span><span class="sxs-lookup"><span data-stu-id="3a1f0-115">Element</span></span>|<span data-ttu-id="3a1f0-116">Description</span><span class="sxs-lookup"><span data-stu-id="3a1f0-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="3a1f0-117">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-117">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a1f0-118">Notes</span><span class="sxs-lookup"><span data-stu-id="3a1f0-118">Remarks</span></span>  

 <span data-ttu-id="3a1f0-119">Cette collection permet au client de configurer les certificats de service à utiliser en fonction de l’URL du service avec lequel il communique.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-119">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="3a1f0-120">Ceci s'avère particulièrement utile dans les scénarios de jeton émis dans lesquels un client peut communiquer avec plusieurs services (autant le service final que les services de jeton de sécurité intermédiaire).</span><span class="sxs-lookup"><span data-stu-id="3a1f0-120">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="3a1f0-121">Pour les liaisons qui utilisent la sécurité de message basée sur des certificats, ce certificat est utilisé pour chiffrer les messages au service et doit être utilisé par le service pour signer les réponses au client.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-121">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="3a1f0-122">Le certificat par défaut est utilisé si une liaison requiert un certificat pour le service et qu’aucun certificat spécifique de l’URL du service n’est trouvé dans ScopedCertificates.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-122">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="3a1f0-123">Pour plus d’informations, consultez la section « certificats délimités » [dans How to : Create a Federated client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="3a1f0-123">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a1f0-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a1f0-124">Example</span></span>  

 <span data-ttu-id="3a1f0-125">L’exemple suivant spécifie un certificat de service que le client doit utiliser lors de la communication avec les points de terminaison dont le nom de domaine se trouve `http://www.contoso.com` sur le protocole http.</span><span class="sxs-lookup"><span data-stu-id="3a1f0-125">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a1f0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a1f0-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="3a1f0-127">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="3a1f0-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3a1f0-128">Procédure : créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="3a1f0-128">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="3a1f0-129">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="3a1f0-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="3a1f0-130">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="3a1f0-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
