---
title: Élément <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154423"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="2a5d1-102">\<appDomainManagerType> Element</span><span class="sxs-lookup"><span data-stu-id="2a5d1-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="2a5d1-103">Spécifie le type qui sert de Gestionnaire de domaine d’application au domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
<span data-ttu-id="2a5d1-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2a5d1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2a5d1-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2a5d1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2a5d1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span><span class="sxs-lookup"><span data-stu-id="2a5d1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a5d1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a5d1-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a5d1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2a5d1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2a5d1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a5d1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="2a5d1-110">Attributes</span></span>  
  
|<span data-ttu-id="2a5d1-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a5d1-111">Attribute</span></span>|<span data-ttu-id="2a5d1-112">Description</span><span class="sxs-lookup"><span data-stu-id="2a5d1-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="2a5d1-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-113">Required attribute.</span></span> <span data-ttu-id="2a5d1-114">Spécifie le nom du type, y compris l’espace de nom, qui sert de gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a5d1-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2a5d1-115">Child Elements</span></span>  
 <span data-ttu-id="2a5d1-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a5d1-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2a5d1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2a5d1-118">Élément</span><span class="sxs-lookup"><span data-stu-id="2a5d1-118">Element</span></span>|<span data-ttu-id="2a5d1-119">Description</span><span class="sxs-lookup"><span data-stu-id="2a5d1-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2a5d1-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2a5d1-121">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a5d1-122">Notes </span><span class="sxs-lookup"><span data-stu-id="2a5d1-122">Remarks</span></span>  
 <span data-ttu-id="2a5d1-123">Pour spécifier le type de gestionnaire de domaine d’application, vous devez spécifier à la fois cet élément et [ \<l’élément>appDomainManagerAssembly.](appdomainmanagerassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="2a5d1-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="2a5d1-124">Si l’un ou l’autre de ces éléments n’est pas spécifié, l’autre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="2a5d1-125">Lorsque le domaine d’application par défaut est chargé, <xref:System.TypeLoadException> est lancé si le type spécifié n’existe pas dans l’assemblage qui est spécifié par [ \<l’appDomainManagerAssembly>](appdomainmanagerassembly-element.md) élément; et le processus ne démarre pas.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="2a5d1-126">Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine de l’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="2a5d1-127">Utilisez <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> les <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriétés et les propriétés pour spécifier un type de gestionnaire de domaine d’application différent pour un nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="2a5d1-128">Spécifier le type de gestionnaire de domaine d’application nécessite que l’application ait une pleine confiance.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="2a5d1-129">(Par exemple, une application fonctionnant sur le bureau a une confiance totale.) Si l’application n’a <xref:System.TypeLoadException> pas la pleine confiance, a est lancée.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="2a5d1-130">Le format du type et de l’espace de <xref:System.Type.FullName%2A?displayProperty=nameWithType> nom est le même format qui est utilisé pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="2a5d1-131">Cet élément de configuration n’est disponible que dans le cadre .NET 4 et plus tard.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a5d1-132"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2a5d1-132">Example</span></span>  
 <span data-ttu-id="2a5d1-133">L’exemple suivant montre comment spécifier que le gestionnaire de `MyMgr` domaine `AdMgrExample` d’application pour le domaine d’application par défaut d’un processus est le type dans l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="2a5d1-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a5d1-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a5d1-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2a5d1-135">\<appDomainManagerAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="2a5d1-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="2a5d1-136">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="2a5d1-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2a5d1-137">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="2a5d1-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2a5d1-138">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="2a5d1-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
