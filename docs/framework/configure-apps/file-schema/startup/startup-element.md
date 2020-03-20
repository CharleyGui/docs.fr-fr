---
title: <startup> (élément)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153727"
---
# <a name="startup-element"></a><span data-ttu-id="7336f-102">\<> élément de démarrage</span><span class="sxs-lookup"><span data-stu-id="7336f-102">\<startup> element</span></span>

<span data-ttu-id="7336f-103">Spécifie les informations de démarrage en temps courant.</span><span class="sxs-lookup"><span data-stu-id="7336f-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="7336f-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="7336f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="7336f-105">&nbsp;&nbsp;**\<>de démarrage**</span><span class="sxs-lookup"><span data-stu-id="7336f-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="7336f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7336f-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7336f-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7336f-107">Attributes and elements</span></span>

 <span data-ttu-id="7336f-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7336f-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7336f-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="7336f-109">Attributes</span></span>

|<span data-ttu-id="7336f-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="7336f-110">Attribute</span></span>|<span data-ttu-id="7336f-111">Description</span><span class="sxs-lookup"><span data-stu-id="7336f-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="7336f-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="7336f-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7336f-113">Précise s’il faut activer la politique d’activation du temps d’exécution .NET Framework 2.0 ou utiliser la politique d’activation .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7336f-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="7336f-114">utiliser l’attributLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="7336f-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="7336f-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="7336f-115">Value</span></span>|<span data-ttu-id="7336f-116">Description</span><span class="sxs-lookup"><span data-stu-id="7336f-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="7336f-117">Activez la politique d’activation de temps d’exécution .NET Framework 2.0 pour le temps d’exécution choisi, qui consiste à lier les techniques d’activation du temps d’exécution de l’héritage (comme la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) au temps d’exécution choisi à partir du fichier de configuration au lieu de les plafonner à la version CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="7336f-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="7336f-118">Ainsi, si la version CLR 4 ou plus tard est choisie à partir du fichier de configuration, les assemblages en mode mixte créés avec des versions antérieures du cadre .NET sont chargés de la version CLR choisie.</span><span class="sxs-lookup"><span data-stu-id="7336f-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="7336f-119">La définition de cette valeur empêche la version CLR 1.1 ou la version CLR 2.0 de se charger dans le même processus, désactivant efficacement la fonction en cours côte à côte.</span><span class="sxs-lookup"><span data-stu-id="7336f-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="7336f-120">Utilisez la stratégie d’activation par défaut pour le cadre .NET 4 et plus tard, qui est de permettre aux techniques d’activation de temps d’exécution hérités pour charger la version CLR 1.1 ou 2.0 dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7336f-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="7336f-121">La définition de cette valeur empêche les assemblages en mode mixte de se charger dans le cadre .NET 4 ou plus tard, à moins qu’ils ne soient construits avec le cadre .NET 4 ou plus tard.</span><span class="sxs-lookup"><span data-stu-id="7336f-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="7336f-122">Cette valeur est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="7336f-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7336f-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7336f-123">Child elements</span></span>

|<span data-ttu-id="7336f-124">Élément</span><span class="sxs-lookup"><span data-stu-id="7336f-124">Element</span></span>|<span data-ttu-id="7336f-125">Description</span><span class="sxs-lookup"><span data-stu-id="7336f-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7336f-126">\<requisRuntime></span><span class="sxs-lookup"><span data-stu-id="7336f-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="7336f-127">Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="7336f-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="7336f-128">Les applications construites avec la version 1.1 ou plus tard doivent utiliser l’élément \*\* \<>SupportRuntime.\*\*</span><span class="sxs-lookup"><span data-stu-id="7336f-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="7336f-129">\<supportRuntime></span><span class="sxs-lookup"><span data-stu-id="7336f-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="7336f-130">Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.</span><span class="sxs-lookup"><span data-stu-id="7336f-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7336f-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7336f-131">Parent elements</span></span>

|<span data-ttu-id="7336f-132">Élément</span><span class="sxs-lookup"><span data-stu-id="7336f-132">Element</span></span>|<span data-ttu-id="7336f-133">Description</span><span class="sxs-lookup"><span data-stu-id="7336f-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="7336f-134">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7336f-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7336f-135">Notes </span><span class="sxs-lookup"><span data-stu-id="7336f-135">Remarks</span></span>

 <span data-ttu-id="7336f-136">\*\* \<L’élément de>Deruntime pris en charge\*\* doit être utilisé par toutes les applications construites à l’aide de la version 1.1 ou plus tard de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7336f-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="7336f-137">Les applications conçues pour prendre en charge uniquement la version 1.0 du temps d’exécution doivent utiliser \*\* \<l’élément>runtime requis.\*\*</span><span class="sxs-lookup"><span data-stu-id="7336f-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="7336f-138">Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore la \*\* \<startup>\*\* élément et ses éléments pour enfants.</span><span class="sxs-lookup"><span data-stu-id="7336f-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="7336f-139">L’attribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="7336f-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="7336f-140">Cet attribut est utile si votre application utilise des trajectoires d’activation héritées, telles que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), et que vous voulez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est construite avec le cadre .NET 4, mais a une dépendance sur un assemblage en mode mixte construit avec une version antérieure du cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="7336f-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="7336f-141">Dans ces scénarios, définissez `true`l’attribut à .</span><span class="sxs-lookup"><span data-stu-id="7336f-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="7336f-142">Définir l’attribut pour `true` empêcher la version CLR 1.1 ou CLR version 2.0 de charger dans le même processus, désactiver efficacement la fonction en cours côte à côte (voir Exécution côte à côte pour COM [Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="7336f-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="7336f-143"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7336f-143">Example</span></span>

 <span data-ttu-id="7336f-144">L’exemple suivant montre comment spécifier la version de l’exécution dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7336f-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7336f-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7336f-145">See also</span></span>

- [<span data-ttu-id="7336f-146">Paramètres de démarrage Schema</span><span class="sxs-lookup"><span data-stu-id="7336f-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7336f-147">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="7336f-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7336f-148">Comment configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="7336f-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="7336f-149">[Exécution côte à côte pour COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7336f-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="7336f-150">Exécution côte à côte in-process</span><span class="sxs-lookup"><span data-stu-id="7336f-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
