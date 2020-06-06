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
ms.openlocfilehash: e9e48ea97e1b70fef7fcc78a113e18c5fec23b7c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115864"
---
# <a name="probing-element"></a><span data-ttu-id="0da6a-102">Élément \<probing></span><span class="sxs-lookup"><span data-stu-id="0da6a-102">\<probing> Element</span></span>
<span data-ttu-id="0da6a-103">Spécifie les sous-répertoires de base de l’application pour le common language runtime à rechercher lors du chargement des assemblys.</span><span class="sxs-lookup"><span data-stu-id="0da6a-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="0da6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0da6a-104">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0da6a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0da6a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0da6a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0da6a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0da6a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="0da6a-107">Attributes</span></span>  
  
|<span data-ttu-id="0da6a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="0da6a-108">Attribute</span></span>|<span data-ttu-id="0da6a-109">Description</span><span class="sxs-lookup"><span data-stu-id="0da6a-109">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="0da6a-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="0da6a-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="0da6a-111">Spécifie les sous-répertoires du répertoire de base de l’application qui peuvent contenir des assemblys.</span><span class="sxs-lookup"><span data-stu-id="0da6a-111">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="0da6a-112">Délimitez chaque sous-répertoire par un point-virgule.</span><span class="sxs-lookup"><span data-stu-id="0da6a-112">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0da6a-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0da6a-113">Child Elements</span></span>  

<span data-ttu-id="0da6a-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0da6a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0da6a-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0da6a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0da6a-116">Élément</span><span class="sxs-lookup"><span data-stu-id="0da6a-116">Element</span></span>|<span data-ttu-id="0da6a-117">Description</span><span class="sxs-lookup"><span data-stu-id="0da6a-117">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="0da6a-118">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="0da6a-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="0da6a-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0da6a-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0da6a-120">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0da6a-120">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0da6a-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="0da6a-121">Example</span></span>  
 <span data-ttu-id="0da6a-122">L’exemple suivant montre comment spécifier les sous-répertoires de base de l’application que le runtime doit rechercher pour les assemblys.</span><span class="sxs-lookup"><span data-stu-id="0da6a-122">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0da6a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0da6a-123">See also</span></span>

- [<span data-ttu-id="0da6a-124">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="0da6a-124">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="0da6a-125">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="0da6a-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="0da6a-126">Spécifier l’emplacement d’un assembly</span><span class="sxs-lookup"><span data-stu-id="0da6a-126">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="0da6a-127">Comment le runtime localise les assemblys</span><span class="sxs-lookup"><span data-stu-id="0da6a-127">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
