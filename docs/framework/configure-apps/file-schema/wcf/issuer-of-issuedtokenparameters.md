---
title: <issuer> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: bfe8163d2d6baba1d6e8053f7f6579673d8b4b21
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157276"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="284aa-102">\<issuer> de \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="284aa-102">\<issuer> of \<issuedTokenParameters></span></span>

<span data-ttu-id="284aa-103">Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="284aa-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="284aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="284aa-104">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="284aa-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="284aa-105">Attributes and Elements</span></span>  

 <span data-ttu-id="284aa-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="284aa-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="284aa-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="284aa-107">Attributes</span></span>  
  
|<span data-ttu-id="284aa-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="284aa-108">Attribute</span></span>|<span data-ttu-id="284aa-109">Description</span><span class="sxs-lookup"><span data-stu-id="284aa-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="284aa-110">address</span><span class="sxs-lookup"><span data-stu-id="284aa-110">address</span></span>|<span data-ttu-id="284aa-111">Chaîne obligatoire.</span><span class="sxs-lookup"><span data-stu-id="284aa-111">Required string.</span></span> <span data-ttu-id="284aa-112">URL du service STS.</span><span class="sxs-lookup"><span data-stu-id="284aa-112">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="284aa-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="284aa-113">Child Elements</span></span>  
  
|<span data-ttu-id="284aa-114">Élément</span><span class="sxs-lookup"><span data-stu-id="284aa-114">Element</span></span>|<span data-ttu-id="284aa-115">Description</span><span class="sxs-lookup"><span data-stu-id="284aa-115">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="284aa-116">Collection d'en-têtes d'adresse de points de terminaison pouvant être créée par le générateur.</span><span class="sxs-lookup"><span data-stu-id="284aa-116">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="284aa-117">Lors de l'utilisation d'un jeton émis, spécifie des paramètres qui permettent au client d'authentifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="284aa-117">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="284aa-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="284aa-118">Parent Elements</span></span>  
  
|<span data-ttu-id="284aa-119">Élément</span><span class="sxs-lookup"><span data-stu-id="284aa-119">Element</span></span>|<span data-ttu-id="284aa-120">Description</span><span class="sxs-lookup"><span data-stu-id="284aa-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="284aa-121">Spécifie le jeton émis en cours.</span><span class="sxs-lookup"><span data-stu-id="284aa-121">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="284aa-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="284aa-122">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="284aa-123">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="284aa-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="284aa-124">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="284aa-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="284aa-125">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="284aa-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="284aa-126">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="284aa-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="284aa-127">Liaisons</span><span class="sxs-lookup"><span data-stu-id="284aa-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="284aa-128">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="284aa-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="284aa-129">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="284aa-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="284aa-130">Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="284aa-130">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="284aa-131">Custom Binding Security</span><span class="sxs-lookup"><span data-stu-id="284aa-131">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
