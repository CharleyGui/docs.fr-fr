---
title: <serviceCertificate>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: a3013d0f7efd3014892cf6400447d708809c5fcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936338"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="e2490-102">\<serviceCertificate > de \<l’élément ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="e2490-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="e2490-103">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="e2490-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="e2490-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e2490-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e2490-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="e2490-105">\<behaviors></span></span>  
<span data-ttu-id="e2490-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e2490-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e2490-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="e2490-107">\<behavior></span></span>  
<span data-ttu-id="e2490-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e2490-108">\<clientCredentials></span></span>  
<span data-ttu-id="e2490-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="e2490-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2490-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2490-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2490-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e2490-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e2490-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e2490-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2490-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e2490-113">Attributes</span></span>  
 <span data-ttu-id="e2490-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e2490-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e2490-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e2490-115">Child Elements</span></span>  
  
|<span data-ttu-id="e2490-116">Élément</span><span class="sxs-lookup"><span data-stu-id="e2490-116">Element</span></span>|<span data-ttu-id="e2490-117">Description</span><span class="sxs-lookup"><span data-stu-id="e2490-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2490-118">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="e2490-118">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="e2490-119">Spécifie un certificat X.509 à utiliser lorsqu'un service ou un service d'émission de jeton de sécurité n'en fournit pas un via un protocole de négociation.</span><span class="sxs-lookup"><span data-stu-id="e2490-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="e2490-120">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="e2490-120">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="e2490-121">Représente une collection de certificats X.509 fournie par les services spécifiques (étendus) à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="e2490-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="e2490-122">Cette collection est utilisée en général pour spécifier les certificats de service pour les services d’émission de jeton de sécurité dans un scénario fédéré.</span><span class="sxs-lookup"><span data-stu-id="e2490-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="e2490-123">\<authentication></span><span class="sxs-lookup"><span data-stu-id="e2490-123">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="e2490-124">Spécifie les comportements d'authentification des certificats de service utilisés par un client.</span><span class="sxs-lookup"><span data-stu-id="e2490-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2490-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e2490-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e2490-126">Élément</span><span class="sxs-lookup"><span data-stu-id="e2490-126">Element</span></span>|<span data-ttu-id="e2490-127">Description</span><span class="sxs-lookup"><span data-stu-id="e2490-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2490-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e2490-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="e2490-129">Spécifie les informations d'identification utilisées par le client pour l'authentifier auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="e2490-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2490-130">Notes</span><span class="sxs-lookup"><span data-stu-id="e2490-130">Remarks</span></span>  
 <span data-ttu-id="e2490-131">Cet élément de configuration spécifie les paramètres utilisés par le client pour valider le certificat présenté par le service à l'aide de l'authentification SSL.</span><span class="sxs-lookup"><span data-stu-id="e2490-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="e2490-132">Il contient également tout certificat pour le service explicitement configuré sur le client à utiliser pour chiffrer des messages au service à l'aide de la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="e2490-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="e2490-133">Les attributs de l' `serviceCertificate` élément sont identiques aux attributs de l' [ \<> ClientCertificate](clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="e2490-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2490-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2490-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="e2490-135">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="e2490-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e2490-136">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="e2490-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="e2490-137">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="e2490-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e2490-138">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e2490-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
