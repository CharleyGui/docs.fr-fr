---
title: <remove>d' <claimTypeRequirements> élément
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 7238c253bfbc3224c8bbd31265e197dd35e56514
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934236"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="d2462-102">\<supprimer > de \<l’élément de > ClaimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="d2462-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="d2462-103">Spécifie les types de revendications à supprimer dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="d2462-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="d2462-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d2462-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2462-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d2462-105">\<bindings></span></span>  
<span data-ttu-id="d2462-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="d2462-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d2462-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="d2462-107">\<binding></span></span>  
<span data-ttu-id="d2462-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="d2462-108">\<security></span></span>  
<span data-ttu-id="d2462-109">\<message></span><span class="sxs-lookup"><span data-stu-id="d2462-109">\<message></span></span>  
<span data-ttu-id="d2462-110">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d2462-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2462-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2462-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2462-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d2462-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d2462-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d2462-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2462-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="d2462-114">Attributes</span></span>  
  
|<span data-ttu-id="d2462-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="d2462-115">Attribute</span></span>|<span data-ttu-id="d2462-116">Description</span><span class="sxs-lookup"><span data-stu-id="d2462-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2462-117">claimType</span><span class="sxs-lookup"><span data-stu-id="d2462-117">claimType</span></span>|<span data-ttu-id="d2462-118">URI qui définit le type de revendication à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d2462-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2462-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d2462-119">Child Elements</span></span>  
 <span data-ttu-id="d2462-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d2462-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2462-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d2462-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d2462-122">Élément</span><span class="sxs-lookup"><span data-stu-id="d2462-122">Element</span></span>|<span data-ttu-id="d2462-123">Description</span><span class="sxs-lookup"><span data-stu-id="d2462-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2462-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="d2462-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="d2462-125">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="d2462-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="d2462-126">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="d2462-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="d2462-127">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="d2462-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="d2462-128">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="d2462-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="d2462-129">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="d2462-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2462-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2462-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
