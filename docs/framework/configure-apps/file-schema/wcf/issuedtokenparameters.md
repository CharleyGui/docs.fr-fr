---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 8432463ff62e4b5e54a491b574cc6a5285efe220
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397950"
---
# <a name="issuedtokenparameters"></a><span data-ttu-id="23dd9-101">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="23dd9-101">\<issuedTokenParameters></span></span>
<span data-ttu-id="23dd9-102">Indique les paramètres d'un jeton de sécurité émis dans un scénario de sécurité fédéré.</span><span class="sxs-lookup"><span data-stu-id="23dd9-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
<span data-ttu-id="23dd9-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="23dd9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="23dd9-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="23dd9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="23dd9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="23dd9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="23dd9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="23dd9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="23dd9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="23dd9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="23dd9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="23dd9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="23dd9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedTokenParameters >**</span><span class="sxs-lookup"><span data-stu-id="23dd9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23dd9-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23dd9-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="23dd9-111">Type</span><span class="sxs-lookup"><span data-stu-id="23dd9-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23dd9-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="23dd9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="23dd9-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="23dd9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23dd9-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="23dd9-114">Attributes</span></span>  
  
|<span data-ttu-id="23dd9-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="23dd9-115">Attribute</span></span>|<span data-ttu-id="23dd9-116">Description</span><span class="sxs-lookup"><span data-stu-id="23dd9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23dd9-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="23dd9-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="23dd9-118">Spécifie les versions des caractéristiques de sécurité (WS-Security, WS-Trust, WS-Secure Conversation et WS-Security Policy) devant être prises en charge par la liaison.</span><span class="sxs-lookup"><span data-stu-id="23dd9-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="23dd9-119">Cette valeur est de type <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="23dd9-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="23dd9-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="23dd9-120">inclusionMode</span></span>|<span data-ttu-id="23dd9-121">Indique les spécifications d'inclusion de jeton.</span><span class="sxs-lookup"><span data-stu-id="23dd9-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="23dd9-122">Cet attribut est de type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="23dd9-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="23dd9-123">keySize</span><span class="sxs-lookup"><span data-stu-id="23dd9-123">keySize</span></span>|<span data-ttu-id="23dd9-124">Entier qui spécifie la taille de clé de jeton.</span><span class="sxs-lookup"><span data-stu-id="23dd9-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="23dd9-125">La valeur par défaut est 256.</span><span class="sxs-lookup"><span data-stu-id="23dd9-125">The default value is 256.</span></span>|  
|<span data-ttu-id="23dd9-126">keyType</span><span class="sxs-lookup"><span data-stu-id="23dd9-126">keyType</span></span>|<span data-ttu-id="23dd9-127">Valeur correcte de <xref:System.IdentityModel.Tokens.SecurityKeyType> indiquant le type de clé.</span><span class="sxs-lookup"><span data-stu-id="23dd9-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="23dd9-128">Par défaut, il s’agit de `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="23dd9-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="23dd9-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="23dd9-129">tokenType</span></span>|<span data-ttu-id="23dd9-130">Chaîne indiquant le type de jeton.</span><span class="sxs-lookup"><span data-stu-id="23dd9-130">A string that specifies the token type.</span></span> <span data-ttu-id="23dd9-131">La valeur par défaut est « http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML  »</span><span class="sxs-lookup"><span data-stu-id="23dd9-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23dd9-132">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="23dd9-132">Child Elements</span></span>  
  
|<span data-ttu-id="23dd9-133">Élément</span><span class="sxs-lookup"><span data-stu-id="23dd9-133">Element</span></span>|<span data-ttu-id="23dd9-134">Description</span><span class="sxs-lookup"><span data-stu-id="23dd9-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23dd9-135">\<additionalRequestParameters></span><span class="sxs-lookup"><span data-stu-id="23dd9-135">\<additionalRequestParameters></span></span>](additionalrequestparameters-element.md)|<span data-ttu-id="23dd9-136">Collection d'éléments de configuration indiquant des paramètres de demande supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="23dd9-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="23dd9-137">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="23dd9-137">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="23dd9-138">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="23dd9-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="23dd9-139">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="23dd9-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="23dd9-140">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="23dd9-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="23dd9-141">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="23dd9-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="23dd9-142">\<issuer></span><span class="sxs-lookup"><span data-stu-id="23dd9-142">\<issuer></span></span>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="23dd9-143">Élément de configuration qui spécifie le point de terminaison émettant le jeton actuel.</span><span class="sxs-lookup"><span data-stu-id="23dd9-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="23dd9-144">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="23dd9-144">\<issuerMetadata></span></span>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="23dd9-145">Élément de configuration qui spécifie l'adresse de point de terminaison correspondant aux métadonnées de l'émetteur de jeton.</span><span class="sxs-lookup"><span data-stu-id="23dd9-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23dd9-146">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="23dd9-146">Parent Elements</span></span>  
  
|<span data-ttu-id="23dd9-147">Élément</span><span class="sxs-lookup"><span data-stu-id="23dd9-147">Element</span></span>|<span data-ttu-id="23dd9-148">Description</span><span class="sxs-lookup"><span data-stu-id="23dd9-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23dd9-149">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="23dd9-149">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="23dd9-150">Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.</span><span class="sxs-lookup"><span data-stu-id="23dd9-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="23dd9-151">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="23dd9-151">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="23dd9-152">Spécifie les options de sécurité d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="23dd9-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23dd9-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23dd9-153">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="23dd9-154">Liaisons</span><span class="sxs-lookup"><span data-stu-id="23dd9-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="23dd9-155">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="23dd9-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="23dd9-156">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="23dd9-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="23dd9-157">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="23dd9-157">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="23dd9-158">Guide pratique pour Créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="23dd9-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="23dd9-159">Sécurité de liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="23dd9-159">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="23dd9-160">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="23dd9-160">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="23dd9-161">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="23dd9-161">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="23dd9-162">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="23dd9-162">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="23dd9-163">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="23dd9-163">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
