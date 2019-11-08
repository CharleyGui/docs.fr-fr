---
title: <security> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 7877fd59aff581eee5b62a1ca224dbf51c956069
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738669"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="ce6fc-102">\<> de sécurité de \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="ce6fc-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="ce6fc-103">Définit les paramètres de sécurité pour une liaison MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="ce6fc-104">Elle spécifie si le transport ou la sécurité SOAP sont activés et, si c'est le cas, le mode d'authentification et les niveaux de protection utilisés.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
<span data-ttu-id="ce6fc-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce6fc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ce6fc-106">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ce6fc-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ce6fc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="ce6fc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="ce6fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**NetMsmqBinding**](netmsmqbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="ce6fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="ce6fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="ce6fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="ce6fc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="ce6fc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce6fc-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce6fc-111">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce6fc-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ce6fc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ce6fc-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce6fc-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="ce6fc-114">Attributes</span></span>  
  
|<span data-ttu-id="ce6fc-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="ce6fc-115">Attribute</span></span>|<span data-ttu-id="ce6fc-116">Description</span><span class="sxs-lookup"><span data-stu-id="ce6fc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce6fc-117">mode</span><span class="sxs-lookup"><span data-stu-id="ce6fc-117">mode</span></span>|<span data-ttu-id="ce6fc-118">Spécifie le type de sécurité qui contrôle l'intégrité, la confidentialité et l'authentification.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-118">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="ce6fc-119">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce6fc-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ce6fc-120">-None : cela désactive la sécurité.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-120">-   None: This disables security.</span></span><br /><span data-ttu-id="ce6fc-121">-Transport : la protection et l’authentification sont proposées par le transport.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-121">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="ce6fc-122">Cela s'applique à la sécurité des message entre les deux gestionnaires de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-122">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="ce6fc-123">Il n'y a aucune sécurité offerte entre l'application et gestionnaire de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-123">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="ce6fc-124">Les applications Msmq existantes sont équivalentes au niveau des fonctionnalités avec ce type de mode de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-124">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="ce6fc-125">-Message : spécifie la sécurité de l’application de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-125">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="ce6fc-126">Il n'y a aucune sécurité offerte à la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-126">There is no security offered at the transport layer.</span></span> <span data-ttu-id="ce6fc-127">Cette valeur est semblable à la sécurité offerte par d’autres liaisons standard.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-127">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="ce6fc-128">-Both : offre la sécurité au niveau du transport et de la couche de messagerie SOAP.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-128">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="ce6fc-129">La même information d'identification est requise pour les deux niveaux.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-129">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="ce6fc-130">La valeur par défaut est Transport.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-130">The default value is Transport.</span></span> <span data-ttu-id="ce6fc-131">Cet attribut est de type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-131">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce6fc-132">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ce6fc-132">Child Elements</span></span>  
  
|<span data-ttu-id="ce6fc-133">Élément</span><span class="sxs-lookup"><span data-stu-id="ce6fc-133">Element</span></span>|<span data-ttu-id="ce6fc-134">Description</span><span class="sxs-lookup"><span data-stu-id="ce6fc-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce6fc-135">message de \<</span><span class="sxs-lookup"><span data-stu-id="ce6fc-135">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="ce6fc-136">Définit le les paramètres de sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-136">Defines the SOAP message security settings.</span></span> <span data-ttu-id="ce6fc-137">Cet élément est de type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-137">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="ce6fc-138">> de transport \<</span><span class="sxs-lookup"><span data-stu-id="ce6fc-138">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="ce6fc-139">Définit les paramètres de sécurité pour le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-139">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="ce6fc-140">Cet élément est de type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ce6fc-140">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce6fc-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ce6fc-141">Parent Elements</span></span>  
  
|<span data-ttu-id="ce6fc-142">Élément</span><span class="sxs-lookup"><span data-stu-id="ce6fc-142">Element</span></span>|<span data-ttu-id="ce6fc-143">Description</span><span class="sxs-lookup"><span data-stu-id="ce6fc-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce6fc-144">liaison</span><span class="sxs-lookup"><span data-stu-id="ce6fc-144">binding</span></span>|<span data-ttu-id="ce6fc-145">Élément de liaison de l' [\<netMsmqBinding >](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ce6fc-145">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce6fc-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce6fc-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="ce6fc-147">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ce6fc-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ce6fc-148">Liaisons</span><span class="sxs-lookup"><span data-stu-id="ce6fc-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ce6fc-149">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="ce6fc-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ce6fc-150">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ce6fc-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ce6fc-151">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="ce6fc-151">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="ce6fc-152">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="ce6fc-152">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
