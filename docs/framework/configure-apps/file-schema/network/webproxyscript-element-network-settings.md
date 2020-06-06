---
title: <webProxyScript>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: dbad888cd0537f63c09840ac1053f924db9ea9bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089064"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="a00dd-102">\<webProxyScript>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a00dd-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="a00dd-103">Configure les caractéristiques du script utilisé pour découvrir les proxys Web.</span><span class="sxs-lookup"><span data-stu-id="a00dd-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="a00dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a00dd-104">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a00dd-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a00dd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a00dd-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a00dd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a00dd-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="a00dd-107">Attributes</span></span>  
  
|<span data-ttu-id="a00dd-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a00dd-108">Attribute</span></span>|<span data-ttu-id="a00dd-109">Description</span><span class="sxs-lookup"><span data-stu-id="a00dd-109">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="a00dd-110">Spécifie la durée maximale de téléchargement du script en heures, minutes et secondes.</span><span class="sxs-lookup"><span data-stu-id="a00dd-110">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="a00dd-111">La valeur par défaut est d’une minute.</span><span class="sxs-lookup"><span data-stu-id="a00dd-111">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a00dd-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a00dd-112">Child Elements</span></span>  
 <span data-ttu-id="a00dd-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a00dd-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a00dd-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a00dd-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a00dd-115">Élément</span><span class="sxs-lookup"><span data-stu-id="a00dd-115">Element</span></span>|<span data-ttu-id="a00dd-116">Description</span><span class="sxs-lookup"><span data-stu-id="a00dd-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a00dd-117">settings</span><span class="sxs-lookup"><span data-stu-id="a00dd-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="a00dd-118">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="a00dd-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a00dd-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="a00dd-119">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a00dd-120">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a00dd-120">Configuration Files</span></span>  
 <span data-ttu-id="a00dd-121">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a00dd-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00dd-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a00dd-122">See also</span></span>

- [<span data-ttu-id="a00dd-123">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="a00dd-123">Network Settings Schema</span></span>](index.md)
