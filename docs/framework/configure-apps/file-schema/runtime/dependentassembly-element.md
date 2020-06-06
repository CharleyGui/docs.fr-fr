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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154203"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="313e9-102">Élément \<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="313e9-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="313e9-103">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="313e9-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="313e9-104">Utilisez un seul `dependentAssembly` élément pour chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="313e9-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="313e9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="313e9-105">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="313e9-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="313e9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="313e9-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="313e9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="313e9-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="313e9-108">Attributes</span></span>  
 <span data-ttu-id="313e9-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="313e9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="313e9-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="313e9-110">Child Elements</span></span>  
  
|<span data-ttu-id="313e9-111">Élément</span><span class="sxs-lookup"><span data-stu-id="313e9-111">Element</span></span>|<span data-ttu-id="313e9-112">Description</span><span class="sxs-lookup"><span data-stu-id="313e9-112">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="313e9-113">Contient des informations d’identification sur l’assembly.</span><span class="sxs-lookup"><span data-stu-id="313e9-113">Contains identifying information about the assembly.</span></span> <span data-ttu-id="313e9-114">Cet élément doit être inclus dans chaque `dependentAssembly` élément.</span><span class="sxs-lookup"><span data-stu-id="313e9-114">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="313e9-115">Spécifie l’emplacement où le runtime peut trouver un assembly partagé s’il n’est pas installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="313e9-115">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="313e9-116">Redirige une version d'assembly vers une autre.</span><span class="sxs-lookup"><span data-stu-id="313e9-116">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="313e9-117">Spécifie si le runtime applique la stratégie d’éditeur pour cet assembly.</span><span class="sxs-lookup"><span data-stu-id="313e9-117">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="313e9-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="313e9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="313e9-119">Élément</span><span class="sxs-lookup"><span data-stu-id="313e9-119">Element</span></span>|<span data-ttu-id="313e9-120">Description</span><span class="sxs-lookup"><span data-stu-id="313e9-120">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="313e9-121">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="313e9-121">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="313e9-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="313e9-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="313e9-123">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="313e9-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="313e9-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="313e9-124">Example</span></span>  
 <span data-ttu-id="313e9-125">L’exemple suivant montre comment encapsuler des informations d’assembly pour deux assemblys.</span><span class="sxs-lookup"><span data-stu-id="313e9-125">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="313e9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="313e9-126">See also</span></span>

- [<span data-ttu-id="313e9-127">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="313e9-127">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="313e9-128">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="313e9-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="313e9-129">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="313e9-129">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
