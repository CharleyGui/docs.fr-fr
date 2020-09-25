---
title: Élément <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 1c3e42dfbc2c27841ed065e90bad24575e4fb2b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178266"
---
# <a name="etwenable-element"></a><span data-ttu-id="cbcbb-102">Élément \<etwEnable></span><span class="sxs-lookup"><span data-stu-id="cbcbb-102">\<etwEnable> Element</span></span>

<span data-ttu-id="cbcbb-103">Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="cbcbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbcbb-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbcbb-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cbcbb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cbcbb-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbcbb-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="cbcbb-107">Attributes</span></span>  
  
|<span data-ttu-id="cbcbb-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="cbcbb-108">Attribute</span></span>|<span data-ttu-id="cbcbb-109">Description</span><span class="sxs-lookup"><span data-stu-id="cbcbb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbcbb-110">enabled</span><span class="sxs-lookup"><span data-stu-id="cbcbb-110">enabled</span></span>|<span data-ttu-id="cbcbb-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="cbcbb-112">Spécifie si ETW doit être activé.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="cbcbb-113">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="cbcbb-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="cbcbb-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="cbcbb-114">Value</span></span>|<span data-ttu-id="cbcbb-115">Description</span><span class="sxs-lookup"><span data-stu-id="cbcbb-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbcbb-116">true</span><span class="sxs-lookup"><span data-stu-id="cbcbb-116">true</span></span>|<span data-ttu-id="cbcbb-117">Activez ETW.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-117">Enable ETW.</span></span> <span data-ttu-id="cbcbb-118">Il s’agit de la valeur par défaut pour les versions de Windows qui commencent par les systèmes d’exploitation Windows Vista et Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="cbcbb-119">false</span><span class="sxs-lookup"><span data-stu-id="cbcbb-119">false</span></span>|<span data-ttu-id="cbcbb-120">Désactivez ETW.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-120">Disable ETW.</span></span> <span data-ttu-id="cbcbb-121">Il s’agit de la valeur par défaut pour les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbcbb-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cbcbb-122">Child Elements</span></span>  

 <span data-ttu-id="cbcbb-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbcbb-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cbcbb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="cbcbb-125">Élément</span><span class="sxs-lookup"><span data-stu-id="cbcbb-125">Element</span></span>|<span data-ttu-id="cbcbb-126">Description</span><span class="sxs-lookup"><span data-stu-id="cbcbb-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cbcbb-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="cbcbb-128">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbcbb-129">Notes</span><span class="sxs-lookup"><span data-stu-id="cbcbb-129">Remarks</span></span>  

 <span data-ttu-id="cbcbb-130">À partir de Windows Vista, ETW est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="cbcbb-131">Utilisez cet élément pour désactiver ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="cbcbb-132">Dans les versions antérieures de Windows, utilisez cet élément pour activer ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbcbb-133">ETW peut être activé ou désactivé globalement sur un serveur à l’aide d’un paramètre de registre.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="cbcbb-134">Consultez [contrôle de la journalisation des .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="cbcbb-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbcbb-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="cbcbb-135">Example</span></span>  

 <span data-ttu-id="cbcbb-136">L’exemple suivant montre comment activer le suivi ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="cbcbb-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbcbb-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbcbb-137">See also</span></span>

- [<span data-ttu-id="cbcbb-138">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="cbcbb-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cbcbb-139">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="cbcbb-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cbcbb-140">Contrôle de l'enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cbcbb-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
