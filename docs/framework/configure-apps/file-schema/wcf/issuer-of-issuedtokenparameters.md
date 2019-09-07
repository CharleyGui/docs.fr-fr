---
title: <issuer> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397941"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="67f65-102">\<> de l’émetteur \<de la > issuedTokenParameters</span><span class="sxs-lookup"><span data-stu-id="67f65-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="67f65-103">Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="67f65-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="67f65-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="67f65-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="67f65-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="67f65-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="67f65-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="67f65-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="67f65-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="67f65-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="67f65-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="67f65-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="67f65-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="67f65-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="67f65-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="67f65-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="67f65-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<émetteur >**</span><span class="sxs-lookup"><span data-stu-id="67f65-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67f65-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67f65-112">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67f65-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="67f65-113">Attributes and Elements</span></span>  
 <span data-ttu-id="67f65-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="67f65-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67f65-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="67f65-115">Attributes</span></span>  
  
|<span data-ttu-id="67f65-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="67f65-116">Attribute</span></span>|<span data-ttu-id="67f65-117">Description</span><span class="sxs-lookup"><span data-stu-id="67f65-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67f65-118">adresse</span><span class="sxs-lookup"><span data-stu-id="67f65-118">address</span></span>|<span data-ttu-id="67f65-119">Chaîne requise.</span><span class="sxs-lookup"><span data-stu-id="67f65-119">Required string.</span></span> <span data-ttu-id="67f65-120">URL du service STS.</span><span class="sxs-lookup"><span data-stu-id="67f65-120">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67f65-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="67f65-121">Child Elements</span></span>  
  
|<span data-ttu-id="67f65-122">Élément</span><span class="sxs-lookup"><span data-stu-id="67f65-122">Element</span></span>|<span data-ttu-id="67f65-123">Description</span><span class="sxs-lookup"><span data-stu-id="67f65-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67f65-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="67f65-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="67f65-125">Collection d'en-têtes d'adresse de points de terminaison pouvant être créée par le générateur.</span><span class="sxs-lookup"><span data-stu-id="67f65-125">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="67f65-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="67f65-126">\<identity></span></span>](identity.md)|<span data-ttu-id="67f65-127">Lors de l'utilisation d'un jeton émis, spécifie des paramètres qui permettent au client d'authentifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="67f65-127">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67f65-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="67f65-128">Parent Elements</span></span>  
  
|<span data-ttu-id="67f65-129">Élément</span><span class="sxs-lookup"><span data-stu-id="67f65-129">Element</span></span>|<span data-ttu-id="67f65-130">Description</span><span class="sxs-lookup"><span data-stu-id="67f65-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67f65-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="67f65-131">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="67f65-132">Spécifie le jeton émis en cours.</span><span class="sxs-lookup"><span data-stu-id="67f65-132">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67f65-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67f65-133">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="67f65-134">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="67f65-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="67f65-135">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="67f65-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="67f65-136">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="67f65-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="67f65-137">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="67f65-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="67f65-138">Liaisons</span><span class="sxs-lookup"><span data-stu-id="67f65-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="67f65-139">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="67f65-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="67f65-140">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="67f65-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="67f65-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="67f65-141">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="67f65-142">Guide pratique pour Créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="67f65-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="67f65-143">Sécurité de liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="67f65-143">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
