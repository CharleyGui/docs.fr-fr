---
title: <issuer> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bdd5ad45984fae7b39defe82c4af75845dfda1b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397941"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="908cb-102">\<issuer> de \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="908cb-102">\<issuer> of \<issuedTokenParameters></span></span>
<span data-ttu-id="908cb-103">Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="908cb-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="908cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="908cb-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="908cb-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="908cb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="908cb-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="908cb-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="908cb-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="908cb-107">Attributes</span></span>  
  
|<span data-ttu-id="908cb-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="908cb-108">Attribute</span></span>|<span data-ttu-id="908cb-109">Description</span><span class="sxs-lookup"><span data-stu-id="908cb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="908cb-110">address</span><span class="sxs-lookup"><span data-stu-id="908cb-110">address</span></span>|<span data-ttu-id="908cb-111">Chaîne obligatoire.</span><span class="sxs-lookup"><span data-stu-id="908cb-111">Required string.</span></span> <span data-ttu-id="908cb-112">URL du service STS.</span><span class="sxs-lookup"><span data-stu-id="908cb-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="908cb-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="908cb-113">Child Elements</span></span>  
  
|<span data-ttu-id="908cb-114">Élément</span><span class="sxs-lookup"><span data-stu-id="908cb-114">Element</span></span>|<span data-ttu-id="908cb-115">Description</span><span class="sxs-lookup"><span data-stu-id="908cb-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="908cb-116">Collection d'en-têtes d'adresse de points de terminaison pouvant être créée par le générateur.</span><span class="sxs-lookup"><span data-stu-id="908cb-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="908cb-117">Lors de l'utilisation d'un jeton émis, spécifie des paramètres qui permettent au client d'authentifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="908cb-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="908cb-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="908cb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="908cb-119">Élément</span><span class="sxs-lookup"><span data-stu-id="908cb-119">Element</span></span>|<span data-ttu-id="908cb-120">Description</span><span class="sxs-lookup"><span data-stu-id="908cb-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="908cb-121">Spécifie le jeton émis en cours.</span><span class="sxs-lookup"><span data-stu-id="908cb-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="908cb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="908cb-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="908cb-123">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="908cb-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="908cb-124">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="908cb-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="908cb-125">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="908cb-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="908cb-126">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="908cb-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="908cb-127">Liaisons</span><span class="sxs-lookup"><span data-stu-id="908cb-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="908cb-128">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="908cb-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="908cb-129">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="908cb-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="908cb-130">Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="908cb-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="908cb-131">Custom Binding Security</span><span class="sxs-lookup"><span data-stu-id="908cb-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
