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
ms.openlocfilehash: 815e1c26a328d986f91992a1e67e438a563ffea6
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663885"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="04f88-102">\<élément assemblyIdentity > pour \<le runtime ></span><span class="sxs-lookup"><span data-stu-id="04f88-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="04f88-103">Contient des informations d’identification sur l’assembly.</span><span class="sxs-lookup"><span data-stu-id="04f88-103">Contains identifying information about the assembly.</span></span>  
  
 <span data-ttu-id="04f88-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="04f88-104">\<configuration></span></span>  
<span data-ttu-id="04f88-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="04f88-105">\<runtime></span></span>  
<span data-ttu-id="04f88-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="04f88-106">\<assemblyBinding></span></span>  
<span data-ttu-id="04f88-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="04f88-107">\<dependentAssembly></span></span>  
<span data-ttu-id="04f88-108">\<assemblyIdentity></span><span class="sxs-lookup"><span data-stu-id="04f88-108">\<assemblyIdentity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f88-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04f88-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04f88-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="04f88-110">Attributes and Elements</span></span>  
 <span data-ttu-id="04f88-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="04f88-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04f88-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="04f88-112">Attributes</span></span>  
  
|<span data-ttu-id="04f88-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="04f88-113">Attribute</span></span>|<span data-ttu-id="04f88-114">Description</span><span class="sxs-lookup"><span data-stu-id="04f88-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="04f88-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="04f88-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="04f88-116">Nom de l’assembly</span><span class="sxs-lookup"><span data-stu-id="04f88-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="04f88-117">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="04f88-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="04f88-118">Chaîne qui spécifie la langue et le pays/la région de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="04f88-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="04f88-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="04f88-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="04f88-120">Valeur hexadécimale qui spécifie le nom fort de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="04f88-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="04f88-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="04f88-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="04f88-122">L’une des valeurs «x86», «amd64», «MSIL» ou «ia64», spécifiant l’architecture de processeur pour un assembly qui contient du code spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="04f88-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="04f88-123">Les valeurs ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="04f88-123">The values are not case-sensitive.</span></span> <span data-ttu-id="04f88-124">Si une autre valeur est assignée à l’attribut `<assemblyIdentity>` , la totalité de l’élément est ignorée.</span><span class="sxs-lookup"><span data-stu-id="04f88-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="04f88-125">Consultez <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="04f88-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="04f88-126">processorArchitecture (attribut)</span><span class="sxs-lookup"><span data-stu-id="04f88-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="04f88-127">`Value`</span><span class="sxs-lookup"><span data-stu-id="04f88-127">Value</span></span>|<span data-ttu-id="04f88-128">Description</span><span class="sxs-lookup"><span data-stu-id="04f88-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="04f88-129">Architecture AMD x86-64 uniquement.</span><span class="sxs-lookup"><span data-stu-id="04f88-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="04f88-130">Architecture Intel Itanium uniquement.</span><span class="sxs-lookup"><span data-stu-id="04f88-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="04f88-131">Neutre en ce qui concerne le processeur et les bits par mot.</span><span class="sxs-lookup"><span data-stu-id="04f88-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="04f88-132">Processeur x86 32 bits, natif ou dans l’environnement Windows sur Windows (WOW) sur une plateforme 64 bits.</span><span class="sxs-lookup"><span data-stu-id="04f88-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04f88-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="04f88-133">Child Elements</span></span>  
 <span data-ttu-id="04f88-134">Aucun.</span><span class="sxs-lookup"><span data-stu-id="04f88-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04f88-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="04f88-135">Parent Elements</span></span>  
  
|<span data-ttu-id="04f88-136">Élément</span><span class="sxs-lookup"><span data-stu-id="04f88-136">Element</span></span>|<span data-ttu-id="04f88-137">Description</span><span class="sxs-lookup"><span data-stu-id="04f88-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="04f88-138">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="04f88-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="04f88-139">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="04f88-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="04f88-140">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="04f88-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="04f88-141">Utilisez un `<dependentAssembly>` seul élément pour chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="04f88-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="04f88-142">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="04f88-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04f88-143">Notes</span><span class="sxs-lookup"><span data-stu-id="04f88-143">Remarks</span></span>  
 <span data-ttu-id="04f88-144">**Chaque\<élément de > dependentAssembly** doit avoir un  **\<élément enfant AssemblyIdentity >** .</span><span class="sxs-lookup"><span data-stu-id="04f88-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="04f88-145">Si l' `processorArchitecture` attribut est présent, l' `<assemblyIdentity>` élément s’applique uniquement à l’assembly avec l’architecture de processeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="04f88-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="04f88-146">Si l' `processorArchitecture` attribut n’est pas présent, `<assemblyIdentity>` l’élément peut s’appliquer à un assembly avec toute architecture de processeur.</span><span class="sxs-lookup"><span data-stu-id="04f88-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="04f88-147">L’exemple suivant montre un fichier de configuration pour deux assemblys portant le même nom et ciblant deux architectures à deux processeurs différentes, et dont les versions n’ont pas été conservées dans la synchronisation. Lorsque l’application s’exécute sur la plateforme x86, le `<assemblyIdentity>` premier élément s’applique et l’autre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="04f88-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="04f88-148">Si l’application s’exécute sur une plateforme autre que x86 ou ia64, les deux sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="04f88-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="04f88-149">Si un fichier de configuration contient `<assemblyIdentity>` un élément `processorArchitecture` sans attribut et qu’il ne contient pas d’élément qui correspond à la plateforme, l’élément `processorArchitecture` sans l’attribut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="04f88-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04f88-150">Exemples</span><span class="sxs-lookup"><span data-stu-id="04f88-150">Example</span></span>  
 <span data-ttu-id="04f88-151">L’exemple suivant montre comment fournir des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="04f88-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04f88-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04f88-152">See also</span></span>

- [<span data-ttu-id="04f88-153">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="04f88-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="04f88-154">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="04f88-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="04f88-155">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="04f88-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
