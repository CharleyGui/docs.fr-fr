---
title: <security> de <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: e4f10ab994429c6cbb690caef38114b8340e6839
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399863"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="f0a05-102">\<> de sécurité \<de MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="f0a05-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="f0a05-103">Définit les paramètres de sécurité de transport pour le canal d'intégration MSMQ (Message Queuing).</span><span class="sxs-lookup"><span data-stu-id="f0a05-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
<span data-ttu-id="f0a05-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0a05-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f0a05-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f0a05-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f0a05-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f0a05-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f0a05-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<msmqIntegrationBinding >** ](msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f0a05-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)</span></span>\
<span data-ttu-id="f0a05-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="f0a05-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f0a05-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de sécurité**</span><span class="sxs-lookup"><span data-stu-id="f0a05-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0a05-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0a05-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0a05-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f0a05-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f0a05-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f0a05-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0a05-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="f0a05-113">Attributes</span></span>  
  
|<span data-ttu-id="f0a05-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="f0a05-114">Attribute</span></span>|<span data-ttu-id="f0a05-115">Description</span><span class="sxs-lookup"><span data-stu-id="f0a05-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0a05-116">mode</span><span class="sxs-lookup"><span data-stu-id="f0a05-116">mode</span></span>|<span data-ttu-id="f0a05-117">Spécifie le type de sécurité qui contrôle l'intégrité, la confidentialité et l'authentification avec le canal d'intégration Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="f0a05-117">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="f0a05-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f0a05-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f0a05-119">None Cela désactive la sécurité.</span><span class="sxs-lookup"><span data-stu-id="f0a05-119">-   None: This disables security.</span></span><br /><span data-ttu-id="f0a05-120">Transport La protection et l’authentification sont proposées par le transport.</span><span class="sxs-lookup"><span data-stu-id="f0a05-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="f0a05-121">Cela s'applique à la sécurité des message entre les deux gestionnaires de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="f0a05-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="f0a05-122">Il n'y a aucune sécurité offerte entre l'application et gestionnaire de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="f0a05-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="f0a05-123">Les applications Msmq existantes sont équivalentes au niveau des fonctionnalités avec ce type de mode de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f0a05-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="f0a05-124">La valeur par défaut est `Transport`.</span><span class="sxs-lookup"><span data-stu-id="f0a05-124">The default value is `Transport`.</span></span> <span data-ttu-id="f0a05-125">Cet attribut est de type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f0a05-125">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0a05-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f0a05-126">Child Elements</span></span>  
  
|<span data-ttu-id="f0a05-127">Élément</span><span class="sxs-lookup"><span data-stu-id="f0a05-127">Element</span></span>|<span data-ttu-id="f0a05-128">Description</span><span class="sxs-lookup"><span data-stu-id="f0a05-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0a05-129">\<transport></span><span class="sxs-lookup"><span data-stu-id="f0a05-129">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="f0a05-130">Définit les paramètres de sécurité pour le transport d'intégration Message Queuing.</span><span class="sxs-lookup"><span data-stu-id="f0a05-130">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="f0a05-131">Cet élément est de type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f0a05-131">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0a05-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f0a05-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f0a05-133">Élément</span><span class="sxs-lookup"><span data-stu-id="f0a05-133">Element</span></span>|<span data-ttu-id="f0a05-134">Description</span><span class="sxs-lookup"><span data-stu-id="f0a05-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0a05-135">\<binding></span><span class="sxs-lookup"><span data-stu-id="f0a05-135">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="f0a05-136">Élément de liaison de l' [ \<> MsmqIntegrationBinding](msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f0a05-136">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0a05-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0a05-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="f0a05-138">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="f0a05-138">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f0a05-139">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="f0a05-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f0a05-140">Liaisons</span><span class="sxs-lookup"><span data-stu-id="f0a05-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f0a05-141">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="f0a05-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f0a05-142">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="f0a05-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f0a05-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="f0a05-143">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="f0a05-144">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="f0a05-144">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
