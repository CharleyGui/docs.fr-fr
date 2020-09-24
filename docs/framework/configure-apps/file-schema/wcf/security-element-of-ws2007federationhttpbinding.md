---
title: <security> élément de <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 943ccc241aef15b58661699408b085d98cf86c3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183700"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="7cabc-102">\<security> élément de \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7cabc-102">\<security> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="7cabc-103">Définit les paramètres de sécurité de l' [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="7cabc-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="7cabc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cabc-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cabc-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7cabc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7cabc-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7cabc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cabc-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="7cabc-107">Attributes</span></span>  
  
|<span data-ttu-id="7cabc-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7cabc-108">Attribute</span></span>|<span data-ttu-id="7cabc-109">Description</span><span class="sxs-lookup"><span data-stu-id="7cabc-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="7cabc-110">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7cabc-110">Optional.</span></span> <span data-ttu-id="7cabc-111">Spécifie le type de sécurité appliqué.</span><span class="sxs-lookup"><span data-stu-id="7cabc-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="7cabc-112">La valeur par défaut est `Message`.</span><span class="sxs-lookup"><span data-stu-id="7cabc-112">The default value is `Message`.</span></span> <span data-ttu-id="7cabc-113">Cet attribut est de type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="7cabc-113">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="7cabc-114">Attribut Mode</span><span class="sxs-lookup"><span data-stu-id="7cabc-114">mode Attribute</span></span>  
  
|<span data-ttu-id="7cabc-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="7cabc-115">Value</span></span>|<span data-ttu-id="7cabc-116">Description</span><span class="sxs-lookup"><span data-stu-id="7cabc-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7cabc-117">None</span><span class="sxs-lookup"><span data-stu-id="7cabc-117">None</span></span>|<span data-ttu-id="7cabc-118">Le message SOAP n'est pas sécurisé pendant le transfert.</span><span class="sxs-lookup"><span data-stu-id="7cabc-118">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="7cabc-119">Message</span><span class="sxs-lookup"><span data-stu-id="7cabc-119">Message</span></span>|<span data-ttu-id="7cabc-120">L'intégrité, la confidentialité, l'authentification du serveur et l'authentification du client sont fournies à l'aide de la sécurité des messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="7cabc-120">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="7cabc-121">Par défaut, le corps est chiffré et signé.</span><span class="sxs-lookup"><span data-stu-id="7cabc-121">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="7cabc-122">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="7cabc-122">The service must be configured with a certificate.</span></span> <span data-ttu-id="7cabc-123">L'authentification du client est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7cabc-123">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="7cabc-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="7cabc-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="7cabc-125">L'intégrité, la confidentialité et l'authentification du serveur sont fournies par HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7cabc-125">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="7cabc-126">Le service doit être configuré à l'aide d'un certificat.</span><span class="sxs-lookup"><span data-stu-id="7cabc-126">The service must be configured with a certificate.</span></span> <span data-ttu-id="7cabc-127">L'authentification du client est fournie au moyen de la sécurité des messages SOAP et est basée sur le jeton émis au client par un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7cabc-127">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cabc-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7cabc-128">Child Elements</span></span>  
  
|<span data-ttu-id="7cabc-129">Élément</span><span class="sxs-lookup"><span data-stu-id="7cabc-129">Element</span></span>|<span data-ttu-id="7cabc-130">Description</span><span class="sxs-lookup"><span data-stu-id="7cabc-130">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="7cabc-131">Définit les paramètres de sécurité au niveau du message.</span><span class="sxs-lookup"><span data-stu-id="7cabc-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="7cabc-132">Cet élément est de type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="7cabc-132">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7cabc-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7cabc-133">Parent Elements</span></span>  
  
|<span data-ttu-id="7cabc-134">Élément</span><span class="sxs-lookup"><span data-stu-id="7cabc-134">Element</span></span>|<span data-ttu-id="7cabc-135">Description</span><span class="sxs-lookup"><span data-stu-id="7cabc-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="7cabc-136">Définit toutes les fonctions de liaison de [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="7cabc-136">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7cabc-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cabc-137">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="7cabc-138">Procédure : créer un WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7cabc-138">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="7cabc-139">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7cabc-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7cabc-140">Sélection d'un type d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="7cabc-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="7cabc-141">Liaisons</span><span class="sxs-lookup"><span data-stu-id="7cabc-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7cabc-142">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="7cabc-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7cabc-143">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="7cabc-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
