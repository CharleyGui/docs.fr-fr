---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398996"
---
# \<xmlElement>
<span data-ttu-id="e7cf6-101">Spécifie un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="e7cf6-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="e7cf6-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7cf6-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7cf6-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e7cf6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e7cf6-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e7cf6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7cf6-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="e7cf6-105">Attributes</span></span>  
  
|<span data-ttu-id="e7cf6-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="e7cf6-106">Attribute</span></span>|<span data-ttu-id="e7cf6-107">Description</span><span class="sxs-lookup"><span data-stu-id="e7cf6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7cf6-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="e7cf6-108">xmlElement</span></span>|<span data-ttu-id="e7cf6-109">Chaîne spécifiant un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="e7cf6-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7cf6-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7cf6-110">Child Elements</span></span>  
 <span data-ttu-id="e7cf6-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e7cf6-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7cf6-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7cf6-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e7cf6-113">Élément</span><span class="sxs-lookup"><span data-stu-id="e7cf6-113">Element</span></span>|<span data-ttu-id="e7cf6-114">Description</span><span class="sxs-lookup"><span data-stu-id="e7cf6-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="e7cf6-115">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="e7cf6-115">A collection of token request parameters.</span></span> <span data-ttu-id="e7cf6-116">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="e7cf6-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7cf6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7cf6-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="e7cf6-118">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="e7cf6-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e7cf6-119">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="e7cf6-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e7cf6-120">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="e7cf6-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="e7cf6-121">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="e7cf6-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e7cf6-122">Liaisons</span><span class="sxs-lookup"><span data-stu-id="e7cf6-122">Bindings</span></span>](../../../wcf/bindings.md)
