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
ms.openlocfilehash: 2de8c752867d00708173d11d1851f415a2e8518d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154203"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="dd811-102">\<dependentAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="dd811-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="dd811-103">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="dd811-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="dd811-104">Utilisez `dependentAssembly` un élément pour chaque assemblage.</span><span class="sxs-lookup"><span data-stu-id="dd811-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
<span data-ttu-id="dd811-105">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dd811-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dd811-106">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="dd811-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="dd811-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblageBinding>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="dd811-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="dd811-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dépendantAssembly>**</span><span class="sxs-lookup"><span data-stu-id="dd811-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd811-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd811-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd811-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="dd811-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd811-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="dd811-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd811-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="dd811-112">Attributes</span></span>  
 <span data-ttu-id="dd811-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dd811-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd811-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="dd811-114">Child Elements</span></span>  
  
|<span data-ttu-id="dd811-115">Élément</span><span class="sxs-lookup"><span data-stu-id="dd811-115">Element</span></span>|<span data-ttu-id="dd811-116">Description</span><span class="sxs-lookup"><span data-stu-id="dd811-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="dd811-117">Contient des informations d’identification sur l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="dd811-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="dd811-118">Cet élément doit être `dependentAssembly` inclus dans chaque élément.</span><span class="sxs-lookup"><span data-stu-id="dd811-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="dd811-119">Précise où l’heure d’exécution peut trouver un assemblage partagé s’il n’est pas installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dd811-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="dd811-120">Redirige une version d'assembly vers une autre.</span><span class="sxs-lookup"><span data-stu-id="dd811-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="dd811-121">Précise si le temps d’exécution applique la politique de l’éditeur pour cette assemblée.</span><span class="sxs-lookup"><span data-stu-id="dd811-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd811-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="dd811-122">Parent Elements</span></span>  
  
|<span data-ttu-id="dd811-123">Élément</span><span class="sxs-lookup"><span data-stu-id="dd811-123">Element</span></span>|<span data-ttu-id="dd811-124">Description</span><span class="sxs-lookup"><span data-stu-id="dd811-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="dd811-125">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="dd811-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="dd811-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd811-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dd811-127">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="dd811-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dd811-128"> Exemple</span><span class="sxs-lookup"><span data-stu-id="dd811-128">Example</span></span>  
 <span data-ttu-id="dd811-129">L’exemple suivant montre comment encapsuler l’information d’assemblage pour deux assemblées.</span><span class="sxs-lookup"><span data-stu-id="dd811-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd811-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd811-130">See also</span></span>

- [<span data-ttu-id="dd811-131">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="dd811-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dd811-132">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="dd811-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="dd811-133">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="dd811-133">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
