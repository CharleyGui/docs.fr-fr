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
ms.openlocfilehash: 022f0efbbb2e6e9a4ac9d3d7ddcc1fb1022cdbee
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169777"
---
# <a name="startup-element"></a><span data-ttu-id="593c0-102">\<démarrage > élément</span><span class="sxs-lookup"><span data-stu-id="593c0-102">\<startup> element</span></span>

<span data-ttu-id="593c0-103">Spécifie les informations de démarrage de common language runtime.</span><span class="sxs-lookup"><span data-stu-id="593c0-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="593c0-104">\<configuration> \<startup></span><span class="sxs-lookup"><span data-stu-id="593c0-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="593c0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="593c0-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="593c0-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="593c0-106">Attributes and elements</span></span>

 <span data-ttu-id="593c0-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="593c0-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="593c0-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="593c0-108">Attributes</span></span>

|<span data-ttu-id="593c0-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="593c0-109">Attribute</span></span>|<span data-ttu-id="593c0-110">Description</span><span class="sxs-lookup"><span data-stu-id="593c0-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="593c0-111">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="593c0-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="593c0-112">Spécifie s’il faut activer la stratégie d’activation du runtime .NET Framework 2.0 ou utiliser la stratégie d’activation de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="593c0-112">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="593c0-113">useLegacyV2RuntimeActivationPolicy attribute</span><span class="sxs-lookup"><span data-stu-id="593c0-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="593c0-114">Value</span><span class="sxs-lookup"><span data-stu-id="593c0-114">Value</span></span>|<span data-ttu-id="593c0-115">Description</span><span class="sxs-lookup"><span data-stu-id="593c0-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="593c0-116">Activer la stratégie d’activation du runtime .NET Framework 2.0 pour le runtime choisi, qui consiste à lier les techniques d’activation runtime hérité (telles que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) au runtime choisi à la place du fichier de configuration de limitant les CLR version 2.0.</span><span class="sxs-lookup"><span data-stu-id="593c0-116">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="593c0-117">Par conséquent, si la version CLR 4 ou version ultérieure est choisie dans le fichier de configuration, les assemblys en mode mixte créés avec les versions antérieures du .NET Framework sont chargés avec la version du CLR choisie.</span><span class="sxs-lookup"><span data-stu-id="593c0-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="593c0-118">Définition de cette valeur empêche CLR version 1.1 ou CLR version 2.0 le chargement dans le même processus, en désactivant efficacement la fonctionnalité côte à côte in-process.</span><span class="sxs-lookup"><span data-stu-id="593c0-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="593c0-119">Utilisez la stratégie d’activation par défaut pour le .NET Framework 4 et versions ultérieures, qui consiste à autoriser les techniques d’activation charger le CLR version 1.1 ou 2.0 dans le processus runtime hérité.</span><span class="sxs-lookup"><span data-stu-id="593c0-119">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="593c0-120">Ce paramètre empêche les assemblys en mode mixte de charger dans le .NET Framework 4 ou version ultérieure, sauf si elles ont été générées avec le .NET Framework 4 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="593c0-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="593c0-121">Cette valeur est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="593c0-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="593c0-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="593c0-122">Child elements</span></span>

|<span data-ttu-id="593c0-123">Élément</span><span class="sxs-lookup"><span data-stu-id="593c0-123">Element</span></span>|<span data-ttu-id="593c0-124">Description</span><span class="sxs-lookup"><span data-stu-id="593c0-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="593c0-125">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="593c0-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="593c0-126">Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="593c0-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="593c0-127">Les applications générées avec la version 1.1 ou ultérieure du runtime doivent utiliser le  **\<supportedRuntime >** élément.</span><span class="sxs-lookup"><span data-stu-id="593c0-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="593c0-128">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="593c0-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="593c0-129">Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.</span><span class="sxs-lookup"><span data-stu-id="593c0-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="593c0-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="593c0-130">Parent elements</span></span>

|<span data-ttu-id="593c0-131">Élément</span><span class="sxs-lookup"><span data-stu-id="593c0-131">Element</span></span>|<span data-ttu-id="593c0-132">Description</span><span class="sxs-lookup"><span data-stu-id="593c0-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="593c0-133">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="593c0-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="593c0-134">Notes</span><span class="sxs-lookup"><span data-stu-id="593c0-134">Remarks</span></span>

 <span data-ttu-id="593c0-135">Le  **\<supportedRuntime >** élément doit être utilisé par toutes les applications générées à l’aide de la version 1.1 ou ultérieure du runtime.</span><span class="sxs-lookup"><span data-stu-id="593c0-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="593c0-136">Les applications générées pour prendre en charge uniquement la version 1.0 du runtime doivent utiliser le  **\<requiredRuntime >** élément.</span><span class="sxs-lookup"><span data-stu-id="593c0-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="593c0-137">Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore les  **\<démarrage >** élément et ses éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="593c0-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="593c0-138">L’attribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="593c0-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="593c0-139">Cet attribut est utile si votre application utilise des chemins d’accès d’activation héritée, telle que la [fonction CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), et vous souhaitez que ces chemins activent la version 4 du CLR au lieu d’une version antérieure, ou si votre application est avec le .NET Framework 4 mais a une dépendance sur un assembly en mode mixte généré avec une version antérieure du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="593c0-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="593c0-140">Dans ces scénarios, la valeur est l’attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="593c0-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="593c0-141">Définition de l’attribut sur `true` empêche le chargement dans le même processus, en désactivant efficacement la fonctionnalité côte à côte in-process de CLR version 1.1 ou CLR version 2.0 (consultez [l’exécution côte à côte pour COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="593c0-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="593c0-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="593c0-142">Example</span></span>

 <span data-ttu-id="593c0-143">L’exemple suivant montre comment spécifier la version du runtime dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="593c0-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="593c0-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="593c0-144">See also</span></span>

- [<span data-ttu-id="593c0-145">Schéma des paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="593c0-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="593c0-146">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="593c0-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="593c0-147">Guide pratique pour configurer une application en vue de prendre en charge le .NET Framework 4 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="593c0-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="593c0-148">[Exécution côte à côte pour COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="593c0-148">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="593c0-149">Exécution côte à côte in-process</span><span class="sxs-lookup"><span data-stu-id="593c0-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
