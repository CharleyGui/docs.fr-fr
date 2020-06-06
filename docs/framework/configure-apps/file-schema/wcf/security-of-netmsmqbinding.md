---
title: <security> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 7877fd59aff581eee5b62a1ca224dbf51c956069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738669"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="dc7f4-102">\<security> de \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="dc7f4-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="dc7f4-103">Définit les paramètres de sécurité pour une liaison MSMQ.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="dc7f4-104">Elle spécifie si le transport ou la sécurité SOAP sont activés et, si c'est le cas, le mode d'authentification et les niveaux de protection utilisés.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="dc7f4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc7f4-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc7f4-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dc7f4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="dc7f4-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc7f4-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="dc7f4-108">Attributes</span></span>  
  
|<span data-ttu-id="dc7f4-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="dc7f4-109">Attribute</span></span>|<span data-ttu-id="dc7f4-110">Description</span><span class="sxs-lookup"><span data-stu-id="dc7f4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc7f4-111">mode</span><span class="sxs-lookup"><span data-stu-id="dc7f4-111">mode</span></span>|<span data-ttu-id="dc7f4-112">Spécifie le type de sécurité qui contrôle l'intégrité, la confidentialité et l'authentification.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-112">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="dc7f4-113">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="dc7f4-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dc7f4-114">-None : cela désactive la sécurité.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-114">-   None: This disables security.</span></span><br /><span data-ttu-id="dc7f4-115">-Transport : la protection et l’authentification sont proposées par le transport.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="dc7f4-116">Cela s'applique à la sécurité des message entre les deux gestionnaires de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="dc7f4-117">Il n'y a aucune sécurité offerte entre l'application et gestionnaire de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="dc7f4-118">Les applications Msmq existantes sont équivalentes au niveau des fonctionnalités avec ce type de mode de sécurité.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="dc7f4-119">-Message : spécifie la sécurité de l’application de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-119">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="dc7f4-120">Il n'y a aucune sécurité offerte à la couche de transport.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-120">There is no security offered at the transport layer.</span></span> <span data-ttu-id="dc7f4-121">Cette valeur est semblable à la sécurité offerte par d’autres liaisons standard.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-121">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="dc7f4-122">-Both : offre la sécurité au niveau du transport et de la couche de messagerie SOAP.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-122">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="dc7f4-123">La même information d'identification est requise pour les deux niveaux.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-123">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="dc7f4-124">La valeur par défaut est Transport.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-124">The default value is Transport.</span></span> <span data-ttu-id="dc7f4-125">Cet attribut est de type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-125">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc7f4-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dc7f4-126">Child Elements</span></span>  
  
|<span data-ttu-id="dc7f4-127">Élément</span><span class="sxs-lookup"><span data-stu-id="dc7f4-127">Element</span></span>|<span data-ttu-id="dc7f4-128">Description</span><span class="sxs-lookup"><span data-stu-id="dc7f4-128">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="dc7f4-129">Définit le les paramètres de sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-129">Defines the SOAP message security settings.</span></span> <span data-ttu-id="dc7f4-130">Cet élément est de type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-130">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="dc7f4-131">Définit les paramètres de sécurité pour le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-131">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="dc7f4-132">Cet élément est de type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="dc7f4-132">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc7f4-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dc7f4-133">Parent Elements</span></span>  
  
|<span data-ttu-id="dc7f4-134">Élément</span><span class="sxs-lookup"><span data-stu-id="dc7f4-134">Element</span></span>|<span data-ttu-id="dc7f4-135">Description</span><span class="sxs-lookup"><span data-stu-id="dc7f4-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc7f4-136">binding</span><span class="sxs-lookup"><span data-stu-id="dc7f4-136">binding</span></span>|<span data-ttu-id="dc7f4-137">Élément de liaison de l’élément[\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dc7f4-137">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc7f4-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc7f4-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="dc7f4-139">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="dc7f4-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dc7f4-140">Liaisons</span><span class="sxs-lookup"><span data-stu-id="dc7f4-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dc7f4-141">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="dc7f4-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dc7f4-142">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="dc7f4-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="dc7f4-143">Files d'attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="dc7f4-143">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
