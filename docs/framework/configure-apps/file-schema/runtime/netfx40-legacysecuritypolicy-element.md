---
title: <NetFx40_LegacySecurityPolicy>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5bfa5449ece1b24d4f47fe3e77e36b26bbe430c
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689846"
---
# <a name="netfx40legacysecuritypolicy-element"></a><span data-ttu-id="3943a-102">\<NetFx40_LegacySecurityPolicy > élément</span><span class="sxs-lookup"><span data-stu-id="3943a-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="3943a-103">Indique si le runtime utilise la stratégie héritée de sécurité d’accès du code (CAS).</span><span class="sxs-lookup"><span data-stu-id="3943a-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

<span data-ttu-id="3943a-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="3943a-104">\<configuration>\\</span></span>
<span data-ttu-id="3943a-105">\<runtime>\\</span><span class="sxs-lookup"><span data-stu-id="3943a-105">\<runtime>\\</span></span>
<span data-ttu-id="3943a-106">\<NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="3943a-106">\<NetFx40_LegacySecurityPolicy></span></span>

## <a name="syntax"></a><span data-ttu-id="3943a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3943a-107">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3943a-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3943a-108">Attributes and Elements</span></span>

<span data-ttu-id="3943a-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3943a-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3943a-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="3943a-110">Attributes</span></span>

|<span data-ttu-id="3943a-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="3943a-111">Attribute</span></span>|<span data-ttu-id="3943a-112">Description</span><span class="sxs-lookup"><span data-stu-id="3943a-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="3943a-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="3943a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3943a-114">Spécifie si le runtime utilise la stratégie CAS héritée.</span><span class="sxs-lookup"><span data-stu-id="3943a-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="3943a-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="3943a-115">enabled Attribute</span></span>

|<span data-ttu-id="3943a-116">Value</span><span class="sxs-lookup"><span data-stu-id="3943a-116">Value</span></span>|<span data-ttu-id="3943a-117">Description</span><span class="sxs-lookup"><span data-stu-id="3943a-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="3943a-118">Le runtime n’utilise pas la stratégie CAS héritée.</span><span class="sxs-lookup"><span data-stu-id="3943a-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="3943a-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="3943a-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="3943a-120">Le runtime utilise la stratégie CAS héritée.</span><span class="sxs-lookup"><span data-stu-id="3943a-120">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3943a-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3943a-121">Child Elements</span></span>

<span data-ttu-id="3943a-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3943a-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3943a-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3943a-123">Parent Elements</span></span>

|<span data-ttu-id="3943a-124">Élément</span><span class="sxs-lookup"><span data-stu-id="3943a-124">Element</span></span>|<span data-ttu-id="3943a-125">Description</span><span class="sxs-lookup"><span data-stu-id="3943a-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="3943a-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3943a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="3943a-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="3943a-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3943a-128">Notes</span><span class="sxs-lookup"><span data-stu-id="3943a-128">Remarks</span></span>

<span data-ttu-id="3943a-129">Dans le .NET Framework version 3.5 et les versions antérieures, la stratégie CAS est toujours en vigueur.</span><span class="sxs-lookup"><span data-stu-id="3943a-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="3943a-130">Dans le .NET Framework 4, la stratégie CAS doit être activée.</span><span class="sxs-lookup"><span data-stu-id="3943a-130">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="3943a-131">La stratégie CAS est spécifique à la version.</span><span class="sxs-lookup"><span data-stu-id="3943a-131">CAS policy is version-specific.</span></span> <span data-ttu-id="3943a-132">Les stratégies CAS personnalisées qui existent dans les versions antérieures du .NET Framework doivent être de nouveau spécifiées dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3943a-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="3943a-133">Appliquer le `<NetFx40_LegacySecurityPolicy>` élément à un assembly .NET Framework 4 n’affecte pas [code transparent de sécurité](../../../../../docs/framework/misc/security-transparent-code.md); les règles de transparence s’appliquent toujours.</span><span class="sxs-lookup"><span data-stu-id="3943a-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3943a-134">Appliquer le `<NetFx40_LegacySecurityPolicy>` élément peut entraîner des altérations des performances significatives pour les assemblys d’images natives créés par le [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) qui ne sont pas installés dans le [GAC ](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="3943a-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="3943a-135">La dégradation des performances sont dû à l’incapacité du runtime à charger les assemblys en tant qu’images natives lorsque l’attribut est appliqué, ce qui provoque leur chargé les assemblys comme juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="3943a-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="3943a-136">Si vous spécifiez une version de .NET Framework cible est antérieure à .NET Framework 4 dans les paramètres du projet pour votre projet Visual Studio, stratégie des autorités de certification sera activée, y compris les stratégies autorités de certification personnalisées que vous avez spécifié pour cette version.</span><span class="sxs-lookup"><span data-stu-id="3943a-136">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="3943a-137">Toutefois, vous ne serez pas en mesure d’utiliser des membres et les nouveaux types de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3943a-137">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="3943a-138">Vous pouvez également spécifier une version antérieure du .NET Framework à l’aide de la [ \<supportedRuntime > élément](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) dans le schéma de paramètres de démarrage dans votre [fichier de configuration d’application](../../../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="3943a-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3943a-139">Syntaxe du fichier de configuration respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="3943a-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="3943a-140">Vous devez utiliser la syntaxe comme indiqué dans les sections syntaxe et exemple.</span><span class="sxs-lookup"><span data-stu-id="3943a-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="3943a-141">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="3943a-141">Configuration File</span></span>

<span data-ttu-id="3943a-142">Cet élément peut être utilisé uniquement dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="3943a-142">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="3943a-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="3943a-143">Example</span></span>

<span data-ttu-id="3943a-144">L’exemple suivant montre comment activer la stratégie CAS héritée d’une application.</span><span class="sxs-lookup"><span data-stu-id="3943a-144">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3943a-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3943a-145">See also</span></span>

- [<span data-ttu-id="3943a-146">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="3943a-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="3943a-147">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3943a-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
