---
title: <clear> d' <claimTypeRequirements> élément
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: aa94a012da11bcec6fb5fe270ad9f3574f88e6d7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172903"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="c4c0f-102">\<clear> d' \<claimTypeRequirements> élément</span><span class="sxs-lookup"><span data-stu-id="c4c0f-102">\<clear> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="c4c0f-103">Indique que tous les types de revendications doivent être supprimés dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="c4c0f-104">Cela garantit que la collection est vide au démarrage.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-104">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="c4c0f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4c0f-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4c0f-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c4c0f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c4c0f-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4c0f-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="c4c0f-108">Attributes</span></span>  

 <span data-ttu-id="c4c0f-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4c0f-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c4c0f-110">Child Elements</span></span>  

 <span data-ttu-id="c4c0f-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4c0f-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c4c0f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c4c0f-113">Élément</span><span class="sxs-lookup"><span data-stu-id="c4c0f-113">Element</span></span>|<span data-ttu-id="c4c0f-114">Description</span><span class="sxs-lookup"><span data-stu-id="c4c0f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="c4c0f-115">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-115">Specifies a collection of required claim types.</span></span> <span data-ttu-id="c4c0f-116">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-116">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="c4c0f-117">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-117">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="c4c0f-118">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-118">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="c4c0f-119">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="c4c0f-119">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4c0f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4c0f-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
