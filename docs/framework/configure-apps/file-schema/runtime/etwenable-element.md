---
title: Élément <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117399"
---
# <a name="etwenable-element"></a><span data-ttu-id="dcc45-102">Élément \<etwEnable></span><span class="sxs-lookup"><span data-stu-id="dcc45-102">\<etwEnable> Element</span></span>
<span data-ttu-id="dcc45-103">Indique s’il faut activer le Suivi d’événements pour Windows (ETW) pour les événements du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="dcc45-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="dcc45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcc45-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcc45-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dcc45-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dcc45-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dcc45-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcc45-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="dcc45-107">Attributes</span></span>  
  
|<span data-ttu-id="dcc45-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="dcc45-108">Attribute</span></span>|<span data-ttu-id="dcc45-109">Description</span><span class="sxs-lookup"><span data-stu-id="dcc45-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dcc45-110">enabled</span><span class="sxs-lookup"><span data-stu-id="dcc45-110">enabled</span></span>|<span data-ttu-id="dcc45-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="dcc45-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="dcc45-112">Spécifie si ETW doit être activé.</span><span class="sxs-lookup"><span data-stu-id="dcc45-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dcc45-113">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="dcc45-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="dcc45-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="dcc45-114">Value</span></span>|<span data-ttu-id="dcc45-115">Description</span><span class="sxs-lookup"><span data-stu-id="dcc45-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dcc45-116">true</span><span class="sxs-lookup"><span data-stu-id="dcc45-116">true</span></span>|<span data-ttu-id="dcc45-117">Activez ETW.</span><span class="sxs-lookup"><span data-stu-id="dcc45-117">Enable ETW.</span></span> <span data-ttu-id="dcc45-118">Il s’agit de la valeur par défaut pour les versions de Windows qui commencent par les systèmes d’exploitation Windows Vista et Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="dcc45-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="dcc45-119">false</span><span class="sxs-lookup"><span data-stu-id="dcc45-119">false</span></span>|<span data-ttu-id="dcc45-120">Désactivez ETW.</span><span class="sxs-lookup"><span data-stu-id="dcc45-120">Disable ETW.</span></span> <span data-ttu-id="dcc45-121">Il s’agit de la valeur par défaut pour les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="dcc45-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcc45-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dcc45-122">Child Elements</span></span>  
 <span data-ttu-id="dcc45-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dcc45-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcc45-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dcc45-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dcc45-125">Élément</span><span class="sxs-lookup"><span data-stu-id="dcc45-125">Element</span></span>|<span data-ttu-id="dcc45-126">Description</span><span class="sxs-lookup"><span data-stu-id="dcc45-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dcc45-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dcc45-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dcc45-128">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="dcc45-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcc45-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="dcc45-129">Remarks</span></span>  
 <span data-ttu-id="dcc45-130">À partir de Windows Vista, ETW est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="dcc45-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="dcc45-131">Utilisez cet élément pour désactiver ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="dcc45-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="dcc45-132">Dans les versions antérieures de Windows, utilisez cet élément pour activer ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="dcc45-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dcc45-133">ETW peut être activé ou désactivé globalement sur un serveur à l’aide d’un paramètre de registre.</span><span class="sxs-lookup"><span data-stu-id="dcc45-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="dcc45-134">Consultez [contrôle de la journalisation des .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="dcc45-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcc45-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="dcc45-135">Example</span></span>  
 <span data-ttu-id="dcc45-136">L’exemple suivant montre comment activer le suivi ETW pour une application.</span><span class="sxs-lookup"><span data-stu-id="dcc45-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dcc45-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcc45-137">See also</span></span>

- [<span data-ttu-id="dcc45-138">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="dcc45-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dcc45-139">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="dcc45-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="dcc45-140">Contrôle de l'enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dcc45-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
