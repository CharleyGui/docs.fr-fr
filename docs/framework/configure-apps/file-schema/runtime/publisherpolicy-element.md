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
ms.openlocfilehash: cc206e584440778858e61fc0bab51fc8ffa2009a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252377"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="38190-102">\<publisherPolicy >, élément</span><span class="sxs-lookup"><span data-stu-id="38190-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="38190-103">Spécifie si le runtime applique la stratégie de l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="38190-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
<span data-ttu-id="38190-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38190-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38190-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="38190-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="38190-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="38190-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="38190-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="38190-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="38190-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<publisherPolicy >**</span><span class="sxs-lookup"><span data-stu-id="38190-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38190-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38190-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38190-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="38190-110">Attributes and Elements</span></span>  
 <span data-ttu-id="38190-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="38190-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38190-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="38190-112">Attributes</span></span>  
  
|<span data-ttu-id="38190-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="38190-113">Attribute</span></span>|<span data-ttu-id="38190-114">Description</span><span class="sxs-lookup"><span data-stu-id="38190-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="38190-115">Spécifie s’il faut appliquer la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="38190-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="38190-116">appliquer l’attribut</span><span class="sxs-lookup"><span data-stu-id="38190-116">apply Attribute</span></span>  
  
|<span data-ttu-id="38190-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="38190-117">Value</span></span>|<span data-ttu-id="38190-118">Description</span><span class="sxs-lookup"><span data-stu-id="38190-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="38190-119">Applique la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="38190-119">Applies publisher policy.</span></span> <span data-ttu-id="38190-120">Il s’agit du paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="38190-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="38190-121">N’applique pas la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="38190-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38190-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38190-122">Child Elements</span></span>  

<span data-ttu-id="38190-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="38190-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38190-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38190-124">Parent Elements</span></span>  
  
|<span data-ttu-id="38190-125">Élément</span><span class="sxs-lookup"><span data-stu-id="38190-125">Element</span></span>|<span data-ttu-id="38190-126">Description</span><span class="sxs-lookup"><span data-stu-id="38190-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="38190-127">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="38190-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="38190-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38190-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="38190-129">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="38190-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="38190-130">Utilisez un `<dependentAssembly>` seul élément pour chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="38190-130">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="38190-131">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="38190-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38190-132">Notes</span><span class="sxs-lookup"><span data-stu-id="38190-132">Remarks</span></span>  
 <span data-ttu-id="38190-133">Lorsqu’un fournisseur de composant publie une nouvelle version d’un assembly, le fournisseur peut inclure une stratégie d’éditeur pour que les applications qui utilisent l’ancienne version utilisent désormais la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="38190-133">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="38190-134">Pour spécifier s’il faut appliquer la stratégie d’éditeur pour un assembly particulier, placez l'  **\<élément publisherPolicy >** dans l'  **\<élément de > dependentAssembly** .</span><span class="sxs-lookup"><span data-stu-id="38190-134">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="38190-135">La valeur par défaut de l’attribut **apply** est **Oui**.</span><span class="sxs-lookup"><span data-stu-id="38190-135">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="38190-136">La définition de l’attribut **apply** sur **no** remplace tous les paramètres **Yes** précédents d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="38190-136">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="38190-137">Une autorisation est requise pour qu’une application ignore explicitement la stratégie de l’éditeur à l’aide de l' [ \<élément publisherPolicy Apply = "no"/>](publisherpolicy-element.md) dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="38190-137">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="38190-138">L’autorisation est accordée en définissant <xref:System.Security.Permissions.SecurityPermissionFlag> l’indicateur <xref:System.Security.Permissions.SecurityPermission>sur.</span><span class="sxs-lookup"><span data-stu-id="38190-138">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="38190-139">Pour plus d’informations, consultez [autorisation de sécurité pour la redirection des liaisons d’assembly](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="38190-139">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38190-140">Exemples</span><span class="sxs-lookup"><span data-stu-id="38190-140">Example</span></span>  
 <span data-ttu-id="38190-141">L’exemple suivant désactive la stratégie d’éditeur pour l’assembly, `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="38190-141">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38190-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38190-142">See also</span></span>

- [<span data-ttu-id="38190-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="38190-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="38190-144">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="38190-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="38190-145">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="38190-145">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="38190-146">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="38190-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
