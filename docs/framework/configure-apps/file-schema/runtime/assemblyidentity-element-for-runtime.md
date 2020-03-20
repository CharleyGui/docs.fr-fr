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
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154307"
---
# <a name="assemblyidentity-element-for-runtime"></a><span data-ttu-id="642fb-102">\<assemblageIdentity> Element pour \<les> de temps d’exécution</span><span class="sxs-lookup"><span data-stu-id="642fb-102">\<assemblyIdentity> Element for \<runtime></span></span>
<span data-ttu-id="642fb-103">Contient des informations d’identification sur l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="642fb-103">Contains identifying information about the assembly.</span></span>  
  
<span data-ttu-id="642fb-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="642fb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="642fb-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="642fb-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="642fb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblageBinding>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="642fb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="642fb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dépendantAssembly>**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="642fb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="642fb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblageIdentity>**</span><span class="sxs-lookup"><span data-stu-id="642fb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="642fb-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="642fb-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="642fb-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="642fb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="642fb-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="642fb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="642fb-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="642fb-112">Attributes</span></span>  
  
|<span data-ttu-id="642fb-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="642fb-113">Attribute</span></span>|<span data-ttu-id="642fb-114">Description</span><span class="sxs-lookup"><span data-stu-id="642fb-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="642fb-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="642fb-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="642fb-116">Le nom de l’assemblée</span><span class="sxs-lookup"><span data-stu-id="642fb-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="642fb-117">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="642fb-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="642fb-118">Une chaîne qui spécifie la langue et le pays/région de l’assemblée.</span><span class="sxs-lookup"><span data-stu-id="642fb-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="642fb-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="642fb-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="642fb-120">Une valeur hexadecimale qui spécifie le nom fort de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="642fb-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="642fb-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="642fb-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="642fb-122">L’une des valeurs "x86", "amd64", "msil", ou "ia64", précisant l’architecture du processeur pour un assemblage contenant du code spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="642fb-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="642fb-123">Les valeurs ne sont pas sensibles aux cas.</span><span class="sxs-lookup"><span data-stu-id="642fb-123">The values are not case-sensitive.</span></span> <span data-ttu-id="642fb-124">Si l’attribut est attribué à `<assemblyIdentity>` toute autre valeur, l’élément entier est ignoré.</span><span class="sxs-lookup"><span data-stu-id="642fb-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="642fb-125">Consultez <xref:System.Reflection.ProcessorArchitecture>.</span><span class="sxs-lookup"><span data-stu-id="642fb-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="642fb-126">processeurArchitecture Attribut</span><span class="sxs-lookup"><span data-stu-id="642fb-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="642fb-127">Valeur</span><span class="sxs-lookup"><span data-stu-id="642fb-127">Value</span></span>|<span data-ttu-id="642fb-128">Description</span><span class="sxs-lookup"><span data-stu-id="642fb-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="642fb-129">ARCHITECTURE AMD x86-64 seulement.</span><span class="sxs-lookup"><span data-stu-id="642fb-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="642fb-130">Intel Itanium architecture seulement.</span><span class="sxs-lookup"><span data-stu-id="642fb-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="642fb-131">Neutre en ce qui concerne le processeur et les bits par mot.</span><span class="sxs-lookup"><span data-stu-id="642fb-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="642fb-132">Un processeur x86 32 bits, natif ou dans l’environnement Windows on Windows (WOW) sur une plate-forme 64 bits.</span><span class="sxs-lookup"><span data-stu-id="642fb-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="642fb-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="642fb-133">Child Elements</span></span>  
 <span data-ttu-id="642fb-134">Aucun.</span><span class="sxs-lookup"><span data-stu-id="642fb-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="642fb-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="642fb-135">Parent Elements</span></span>  
  
|<span data-ttu-id="642fb-136">Élément</span><span class="sxs-lookup"><span data-stu-id="642fb-136">Element</span></span>|<span data-ttu-id="642fb-137">Description</span><span class="sxs-lookup"><span data-stu-id="642fb-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="642fb-138">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="642fb-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="642fb-139">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="642fb-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="642fb-140">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="642fb-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="642fb-141">Utilisez `<dependentAssembly>` un élément pour chaque assemblage.</span><span class="sxs-lookup"><span data-stu-id="642fb-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="642fb-142">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="642fb-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="642fb-143">Notes </span><span class="sxs-lookup"><span data-stu-id="642fb-143">Remarks</span></span>  
 <span data-ttu-id="642fb-144">Chaque \*\* \<élément>dépendant\*\* doit avoir une \*\* \<assembléeIdentity>\*\* élément enfant.</span><span class="sxs-lookup"><span data-stu-id="642fb-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="642fb-145">Si `processorArchitecture` l’attribut est `<assemblyIdentity>` présent, l’élément ne s’applique qu’à l’assemblage avec l’architecture correspondante du processeur.</span><span class="sxs-lookup"><span data-stu-id="642fb-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="642fb-146">Si `processorArchitecture` l’attribut n’est pas présent, l’élément `<assemblyIdentity>` peut s’appliquer à un assemblage avec n’importe quelle architecture de processeur.</span><span class="sxs-lookup"><span data-stu-id="642fb-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="642fb-147">L’exemple suivant montre un fichier de configuration pour deux assemblages du même nom qui ciblent deux architectures de processeur différentes, et dont les versions n’ont pas été maintenues en synchronisation. Lorsque l’application s’exécute sur la `<assemblyIdentity>` plate-forme x86, le premier élément s’applique et l’autre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="642fb-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="642fb-148">Si l’application s’exécute sur une plate-forme autre que x86 ou ia64, les deux sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="642fb-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
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
  
 <span data-ttu-id="642fb-149">Si un fichier `<assemblyIdentity>` de configuration `processorArchitecture` contient un élément sans attribut et ne contient `processorArchitecture` pas d’élément qui correspond à la plate-forme, l’élément sans l’attribut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="642fb-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="642fb-150"> Exemple</span><span class="sxs-lookup"><span data-stu-id="642fb-150">Example</span></span>  
 <span data-ttu-id="642fb-151">L’exemple suivant montre comment fournir des informations sur une assemblée.</span><span class="sxs-lookup"><span data-stu-id="642fb-151">The following example shows how to provide information about an assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="642fb-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="642fb-152">See also</span></span>

- [<span data-ttu-id="642fb-153">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="642fb-153">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="642fb-154">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="642fb-154">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="642fb-155">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="642fb-155">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
