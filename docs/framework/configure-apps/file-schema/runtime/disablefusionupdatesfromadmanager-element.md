---
title: Élément <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1923e70143ea2a158447eccdb35d347fe4f51ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663771"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="27cb0-102">\<disableFusionUpdatesFromADManager >, élément</span><span class="sxs-lookup"><span data-stu-id="27cb0-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="27cb0-103">Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.</span><span class="sxs-lookup"><span data-stu-id="27cb0-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="27cb0-104">\<Élément de > de configuration</span><span class="sxs-lookup"><span data-stu-id="27cb0-104">\<configuration> Element</span></span>  
<span data-ttu-id="27cb0-105">\<Élément > du Runtime</span><span class="sxs-lookup"><span data-stu-id="27cb0-105">\<runtime> Element</span></span>  
<span data-ttu-id="27cb0-106">\<disableFusionUpdatesFromADManager></span><span class="sxs-lookup"><span data-stu-id="27cb0-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27cb0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27cb0-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27cb0-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="27cb0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="27cb0-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="27cb0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27cb0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="27cb0-110">Attributes</span></span>  
  
|<span data-ttu-id="27cb0-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="27cb0-111">Attribute</span></span>|<span data-ttu-id="27cb0-112">Description</span><span class="sxs-lookup"><span data-stu-id="27cb0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27cb0-113">enabled</span><span class="sxs-lookup"><span data-stu-id="27cb0-113">enabled</span></span>|<span data-ttu-id="27cb0-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="27cb0-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="27cb0-115">Spécifie si la capacité par défaut de remplacer les paramètres de fusion est désactivée.</span><span class="sxs-lookup"><span data-stu-id="27cb0-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="27cb0-116">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="27cb0-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="27cb0-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="27cb0-117">Value</span></span>|<span data-ttu-id="27cb0-118">Description</span><span class="sxs-lookup"><span data-stu-id="27cb0-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="27cb0-119">0</span><span class="sxs-lookup"><span data-stu-id="27cb0-119">0</span></span>|<span data-ttu-id="27cb0-120">Ne désactivez pas la possibilité de remplacer les paramètres de fusion.</span><span class="sxs-lookup"><span data-stu-id="27cb0-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="27cb0-121">Il s’agit du comportement par défaut, à partir du .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="27cb0-121">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="27cb0-122">1</span><span class="sxs-lookup"><span data-stu-id="27cb0-122">1</span></span>|<span data-ttu-id="27cb0-123">Désactivez la possibilité de remplacer les paramètres de fusion.</span><span class="sxs-lookup"><span data-stu-id="27cb0-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="27cb0-124">Cela revient au comportement des versions antérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27cb0-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27cb0-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27cb0-125">Child Elements</span></span>  
 <span data-ttu-id="27cb0-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="27cb0-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27cb0-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27cb0-127">Parent Elements</span></span>  
  
|<span data-ttu-id="27cb0-128">Élément</span><span class="sxs-lookup"><span data-stu-id="27cb0-128">Element</span></span>|<span data-ttu-id="27cb0-129">Description</span><span class="sxs-lookup"><span data-stu-id="27cb0-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="27cb0-130">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27cb0-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="27cb0-131">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="27cb0-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27cb0-132">Notes</span><span class="sxs-lookup"><span data-stu-id="27cb0-132">Remarks</span></span>  
 <span data-ttu-id="27cb0-133">À partir du .NET Framework 4, le comportement par défaut consiste à autoriser <xref:System.AppDomainManager> l’objet à substituer des paramètres de configuration <xref:System.AppDomainSetup.ConfigurationFile%2A> à l’aide <xref:System.AppDomainSetup.SetConfigurationBytes%2A> de la propriété <xref:System.AppDomainSetup> ou de la méthode de l’objet qui est passé à votre implémentation. de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> méthode, dans votre sous-classe <xref:System.AppDomainManager>de.</span><span class="sxs-lookup"><span data-stu-id="27cb0-133">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="27cb0-134">Pour le domaine d’application par défaut, les paramètres que vous modifiez remplacent ceux qui ont été spécifiés par le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="27cb0-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="27cb0-135">Pour les autres domaines d’application, ils remplacent les paramètres de configuration qui ont <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> été <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> passés à la méthode ou.</span><span class="sxs-lookup"><span data-stu-id="27cb0-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="27cb0-136">Vous pouvez transmettre de nouvelles informations de configuration ou passer la valeur`Nothing` null (dans Visual Basic) pour éliminer les informations de configuration qui ont été transmises.</span><span class="sxs-lookup"><span data-stu-id="27cb0-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="27cb0-137">Ne transmettez pas d’informations de configuration <xref:System.AppDomainSetup.ConfigurationFile%2A> à la fois <xref:System.AppDomainSetup.SetConfigurationBytes%2A> à la propriété et à la méthode.</span><span class="sxs-lookup"><span data-stu-id="27cb0-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="27cb0-138">Si vous passez des informations de configuration aux deux, les informations que vous <xref:System.AppDomainSetup.ConfigurationFile%2A> passez à la propriété sont ignorées, car la <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode remplace les informations de configuration du fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="27cb0-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="27cb0-139">Si vous utilisez la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété, vous pouvez passer NULL (`Nothing` en Visual Basic) à la <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode pour éliminer les octets de configuration qui ont été spécifiés dans l' <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> appel <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> à la méthode ou.</span><span class="sxs-lookup"><span data-stu-id="27cb0-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="27cb0-140">En plus des informations de configuration, vous pouvez modifier les paramètres suivants sur <xref:System.AppDomainSetup> l’objet qui est passé à votre implémentation de <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> la <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>méthode <xref:System.AppDomainSetup.ApplicationBase%2A>: <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>,, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>,, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, ,,<xref:System.AppDomainSetup.LoaderOptimization%2A>,, et<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>. <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.ShadowCopyFiles%2A></span><span class="sxs-lookup"><span data-stu-id="27cb0-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="27cb0-141">En guise d’alternative à `<disableFusionUpdatesFromADManager>` l’utilisation de l’élément, vous pouvez désactiver le comportement par défaut en créant un paramètre de registre ou en définissant une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="27cb0-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="27cb0-142">Dans le registre, créez une valeur DWORD nommée `COMPLUS_disableFusionUpdatesFromADManager` sous `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework`, puis définissez la valeur sur 1.</span><span class="sxs-lookup"><span data-stu-id="27cb0-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="27cb0-143">Sur la ligne de commande, affectez la `COMPLUS_disableFusionUpdatesFromADManager` valeur 1 à la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="27cb0-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27cb0-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="27cb0-144">Example</span></span>  
 <span data-ttu-id="27cb0-145">L’exemple suivant montre comment désactiver la possibilité de substituer des paramètres de fusion à l' `<disableFusionUpdatesFromADManager>` aide de l’élément.</span><span class="sxs-lookup"><span data-stu-id="27cb0-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27cb0-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27cb0-146">See also</span></span>

- [<span data-ttu-id="27cb0-147">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="27cb0-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="27cb0-148">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="27cb0-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="27cb0-149">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="27cb0-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
