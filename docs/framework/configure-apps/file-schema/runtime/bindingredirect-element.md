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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154294"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="0fd1f-102">\<bindingRedirect> Element</span><span class="sxs-lookup"><span data-stu-id="0fd1f-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="0fd1f-103">Redirige une version d'assembly vers une autre.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-103">Redirects one assembly version to another.</span></span>  
  
<span data-ttu-id="0fd1f-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0fd1f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0fd1f-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0fd1f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="0fd1f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblageBinding>**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="0fd1f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="0fd1f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dépendantAssembly>**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="0fd1f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="0fd1f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**</span><span class="sxs-lookup"><span data-stu-id="0fd1f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd1f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fd1f-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fd1f-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0fd1f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0fd1f-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fd1f-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="0fd1f-112">Attributes</span></span>  
  
|<span data-ttu-id="0fd1f-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="0fd1f-113">Attribute</span></span>|<span data-ttu-id="0fd1f-114">Description</span><span class="sxs-lookup"><span data-stu-id="0fd1f-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="0fd1f-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="0fd1f-116">Spécifie la version de l'assembly demandée initialement.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="0fd1f-117">Le format d’un numéro de version d’assemblage est *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="0fd1f-118">Les valeurs valides pour chaque partie de ce numéro de version vont de 0 à 65535.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="0fd1f-119">Vous pouvez également spécifier une plage de versions en respectant le format suivant :</span><span class="sxs-lookup"><span data-stu-id="0fd1f-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="0fd1f-120">*n.n.n.n - n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="0fd1f-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="0fd1f-121">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="0fd1f-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="0fd1f-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="0fd1f-123">Cette valeur peut spécifier une version antérieure à `oldVersion`.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fd1f-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0fd1f-124">Child Elements</span></span>  
  
|<span data-ttu-id="0fd1f-125">Élément</span><span class="sxs-lookup"><span data-stu-id="0fd1f-125">Element</span></span>|<span data-ttu-id="0fd1f-126">Description</span><span class="sxs-lookup"><span data-stu-id="0fd1f-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fd1f-127">None</span><span class="sxs-lookup"><span data-stu-id="0fd1f-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="0fd1f-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0fd1f-128">Parent Elements</span></span>  
  
|<span data-ttu-id="0fd1f-129">Élément</span><span class="sxs-lookup"><span data-stu-id="0fd1f-129">Element</span></span>|<span data-ttu-id="0fd1f-130">Description</span><span class="sxs-lookup"><span data-stu-id="0fd1f-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="0fd1f-131">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="0fd1f-132">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="0fd1f-133">Encapsule la stratégie de liaisons et l’emplacement de chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="0fd1f-134">Utilisez un élément dependentAssembly pour chaque assembly.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="0fd1f-135">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fd1f-136">Notes </span><span class="sxs-lookup"><span data-stu-id="0fd1f-136">Remarks</span></span>  
 <span data-ttu-id="0fd1f-137">Lorsque vous générez une application .NET Framework basée sur un assembly avec nom fort, l'application utilise par défaut cette version de l'assembly au moment de l'exécution, même si une nouvelle version est disponible.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="0fd1f-138">Vous pouvez toutefois configurer l'application pour faire en sorte qu'elle s'exécute en utilisant une version plus récente de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="0fd1f-139">Pour plus de détails sur la façon dont le temps d’exécution utilise ces fichiers pour déterminer quelle version d’assemblage utiliser, voir [Comment les assemblages De localisation de runtime](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="0fd1f-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="0fd1f-140">Vous pouvez rediriger plusieurs versions d'assembly en incluant plusieurs éléments `bindingRedirect` dans un élément `dependentAssembly`.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="0fd1f-141">Vous pouvez également rediriger une version plus récente vers une version antérieure de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="0fd1f-142">La redirection de liaison d’assembly explicite dans un fichier de configuration de l’application nécessite une autorisation de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="0fd1f-143">Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="0fd1f-144">La permission est accordée <xref:System.Security.Permissions.SecurityPermissionFlag> en <xref:System.Security.Permissions.SecurityPermission>fixant le drapeau sur le .</span><span class="sxs-lookup"><span data-stu-id="0fd1f-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="0fd1f-145">Pour plus d’informations, voir [l’autorisation de sécurité de réorientation contraignante de l’Assemblée](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="0fd1f-145">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fd1f-146"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0fd1f-146">Example</span></span>  
 <span data-ttu-id="0fd1f-147">L'exemple suivant montre comment rediriger une version d'assembly vers une autre.</span><span class="sxs-lookup"><span data-stu-id="0fd1f-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0fd1f-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fd1f-148">See also</span></span>

- [<span data-ttu-id="0fd1f-149">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="0fd1f-149">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0fd1f-150">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="0fd1f-150">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0fd1f-151">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="0fd1f-151">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
