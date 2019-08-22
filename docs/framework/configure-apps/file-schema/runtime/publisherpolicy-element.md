---
title: Élément <publisherPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c8f8744d3ef1ca30eb05a4c8c3290d8a514714b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663510"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="30376-102">\<publisherPolicy >, élément</span><span class="sxs-lookup"><span data-stu-id="30376-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="30376-103">Spécifie si le runtime applique la stratégie de l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="30376-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="30376-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="30376-104">\<configuration></span></span>  
<span data-ttu-id="30376-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="30376-105">\<runtime></span></span>  
<span data-ttu-id="30376-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="30376-106">\<assemblyBinding></span></span>  
<span data-ttu-id="30376-107">\<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="30376-107">\<dependentAssembly></span></span>  
<span data-ttu-id="30376-108">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="30376-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30376-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30376-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30376-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="30376-110">Attributes and Elements</span></span>  
 <span data-ttu-id="30376-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="30376-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30376-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="30376-112">Attributes</span></span>  
  
|<span data-ttu-id="30376-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="30376-113">Attribute</span></span>|<span data-ttu-id="30376-114">Description</span><span class="sxs-lookup"><span data-stu-id="30376-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="30376-115">Spécifie s’il faut appliquer la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="30376-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="30376-116">appliquer l’attribut</span><span class="sxs-lookup"><span data-stu-id="30376-116">apply Attribute</span></span>  
  
|<span data-ttu-id="30376-117">`Value`</span><span class="sxs-lookup"><span data-stu-id="30376-117">Value</span></span>|<span data-ttu-id="30376-118">Description</span><span class="sxs-lookup"><span data-stu-id="30376-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="30376-119">Applique la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="30376-119">Applies publisher policy.</span></span> <span data-ttu-id="30376-120">Il s’agit du paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="30376-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="30376-121">N’applique pas la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="30376-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30376-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="30376-122">Child Elements</span></span>  
 <span data-ttu-id="30376-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="30376-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30376-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="30376-124">Parent Elements</span></span>  
  
|<span data-ttu-id="30376-125">Élément</span><span class="sxs-lookup"><span data-stu-id="30376-125">Element</span></span>|<span data-ttu-id="30376-126">Description</span><span class="sxs-lookup"><span data-stu-id="30376-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="30376-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30376-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="30376-128">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="30376-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30376-129">Notes</span><span class="sxs-lookup"><span data-stu-id="30376-129">Remarks</span></span>  
 <span data-ttu-id="30376-130">Lorsqu’un fournisseur de composant publie une nouvelle version d’un assembly, le fournisseur peut inclure une stratégie d’éditeur pour que les applications qui utilisent l’ancienne version utilisent désormais la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="30376-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="30376-131">Pour spécifier s’il faut appliquer la stratégie d’éditeur pour un assembly particulier, placez l'  **\<élément publisherPolicy >** dans l'  **\<élément de > dependentAssembly** .</span><span class="sxs-lookup"><span data-stu-id="30376-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="30376-132">La valeur par défaut de l’attribut **apply** est **Oui**.</span><span class="sxs-lookup"><span data-stu-id="30376-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="30376-133">La définition de l’attribut **apply** sur **no** remplace tous les paramètres **Yes** précédents d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="30376-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="30376-134">Une autorisation est requise pour qu’une application ignore explicitement la stratégie de l’éditeur à l’aide de l' [ \<élément publisherPolicy Apply = "no"/>](publisherpolicy-element.md) dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="30376-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="30376-135">L’autorisation est accordée en définissant <xref:System.Security.Permissions.SecurityPermissionFlag> l’indicateur <xref:System.Security.Permissions.SecurityPermission>sur.</span><span class="sxs-lookup"><span data-stu-id="30376-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="30376-136">Pour plus d’informations, consultez [autorisation de sécurité pour la redirection des liaisons](../../assembly-binding-redirection-security-permission.md)d’assembly.</span><span class="sxs-lookup"><span data-stu-id="30376-136">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30376-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="30376-137">Example</span></span>  
 <span data-ttu-id="30376-138">L’exemple suivant désactive la stratégie d’éditeur pour l’assembly, `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="30376-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30376-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30376-139">See also</span></span>

- [<span data-ttu-id="30376-140">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="30376-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="30376-141">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="30376-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="30376-142">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="30376-142">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="30376-143">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="30376-143">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
