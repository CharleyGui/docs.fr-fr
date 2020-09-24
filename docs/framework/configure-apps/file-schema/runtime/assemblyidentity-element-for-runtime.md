---
title: Élément <assemblyIdentity> pour <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: f3e74b05ac0fd7c57963f2aad047ba3f2d63a10a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170179"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="39821-102">\<assemblyIdentity>, élément de \<runtime></span><span class="sxs-lookup"><span data-stu-id="39821-102">\<assemblyIdentity> Element for \<runtime></span></span>

<span data-ttu-id="39821-103">Contient des informations d’identification sur l’assembly.</span><span class="sxs-lookup"><span data-stu-id="39821-103">Contains identifying information about the assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a><span data-ttu-id="39821-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39821-104">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39821-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="39821-105">Attributes and Elements</span></span>  

 <span data-ttu-id="39821-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="39821-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39821-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="39821-107">Attributes</span></span>  
  
|<span data-ttu-id="39821-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="39821-108">Attribute</span></span>|<span data-ttu-id="39821-109">Description</span><span class="sxs-lookup"><span data-stu-id="39821-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="39821-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="39821-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="39821-111">Nom de l’assembly</span><span class="sxs-lookup"><span data-stu-id="39821-111">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="39821-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="39821-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="39821-113">Chaîne qui spécifie la langue et le pays/la région de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="39821-113">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="39821-114">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="39821-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="39821-115">Valeur hexadécimale qui spécifie le nom fort de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="39821-115">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="39821-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="39821-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="39821-117">L’une des valeurs « x86 », « amd64 », « MSIL » ou « ia64 », spécifiant l’architecture de processeur pour un assembly qui contient du code spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="39821-117">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="39821-118">Les valeurs ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="39821-118">The values are not case-sensitive.</span></span> <span data-ttu-id="39821-119">Si une autre valeur est assignée à l’attribut, la totalité de l' `<assemblyIdentity>` élément est ignorée.</span><span class="sxs-lookup"><span data-stu-id="39821-119">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="39821-120">Consultez <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="39821-120">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="39821-121">processorArchitecture (attribut)</span><span class="sxs-lookup"><span data-stu-id="39821-121">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="39821-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="39821-122">Value</span></span>|<span data-ttu-id="39821-123">Description</span><span class="sxs-lookup"><span data-stu-id="39821-123">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="39821-124">Architecture AMD x86-64 uniquement.</span><span class="sxs-lookup"><span data-stu-id="39821-124">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="39821-125">Architecture Intel Itanium uniquement.</span><span class="sxs-lookup"><span data-stu-id="39821-125">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="39821-126">Neutre en ce qui concerne le processeur et les bits par mot.</span><span class="sxs-lookup"><span data-stu-id="39821-126">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="39821-127">Processeur x86 32 bits, natif ou dans l’environnement Windows sur Windows (WOW) sur une plateforme 64 bits.</span><span class="sxs-lookup"><span data-stu-id="39821-127">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39821-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="39821-128">Child Elements</span></span>  

 <span data-ttu-id="39821-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="39821-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39821-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="39821-130">Parent Elements</span></span>  
  
|<span data-ttu-id="39821-131">Élément</span><span class="sxs-lookup"><span data-stu-id="39821-131">Element</span></span>|<span data-ttu-id="39821-132">Description</span><span class="sxs-lookup"><span data-stu-id="39821-132">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="39821-133">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="39821-133">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="39821-134">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39821-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="39821-135">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="39821-135">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="39821-136">Utilisez un seul `<dependentAssembly>` élément pour chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="39821-136">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="39821-137">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="39821-137">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39821-138">Notes</span><span class="sxs-lookup"><span data-stu-id="39821-138">Remarks</span></span>  

 <span data-ttu-id="39821-139">Chaque **\<dependentAssembly>** élément doit avoir un **\<assemblyIdentity>** élément enfant.</span><span class="sxs-lookup"><span data-stu-id="39821-139">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="39821-140">Si l' `processorArchitecture` attribut est présent, l' `<assemblyIdentity>` élément s’applique uniquement à l’assembly avec l’architecture de processeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="39821-140">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="39821-141">Si l' `processorArchitecture` attribut n’est pas présent, l' `<assemblyIdentity>` élément peut s’appliquer à un assembly avec toute architecture de processeur.</span><span class="sxs-lookup"><span data-stu-id="39821-141">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="39821-142">L’exemple suivant montre un fichier de configuration pour deux assemblys portant le même nom et ciblant deux architectures à deux processeurs différentes, et dont les versions n’ont pas été conservées dans la synchronisation. Lorsque l’application s’exécute sur la plateforme x86, le premier `<assemblyIdentity>` élément s’applique et l’autre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="39821-142">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="39821-143">Si l’application s’exécute sur une plateforme autre que x86 ou ia64, les deux sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="39821-143">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="39821-144">Si un fichier de configuration contient un `<assemblyIdentity>` élément sans `processorArchitecture` attribut et qu’il ne contient pas d’élément qui correspond à la plateforme, l’élément sans l' `processorArchitecture` attribut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="39821-144">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39821-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="39821-145">Example</span></span>  

 <span data-ttu-id="39821-146">L’exemple suivant montre comment fournir des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="39821-146">The following example shows how to provide information about an assembly.</span></span>  
  
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
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39821-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39821-147">See also</span></span>

- [<span data-ttu-id="39821-148">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="39821-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="39821-149">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="39821-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="39821-150">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="39821-150">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
