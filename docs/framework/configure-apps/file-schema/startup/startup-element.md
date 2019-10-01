---
title: <startup>, élément
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 634d9c5248c33619abec50d441d95c111febdcbf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699417"
---
# <a name="startup-element"></a><span data-ttu-id="b1ee1-102">élément @no__t 0startup ></span><span class="sxs-lookup"><span data-stu-id="b1ee1-102">\<startup> element</span></span>

<span data-ttu-id="b1ee1-103">Spécifie common language runtime informations de démarrage.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="b1ee1-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="b1ee1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b1ee1-105">&nbsp;&nbsp; **\<startup>**</span><span class="sxs-lookup"><span data-stu-id="b1ee1-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="b1ee1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1ee1-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1ee1-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b1ee1-107">Attributes and elements</span></span>

 <span data-ttu-id="b1ee1-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1ee1-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="b1ee1-109">Attributes</span></span>

|<span data-ttu-id="b1ee1-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b1ee1-110">Attribute</span></span>|<span data-ttu-id="b1ee1-111">Description</span><span class="sxs-lookup"><span data-stu-id="b1ee1-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="b1ee1-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b1ee1-113">Spécifie s’il faut activer la stratégie d’activation du Runtime .NET Framework 2,0 ou utiliser la stratégie d’activation .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="b1ee1-114">useLegacyV2RuntimeActivationPolicy (attribut)</span><span class="sxs-lookup"><span data-stu-id="b1ee1-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="b1ee1-115">Value</span><span class="sxs-lookup"><span data-stu-id="b1ee1-115">Value</span></span>|<span data-ttu-id="b1ee1-116">Description</span><span class="sxs-lookup"><span data-stu-id="b1ee1-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="b1ee1-117">Activez .NET Framework stratégie d’activation du runtime 2,0 pour le runtime choisi, qui consiste à lier les techniques héritées d’activation du Runtime (telles que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) au runtime choisi à partir du fichier de configuration au lieu de les découper au niveau du CLR version 2,0.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="b1ee1-118">Par conséquent, si CLR version 4 ou ultérieure est choisi dans le fichier de configuration, les assemblys en mode mixte créés avec des versions antérieures du .NET Framework sont chargés avec la version CLR choisie.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="b1ee1-119">La définition de cette valeur empêche le chargement du CLR version 1,1 ou CLR version 2,0 dans le même processus, ce qui a pour effet de désactiver la fonctionnalité côte à côte in-process.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="b1ee1-120">Utilisez la stratégie d’activation par défaut pour le .NET Framework 4 et versions ultérieures, ce qui permet d’autoriser les techniques d’activation du runtime héritées à charger CLR version 1,1 ou 2,0 dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="b1ee1-121">La définition de cette valeur empêche le chargement des assemblys en mode mixte dans le .NET Framework 4 ou ultérieur, sauf s’ils ont été générés avec le .NET Framework 4 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="b1ee1-122">Cette valeur est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b1ee1-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b1ee1-123">Child elements</span></span>

|<span data-ttu-id="b1ee1-124">Élément</span><span class="sxs-lookup"><span data-stu-id="b1ee1-124">Element</span></span>|<span data-ttu-id="b1ee1-125">Description</span><span class="sxs-lookup"><span data-stu-id="b1ee1-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1ee1-126">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="b1ee1-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="b1ee1-127">Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="b1ee1-128">Les applications générées avec la version 1,1 ou ultérieure du Runtime doivent utiliser l’élément **\<supportedRuntime >** .</span><span class="sxs-lookup"><span data-stu-id="b1ee1-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="b1ee1-129">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="b1ee1-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="b1ee1-130">Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b1ee1-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b1ee1-131">Parent elements</span></span>

|<span data-ttu-id="b1ee1-132">Élément</span><span class="sxs-lookup"><span data-stu-id="b1ee1-132">Element</span></span>|<span data-ttu-id="b1ee1-133">Description</span><span class="sxs-lookup"><span data-stu-id="b1ee1-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b1ee1-134">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b1ee1-135">Notes</span><span class="sxs-lookup"><span data-stu-id="b1ee1-135">Remarks</span></span>

 <span data-ttu-id="b1ee1-136">L’élément **\<supportedRuntime >** doit être utilisé par toutes les applications générées à l’aide de la version 1,1 ou ultérieure du Runtime.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="b1ee1-137">Les applications générées pour prendre en charge uniquement la version 1,0 du Runtime doivent utiliser l’élément **\<requiredRuntime >** .</span><span class="sxs-lookup"><span data-stu-id="b1ee1-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="b1ee1-138">Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore l’élément **\<startup >** et ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="b1ee1-139">Attribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="b1ee1-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="b1ee1-140">Cet attribut est utile si votre application utilise des chemins d’activation hérités, tels que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), et si vous souhaitez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est générée avec le .net Framework 4, mais a une dépendance sur un assembly en mode mixte créé avec une version antérieure du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="b1ee1-141">Dans ces scénarios, affectez la valeur `true` à l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="b1ee1-142">La définition de l’attribut sur `true` empêche le chargement du CLR version 1,1 ou CLR version 2,0 dans le même processus, ce qui a pour effet de désactiver la fonctionnalité côte à côte in-process (voir [exécution côte à côte pour COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="b1ee1-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="b1ee1-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1ee1-143">Example</span></span>

 <span data-ttu-id="b1ee1-144">L’exemple suivant montre comment spécifier la version du runtime dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b1ee1-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b1ee1-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1ee1-145">See also</span></span>

- [<span data-ttu-id="b1ee1-146">Schéma des paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="b1ee1-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b1ee1-147">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b1ee1-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b1ee1-148">Guide pratique pour configurer une application en vue de prendre en charge le .NET Framework 4 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b1ee1-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="b1ee1-149">[Exécution côte à côte pour COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b1ee1-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="b1ee1-150">Exécution côte à côte in-process</span><span class="sxs-lookup"><span data-stu-id="b1ee1-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
