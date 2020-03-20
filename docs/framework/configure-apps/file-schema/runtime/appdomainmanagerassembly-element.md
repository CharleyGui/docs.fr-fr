---
title: Élément <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154422"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="44aed-102">\<appDomainManagerAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="44aed-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="44aed-103">Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.</span><span class="sxs-lookup"><span data-stu-id="44aed-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="44aed-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="44aed-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="44aed-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="44aed-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="44aed-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span><span class="sxs-lookup"><span data-stu-id="44aed-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44aed-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44aed-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44aed-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="44aed-108">Attributes and Elements</span></span>  
 <span data-ttu-id="44aed-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="44aed-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44aed-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="44aed-110">Attributes</span></span>  
  
|<span data-ttu-id="44aed-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="44aed-111">Attribute</span></span>|<span data-ttu-id="44aed-112">Description</span><span class="sxs-lookup"><span data-stu-id="44aed-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="44aed-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="44aed-113">Required attribute.</span></span> <span data-ttu-id="44aed-114">Spécifie le nom d’affichage de l’assemblage qui fournit au gestionnaire de domaine d’application le domaine de l’application par défaut dans le processus.</span><span class="sxs-lookup"><span data-stu-id="44aed-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44aed-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="44aed-115">Child Elements</span></span>  
 <span data-ttu-id="44aed-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="44aed-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44aed-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="44aed-117">Parent Elements</span></span>  
  
|<span data-ttu-id="44aed-118">Élément</span><span class="sxs-lookup"><span data-stu-id="44aed-118">Element</span></span>|<span data-ttu-id="44aed-119">Description</span><span class="sxs-lookup"><span data-stu-id="44aed-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="44aed-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44aed-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="44aed-121">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="44aed-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44aed-122">Notes </span><span class="sxs-lookup"><span data-stu-id="44aed-122">Remarks</span></span>  
 <span data-ttu-id="44aed-123">Pour spécifier le type de gestionnaire de domaine d’application, vous devez spécifier à la fois cet élément et [ \<l’élément appDomainManagerType>.](appdomainmanagertype-element.md)</span><span class="sxs-lookup"><span data-stu-id="44aed-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="44aed-124">Si l’un ou l’autre de ces éléments n’est pas spécifié, l’autre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="44aed-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="44aed-125">Lorsque le domaine d’application par défaut est chargé, <xref:System.TypeLoadException> est lancé si l’assemblage spécifié n’existe pas ou si l’assemblage ne contient pas le type spécifié par [ \<l’appDomainManagerType>](appdomainmanagertype-element.md) élément; et le processus ne démarre pas.</span><span class="sxs-lookup"><span data-stu-id="44aed-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="44aed-126">Si l’assemblage est trouvé mais que <xref:System.IO.FileLoadException> l’information de la version ne correspond pas, a est lancée.</span><span class="sxs-lookup"><span data-stu-id="44aed-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="44aed-127">Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine de l’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="44aed-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="44aed-128">Utilisez <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> les <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriétés et les propriétés pour spécifier un type de gestionnaire de domaine d’application différent pour un nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="44aed-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="44aed-129">Spécifier le type de gestionnaire de domaine d’application nécessite que l’application ait une pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="44aed-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="44aed-130">(Par exemple, une application fonctionnant sur le bureau a une confiance totale.) Si l’application n’a <xref:System.TypeLoadException> pas la pleine confiance, a est lancée.</span><span class="sxs-lookup"><span data-stu-id="44aed-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="44aed-131">Pour le format du nom d’affichage de l’assemblage, voir la <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="44aed-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="44aed-132">Cet élément de configuration n’est disponible que dans le cadre .NET 4 et plus tard.</span><span class="sxs-lookup"><span data-stu-id="44aed-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44aed-133"> Exemple</span><span class="sxs-lookup"><span data-stu-id="44aed-133">Example</span></span>  
 <span data-ttu-id="44aed-134">L’exemple suivant montre comment spécifier que le gestionnaire de `MyMgr` domaine `AdMgrExample` d’application pour le domaine d’application par défaut d’un processus est le type dans l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="44aed-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44aed-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44aed-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="44aed-136">\<appDomainManagerType> Element</span><span class="sxs-lookup"><span data-stu-id="44aed-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="44aed-137">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="44aed-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="44aed-138">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="44aed-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="44aed-139">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="44aed-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
