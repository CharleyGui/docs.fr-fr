---
title: <NetFx40_LegacySecurityPolicy>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: d5192eb56bb8b640544bdc52a0bb9d8a5277efef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116250"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="c548d-102">Élément \<NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="c548d-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="c548d-103">Indique si le runtime utilise la stratégie héritée de sécurité d’accès du code (CAS).</span><span class="sxs-lookup"><span data-stu-id="c548d-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**  

## <a name="syntax"></a><span data-ttu-id="c548d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c548d-104">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c548d-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c548d-105">Attributes and Elements</span></span>

<span data-ttu-id="c548d-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c548d-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c548d-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="c548d-107">Attributes</span></span>

|<span data-ttu-id="c548d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c548d-108">Attribute</span></span>|<span data-ttu-id="c548d-109">Description</span><span class="sxs-lookup"><span data-stu-id="c548d-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="c548d-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c548d-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="c548d-111">Spécifie si le runtime utilise la stratégie CAS héritée.</span><span class="sxs-lookup"><span data-stu-id="c548d-111">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="c548d-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="c548d-112">enabled Attribute</span></span>

|<span data-ttu-id="c548d-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="c548d-113">Value</span></span>|<span data-ttu-id="c548d-114">Description</span><span class="sxs-lookup"><span data-stu-id="c548d-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="c548d-115">Le runtime n’utilise pas la stratégie CAS héritée.</span><span class="sxs-lookup"><span data-stu-id="c548d-115">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="c548d-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c548d-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="c548d-117">Le runtime utilise la stratégie CAS héritée.</span><span class="sxs-lookup"><span data-stu-id="c548d-117">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c548d-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c548d-118">Child Elements</span></span>

<span data-ttu-id="c548d-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c548d-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c548d-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c548d-120">Parent Elements</span></span>

|<span data-ttu-id="c548d-121">Élément</span><span class="sxs-lookup"><span data-stu-id="c548d-121">Element</span></span>|<span data-ttu-id="c548d-122">Description</span><span class="sxs-lookup"><span data-stu-id="c548d-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c548d-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c548d-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="c548d-124">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="c548d-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c548d-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="c548d-125">Remarks</span></span>

<span data-ttu-id="c548d-126">Dans le .NET Framework version 3,5 et les versions antérieures, la stratégie CAS est toujours activée.</span><span class="sxs-lookup"><span data-stu-id="c548d-126">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="c548d-127">Dans la .NET Framework 4, la stratégie CAS doit être activée.</span><span class="sxs-lookup"><span data-stu-id="c548d-127">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="c548d-128">La stratégie CAS est spécifique à la version.</span><span class="sxs-lookup"><span data-stu-id="c548d-128">CAS policy is version-specific.</span></span> <span data-ttu-id="c548d-129">Les stratégies CAS personnalisées qui existent dans les versions antérieures du .NET Framework doivent être spécifiées à l' .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c548d-129">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="c548d-130">L’application `<NetFx40_LegacySecurityPolicy>` de l’élément à un assembly .NET Framework 4 n’affecte pas le [code transparent de sécurité](../../../misc/security-transparent-code.md); les règles de transparence s’appliquent toujours.</span><span class="sxs-lookup"><span data-stu-id="c548d-130">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c548d-131">L’application de l' `<NetFx40_LegacySecurityPolicy>` élément peut entraîner des pénalités de performances significatives pour les assemblys d’images natives créés par le [Générateur d’images natives (Ngen. exe)](../../../tools/ngen-exe-native-image-generator.md) qui ne sont pas installés dans le [global assembly cache](../../../app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="c548d-131">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="c548d-132">La dégradation des performances est provoquée par l’incapacité du runtime à charger les assemblys en tant qu’images natives lorsque l’attribut est appliqué, ce qui entraîne leur chargement en tant qu’assemblys juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="c548d-132">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="c548d-133">Si vous spécifiez une version de .NET Framework cible antérieure à la .NET Framework 4 dans les paramètres de projet de votre projet Visual Studio, la stratégie CAS est activée, y compris les stratégies CAS personnalisées que vous avez spécifiées pour cette version.</span><span class="sxs-lookup"><span data-stu-id="c548d-133">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="c548d-134">Toutefois, vous ne pourrez pas utiliser les nouveaux types et membres de .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c548d-134">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="c548d-135">Vous pouvez également spécifier une version antérieure du .NET Framework à l’aide de l' [ \<supportedRuntime> élément](../startup/supportedruntime-element.md) dans le schéma des paramètres de démarrage de votre [fichier de configuration](../../index.md)de l’application.</span><span class="sxs-lookup"><span data-stu-id="c548d-135">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c548d-136">La syntaxe du fichier de configuration respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="c548d-136">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="c548d-137">Vous devez utiliser la syntaxe fournie dans les sections syntaxe et example.</span><span class="sxs-lookup"><span data-stu-id="c548d-137">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="c548d-138">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c548d-138">Configuration File</span></span>

<span data-ttu-id="c548d-139">Cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="c548d-139">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="c548d-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="c548d-140">Example</span></span>

<span data-ttu-id="c548d-141">L’exemple suivant montre comment activer la stratégie CAS héritée pour une application.</span><span class="sxs-lookup"><span data-stu-id="c548d-141">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c548d-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c548d-142">See also</span></span>

- [<span data-ttu-id="c548d-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="c548d-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c548d-144">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c548d-144">Configuration File Schema</span></span>](../index.md)
