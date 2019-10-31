---
title: Élément <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 7ba52cdf0102af05954509a11fa90e9b8a337876
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118314"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="759b1-102">\<élément appDomainManagerAssembly ></span><span class="sxs-lookup"><span data-stu-id="759b1-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="759b1-103">Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.</span><span class="sxs-lookup"><span data-stu-id="759b1-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="759b1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="759b1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="759b1-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="759b1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="759b1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<AppDomainManagerAssembly** ></span><span class="sxs-lookup"><span data-stu-id="759b1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759b1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="759b1-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="759b1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="759b1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="759b1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="759b1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="759b1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="759b1-110">Attributes</span></span>  
  
|<span data-ttu-id="759b1-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="759b1-111">Attribute</span></span>|<span data-ttu-id="759b1-112">Description</span><span class="sxs-lookup"><span data-stu-id="759b1-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="759b1-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="759b1-113">Required attribute.</span></span> <span data-ttu-id="759b1-114">Spécifie le nom complet de l’assembly qui fournit le gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.</span><span class="sxs-lookup"><span data-stu-id="759b1-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="759b1-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="759b1-115">Child Elements</span></span>  
 <span data-ttu-id="759b1-116">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="759b1-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="759b1-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="759b1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="759b1-118">Élément</span><span class="sxs-lookup"><span data-stu-id="759b1-118">Element</span></span>|<span data-ttu-id="759b1-119">Description</span><span class="sxs-lookup"><span data-stu-id="759b1-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="759b1-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="759b1-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="759b1-121">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="759b1-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="759b1-122">Notes</span><span class="sxs-lookup"><span data-stu-id="759b1-122">Remarks</span></span>  
 <span data-ttu-id="759b1-123">Pour spécifier le type du gestionnaire de domaine d’application, vous devez spécifier cet élément et l’élément [\<appDomainManagerType >](appdomainmanagertype-element.md) .</span><span class="sxs-lookup"><span data-stu-id="759b1-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="759b1-124">Si l’un de ces éléments n’est pas spécifié, l’autre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="759b1-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="759b1-125">Quand le domaine d’application par défaut est chargé, <xref:System.TypeLoadException> est levée si l’assembly spécifié n’existe pas ou si l’assembly ne contient pas le type spécifié par l’élément [\<appDomainManagerType >](appdomainmanagertype-element.md) ; et le processus ne démarre pas.</span><span class="sxs-lookup"><span data-stu-id="759b1-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="759b1-126">Si l’assembly est trouvé, mais que les informations de version ne correspondent pas, une <xref:System.IO.FileLoadException> est levée.</span><span class="sxs-lookup"><span data-stu-id="759b1-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="759b1-127">Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine d’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="759b1-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="759b1-128">Utilisez les propriétés <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> et <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> pour spécifier un autre type de gestionnaire de domaine d’application pour un nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="759b1-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="759b1-129">Si vous spécifiez le type de gestionnaire de domaine d’application, l’application doit avoir une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="759b1-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="759b1-130">(Par exemple, une application qui s’exécute sur le bureau bénéficie d’une confiance totale.) Si l’application ne dispose pas d’une confiance totale, une <xref:System.TypeLoadException> est levée.</span><span class="sxs-lookup"><span data-stu-id="759b1-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="759b1-131">Pour connaître le format du nom complet de l’assembly, consultez la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="759b1-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="759b1-132">Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="759b1-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="759b1-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="759b1-133">Example</span></span>  
 <span data-ttu-id="759b1-134">L’exemple suivant montre comment spécifier que le gestionnaire de domaine d’application pour le domaine d’application par défaut d’un processus est le type de `MyMgr` dans l’assembly `AdMgrExample`.</span><span class="sxs-lookup"><span data-stu-id="759b1-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="759b1-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="759b1-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="759b1-136">\<élément appDomainManagerType ></span><span class="sxs-lookup"><span data-stu-id="759b1-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="759b1-137">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="759b1-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="759b1-138">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="759b1-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="759b1-139">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="759b1-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
