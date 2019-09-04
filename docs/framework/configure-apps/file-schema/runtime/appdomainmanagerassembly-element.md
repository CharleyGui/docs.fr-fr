---
title: Élément <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 083e3ba21dcd196eacfe3d9fd649c211da9dc125
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252848"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="5496f-102">\<appDomainManagerAssembly >, élément</span><span class="sxs-lookup"><span data-stu-id="5496f-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="5496f-103">Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.</span><span class="sxs-lookup"><span data-stu-id="5496f-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="5496f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5496f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5496f-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5496f-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5496f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerAssembly>**</span><span class="sxs-lookup"><span data-stu-id="5496f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5496f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5496f-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5496f-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5496f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5496f-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5496f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5496f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="5496f-110">Attributes</span></span>  
  
|<span data-ttu-id="5496f-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="5496f-111">Attribute</span></span>|<span data-ttu-id="5496f-112">Description</span><span class="sxs-lookup"><span data-stu-id="5496f-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="5496f-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="5496f-113">Required attribute.</span></span> <span data-ttu-id="5496f-114">Spécifie le nom complet de l’assembly qui fournit le gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5496f-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5496f-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5496f-115">Child Elements</span></span>  
 <span data-ttu-id="5496f-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5496f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5496f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5496f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5496f-118">Élément</span><span class="sxs-lookup"><span data-stu-id="5496f-118">Element</span></span>|<span data-ttu-id="5496f-119">Description</span><span class="sxs-lookup"><span data-stu-id="5496f-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5496f-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5496f-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5496f-121">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5496f-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5496f-122">Notes</span><span class="sxs-lookup"><span data-stu-id="5496f-122">Remarks</span></span>  
 <span data-ttu-id="5496f-123">Pour spécifier le type du gestionnaire de domaine d’application, vous devez spécifier cet élément et l' [ \<élément AppDomainManagerType >](appdomainmanagertype-element.md) .</span><span class="sxs-lookup"><span data-stu-id="5496f-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="5496f-124">Si l’un de ces éléments n’est pas spécifié, l’autre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="5496f-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="5496f-125">Quand le domaine d’application par défaut est <xref:System.TypeLoadException> chargé, est levé si l’assembly spécifié n’existe pas ou si l’assembly ne contient pas le type spécifié par l' [ \<élément AppDomainManagerType >](appdomainmanagertype-element.md) ; et si le processus échoue à activer.</span><span class="sxs-lookup"><span data-stu-id="5496f-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="5496f-126">Si l’assembly est trouvé, mais que les informations de version ne <xref:System.IO.FileLoadException> correspondent pas, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="5496f-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="5496f-127">Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine d’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="5496f-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="5496f-128">Utilisez les <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> propriétés <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> et pour spécifier un autre type de gestionnaire de domaine d’application pour un nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="5496f-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="5496f-129">Si vous spécifiez le type de gestionnaire de domaine d’application, l’application doit avoir une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="5496f-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="5496f-130">(Par exemple, une application qui s’exécute sur le bureau bénéficie d’une confiance totale.) Si l’application ne dispose pas d’une confiance totale <xref:System.TypeLoadException> , une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="5496f-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="5496f-131">Pour connaître le format du nom complet de l’assembly <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> , consultez la propriété.</span><span class="sxs-lookup"><span data-stu-id="5496f-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="5496f-132">Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="5496f-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5496f-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="5496f-133">Example</span></span>  
 <span data-ttu-id="5496f-134">L’exemple suivant montre comment spécifier que le gestionnaire de domaine d’application pour le domaine d’application par défaut d’un `MyMgr` processus est le `AdMgrExample` type dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="5496f-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5496f-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5496f-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5496f-136">\<appDomainManagerType >, élément</span><span class="sxs-lookup"><span data-stu-id="5496f-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="5496f-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="5496f-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5496f-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5496f-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5496f-139">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="5496f-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
