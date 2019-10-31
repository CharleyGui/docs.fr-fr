---
title: Élément <dependentAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
ms.openlocfilehash: 33309ed89b4d31580da5de3aeb38e9e1fd8ae4d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117596"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="3c230-102">\<élément > dependentAssembly</span><span class="sxs-lookup"><span data-stu-id="3c230-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="3c230-103">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="3c230-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="3c230-104">Utilisez un élément `dependentAssembly` pour chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="3c230-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
<span data-ttu-id="3c230-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3c230-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3c230-106">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="3c230-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3c230-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding**](assemblybinding-element-for-runtime.md) ></span><span class="sxs-lookup"><span data-stu-id="3c230-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="3c230-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**dependentAssembly** ></span><span class="sxs-lookup"><span data-stu-id="3c230-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c230-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c230-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c230-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3c230-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3c230-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3c230-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c230-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="3c230-112">Attributes</span></span>  
 <span data-ttu-id="3c230-113">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="3c230-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c230-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3c230-114">Child Elements</span></span>  
  
|<span data-ttu-id="3c230-115">Élément</span><span class="sxs-lookup"><span data-stu-id="3c230-115">Element</span></span>|<span data-ttu-id="3c230-116">Description</span><span class="sxs-lookup"><span data-stu-id="3c230-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="3c230-117">Contient des informations d’identification sur l’assembly.</span><span class="sxs-lookup"><span data-stu-id="3c230-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="3c230-118">Cet élément doit être inclus dans chaque élément `dependentAssembly`.</span><span class="sxs-lookup"><span data-stu-id="3c230-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="3c230-119">Spécifie l’emplacement où le runtime peut trouver un assembly partagé s’il n’est pas installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3c230-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="3c230-120">Redirige une version d'assembly vers une autre.</span><span class="sxs-lookup"><span data-stu-id="3c230-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="3c230-121">Spécifie si le runtime applique la stratégie d’éditeur pour cet assembly.</span><span class="sxs-lookup"><span data-stu-id="3c230-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c230-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3c230-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3c230-123">Élément</span><span class="sxs-lookup"><span data-stu-id="3c230-123">Element</span></span>|<span data-ttu-id="3c230-124">Description</span><span class="sxs-lookup"><span data-stu-id="3c230-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="3c230-125">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="3c230-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="3c230-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c230-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3c230-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3c230-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3c230-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c230-128">Example</span></span>  
 <span data-ttu-id="3c230-129">L’exemple suivant montre comment encapsuler des informations d’assembly pour deux assemblys.</span><span class="sxs-lookup"><span data-stu-id="3c230-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c230-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c230-130">See also</span></span>

- [<span data-ttu-id="3c230-131">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="3c230-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3c230-132">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3c230-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3c230-133">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="3c230-133">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
