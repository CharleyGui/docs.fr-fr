---
title: Élément <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: c3971379b358ae16fc463df2b8d6288cf8881391
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205033"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="c89c8-102">Élément \<disableFusionUpdatesFromADManager></span><span class="sxs-lookup"><span data-stu-id="c89c8-102">\<disableFusionUpdatesFromADManager> Element</span></span>

<span data-ttu-id="c89c8-103">Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.</span><span class="sxs-lookup"><span data-stu-id="c89c8-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a><span data-ttu-id="c89c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c89c8-104">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c89c8-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c89c8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c89c8-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c89c8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c89c8-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="c89c8-107">Attributes</span></span>  
  
|<span data-ttu-id="c89c8-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c89c8-108">Attribute</span></span>|<span data-ttu-id="c89c8-109">Description</span><span class="sxs-lookup"><span data-stu-id="c89c8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c89c8-110">enabled</span><span class="sxs-lookup"><span data-stu-id="c89c8-110">enabled</span></span>|<span data-ttu-id="c89c8-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c89c8-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="c89c8-112">Spécifie si la capacité par défaut de remplacer les paramètres de fusion est désactivée.</span><span class="sxs-lookup"><span data-stu-id="c89c8-112">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c89c8-113">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="c89c8-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="c89c8-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="c89c8-114">Value</span></span>|<span data-ttu-id="c89c8-115">Description</span><span class="sxs-lookup"><span data-stu-id="c89c8-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c89c8-116">0</span><span class="sxs-lookup"><span data-stu-id="c89c8-116">0</span></span>|<span data-ttu-id="c89c8-117">Ne désactivez pas la possibilité de remplacer les paramètres de fusion.</span><span class="sxs-lookup"><span data-stu-id="c89c8-117">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="c89c8-118">Il s’agit du comportement par défaut, à partir du .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c89c8-118">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="c89c8-119">1</span><span class="sxs-lookup"><span data-stu-id="c89c8-119">1</span></span>|<span data-ttu-id="c89c8-120">Désactivez la possibilité de remplacer les paramètres de fusion.</span><span class="sxs-lookup"><span data-stu-id="c89c8-120">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="c89c8-121">Cela revient au comportement des versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c89c8-121">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c89c8-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c89c8-122">Child Elements</span></span>  

 <span data-ttu-id="c89c8-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c89c8-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c89c8-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c89c8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c89c8-125">Élément</span><span class="sxs-lookup"><span data-stu-id="c89c8-125">Element</span></span>|<span data-ttu-id="c89c8-126">Description</span><span class="sxs-lookup"><span data-stu-id="c89c8-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c89c8-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c89c8-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c89c8-128">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c89c8-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c89c8-129">Notes</span><span class="sxs-lookup"><span data-stu-id="c89c8-129">Remarks</span></span>  

 <span data-ttu-id="c89c8-130">À partir du .NET Framework 4, le comportement par défaut consiste à autoriser l' <xref:System.AppDomainManager> objet à substituer des paramètres de configuration à l’aide de la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété ou <xref:System.AppDomainSetup.SetConfigurationBytes%2A> de la méthode de l' <xref:System.AppDomainSetup> objet qui est passé à votre implémentation de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> méthode, dans votre sous-classe de <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="c89c8-130">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="c89c8-131">Pour le domaine d’application par défaut, les paramètres que vous modifiez remplacent ceux qui ont été spécifiés par le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="c89c8-131">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="c89c8-132">Pour les autres domaines d’application, ils remplacent les paramètres de configuration qui ont été passés à la <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> méthode ou.</span><span class="sxs-lookup"><span data-stu-id="c89c8-132">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="c89c8-133">Vous pouvez transmettre de nouvelles informations de configuration ou passer la valeur null ( `Nothing` dans Visual Basic) pour éliminer les informations de configuration qui ont été transmises.</span><span class="sxs-lookup"><span data-stu-id="c89c8-133">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="c89c8-134">Ne transmettez pas d’informations de configuration à la fois à la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété et à la <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="c89c8-134">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="c89c8-135">Si vous passez des informations de configuration aux deux, les informations que vous passez à la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété sont ignorées, car la <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode remplace les informations de configuration du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="c89c8-135">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="c89c8-136">Si vous utilisez la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété, vous pouvez passer NULL ( `Nothing` en Visual Basic) à la <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode pour éliminer les octets de configuration qui ont été spécifiés dans l’appel à la <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> méthode ou.</span><span class="sxs-lookup"><span data-stu-id="c89c8-136">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="c89c8-137">En plus des informations de configuration, vous pouvez modifier les paramètres suivants sur l' <xref:System.AppDomainSetup> objet qui est passé à votre implémentation de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> méthode : <xref:System.AppDomainSetup.ApplicationBase%2A> , <xref:System.AppDomainSetup.ApplicationName%2A> , <xref:System.AppDomainSetup.CachePath%2A> ,,, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> , <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> , <xref:System.AppDomainSetup.DynamicBase%2A> , <xref:System.AppDomainSetup.LoaderOptimization%2A> , <xref:System.AppDomainSetup.PrivateBinPath%2A> , <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> , <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> et <xref:System.AppDomainSetup.ShadowCopyFiles%2A> .</span><span class="sxs-lookup"><span data-stu-id="c89c8-137">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="c89c8-138">En guise d’alternative à l’utilisation de l' `<disableFusionUpdatesFromADManager>` élément, vous pouvez désactiver le comportement par défaut en créant un paramètre de registre ou en définissant une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c89c8-138">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="c89c8-139">Dans le registre, créez une valeur DWORD nommée `COMPLUS_disableFusionUpdatesFromADManager` sous `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework` , puis définissez la valeur sur 1.</span><span class="sxs-lookup"><span data-stu-id="c89c8-139">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="c89c8-140">Sur la ligne de commande, affectez la valeur 1 à la variable `COMPLUS_disableFusionUpdatesFromADManager` d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c89c8-140">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c89c8-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="c89c8-141">Example</span></span>  

 <span data-ttu-id="c89c8-142">L’exemple suivant montre comment désactiver la possibilité de substituer des paramètres de fusion à l’aide de l' `<disableFusionUpdatesFromADManager>` élément.</span><span class="sxs-lookup"><span data-stu-id="c89c8-142">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c89c8-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c89c8-143">See also</span></span>

- [<span data-ttu-id="c89c8-144">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="c89c8-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c89c8-145">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c89c8-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c89c8-146">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="c89c8-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
