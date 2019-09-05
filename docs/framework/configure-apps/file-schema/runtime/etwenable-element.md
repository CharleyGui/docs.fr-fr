---
title: Élément <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb4d0ed5b33170c40aacb32bebbf1b59ca659be4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252620"
---
# <a name="etwenable-element"></a><span data-ttu-id="d15e6-102">\<etwEnable >, élément</span><span class="sxs-lookup"><span data-stu-id="d15e6-102">\<etwEnable> Element</span></span>
<span data-ttu-id="d15e6-103">Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d15e6-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
<span data-ttu-id="d15e6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d15e6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d15e6-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d15e6-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d15e6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<etwEnabled >**</span><span class="sxs-lookup"><span data-stu-id="d15e6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d15e6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d15e6-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d15e6-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d15e6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d15e6-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d15e6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d15e6-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="d15e6-110">Attributes</span></span>  
  
|<span data-ttu-id="d15e6-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="d15e6-111">Attribute</span></span>|<span data-ttu-id="d15e6-112">Description</span><span class="sxs-lookup"><span data-stu-id="d15e6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d15e6-113">enabled</span><span class="sxs-lookup"><span data-stu-id="d15e6-113">enabled</span></span>|<span data-ttu-id="d15e6-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="d15e6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d15e6-115">Spécifie si ETW doit être activé.</span><span class="sxs-lookup"><span data-stu-id="d15e6-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d15e6-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="d15e6-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="d15e6-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="d15e6-117">Value</span></span>|<span data-ttu-id="d15e6-118">Description</span><span class="sxs-lookup"><span data-stu-id="d15e6-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d15e6-119">true</span><span class="sxs-lookup"><span data-stu-id="d15e6-119">true</span></span>|<span data-ttu-id="d15e6-120">Activez ETW.</span><span class="sxs-lookup"><span data-stu-id="d15e6-120">Enable ETW.</span></span> <span data-ttu-id="d15e6-121">Il s’agit de la valeur par défaut pour les versions de Windows qui commencent par les systèmes d’exploitation Windows Vista et Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="d15e6-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="d15e6-122">false</span><span class="sxs-lookup"><span data-stu-id="d15e6-122">false</span></span>|<span data-ttu-id="d15e6-123">Désactivez ETW.</span><span class="sxs-lookup"><span data-stu-id="d15e6-123">Disable ETW.</span></span> <span data-ttu-id="d15e6-124">Il s’agit de la valeur par défaut pour les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="d15e6-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d15e6-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d15e6-125">Child Elements</span></span>  
 <span data-ttu-id="d15e6-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d15e6-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d15e6-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d15e6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d15e6-128">Élément</span><span class="sxs-lookup"><span data-stu-id="d15e6-128">Element</span></span>|<span data-ttu-id="d15e6-129">Description</span><span class="sxs-lookup"><span data-stu-id="d15e6-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d15e6-130">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d15e6-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d15e6-131">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d15e6-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d15e6-132">Notes</span><span class="sxs-lookup"><span data-stu-id="d15e6-132">Remarks</span></span>  
 <span data-ttu-id="d15e6-133">À partir de Windows Vista, ETW est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="d15e6-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="d15e6-134">Utilisez cet élément pour désactiver ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="d15e6-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="d15e6-135">Dans les versions antérieures de Windows, utilisez cet élément pour activer ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="d15e6-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d15e6-136">ETW peut être activé ou désactivé globalement sur un serveur à l’aide d’un paramètre de registre.</span><span class="sxs-lookup"><span data-stu-id="d15e6-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="d15e6-137">Consultez [contrôle de la journalisation des .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="d15e6-137">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d15e6-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="d15e6-138">Example</span></span>  
 <span data-ttu-id="d15e6-139">L’exemple suivant montre comment activer le suivi ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="d15e6-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d15e6-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d15e6-140">See also</span></span>

- [<span data-ttu-id="d15e6-141">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="d15e6-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d15e6-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d15e6-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d15e6-143">Contrôle de l’enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d15e6-143">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
