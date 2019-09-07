---
title: <clear>d' <claimTypeRequirements> élément
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400526"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="2dedf-102">\<Effacer > de \<l’élément de > ClaimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="2dedf-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="2dedf-103">Indique que tous les types de revendications doivent être supprimés dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="2dedf-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="2dedf-104">Cela garantit que la collection est vide au démarrage.</span><span class="sxs-lookup"><span data-stu-id="2dedf-104">This ensures that the collection starts empty.</span></span>  
  
<span data-ttu-id="2dedf-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2dedf-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2dedf-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2dedf-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2dedf-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2dedf-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2dedf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2dedf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="2dedf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="2dedf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2dedf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2dedf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="2dedf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de messages**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2dedf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="2dedf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="2dedf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="2dedf-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<désactivez >**</span><span class="sxs-lookup"><span data-stu-id="2dedf-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dedf-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dedf-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2dedf-115">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2dedf-115">Attributes and Elements</span></span>  
 <span data-ttu-id="2dedf-116">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2dedf-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2dedf-117">Attributs</span><span class="sxs-lookup"><span data-stu-id="2dedf-117">Attributes</span></span>  
 <span data-ttu-id="2dedf-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2dedf-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2dedf-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2dedf-119">Child Elements</span></span>  
 <span data-ttu-id="2dedf-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2dedf-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2dedf-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2dedf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2dedf-122">Élément</span><span class="sxs-lookup"><span data-stu-id="2dedf-122">Element</span></span>|<span data-ttu-id="2dedf-123">Description</span><span class="sxs-lookup"><span data-stu-id="2dedf-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2dedf-124">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="2dedf-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="2dedf-125">Spécifie une collection de types de revendications requis.</span><span class="sxs-lookup"><span data-stu-id="2dedf-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="2dedf-126">Chaque élément est de type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="2dedf-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="2dedf-127">Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes.</span><span class="sxs-lookup"><span data-stu-id="2dedf-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="2dedf-128">Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini.</span><span class="sxs-lookup"><span data-stu-id="2dedf-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="2dedf-129">Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.</span><span class="sxs-lookup"><span data-stu-id="2dedf-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2dedf-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dedf-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
