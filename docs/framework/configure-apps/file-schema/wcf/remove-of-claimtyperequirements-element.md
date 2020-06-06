---
title: <remove>d' <claimTypeRequirements> élément
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399995"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="86b14-102">\<remove>d' \<claimTypeRequirements> élément</span><span class="sxs-lookup"><span data-stu-id="86b14-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="86b14-103">Spécifie les types de revendications à supprimer dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="86b14-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="86b14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86b14-104">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86b14-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="86b14-105">Attributes and Elements</span></span>  
 <span data-ttu-id="86b14-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="86b14-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86b14-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="86b14-107">Attributes</span></span>  
  
|<span data-ttu-id="86b14-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="86b14-108">Attribute</span></span>|<span data-ttu-id="86b14-109">Description</span><span class="sxs-lookup"><span data-stu-id="86b14-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86b14-110">claimType</span><span class="sxs-lookup"><span data-stu-id="86b14-110">claimType</span></span>|<span data-ttu-id="86b14-111">URI qui définit le type de revendication à supprimer.</span><span class="sxs-lookup"><span data-stu-id="86b14-111">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86b14-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="86b14-112">Child Elements</span></span>  
 <span data-ttu-id="86b14-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="86b14-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86b14-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="86b14-114">Parent Elements</span></span>  
  
|<span data-ttu-id="86b14-115">Élément</span><span class="sxs-lookup"><span data-stu-id="86b14-115">Element</span></span>|<span data-ttu-id="86b14-116">Description</span><span class="sxs-lookup"><span data-stu-id="86b14-116">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="86b14-117">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="86b14-117">Specifies a collection of required claim types.</span></span> <span data-ttu-id="86b14-118">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="86b14-118">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="86b14-119">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="86b14-119">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="86b14-120">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="86b14-120">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="86b14-121">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="86b14-121">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86b14-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86b14-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
