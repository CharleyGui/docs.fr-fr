---
title: <security> de <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: be2f48f7d9c3be4ea0a5fe95436930b3f23c7551
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170062"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="f5834-102">\<security> de \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="f5834-102">\<security> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="f5834-103">Définit les paramètres de sécurité de transport pour le canal d'intégration MSMQ (Message Queuing).</span><span class="sxs-lookup"><span data-stu-id="f5834-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f5834-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5834-104">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5834-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f5834-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f5834-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f5834-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5834-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="f5834-107">Attributes</span></span>  
  
|<span data-ttu-id="f5834-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f5834-108">Attribute</span></span>|<span data-ttu-id="f5834-109">Description</span><span class="sxs-lookup"><span data-stu-id="f5834-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5834-110">mode</span><span class="sxs-lookup"><span data-stu-id="f5834-110">mode</span></span>|<span data-ttu-id="f5834-111">Spécifie le type de sécurité qui contrôle l'intégrité, la confidentialité et l'authentification avec le canal d'intégration Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="f5834-111">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="f5834-112">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5834-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f5834-113">-None : cela désactive la sécurité.</span><span class="sxs-lookup"><span data-stu-id="f5834-113">-   None: This disables security.</span></span><br /><span data-ttu-id="f5834-114">-Transport : la protection et l’authentification sont proposées par le transport.</span><span class="sxs-lookup"><span data-stu-id="f5834-114">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="f5834-115">Cela s'applique à la sécurité des message entre les deux gestionnaires de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="f5834-115">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="f5834-116">Il n'y a aucune sécurité offerte entre l'application et gestionnaire de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="f5834-116">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="f5834-117">Les applications Msmq existantes sont équivalentes au niveau des fonctionnalités avec ce type de mode de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f5834-117">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="f5834-118">La valeur par défaut est `Transport`.</span><span class="sxs-lookup"><span data-stu-id="f5834-118">The default value is `Transport`.</span></span> <span data-ttu-id="f5834-119">Cet attribut est de type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f5834-119">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5834-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f5834-120">Child Elements</span></span>  
  
|<span data-ttu-id="f5834-121">Élément</span><span class="sxs-lookup"><span data-stu-id="f5834-121">Element</span></span>|<span data-ttu-id="f5834-122">Description</span><span class="sxs-lookup"><span data-stu-id="f5834-122">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="f5834-123">Définit les paramètres de sécurité pour le transport d'intégration Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="f5834-123">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="f5834-124">Cet élément est de type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f5834-124">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5834-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f5834-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f5834-126">Élément</span><span class="sxs-lookup"><span data-stu-id="f5834-126">Element</span></span>|<span data-ttu-id="f5834-127">Description</span><span class="sxs-lookup"><span data-stu-id="f5834-127">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f5834-128">Élément de liaison de [\<msmqIntegrationBinding>](msmqintegrationbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f5834-128">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5834-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5834-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="f5834-130">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="f5834-130">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f5834-131">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="f5834-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f5834-132">Liaisons</span><span class="sxs-lookup"><span data-stu-id="f5834-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f5834-133">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="f5834-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f5834-134">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="f5834-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
