---
title: <remove>d' <claimTypeRequirements> élément
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399995"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="ae935-102">\<supprimer > de \<l’élément de > ClaimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="ae935-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="ae935-103">Spécifie les types de revendications à supprimer dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="ae935-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
<span data-ttu-id="ae935-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ae935-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ae935-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ae935-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ae935-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ae935-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ae935-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ae935-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="ae935-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="ae935-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ae935-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ae935-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="ae935-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de messages**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ae935-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="ae935-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="ae935-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="ae935-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<supprimer >**</span><span class="sxs-lookup"><span data-stu-id="ae935-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae935-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae935-113">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae935-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ae935-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ae935-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ae935-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae935-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="ae935-116">Attributes</span></span>  
  
|<span data-ttu-id="ae935-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="ae935-117">Attribute</span></span>|<span data-ttu-id="ae935-118">Description</span><span class="sxs-lookup"><span data-stu-id="ae935-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae935-119">claimType</span><span class="sxs-lookup"><span data-stu-id="ae935-119">claimType</span></span>|<span data-ttu-id="ae935-120">URI qui définit le type de revendication à supprimer.</span><span class="sxs-lookup"><span data-stu-id="ae935-120">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae935-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ae935-121">Child Elements</span></span>  
 <span data-ttu-id="ae935-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ae935-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae935-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ae935-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ae935-124">Élément</span><span class="sxs-lookup"><span data-stu-id="ae935-124">Element</span></span>|<span data-ttu-id="ae935-125">Description</span><span class="sxs-lookup"><span data-stu-id="ae935-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae935-126">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="ae935-126">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="ae935-127">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="ae935-127">Specifies a collection of required claim types.</span></span> <span data-ttu-id="ae935-128">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="ae935-128">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="ae935-129">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="ae935-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="ae935-130">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="ae935-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="ae935-131">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="ae935-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae935-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae935-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
