---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 0ab7fbd64cc92e940617f5334eeb16fcb3a50c4a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181230"
---
# \<xmlElement>

<span data-ttu-id="11b3a-101">Spécifie un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="11b3a-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="11b3a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11b3a-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11b3a-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="11b3a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="11b3a-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="11b3a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11b3a-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="11b3a-105">Attributes</span></span>  
  
|<span data-ttu-id="11b3a-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="11b3a-106">Attribute</span></span>|<span data-ttu-id="11b3a-107">Description</span><span class="sxs-lookup"><span data-stu-id="11b3a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11b3a-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="11b3a-108">xmlElement</span></span>|<span data-ttu-id="11b3a-109">Chaîne spécifiant un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="11b3a-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11b3a-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="11b3a-110">Child Elements</span></span>  

 <span data-ttu-id="11b3a-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="11b3a-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11b3a-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="11b3a-112">Parent Elements</span></span>  
  
|<span data-ttu-id="11b3a-113">Élément</span><span class="sxs-lookup"><span data-stu-id="11b3a-113">Element</span></span>|<span data-ttu-id="11b3a-114">Description</span><span class="sxs-lookup"><span data-stu-id="11b3a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="11b3a-115">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="11b3a-115">A collection of token request parameters.</span></span> <span data-ttu-id="11b3a-116">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="11b3a-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11b3a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11b3a-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="11b3a-118">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="11b3a-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="11b3a-119">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="11b3a-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="11b3a-120">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="11b3a-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="11b3a-121">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="11b3a-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="11b3a-122">Liaisons</span><span class="sxs-lookup"><span data-stu-id="11b3a-122">Bindings</span></span>](../../../wcf/bindings.md)
