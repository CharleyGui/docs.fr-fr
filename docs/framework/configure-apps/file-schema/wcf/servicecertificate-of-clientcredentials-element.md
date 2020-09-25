---
title: <serviceCertificate> d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 502452c664f2dcb0856f72e25ff8b1517f432919
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172890"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="a9238-102">\<serviceCertificate> d' \<clientCredentials> élément</span><span class="sxs-lookup"><span data-stu-id="a9238-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>

<span data-ttu-id="a9238-103">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="a9238-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="a9238-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9238-104">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9238-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a9238-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a9238-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a9238-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9238-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a9238-107">Attributes</span></span>  

 <span data-ttu-id="a9238-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a9238-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a9238-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a9238-109">Child Elements</span></span>  
  
|<span data-ttu-id="a9238-110">Élément</span><span class="sxs-lookup"><span data-stu-id="a9238-110">Element</span></span>|<span data-ttu-id="a9238-111">Description</span><span class="sxs-lookup"><span data-stu-id="a9238-111">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|<span data-ttu-id="a9238-112">Spécifie un certificat X.509 à utiliser lorsqu'un service ou un service d'émission de jeton de sécurité n'en fournit pas un via un protocole de négociation.</span><span class="sxs-lookup"><span data-stu-id="a9238-112">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="a9238-113">Représente une collection de certificats X.509 fournie par les services spécifiques (étendus) à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="a9238-113">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="a9238-114">Cette collection est utilisée en général pour spécifier les certificats de service pour les services d’émission de jeton de sécurité dans un scénario fédéré.</span><span class="sxs-lookup"><span data-stu-id="a9238-114">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="a9238-115">Spécifie les comportements d'authentification des certificats de service utilisés par un client.</span><span class="sxs-lookup"><span data-stu-id="a9238-115">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9238-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a9238-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a9238-117">Élément</span><span class="sxs-lookup"><span data-stu-id="a9238-117">Element</span></span>|<span data-ttu-id="a9238-118">Description</span><span class="sxs-lookup"><span data-stu-id="a9238-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="a9238-119">Spécifie les informations d'identification utilisées par le client pour l'authentifier auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="a9238-119">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9238-120">Notes</span><span class="sxs-lookup"><span data-stu-id="a9238-120">Remarks</span></span>  

 <span data-ttu-id="a9238-121">Cet élément de configuration spécifie les paramètres utilisés par le client pour valider le certificat présenté par le service à l'aide de l'authentification SSL.</span><span class="sxs-lookup"><span data-stu-id="a9238-121">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="a9238-122">Il contient également tout certificat pour le service explicitement configuré sur le client à utiliser pour chiffrer des messages au service à l'aide de la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="a9238-122">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="a9238-123">Les attributs de l' `serviceCertificate` élément sont identiques aux attributs de [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="a9238-123">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9238-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9238-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="a9238-125">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="a9238-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a9238-126">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="a9238-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a9238-127">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="a9238-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a9238-128">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="a9238-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
