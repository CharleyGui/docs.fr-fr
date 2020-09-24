---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: c90024a0629f39d160967ca00434e48f682d8933
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157315"
---
# \<issuedTokenParameters>

<span data-ttu-id="9ae7e-101">Indique les paramètres d'un jeton de sécurité émis dans un scénario de sécurité fédéré.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-101">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="9ae7e-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ae7e-102">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="9ae7e-103">Type</span><span class="sxs-lookup"><span data-stu-id="9ae7e-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ae7e-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9ae7e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9ae7e-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ae7e-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="9ae7e-106">Attributes</span></span>  
  
|<span data-ttu-id="9ae7e-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="9ae7e-107">Attribute</span></span>|<span data-ttu-id="9ae7e-108">Description</span><span class="sxs-lookup"><span data-stu-id="9ae7e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ae7e-109">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="9ae7e-109">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="9ae7e-110">Spécifie les versions des caractéristiques de sécurité (WS-Security, WS-Trust, WS-Secure Conversation et WS-Security Policy) devant être prises en charge par la liaison.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-110">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="9ae7e-111">Cette valeur est de type <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-111">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="9ae7e-112">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="9ae7e-112">inclusionMode</span></span>|<span data-ttu-id="9ae7e-113">Indique les spécifications d'inclusion de jeton.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-113">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="9ae7e-114">Cet attribut est de type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-114">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="9ae7e-115">keySize</span><span class="sxs-lookup"><span data-stu-id="9ae7e-115">keySize</span></span>|<span data-ttu-id="9ae7e-116">Entier qui spécifie la taille de clé de jeton.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-116">An integer that specifies the token key size.</span></span> <span data-ttu-id="9ae7e-117">La valeur par défaut est 256.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-117">The default value is 256.</span></span>|  
|<span data-ttu-id="9ae7e-118">keyType</span><span class="sxs-lookup"><span data-stu-id="9ae7e-118">keyType</span></span>|<span data-ttu-id="9ae7e-119">Valeur correcte de <xref:System.IdentityModel.Tokens.SecurityKeyType> indiquant le type de clé.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-119">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="9ae7e-120">Par défaut, il s’agit de `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-120">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="9ae7e-121">tokenType</span><span class="sxs-lookup"><span data-stu-id="9ae7e-121">tokenType</span></span>|<span data-ttu-id="9ae7e-122">Chaîne indiquant le type de jeton.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-122">A string that specifies the token type.</span></span> <span data-ttu-id="9ae7e-123">La valeur par défaut est « http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML »</span><span class="sxs-lookup"><span data-stu-id="9ae7e-123">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ae7e-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9ae7e-124">Child Elements</span></span>  
  
|<span data-ttu-id="9ae7e-125">Élément</span><span class="sxs-lookup"><span data-stu-id="9ae7e-125">Element</span></span>|<span data-ttu-id="9ae7e-126">Description</span><span class="sxs-lookup"><span data-stu-id="9ae7e-126">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="9ae7e-127">Collection d'éléments de configuration indiquant des paramètres de demande supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-127">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="9ae7e-128">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-128">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="9ae7e-129">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9ae7e-130">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9ae7e-131">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="9ae7e-132">Élément de configuration qui spécifie le point de terminaison émettant le jeton actuel.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-132">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="9ae7e-133">Élément de configuration qui spécifie l'adresse de point de terminaison correspondant aux métadonnées de l'émetteur de jeton.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-133">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ae7e-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9ae7e-134">Parent Elements</span></span>  
  
|<span data-ttu-id="9ae7e-135">Élément</span><span class="sxs-lookup"><span data-stu-id="9ae7e-135">Element</span></span>|<span data-ttu-id="9ae7e-136">Description</span><span class="sxs-lookup"><span data-stu-id="9ae7e-136">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="9ae7e-137">Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-137">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="9ae7e-138">Spécifie les options de sécurité d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="9ae7e-138">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ae7e-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ae7e-139">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9ae7e-140">Liaisons</span><span class="sxs-lookup"><span data-stu-id="9ae7e-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9ae7e-141">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="9ae7e-141">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9ae7e-142">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="9ae7e-142">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="9ae7e-143">Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9ae7e-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="9ae7e-144">Custom Binding Security</span><span class="sxs-lookup"><span data-stu-id="9ae7e-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="9ae7e-145">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="9ae7e-145">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="9ae7e-146">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="9ae7e-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9ae7e-147">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="9ae7e-147">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="9ae7e-148">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="9ae7e-148">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
