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
ms.openlocfilehash: 89fa8a991cc7d0352eb0a13cdfd3a6063ea468e7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115849"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="870a5-102">Élément \<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="870a5-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="870a5-103">Spécifie si le runtime applique la stratégie de l'éditeur.</span><span class="sxs-lookup"><span data-stu-id="870a5-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="870a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="870a5-104">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="870a5-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="870a5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="870a5-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="870a5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="870a5-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="870a5-107">Attributes</span></span>  
  
|<span data-ttu-id="870a5-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="870a5-108">Attribute</span></span>|<span data-ttu-id="870a5-109">Description</span><span class="sxs-lookup"><span data-stu-id="870a5-109">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="870a5-110">Spécifie s’il faut appliquer la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="870a5-110">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="870a5-111">appliquer l’attribut</span><span class="sxs-lookup"><span data-stu-id="870a5-111">apply Attribute</span></span>  
  
|<span data-ttu-id="870a5-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="870a5-112">Value</span></span>|<span data-ttu-id="870a5-113">Description</span><span class="sxs-lookup"><span data-stu-id="870a5-113">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="870a5-114">Applique la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="870a5-114">Applies publisher policy.</span></span> <span data-ttu-id="870a5-115">Il s'agit du paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="870a5-115">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="870a5-116">N’applique pas la stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="870a5-116">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="870a5-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="870a5-117">Child Elements</span></span>  

<span data-ttu-id="870a5-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="870a5-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="870a5-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="870a5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="870a5-120">Élément</span><span class="sxs-lookup"><span data-stu-id="870a5-120">Element</span></span>|<span data-ttu-id="870a5-121">Description</span><span class="sxs-lookup"><span data-stu-id="870a5-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="870a5-122">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="870a5-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="870a5-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="870a5-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="870a5-124">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="870a5-124">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="870a5-125">Utilisez un seul `<dependentAssembly>` élément pour chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="870a5-125">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="870a5-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="870a5-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="870a5-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="870a5-127">Remarks</span></span>  
 <span data-ttu-id="870a5-128">Lorsqu’un fournisseur de composant publie une nouvelle version d’un assembly, le fournisseur peut inclure une stratégie d’éditeur pour que les applications qui utilisent l’ancienne version utilisent désormais la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="870a5-128">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="870a5-129">Pour spécifier s’il faut appliquer la stratégie d’éditeur pour un assembly particulier, placez l' **\<publisherPolicy>** élément dans l' **\<dependentAssembly>** élément.</span><span class="sxs-lookup"><span data-stu-id="870a5-129">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="870a5-130">La valeur par défaut de l’attribut **apply** est **Oui**.</span><span class="sxs-lookup"><span data-stu-id="870a5-130">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="870a5-131">La définition de l’attribut **apply** sur **no** remplace tous les paramètres **Yes** précédents d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="870a5-131">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="870a5-132">Une autorisation est requise pour qu’une application ignore explicitement la stratégie de l’éditeur à l’aide [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) de l’élément dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="870a5-132">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="870a5-133">L’autorisation est accordée en définissant l' <xref:System.Security.Permissions.SecurityPermissionFlag> indicateur sur <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="870a5-133">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="870a5-134">Pour plus d’informations, consultez [autorisation de sécurité pour la redirection des liaisons d’assembly](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="870a5-134">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="870a5-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="870a5-135">Example</span></span>  
 <span data-ttu-id="870a5-136">L’exemple suivant désactive la stratégie d’éditeur pour l’assembly, `myAssembly` .</span><span class="sxs-lookup"><span data-stu-id="870a5-136">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="870a5-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="870a5-137">See also</span></span>

- [<span data-ttu-id="870a5-138">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="870a5-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="870a5-139">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="870a5-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="870a5-140">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="870a5-140">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="870a5-141">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="870a5-141">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
