---
title: <serviceCertificate>d' <clientCredentials> élément
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399685"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="93401-102">\<serviceCertificate > de \<l’élément ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="93401-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="93401-103">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="93401-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
<span data-ttu-id="93401-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="93401-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93401-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="93401-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="93401-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="93401-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="93401-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="93401-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="93401-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="93401-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="93401-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="93401-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="93401-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**</span><span class="sxs-lookup"><span data-stu-id="93401-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93401-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93401-111">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93401-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="93401-112">Attributes and Elements</span></span>  
 <span data-ttu-id="93401-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="93401-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93401-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="93401-114">Attributes</span></span>  
 <span data-ttu-id="93401-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="93401-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93401-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="93401-116">Child Elements</span></span>  
  
|<span data-ttu-id="93401-117">Élément</span><span class="sxs-lookup"><span data-stu-id="93401-117">Element</span></span>|<span data-ttu-id="93401-118">Description</span><span class="sxs-lookup"><span data-stu-id="93401-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93401-119">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="93401-119">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="93401-120">Spécifie un certificat X.509 à utiliser lorsqu'un service ou un service d'émission de jeton de sécurité n'en fournit pas un via un protocole de négociation.</span><span class="sxs-lookup"><span data-stu-id="93401-120">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="93401-121">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="93401-121">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="93401-122">Représente une collection de certificats X.509 fournie par les services spécifiques (étendus) à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="93401-122">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="93401-123">Cette collection est utilisée en général pour spécifier les certificats de service pour les services d’émission de jeton de sécurité dans un scénario fédéré.</span><span class="sxs-lookup"><span data-stu-id="93401-123">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="93401-124">\<authentication></span><span class="sxs-lookup"><span data-stu-id="93401-124">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="93401-125">Spécifie les comportements d'authentification des certificats de service utilisés par un client.</span><span class="sxs-lookup"><span data-stu-id="93401-125">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93401-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="93401-126">Parent Elements</span></span>  
  
|<span data-ttu-id="93401-127">Élément</span><span class="sxs-lookup"><span data-stu-id="93401-127">Element</span></span>|<span data-ttu-id="93401-128">Description</span><span class="sxs-lookup"><span data-stu-id="93401-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93401-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="93401-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="93401-130">Spécifie les informations d'identification utilisées par le client pour l'authentifier auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="93401-130">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93401-131">Notes</span><span class="sxs-lookup"><span data-stu-id="93401-131">Remarks</span></span>  
 <span data-ttu-id="93401-132">Cet élément de configuration spécifie les paramètres utilisés par le client pour valider le certificat présenté par le service à l'aide de l'authentification SSL.</span><span class="sxs-lookup"><span data-stu-id="93401-132">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="93401-133">Il contient également tout certificat pour le service explicitement configuré sur le client à utiliser pour chiffrer des messages au service à l'aide de la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="93401-133">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="93401-134">Les attributs de l' `serviceCertificate` élément sont identiques aux attributs de l' [ \<> ClientCertificate](clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="93401-134">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93401-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93401-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="93401-136">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="93401-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="93401-137">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="93401-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="93401-138">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="93401-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="93401-139">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="93401-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
