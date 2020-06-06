---
title: Élément <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154423"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="96141-102">Élément \<appDomainManagerType></span><span class="sxs-lookup"><span data-stu-id="96141-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="96141-103">Spécifie le type qui sert de Gestionnaire de domaine d’application au domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="96141-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a><span data-ttu-id="96141-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96141-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96141-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="96141-105">Attributes and Elements</span></span>  
 <span data-ttu-id="96141-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="96141-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96141-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="96141-107">Attributes</span></span>  
  
|<span data-ttu-id="96141-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="96141-108">Attribute</span></span>|<span data-ttu-id="96141-109">Description</span><span class="sxs-lookup"><span data-stu-id="96141-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="96141-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="96141-110">Required attribute.</span></span> <span data-ttu-id="96141-111">Spécifie le nom du type, y compris l’espace de noms, qui sert de gestionnaire de domaine d’application pour le domaine d’application par défaut dans le processus.</span><span class="sxs-lookup"><span data-stu-id="96141-111">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96141-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="96141-112">Child Elements</span></span>  
 <span data-ttu-id="96141-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="96141-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96141-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="96141-114">Parent Elements</span></span>  
  
|<span data-ttu-id="96141-115">Élément</span><span class="sxs-lookup"><span data-stu-id="96141-115">Element</span></span>|<span data-ttu-id="96141-116">Description</span><span class="sxs-lookup"><span data-stu-id="96141-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="96141-117">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96141-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="96141-118">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="96141-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96141-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="96141-119">Remarks</span></span>  
 <span data-ttu-id="96141-120">Pour spécifier le type du gestionnaire de domaine d’application, vous devez spécifier à la fois cet élément et l' [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) élément.</span><span class="sxs-lookup"><span data-stu-id="96141-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="96141-121">Si l’un de ces éléments n’est pas spécifié, l’autre est ignorée.</span><span class="sxs-lookup"><span data-stu-id="96141-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="96141-122">Quand le domaine d’application par défaut est chargé, <xref:System.TypeLoadException> est levé si le type spécifié n’existe pas dans l’assembly spécifié par l' [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) élément et que le processus ne démarre pas.</span><span class="sxs-lookup"><span data-stu-id="96141-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="96141-123">Lorsque vous spécifiez le type de gestionnaire de domaine d’application pour le domaine d’application par défaut, d’autres domaines d’application créés à partir du domaine d’application par défaut héritent du type de gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="96141-123">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="96141-124">Utilisez les <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Propriétés et pour spécifier un autre type de gestionnaire de domaine d’application pour un nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="96141-124">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="96141-125">Si vous spécifiez le type de gestionnaire de domaine d’application, l’application doit avoir une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="96141-125">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="96141-126">(Par exemple, une application qui s’exécute sur le bureau bénéficie d’une confiance totale.) Si l’application ne dispose pas d’une confiance totale, une <xref:System.TypeLoadException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="96141-126">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="96141-127">Le format du type et de l’espace de noms est le même que celui utilisé pour la <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="96141-127">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="96141-128">Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="96141-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96141-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="96141-129">Example</span></span>  
 <span data-ttu-id="96141-130">L’exemple suivant montre comment spécifier que le gestionnaire de domaine d’application pour le domaine d’application par défaut d’un processus est le `MyMgr` type dans l' `AdMgrExample` assembly.</span><span class="sxs-lookup"><span data-stu-id="96141-130">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96141-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96141-131">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="96141-132">\<appDomainManagerAssembly>Appartient</span><span class="sxs-lookup"><span data-stu-id="96141-132">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="96141-133">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="96141-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="96141-134">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="96141-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="96141-135">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="96141-135">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
