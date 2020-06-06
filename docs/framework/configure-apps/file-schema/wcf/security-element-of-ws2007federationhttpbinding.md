---
title: <security>élément de<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738726"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="ad1af-102">\<security>élément de\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ad1af-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="ad1af-103">Définit les paramètres de sécurité de l' [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="ad1af-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="ad1af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad1af-104">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad1af-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ad1af-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ad1af-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ad1af-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad1af-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="ad1af-107">Attributes</span></span>  
  
|<span data-ttu-id="ad1af-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="ad1af-108">Attribute</span></span>|<span data-ttu-id="ad1af-109">Description</span><span class="sxs-lookup"><span data-stu-id="ad1af-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="ad1af-110">facultatif.</span><span class="sxs-lookup"><span data-stu-id="ad1af-110">Optional.</span></span> <span data-ttu-id="ad1af-111">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="ad1af-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="ad1af-112">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="ad1af-112">The default value is `Message`.</span></span> <span data-ttu-id="ad1af-113">Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ad1af-113">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ad1af-114">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="ad1af-114">mode Attribute</span></span>  
  
|<span data-ttu-id="ad1af-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="ad1af-115">Value</span></span>|<span data-ttu-id="ad1af-116">Description</span><span class="sxs-lookup"><span data-stu-id="ad1af-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ad1af-117">None</span><span class="sxs-lookup"><span data-stu-id="ad1af-117">None</span></span>|<span data-ttu-id="ad1af-118">Le message SOAP n'est pas sécurisé pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="ad1af-118">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="ad1af-119">Message</span><span class="sxs-lookup"><span data-stu-id="ad1af-119">Message</span></span>|<span data-ttu-id="ad1af-120">L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="ad1af-120">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="ad1af-121">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="ad1af-121">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="ad1af-122">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="ad1af-122">The service must be configured with a certificate.</span></span> <span data-ttu-id="ad1af-123">L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ad1af-123">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="ad1af-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="ad1af-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="ad1af-125">L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ad1af-125">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="ad1af-126">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="ad1af-126">The service must be configured with a certificate.</span></span> <span data-ttu-id="ad1af-127">L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ad1af-127">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad1af-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ad1af-128">Child Elements</span></span>  
  
|<span data-ttu-id="ad1af-129">Élément</span><span class="sxs-lookup"><span data-stu-id="ad1af-129">Element</span></span>|<span data-ttu-id="ad1af-130">Description</span><span class="sxs-lookup"><span data-stu-id="ad1af-130">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="ad1af-131">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="ad1af-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="ad1af-132">Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="ad1af-132">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad1af-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ad1af-133">Parent Elements</span></span>  
  
|<span data-ttu-id="ad1af-134">Élément</span><span class="sxs-lookup"><span data-stu-id="ad1af-134">Element</span></span>|<span data-ttu-id="ad1af-135">Description</span><span class="sxs-lookup"><span data-stu-id="ad1af-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="ad1af-136">Définit toutes les fonctions de liaison de [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ad1af-136">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad1af-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad1af-137">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="ad1af-138">Guide pratique pour créer une liaison WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ad1af-138">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="ad1af-139">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="ad1af-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ad1af-140">Sélection d'un type d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="ad1af-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="ad1af-141">Liaisons</span><span class="sxs-lookup"><span data-stu-id="ad1af-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ad1af-142">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="ad1af-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ad1af-143">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="ad1af-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
