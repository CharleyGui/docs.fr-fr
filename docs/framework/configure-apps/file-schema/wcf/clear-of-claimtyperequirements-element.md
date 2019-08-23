---
title: <clear>d' <claimTypeRequirements> élément
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: e7e3bebd85decbaa4d216743f9bea9e135b87995
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926134"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="e986c-102">\<Effacer > de \<l’élément de > ClaimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="e986c-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="e986c-103">Indique que tous les types de revendications doivent être supprimés dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="e986c-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="e986c-104">Cela garantit que la collection est vide au démarrage.</span><span class="sxs-lookup"><span data-stu-id="e986c-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="e986c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e986c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e986c-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e986c-106">\<bindings></span></span>  
<span data-ttu-id="e986c-107">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="e986c-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="e986c-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="e986c-108">\<binding></span></span>  
<span data-ttu-id="e986c-109">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="e986c-109">\<security></span></span>  
<span data-ttu-id="e986c-110">\<message></span><span class="sxs-lookup"><span data-stu-id="e986c-110">\<message></span></span>  
<span data-ttu-id="e986c-111">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="e986c-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e986c-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e986c-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e986c-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e986c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e986c-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e986c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e986c-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="e986c-115">Attributes</span></span>  
 <span data-ttu-id="e986c-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e986c-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e986c-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e986c-117">Child Elements</span></span>  
 <span data-ttu-id="e986c-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e986c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e986c-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e986c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e986c-120">Élément</span><span class="sxs-lookup"><span data-stu-id="e986c-120">Element</span></span>|<span data-ttu-id="e986c-121">Description</span><span class="sxs-lookup"><span data-stu-id="e986c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e986c-122">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="e986c-122">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="e986c-123">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="e986c-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="e986c-124">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="e986c-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="e986c-125">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="e986c-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e986c-126">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="e986c-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e986c-127">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="e986c-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e986c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e986c-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
