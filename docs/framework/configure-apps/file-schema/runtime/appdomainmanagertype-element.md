---
title: Élément <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ffb297cc38f20917e720b216607e9ccfc966866
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252832"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="35fa2-102">\<appDomainManagerType >, élément</span><span class="sxs-lookup"><span data-stu-id="35fa2-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="35fa2-103">Spécifie le type qui sert de Gestionnaire de domaine d’application au domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="35fa2-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
<span data-ttu-id="35fa2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="35fa2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="35fa2-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="35fa2-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="35fa2-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerType>**</span><span class="sxs-lookup"><span data-stu-id="35fa2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35fa2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35fa2-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35fa2-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="35fa2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="35fa2-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="35fa2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35fa2-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="35fa2-110">Attributes</span></span>  
  
|<span data-ttu-id="35fa2-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="35fa2-111">Attribute</span></span>|<span data-ttu-id="35fa2-112">Description</span><span class="sxs-lookup"><span data-stu-id="35fa2-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="35fa2-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="35fa2-113">Required attribute.</span></span> <span data-ttu-id="35fa2-114">Spécifie le nom du type, y compris l’espace de noms, qui sert de gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.</span><span class="sxs-lookup"><span data-stu-id="35fa2-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35fa2-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="35fa2-115">Child Elements</span></span>  
 <span data-ttu-id="35fa2-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="35fa2-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35fa2-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="35fa2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="35fa2-118">Élément</span><span class="sxs-lookup"><span data-stu-id="35fa2-118">Element</span></span>|<span data-ttu-id="35fa2-119">Description</span><span class="sxs-lookup"><span data-stu-id="35fa2-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="35fa2-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="35fa2-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="35fa2-121">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="35fa2-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35fa2-122">Notes</span><span class="sxs-lookup"><span data-stu-id="35fa2-122">Remarks</span></span>  
 <span data-ttu-id="35fa2-123">Pour spécifier le type du gestionnaire de domaine d’application, vous devez spécifier cet élément et l' [ \<élément AppDomainManagerAssembly >](appdomainmanagerassembly-element.md) .</span><span class="sxs-lookup"><span data-stu-id="35fa2-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="35fa2-124">Si l’un de ces éléments n’est pas spécifié, l’autre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="35fa2-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="35fa2-125">Quand le domaine d’application par défaut est <xref:System.TypeLoadException> chargé, est levé si le type spécifié n’existe pas dans l’assembly spécifié par l' [ \<élément AppDomainManagerAssembly >](appdomainmanagerassembly-element.md) et que le processus ne démarre pas.</span><span class="sxs-lookup"><span data-stu-id="35fa2-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="35fa2-126">Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine d’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="35fa2-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="35fa2-127">Utilisez les <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> propriétés <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> et pour spécifier un autre type de gestionnaire de domaine d’application pour un nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="35fa2-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="35fa2-128">Si vous spécifiez le type de gestionnaire de domaine d’application, l’application doit avoir une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="35fa2-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="35fa2-129">(Par exemple, une application qui s’exécute sur le bureau bénéficie d’une confiance totale.) Si l’application ne dispose pas d’une confiance totale <xref:System.TypeLoadException> , une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="35fa2-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="35fa2-130">Le format du type et de l’espace de noms est le même que celui utilisé <xref:System.Type.FullName%2A?displayProperty=nameWithType> pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="35fa2-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="35fa2-131">Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="35fa2-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35fa2-132">Exemples</span><span class="sxs-lookup"><span data-stu-id="35fa2-132">Example</span></span>  
 <span data-ttu-id="35fa2-133">L’exemple suivant montre comment spécifier que le gestionnaire de domaine d’application pour le domaine d’application par défaut d’un `MyMgr` processus est le `AdMgrExample` type dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="35fa2-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35fa2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35fa2-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="35fa2-135">\<appDomainManagerAssembly >, élément</span><span class="sxs-lookup"><span data-stu-id="35fa2-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="35fa2-136">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="35fa2-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="35fa2-137">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="35fa2-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="35fa2-138">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="35fa2-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
