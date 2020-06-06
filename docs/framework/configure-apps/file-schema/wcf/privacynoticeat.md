---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738767"
---
# \<privacyNoticeAt>
<span data-ttu-id="fd5d0-101">Représente un élément de configuration qui spécifie un avis de confidentialité utilisé dans la liaison `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="fd5d0-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="fd5d0-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd5d0-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="fd5d0-103">Type</span><span class="sxs-lookup"><span data-stu-id="fd5d0-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd5d0-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fd5d0-104">Attributes and Elements</span></span>  
 <span data-ttu-id="fd5d0-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fd5d0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd5d0-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="fd5d0-106">Attributes</span></span>  
  
|<span data-ttu-id="fd5d0-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="fd5d0-107">Attribute</span></span>|<span data-ttu-id="fd5d0-108">Description</span><span class="sxs-lookup"><span data-stu-id="fd5d0-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="fd5d0-109">Chaîne qui spécifie l'URI dans lequel l'information préalable de confidentialité est située.</span><span class="sxs-lookup"><span data-stu-id="fd5d0-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="fd5d0-110">Entier qui spécifie la version de cet avis de confidentialité.</span><span class="sxs-lookup"><span data-stu-id="fd5d0-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd5d0-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd5d0-111">Child Elements</span></span>  
 <span data-ttu-id="fd5d0-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fd5d0-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd5d0-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd5d0-113">Parent Elements</span></span>  
  
|<span data-ttu-id="fd5d0-114">Élément</span><span class="sxs-lookup"><span data-stu-id="fd5d0-114">Element</span></span>|<span data-ttu-id="fd5d0-115">Description</span><span class="sxs-lookup"><span data-stu-id="fd5d0-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="fd5d0-116">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="fd5d0-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd5d0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd5d0-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fd5d0-118">Liaisons</span><span class="sxs-lookup"><span data-stu-id="fd5d0-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fd5d0-119">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="fd5d0-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fd5d0-120">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="fd5d0-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
