---
title: Élément <probing>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae789e99a1306102c67f2252760e215989132406
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971626"
---
# <a name="probing-element"></a><span data-ttu-id="5215f-102">\<détection de l’élément ></span><span class="sxs-lookup"><span data-stu-id="5215f-102">\<probing> Element</span></span>
<span data-ttu-id="5215f-103">Spécifie les sous-répertoires de base de l’application pour le common language runtime à rechercher lors du chargement des assemblys.</span><span class="sxs-lookup"><span data-stu-id="5215f-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
<span data-ttu-id="5215f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5215f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5215f-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5215f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5215f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="5215f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="5215f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<probing>**</span><span class="sxs-lookup"><span data-stu-id="5215f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5215f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5215f-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5215f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5215f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5215f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5215f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5215f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="5215f-111">Attributes</span></span>  
  
|<span data-ttu-id="5215f-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="5215f-112">Attribute</span></span>|<span data-ttu-id="5215f-113">Description</span><span class="sxs-lookup"><span data-stu-id="5215f-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="5215f-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="5215f-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="5215f-115">Spécifie les sous-répertoires du répertoire de base de l’application qui peuvent contenir des assemblys.</span><span class="sxs-lookup"><span data-stu-id="5215f-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="5215f-116">Délimitez chaque sous-répertoire par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="5215f-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5215f-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5215f-117">Child Elements</span></span>  

<span data-ttu-id="5215f-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5215f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5215f-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5215f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5215f-120">Élément</span><span class="sxs-lookup"><span data-stu-id="5215f-120">Element</span></span>|<span data-ttu-id="5215f-121">Description</span><span class="sxs-lookup"><span data-stu-id="5215f-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="5215f-122">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="5215f-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="5215f-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5215f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5215f-124">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5215f-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5215f-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="5215f-125">Example</span></span>  
 <span data-ttu-id="5215f-126">L’exemple suivant montre comment spécifier les sous-répertoires de base de l’application que le runtime doit rechercher pour les assemblys.</span><span class="sxs-lookup"><span data-stu-id="5215f-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5215f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5215f-127">See also</span></span>

- [<span data-ttu-id="5215f-128">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="5215f-128">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="5215f-129">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5215f-129">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="5215f-130">Spécifier l’emplacement d’un assembly</span><span class="sxs-lookup"><span data-stu-id="5215f-130">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="5215f-131">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="5215f-131">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
