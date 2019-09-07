---
title: <issuerMetadata> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400339"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="906a7-102">\<issuerMetadata > de \<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="906a7-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

<span data-ttu-id="906a7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="906a7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="906a7-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="906a7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="906a7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="906a7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="906a7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="906a7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="906a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="906a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="906a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="906a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)</span></span>\
<span data-ttu-id="906a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenParameters >** ](issuedtokenparameters.md)</span><span class="sxs-lookup"><span data-stu-id="906a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)</span></span>\
<span data-ttu-id="906a7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="906a7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906a7-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="906a7-111">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="906a7-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="906a7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="906a7-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="906a7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="906a7-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="906a7-114">Attributes</span></span>  
  
|<span data-ttu-id="906a7-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="906a7-115">Attribute</span></span>|<span data-ttu-id="906a7-116">Description</span><span class="sxs-lookup"><span data-stu-id="906a7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="906a7-117">adresse</span><span class="sxs-lookup"><span data-stu-id="906a7-117">address</span></span>|<span data-ttu-id="906a7-118">Requis.</span><span class="sxs-lookup"><span data-stu-id="906a7-118">Required.</span></span> <span data-ttu-id="906a7-119">Chaîne qui spécifie l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="906a7-119">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="906a7-120">L'adresse doit être un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="906a7-120">The address must be an absolute URI.</span></span> <span data-ttu-id="906a7-121">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="906a7-121">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="906a7-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="906a7-122">Child Elements</span></span>  
  
|<span data-ttu-id="906a7-123">Élément</span><span class="sxs-lookup"><span data-stu-id="906a7-123">Element</span></span>|<span data-ttu-id="906a7-124">Description</span><span class="sxs-lookup"><span data-stu-id="906a7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="906a7-125">\<headers></span><span class="sxs-lookup"><span data-stu-id="906a7-125">\<headers></span></span>](headers-element.md)|<span data-ttu-id="906a7-126">Collection d'en-têtes d'adresses.</span><span class="sxs-lookup"><span data-stu-id="906a7-126">A collection of address headers.</span></span>|  
|[<span data-ttu-id="906a7-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="906a7-127">\<identity></span></span>](identity.md)|<span data-ttu-id="906a7-128">Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="906a7-128">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="906a7-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="906a7-129">Parent Elements</span></span>  
  
|<span data-ttu-id="906a7-130">Élément</span><span class="sxs-lookup"><span data-stu-id="906a7-130">Element</span></span>|<span data-ttu-id="906a7-131">Description</span><span class="sxs-lookup"><span data-stu-id="906a7-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="906a7-132">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="906a7-132">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="906a7-133">Indique les paramètres d'un jeton de sécurité émis dans un scénario de sécurité fédéré.</span><span class="sxs-lookup"><span data-stu-id="906a7-133">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="906a7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="906a7-134">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="906a7-135">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="906a7-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="906a7-136">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="906a7-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="906a7-137">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="906a7-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="906a7-138">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="906a7-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="906a7-139">Liaisons</span><span class="sxs-lookup"><span data-stu-id="906a7-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="906a7-140">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="906a7-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="906a7-141">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="906a7-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="906a7-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="906a7-142">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="906a7-143">Guide pratique pour Créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="906a7-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="906a7-144">Sécurité de liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="906a7-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
