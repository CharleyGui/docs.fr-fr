---
title: Élément <developmentMode>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0253c3ced52b575097fe5d18abb8ce188c0164fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252694"
---
# <a name="developmentmode-element"></a><span data-ttu-id="ab4b7-102">\<Mode developmentmode >, élément</span><span class="sxs-lookup"><span data-stu-id="ab4b7-102">\<developmentMode> Element</span></span>
<span data-ttu-id="ab4b7-103">Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
<span data-ttu-id="ab4b7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab4b7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ab4b7-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab4b7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ab4b7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<developmentMode>**</span><span class="sxs-lookup"><span data-stu-id="ab4b7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab4b7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab4b7-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab4b7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ab4b7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ab4b7-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab4b7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="ab4b7-110">Attributes</span></span>  
  
|<span data-ttu-id="ab4b7-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="ab4b7-111">Attribute</span></span>|<span data-ttu-id="ab4b7-112">Description</span><span class="sxs-lookup"><span data-stu-id="ab4b7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab4b7-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="ab4b7-113">**developerInstallation**</span></span>|<span data-ttu-id="ab4b7-114">Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="ab4b7-115">Attribut developerInstallation</span><span class="sxs-lookup"><span data-stu-id="ab4b7-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="ab4b7-116">`Value`</span><span class="sxs-lookup"><span data-stu-id="ab4b7-116">Value</span></span>|<span data-ttu-id="ab4b7-117">Description</span><span class="sxs-lookup"><span data-stu-id="ab4b7-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab4b7-118">**true**</span><span class="sxs-lookup"><span data-stu-id="ab4b7-118">**true**</span></span>|<span data-ttu-id="ab4b7-119">Recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="ab4b7-120">**false**</span><span class="sxs-lookup"><span data-stu-id="ab4b7-120">**false**</span></span>|<span data-ttu-id="ab4b7-121">Ne recherche pas les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="ab4b7-122">Il s’agit de la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="ab4b7-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab4b7-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ab4b7-123">Child Elements</span></span>  
 <span data-ttu-id="ab4b7-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab4b7-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ab4b7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ab4b7-126">Élément</span><span class="sxs-lookup"><span data-stu-id="ab4b7-126">Element</span></span>|<span data-ttu-id="ab4b7-127">Description</span><span class="sxs-lookup"><span data-stu-id="ab4b7-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ab4b7-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ab4b7-129">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab4b7-130">Notes</span><span class="sxs-lookup"><span data-stu-id="ab4b7-130">Remarks</span></span>  
 <span data-ttu-id="ab4b7-131">Utilisez ce paramètre uniquement au moment du développement.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-131">Use this setting only at development time.</span></span> <span data-ttu-id="ab4b7-132">Le runtime ne vérifie pas les versions des assemblys avec nom fort qui se trouvent dans DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="ab4b7-133">Il utilise simplement le premier assembly qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab4b7-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab4b7-134">Example</span></span>  
 <span data-ttu-id="ab4b7-135">L’exemple suivant montre comment faire en sorte que le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="ab4b7-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab4b7-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab4b7-136">See also</span></span>

- [<span data-ttu-id="ab4b7-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="ab4b7-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ab4b7-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ab4b7-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ab4b7-139">Guide pratique pour Localiser des assemblys à l’aide de DEVPATH</span><span class="sxs-lookup"><span data-stu-id="ab4b7-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
