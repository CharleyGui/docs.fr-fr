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
ms.openlocfilehash: ddcabb831193baee30016f663f32d8562283d936
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205020"
---
# <a name="developmentmode-element"></a><span data-ttu-id="47c9b-102">Élément \<developmentMode></span><span class="sxs-lookup"><span data-stu-id="47c9b-102">\<developmentMode> Element</span></span>

<span data-ttu-id="47c9b-103">Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="47c9b-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="47c9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47c9b-104">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47c9b-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="47c9b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="47c9b-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="47c9b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47c9b-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="47c9b-107">Attributes</span></span>  
  
|<span data-ttu-id="47c9b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="47c9b-108">Attribute</span></span>|<span data-ttu-id="47c9b-109">Description</span><span class="sxs-lookup"><span data-stu-id="47c9b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47c9b-110">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="47c9b-110">**developerInstallation**</span></span>|<span data-ttu-id="47c9b-111">Indique si le runtime recherche des assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="47c9b-111">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="47c9b-112">Attribut developerInstallation</span><span class="sxs-lookup"><span data-stu-id="47c9b-112">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="47c9b-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="47c9b-113">Value</span></span>|<span data-ttu-id="47c9b-114">Description</span><span class="sxs-lookup"><span data-stu-id="47c9b-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47c9b-115">**true**</span><span class="sxs-lookup"><span data-stu-id="47c9b-115">**true**</span></span>|<span data-ttu-id="47c9b-116">Recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="47c9b-116">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="47c9b-117">**false**</span><span class="sxs-lookup"><span data-stu-id="47c9b-117">**false**</span></span>|<span data-ttu-id="47c9b-118">Ne recherche pas les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="47c9b-118">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="47c9b-119">Il s'agit du paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="47c9b-119">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47c9b-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="47c9b-120">Child Elements</span></span>  

 <span data-ttu-id="47c9b-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="47c9b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47c9b-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="47c9b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="47c9b-123">Élément</span><span class="sxs-lookup"><span data-stu-id="47c9b-123">Element</span></span>|<span data-ttu-id="47c9b-124">Description</span><span class="sxs-lookup"><span data-stu-id="47c9b-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="47c9b-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47c9b-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="47c9b-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="47c9b-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47c9b-127">Notes</span><span class="sxs-lookup"><span data-stu-id="47c9b-127">Remarks</span></span>  

 <span data-ttu-id="47c9b-128">Utilisez ce paramètre uniquement au moment du développement.</span><span class="sxs-lookup"><span data-stu-id="47c9b-128">Use this setting only at development time.</span></span> <span data-ttu-id="47c9b-129">Le runtime ne vérifie pas les versions des assemblys avec nom fort qui se trouvent dans DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="47c9b-129">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="47c9b-130">Il utilise simplement le premier assembly qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="47c9b-130">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47c9b-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="47c9b-131">Example</span></span>  

 <span data-ttu-id="47c9b-132">L’exemple suivant montre comment faire en sorte que le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="47c9b-132">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47c9b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47c9b-133">See also</span></span>

- [<span data-ttu-id="47c9b-134">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="47c9b-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="47c9b-135">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="47c9b-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="47c9b-136">Procédure : Localiser des assemblys à l’aide de DEVPATH</span><span class="sxs-lookup"><span data-stu-id="47c9b-136">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
