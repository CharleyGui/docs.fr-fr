---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399706"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="e66c4-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="e66c4-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="e66c4-102">Fournit un élément de configuration de flux de travail qui établit au niveau du service la validité d'une transmission, d'un message ou d'un donneur d'ordre.</span><span class="sxs-lookup"><span data-stu-id="e66c4-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="e66c4-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e66c4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e66c4-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e66c4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e66c4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e66c4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e66c4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e66c4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="e66c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e66c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="e66c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceAuthenticationManager >**</span><span class="sxs-lookup"><span data-stu-id="e66c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e66c4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e66c4-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e66c4-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e66c4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e66c4-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e66c4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e66c4-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="e66c4-112">Attributes</span></span>  
  
|<span data-ttu-id="e66c4-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="e66c4-113">Attribute</span></span>|<span data-ttu-id="e66c4-114">Description</span><span class="sxs-lookup"><span data-stu-id="e66c4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e66c4-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="e66c4-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="e66c4-116">Chaîne qui spécifie le type de la stratégie d'authentification pour le comportement actuel.</span><span class="sxs-lookup"><span data-stu-id="e66c4-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e66c4-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e66c4-117">Child Elements</span></span>  
 <span data-ttu-id="e66c4-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e66c4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e66c4-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e66c4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e66c4-120">Élément</span><span class="sxs-lookup"><span data-stu-id="e66c4-120">Element</span></span>|<span data-ttu-id="e66c4-121">Description</span><span class="sxs-lookup"><span data-stu-id="e66c4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e66c4-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e66c4-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e66c4-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="e66c4-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e66c4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e66c4-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
