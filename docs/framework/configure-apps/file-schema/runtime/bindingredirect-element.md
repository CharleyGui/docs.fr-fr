---
title: Élément <bindingRedirect>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154294"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="47fbc-102">Élément \<bindingRedirect></span><span class="sxs-lookup"><span data-stu-id="47fbc-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="47fbc-103">Redirige une version d'assembly vers une autre.</span><span class="sxs-lookup"><span data-stu-id="47fbc-103">Redirects one assembly version to another.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**  
  
## <a name="syntax"></a><span data-ttu-id="47fbc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47fbc-104">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47fbc-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="47fbc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="47fbc-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="47fbc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47fbc-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="47fbc-107">Attributes</span></span>  
  
|<span data-ttu-id="47fbc-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="47fbc-108">Attribute</span></span>|<span data-ttu-id="47fbc-109">Description</span><span class="sxs-lookup"><span data-stu-id="47fbc-109">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="47fbc-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="47fbc-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="47fbc-111">Spécifie la version de l'assembly demandée initialement.</span><span class="sxs-lookup"><span data-stu-id="47fbc-111">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="47fbc-112">Le format d’un numéro de version d’assembly est *major. minor. Build. Revision*.</span><span class="sxs-lookup"><span data-stu-id="47fbc-112">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="47fbc-113">Les valeurs valides pour chaque partie de ce numéro de version vont de 0 à 65535.</span><span class="sxs-lookup"><span data-stu-id="47fbc-113">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="47fbc-114">Vous pouvez également spécifier une plage de versions en respectant le format suivant :</span><span class="sxs-lookup"><span data-stu-id="47fbc-114">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="47fbc-115">*n. n. n. n-n. n. n*</span><span class="sxs-lookup"><span data-stu-id="47fbc-115">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="47fbc-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="47fbc-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="47fbc-117">Spécifie la version de l’assembly à utiliser à la place de la version initialement demandée au format : *n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="47fbc-117">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="47fbc-118">Cette valeur peut spécifier une version antérieure à `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="47fbc-118">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47fbc-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="47fbc-119">Child Elements</span></span>  
  
|<span data-ttu-id="47fbc-120">Élément</span><span class="sxs-lookup"><span data-stu-id="47fbc-120">Element</span></span>|<span data-ttu-id="47fbc-121">Description</span><span class="sxs-lookup"><span data-stu-id="47fbc-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47fbc-122">None</span><span class="sxs-lookup"><span data-stu-id="47fbc-122">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="47fbc-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="47fbc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="47fbc-124">Élément</span><span class="sxs-lookup"><span data-stu-id="47fbc-124">Element</span></span>|<span data-ttu-id="47fbc-125">Description</span><span class="sxs-lookup"><span data-stu-id="47fbc-125">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="47fbc-126">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="47fbc-126">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="47fbc-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47fbc-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="47fbc-128">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="47fbc-128">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="47fbc-129">Utilisez un élément dependentAssembly pour chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="47fbc-129">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="47fbc-130">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="47fbc-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47fbc-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="47fbc-131">Remarks</span></span>  
 <span data-ttu-id="47fbc-132">Lorsque vous générez une application .NET Framework basée sur un assembly avec nom fort, l'application utilise par défaut cette version de l'assembly au moment de l'exécution, même si une nouvelle version est disponible.</span><span class="sxs-lookup"><span data-stu-id="47fbc-132">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="47fbc-133">Vous pouvez toutefois configurer l'application pour faire en sorte qu'elle s'exécute en utilisant une version plus récente de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="47fbc-133">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="47fbc-134">Pour plus d’informations sur la façon dont le runtime utilise ces fichiers pour déterminer la version de l’assembly à utiliser, consultez [la manière dont le runtime localise les assemblys](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="47fbc-134">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="47fbc-135">Vous pouvez rediriger plusieurs versions d'assembly en incluant plusieurs éléments `bindingRedirect` dans un élément `dependentAssembly`.</span><span class="sxs-lookup"><span data-stu-id="47fbc-135">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="47fbc-136">Vous pouvez également rediriger une version plus récente vers une version antérieure de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="47fbc-136">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="47fbc-137">La redirection de liaison d’assembly explicite dans un fichier de configuration de l’application nécessite une autorisation de sécurité.</span><span class="sxs-lookup"><span data-stu-id="47fbc-137">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="47fbc-138">Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers.</span><span class="sxs-lookup"><span data-stu-id="47fbc-138">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="47fbc-139">L’autorisation est accordée en définissant l' <xref:System.Security.Permissions.SecurityPermissionFlag> indicateur sur <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="47fbc-139">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="47fbc-140">Pour plus d’informations, consultez [autorisation de sécurité pour la redirection des liaisons d’assembly](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="47fbc-140">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="47fbc-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="47fbc-141">Example</span></span>  
 <span data-ttu-id="47fbc-142">L'exemple suivant montre comment rediriger une version d'assembly vers une autre.</span><span class="sxs-lookup"><span data-stu-id="47fbc-142">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47fbc-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47fbc-143">See also</span></span>

- [<span data-ttu-id="47fbc-144">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="47fbc-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="47fbc-145">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="47fbc-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="47fbc-146">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="47fbc-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
