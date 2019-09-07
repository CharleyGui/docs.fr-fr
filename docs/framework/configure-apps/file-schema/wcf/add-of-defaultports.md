---
title: <add> de <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400639"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="5ed1b-102">\<Ajouter > de \<la > defaultPorts</span><span class="sxs-lookup"><span data-stu-id="5ed1b-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="5ed1b-103">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="5ed1b-103">A default communications endpoint that the client application listens to.</span></span>  
  
<span data-ttu-id="5ed1b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ed1b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ed1b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5ed1b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5ed1b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5ed1b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5ed1b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5ed1b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="5ed1b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5ed1b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="5ed1b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="5ed1b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="5ed1b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultPorts >** ](defaultports.md)</span><span class="sxs-lookup"><span data-stu-id="5ed1b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)</span></span>\
<span data-ttu-id="5ed1b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="5ed1b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed1b-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ed1b-112">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ed1b-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5ed1b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5ed1b-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5ed1b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ed1b-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="5ed1b-115">Attributes</span></span>  
  
|<span data-ttu-id="5ed1b-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="5ed1b-116">Attribute</span></span>|<span data-ttu-id="5ed1b-117">Description</span><span class="sxs-lookup"><span data-stu-id="5ed1b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ed1b-118">port</span><span class="sxs-lookup"><span data-stu-id="5ed1b-118">port</span></span>|<span data-ttu-id="5ed1b-119">Entier qui spécifie le numéro de port de communication par défaut.</span><span class="sxs-lookup"><span data-stu-id="5ed1b-119">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="5ed1b-120">scheme</span><span class="sxs-lookup"><span data-stu-id="5ed1b-120">scheme</span></span>|<span data-ttu-id="5ed1b-121">Chaîne qui spécifie le groupe de paramètres de protocole associé à un port de communication.</span><span class="sxs-lookup"><span data-stu-id="5ed1b-121">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ed1b-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5ed1b-122">Child Elements</span></span>  
 <span data-ttu-id="5ed1b-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5ed1b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ed1b-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5ed1b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5ed1b-125">Élément</span><span class="sxs-lookup"><span data-stu-id="5ed1b-125">Element</span></span>|<span data-ttu-id="5ed1b-126">Description</span><span class="sxs-lookup"><span data-stu-id="5ed1b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ed1b-127">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5ed1b-127">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="5ed1b-128">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="5ed1b-128">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ed1b-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ed1b-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
