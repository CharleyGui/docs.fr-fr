---
title: <security> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1bbc3a460ce707e71b72a469af2e03acd8dc79e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936685"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="93fa9-102">\<> de sécurité \<de NetMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="93fa9-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="93fa9-103">Définit les paramètres de sécurité pour une liaison MSMQ.</span><span class="sxs-lookup"><span data-stu-id="93fa9-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="93fa9-104">Elle spécifie si le transport ou la sécurité SOAP sont activés et, si c'est le cas, le mode d'authentification et les niveaux de protection utilisés.</span><span class="sxs-lookup"><span data-stu-id="93fa9-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="93fa9-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="93fa9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="93fa9-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="93fa9-106">\<bindings></span></span>  
<span data-ttu-id="93fa9-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="93fa9-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="93fa9-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="93fa9-108">\<binding></span></span>  
<span data-ttu-id="93fa9-109">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="93fa9-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93fa9-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93fa9-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93fa9-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="93fa9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="93fa9-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="93fa9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93fa9-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="93fa9-113">Attributes</span></span>  
  
|<span data-ttu-id="93fa9-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="93fa9-114">Attribute</span></span>|<span data-ttu-id="93fa9-115">Description</span><span class="sxs-lookup"><span data-stu-id="93fa9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93fa9-116">mode</span><span class="sxs-lookup"><span data-stu-id="93fa9-116">mode</span></span>|<span data-ttu-id="93fa9-117">Spécifie le type de sécurité qui contrôle l'intégrité, la confidentialité et l'authentification.</span><span class="sxs-lookup"><span data-stu-id="93fa9-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="93fa9-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="93fa9-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="93fa9-119">None Cela désactive la sécurité.</span><span class="sxs-lookup"><span data-stu-id="93fa9-119">-   None: This disables security.</span></span><br /><span data-ttu-id="93fa9-120">Transport La protection et l’authentification sont proposées par le transport.</span><span class="sxs-lookup"><span data-stu-id="93fa9-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="93fa9-121">Cela s'applique à la sécurité des message entre les deux gestionnaires de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="93fa9-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="93fa9-122">Il n'y a aucune sécurité offerte entre l'application et gestionnaire de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="93fa9-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="93fa9-123">Les applications Msmq existantes sont équivalentes au niveau des fonctionnalités avec ce type de mode de sécurité.</span><span class="sxs-lookup"><span data-stu-id="93fa9-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="93fa9-124">Attente Spécifie la sécurité de l’application de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="93fa9-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="93fa9-125">Il n'y a aucune sécurité offerte à la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="93fa9-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="93fa9-126">Cette valeur est semblable à la sécurité offerte par d’autres liaisons standard.</span><span class="sxs-lookup"><span data-stu-id="93fa9-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="93fa9-127">Versions Offre la sécurité au niveau du transport et de la couche de messagerie SOAP.</span><span class="sxs-lookup"><span data-stu-id="93fa9-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="93fa9-128">La même information d'identification est requise pour les deux niveaux.</span><span class="sxs-lookup"><span data-stu-id="93fa9-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="93fa9-129">La valeur par défaut est Transport.</span><span class="sxs-lookup"><span data-stu-id="93fa9-129">The default value is Transport.</span></span> <span data-ttu-id="93fa9-130">Cet attribut est de type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="93fa9-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93fa9-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="93fa9-131">Child Elements</span></span>  
  
|<span data-ttu-id="93fa9-132">Élément</span><span class="sxs-lookup"><span data-stu-id="93fa9-132">Element</span></span>|<span data-ttu-id="93fa9-133">Description</span><span class="sxs-lookup"><span data-stu-id="93fa9-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93fa9-134">\<message></span><span class="sxs-lookup"><span data-stu-id="93fa9-134">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="93fa9-135">Définit le les paramètres de sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="93fa9-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="93fa9-136">Cet élément est de type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="93fa9-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="93fa9-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="93fa9-137">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="93fa9-138">Définit les paramètres de sécurité pour le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="93fa9-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="93fa9-139">Cet élément est de type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="93fa9-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93fa9-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="93fa9-140">Parent Elements</span></span>  
  
|<span data-ttu-id="93fa9-141">Élément</span><span class="sxs-lookup"><span data-stu-id="93fa9-141">Element</span></span>|<span data-ttu-id="93fa9-142">Description</span><span class="sxs-lookup"><span data-stu-id="93fa9-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93fa9-143">liaison</span><span class="sxs-lookup"><span data-stu-id="93fa9-143">binding</span></span>|<span data-ttu-id="93fa9-144">Élément de liaison de l' [ \<> NetMsmqBinding](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="93fa9-144">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93fa9-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93fa9-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="93fa9-146">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="93fa9-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="93fa9-147">Liaisons</span><span class="sxs-lookup"><span data-stu-id="93fa9-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="93fa9-148">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="93fa9-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="93fa9-149">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="93fa9-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="93fa9-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="93fa9-150">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="93fa9-151">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="93fa9-151">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
