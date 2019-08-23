---
title: <add> de <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: d2723dad14a63c4b05fdb70157f7eb21d193d3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926705"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="4b5e3-102">\<Ajouter > de \<la > defaultPorts</span><span class="sxs-lookup"><span data-stu-id="4b5e3-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="4b5e3-103">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="4b5e3-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="4b5e3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4b5e3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b5e3-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="4b5e3-105">\<behaviors></span></span>  
<span data-ttu-id="4b5e3-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4b5e3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4b5e3-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="4b5e3-107">\<behavior></span></span>  
<span data-ttu-id="4b5e3-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="4b5e3-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="4b5e3-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="4b5e3-109">\<defaultPorts></span></span>  
<span data-ttu-id="4b5e3-110">\<add></span><span class="sxs-lookup"><span data-stu-id="4b5e3-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b5e3-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b5e3-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b5e3-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4b5e3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4b5e3-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4b5e3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b5e3-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="4b5e3-114">Attributes</span></span>  
  
|<span data-ttu-id="4b5e3-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="4b5e3-115">Attribute</span></span>|<span data-ttu-id="4b5e3-116">Description</span><span class="sxs-lookup"><span data-stu-id="4b5e3-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b5e3-117">port</span><span class="sxs-lookup"><span data-stu-id="4b5e3-117">port</span></span>|<span data-ttu-id="4b5e3-118">Entier qui spécifie le numéro de port de communication par défaut.</span><span class="sxs-lookup"><span data-stu-id="4b5e3-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="4b5e3-119">scheme</span><span class="sxs-lookup"><span data-stu-id="4b5e3-119">scheme</span></span>|<span data-ttu-id="4b5e3-120">Chaîne qui spécifie le groupe de paramètres de protocole associé à un port de communication.</span><span class="sxs-lookup"><span data-stu-id="4b5e3-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b5e3-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4b5e3-121">Child Elements</span></span>  
 <span data-ttu-id="4b5e3-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4b5e3-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b5e3-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4b5e3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4b5e3-124">Élément</span><span class="sxs-lookup"><span data-stu-id="4b5e3-124">Element</span></span>|<span data-ttu-id="4b5e3-125">Description</span><span class="sxs-lookup"><span data-stu-id="4b5e3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b5e3-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="4b5e3-126">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="4b5e3-127">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="4b5e3-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b5e3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b5e3-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
