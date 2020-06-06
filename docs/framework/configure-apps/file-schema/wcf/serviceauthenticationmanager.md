---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399706"
---
# \<serviceAuthenticationManager>
<span data-ttu-id="46e4c-101">Fournit un élément de configuration de flux de travail qui établit au niveau du service la validité d'une transmission, d'un message ou d'un donneur d'ordre.</span><span class="sxs-lookup"><span data-stu-id="46e4c-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="46e4c-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46e4c-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46e4c-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="46e4c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="46e4c-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="46e4c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46e4c-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="46e4c-105">Attributes</span></span>  
  
|<span data-ttu-id="46e4c-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="46e4c-106">Attribute</span></span>|<span data-ttu-id="46e4c-107">Description</span><span class="sxs-lookup"><span data-stu-id="46e4c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46e4c-108">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="46e4c-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="46e4c-109">Chaîne qui spécifie le type de la stratégie d'authentification pour le comportement actuel.</span><span class="sxs-lookup"><span data-stu-id="46e4c-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46e4c-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="46e4c-110">Child Elements</span></span>  
 <span data-ttu-id="46e4c-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="46e4c-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46e4c-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="46e4c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="46e4c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="46e4c-113">Element</span></span>|<span data-ttu-id="46e4c-114">Description</span><span class="sxs-lookup"><span data-stu-id="46e4c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="46e4c-115">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="46e4c-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46e4c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46e4c-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
