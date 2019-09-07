---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398996"
---
# <a name="xmlelement"></a><span data-ttu-id="c6a17-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="c6a17-101">\<xmlElement></span></span>
<span data-ttu-id="c6a17-102">Spécifie un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="c6a17-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
<span data-ttu-id="c6a17-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6a17-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c6a17-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c6a17-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c6a17-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c6a17-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c6a17-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c6a17-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="c6a17-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="c6a17-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c6a17-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c6a17-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="c6a17-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de messages**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c6a17-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="c6a17-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tokenRequestParameters >** ](tokenrequestparameters.md)</span><span class="sxs-lookup"><span data-stu-id="c6a17-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)</span></span>\
<span data-ttu-id="c6a17-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> xmlElement**</span><span class="sxs-lookup"><span data-stu-id="c6a17-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6a17-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6a17-112">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6a17-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c6a17-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c6a17-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c6a17-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6a17-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="c6a17-115">Attributes</span></span>  
  
|<span data-ttu-id="c6a17-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="c6a17-116">Attribute</span></span>|<span data-ttu-id="c6a17-117">Description</span><span class="sxs-lookup"><span data-stu-id="c6a17-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6a17-118">xmlElement</span><span class="sxs-lookup"><span data-stu-id="c6a17-118">xmlElement</span></span>|<span data-ttu-id="c6a17-119">Chaîne spécifiant un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="c6a17-119">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6a17-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c6a17-120">Child Elements</span></span>  
 <span data-ttu-id="c6a17-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c6a17-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6a17-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c6a17-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c6a17-123">Élément</span><span class="sxs-lookup"><span data-stu-id="c6a17-123">Element</span></span>|<span data-ttu-id="c6a17-124">Description</span><span class="sxs-lookup"><span data-stu-id="c6a17-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6a17-125">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="c6a17-125">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="c6a17-126">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="c6a17-126">A collection of token request parameters.</span></span> <span data-ttu-id="c6a17-127">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="c6a17-127">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6a17-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6a17-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="c6a17-129">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="c6a17-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c6a17-130">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="c6a17-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c6a17-131">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="c6a17-131">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c6a17-132">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="c6a17-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c6a17-133">Liaisons</span><span class="sxs-lookup"><span data-stu-id="c6a17-133">Bindings</span></span>](../../../wcf/bindings.md)
