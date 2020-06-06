---
title: Élément <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154422"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="16a5f-102">Élément \<appDomainManagerAssembly></span><span class="sxs-lookup"><span data-stu-id="16a5f-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="16a5f-103">Spécifie l’assembly qui fournit le Gestionnaire du domaine d’application par défaut du processus.</span><span class="sxs-lookup"><span data-stu-id="16a5f-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="16a5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16a5f-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16a5f-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="16a5f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="16a5f-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="16a5f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16a5f-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="16a5f-107">Attributes</span></span>  
  
|<span data-ttu-id="16a5f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="16a5f-108">Attribute</span></span>|<span data-ttu-id="16a5f-109">Description</span><span class="sxs-lookup"><span data-stu-id="16a5f-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="16a5f-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="16a5f-110">Required attribute.</span></span> <span data-ttu-id="16a5f-111">Spécifie le nom complet de l’assembly qui fournit le gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.</span><span class="sxs-lookup"><span data-stu-id="16a5f-111">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16a5f-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="16a5f-112">Child Elements</span></span>  
 <span data-ttu-id="16a5f-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="16a5f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16a5f-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="16a5f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="16a5f-115">Élément</span><span class="sxs-lookup"><span data-stu-id="16a5f-115">Element</span></span>|<span data-ttu-id="16a5f-116">Description</span><span class="sxs-lookup"><span data-stu-id="16a5f-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16a5f-117">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16a5f-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16a5f-118">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="16a5f-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16a5f-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="16a5f-119">Remarks</span></span>  
 <span data-ttu-id="16a5f-120">Pour spécifier le type du gestionnaire de domaine d’application, vous devez spécifier à la fois cet élément et l' [\<appDomainManagerType>](appdomainmanagertype-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="16a5f-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="16a5f-121">Si l’un de ces éléments n’est pas spécifié, l’autre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="16a5f-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="16a5f-122">Quand le domaine d’application par défaut est chargé, <xref:System.TypeLoadException> est levé si l’assembly spécifié n’existe pas ou si l’assembly ne contient pas le type spécifié par l' [\<appDomainManagerType>](appdomainmanagertype-element.md) élément et que le processus ne peut pas démarrer.</span><span class="sxs-lookup"><span data-stu-id="16a5f-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="16a5f-123">Si l’assembly est trouvé, mais que les informations de version ne correspondent pas, une <xref:System.IO.FileLoadException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="16a5f-123">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="16a5f-124">Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine d’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="16a5f-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="16a5f-125">Utilisez les <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Propriétés et pour spécifier un autre type de gestionnaire de domaine d’application pour un nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="16a5f-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="16a5f-126">Si vous spécifiez le type de gestionnaire de domaine d’application, l’application doit avoir une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="16a5f-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="16a5f-127">(Par exemple, une application qui s’exécute sur le bureau bénéficie d’une confiance totale.) Si l’application ne dispose pas d’une confiance totale, une <xref:System.TypeLoadException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="16a5f-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="16a5f-128">Pour connaître le format du nom complet de l’assembly, consultez la <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="16a5f-128">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="16a5f-129">Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="16a5f-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16a5f-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="16a5f-130">Example</span></span>  
 <span data-ttu-id="16a5f-131">L’exemple suivant montre comment spécifier que le gestionnaire de domaine d’application pour le domaine d’application par défaut d’un processus est le `MyMgr` type dans l' `AdMgrExample` assembly.</span><span class="sxs-lookup"><span data-stu-id="16a5f-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16a5f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16a5f-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="16a5f-133">\<appDomainManagerType>Appartient</span><span class="sxs-lookup"><span data-stu-id="16a5f-133">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="16a5f-134">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="16a5f-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16a5f-135">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="16a5f-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="16a5f-136">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="16a5f-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
