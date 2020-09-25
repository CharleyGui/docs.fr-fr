---
title: <issuerMetadata> de <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 389ac9e96c1462f59bc42b2e20cb511acdefda00
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185663"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="bd9e0-102">\<issuerMetadata> de \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="bd9e0-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="bd9e0-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd9e0-103">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd9e0-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bd9e0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bd9e0-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd9e0-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="bd9e0-106">Attributes</span></span>  
  
|<span data-ttu-id="bd9e0-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="bd9e0-107">Attribute</span></span>|<span data-ttu-id="bd9e0-108">Description</span><span class="sxs-lookup"><span data-stu-id="bd9e0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd9e0-109">address</span><span class="sxs-lookup"><span data-stu-id="bd9e0-109">address</span></span>|<span data-ttu-id="bd9e0-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-110">Required.</span></span> <span data-ttu-id="bd9e0-111">Chaîne qui spécifie l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-111">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="bd9e0-112">L'adresse doit être un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-112">The address must be an absolute URI.</span></span> <span data-ttu-id="bd9e0-113">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-113">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd9e0-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bd9e0-114">Child Elements</span></span>  
  
|<span data-ttu-id="bd9e0-115">Élément</span><span class="sxs-lookup"><span data-stu-id="bd9e0-115">Element</span></span>|<span data-ttu-id="bd9e0-116">Description</span><span class="sxs-lookup"><span data-stu-id="bd9e0-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="bd9e0-117">Collection d'en-têtes d'adresses.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-117">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="bd9e0-118">Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-118">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd9e0-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bd9e0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bd9e0-120">Élément</span><span class="sxs-lookup"><span data-stu-id="bd9e0-120">Element</span></span>|<span data-ttu-id="bd9e0-121">Description</span><span class="sxs-lookup"><span data-stu-id="bd9e0-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="bd9e0-122">Indique les paramètres d'un jeton de sécurité émis dans un scénario de sécurité fédéré.</span><span class="sxs-lookup"><span data-stu-id="bd9e0-122">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd9e0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd9e0-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bd9e0-124">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="bd9e0-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="bd9e0-125">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="bd9e0-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="bd9e0-126">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="bd9e0-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="bd9e0-127">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="bd9e0-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="bd9e0-128">Liaisons</span><span class="sxs-lookup"><span data-stu-id="bd9e0-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bd9e0-129">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="bd9e0-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bd9e0-130">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="bd9e0-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="bd9e0-131">Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd9e0-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="bd9e0-132">Custom Binding Security</span><span class="sxs-lookup"><span data-stu-id="bd9e0-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
