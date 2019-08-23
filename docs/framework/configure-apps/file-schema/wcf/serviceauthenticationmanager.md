---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 65488c34931f6d7c424ece58a4855e746ea455bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936411"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="54bd9-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="54bd9-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="54bd9-102">Fournit un élément de configuration de flux de travail qui établit au niveau du service la validité d'une transmission, d'un message ou d'un donneur d'ordre.</span><span class="sxs-lookup"><span data-stu-id="54bd9-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="54bd9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="54bd9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="54bd9-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="54bd9-104">\<behaviors></span></span>  
<span data-ttu-id="54bd9-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="54bd9-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="54bd9-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="54bd9-106">\<behavior></span></span>  
<span data-ttu-id="54bd9-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="54bd9-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54bd9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54bd9-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54bd9-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="54bd9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="54bd9-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="54bd9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54bd9-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="54bd9-111">Attributes</span></span>  
  
|<span data-ttu-id="54bd9-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="54bd9-112">Attribute</span></span>|<span data-ttu-id="54bd9-113">Description</span><span class="sxs-lookup"><span data-stu-id="54bd9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54bd9-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="54bd9-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="54bd9-115">Chaîne qui spécifie le type de la stratégie d'authentification pour le comportement actuel.</span><span class="sxs-lookup"><span data-stu-id="54bd9-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54bd9-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="54bd9-116">Child Elements</span></span>  
 <span data-ttu-id="54bd9-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="54bd9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54bd9-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="54bd9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="54bd9-119">Élément</span><span class="sxs-lookup"><span data-stu-id="54bd9-119">Element</span></span>|<span data-ttu-id="54bd9-120">Description</span><span class="sxs-lookup"><span data-stu-id="54bd9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54bd9-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="54bd9-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="54bd9-122">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="54bd9-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54bd9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54bd9-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
