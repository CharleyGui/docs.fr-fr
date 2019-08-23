---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: cc178dcc3684ab338282acc369e0ab5c789c15e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941437"
---
# <a name="xmlelement"></a><span data-ttu-id="a3643-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="a3643-101">\<xmlElement></span></span>
<span data-ttu-id="a3643-102">Spécifie un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="a3643-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="a3643-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a3643-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a3643-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a3643-104">\<bindings></span></span>  
<span data-ttu-id="a3643-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="a3643-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a3643-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="a3643-106">\<binding></span></span>  
<span data-ttu-id="a3643-107">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="a3643-107">\<security></span></span>  
<span data-ttu-id="a3643-108">\<message></span><span class="sxs-lookup"><span data-stu-id="a3643-108">\<message></span></span>  
<span data-ttu-id="a3643-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="a3643-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3643-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3643-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3643-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a3643-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a3643-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a3643-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3643-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a3643-113">Attributes</span></span>  
  
|<span data-ttu-id="a3643-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a3643-114">Attribute</span></span>|<span data-ttu-id="a3643-115">Description</span><span class="sxs-lookup"><span data-stu-id="a3643-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3643-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="a3643-116">xmlElement</span></span>|<span data-ttu-id="a3643-117">Chaîne spécifiant un élément XML qui est envoyé dans le corps du message au service d'émission de jeton de sécurité (STS) lors de la demande d'un jeton.</span><span class="sxs-lookup"><span data-stu-id="a3643-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3643-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a3643-118">Child Elements</span></span>  
 <span data-ttu-id="a3643-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a3643-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3643-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a3643-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a3643-121">Élément</span><span class="sxs-lookup"><span data-stu-id="a3643-121">Element</span></span>|<span data-ttu-id="a3643-122">Description</span><span class="sxs-lookup"><span data-stu-id="a3643-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3643-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="a3643-123">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="a3643-124">Collection de paramètres de demande de jeton.</span><span class="sxs-lookup"><span data-stu-id="a3643-124">A collection of token request parameters.</span></span> <span data-ttu-id="a3643-125">Chaque paramètre est un élément XML.</span><span class="sxs-lookup"><span data-stu-id="a3643-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3643-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3643-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="a3643-127">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="a3643-127">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a3643-128">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="a3643-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a3643-129">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a3643-129">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a3643-130">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="a3643-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a3643-131">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a3643-131">Bindings</span></span>](../../../wcf/bindings.md)
