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
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117628"
---
# <a name="developmentmode-element"></a><span data-ttu-id="c07eb-102">\<élément mode developmentmode ></span><span class="sxs-lookup"><span data-stu-id="c07eb-102">\<developmentMode> Element</span></span>
<span data-ttu-id="c07eb-103">Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="c07eb-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
<span data-ttu-id="c07eb-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c07eb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c07eb-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c07eb-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c07eb-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<mode developmentmode** ></span><span class="sxs-lookup"><span data-stu-id="c07eb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c07eb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c07eb-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c07eb-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c07eb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c07eb-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c07eb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c07eb-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="c07eb-110">Attributes</span></span>  
  
|<span data-ttu-id="c07eb-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="c07eb-111">Attribute</span></span>|<span data-ttu-id="c07eb-112">Description</span><span class="sxs-lookup"><span data-stu-id="c07eb-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c07eb-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="c07eb-113">**developerInstallation**</span></span>|<span data-ttu-id="c07eb-114">Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="c07eb-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="c07eb-115">Attribut developerInstallation</span><span class="sxs-lookup"><span data-stu-id="c07eb-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="c07eb-116">valeur</span><span class="sxs-lookup"><span data-stu-id="c07eb-116">Value</span></span>|<span data-ttu-id="c07eb-117">Description</span><span class="sxs-lookup"><span data-stu-id="c07eb-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c07eb-118">**true**</span><span class="sxs-lookup"><span data-stu-id="c07eb-118">**true**</span></span>|<span data-ttu-id="c07eb-119">Recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="c07eb-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="c07eb-120">**false**</span><span class="sxs-lookup"><span data-stu-id="c07eb-120">**false**</span></span>|<span data-ttu-id="c07eb-121">Ne recherche pas les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="c07eb-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="c07eb-122">Il s’agit de la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="c07eb-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c07eb-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c07eb-123">Child Elements</span></span>  
 <span data-ttu-id="c07eb-124">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="c07eb-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c07eb-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c07eb-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c07eb-126">Élément</span><span class="sxs-lookup"><span data-stu-id="c07eb-126">Element</span></span>|<span data-ttu-id="c07eb-127">Description</span><span class="sxs-lookup"><span data-stu-id="c07eb-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c07eb-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c07eb-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c07eb-129">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c07eb-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c07eb-130">Notes</span><span class="sxs-lookup"><span data-stu-id="c07eb-130">Remarks</span></span>  
 <span data-ttu-id="c07eb-131">Utilisez ce paramètre uniquement au moment du développement.</span><span class="sxs-lookup"><span data-stu-id="c07eb-131">Use this setting only at development time.</span></span> <span data-ttu-id="c07eb-132">Le runtime ne vérifie pas les versions des assemblys avec nom fort qui se trouvent dans DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="c07eb-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="c07eb-133">Il utilise simplement le premier assembly qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="c07eb-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c07eb-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="c07eb-134">Example</span></span>  
 <span data-ttu-id="c07eb-135">L’exemple suivant montre comment faire en sorte que le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="c07eb-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c07eb-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c07eb-136">See also</span></span>

- [<span data-ttu-id="c07eb-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="c07eb-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c07eb-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="c07eb-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c07eb-139">Comment : localiser des assemblys à l'aide de DEVPATH</span><span class="sxs-lookup"><span data-stu-id="c07eb-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
