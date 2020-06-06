---
title: <NetFx40_PInvokeStackResilience>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 86f50aafe0b21d5080288e09ac7118ca1e4c939a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116160"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="05627-102">Élément \<NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="05627-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="05627-103">Indique si le runtime corrige automatiquement les déclarations incorrectes d’appel de code non managé à l’exécution, au prix de transitions plus lentes entre le code managé et le code non managé.</span><span class="sxs-lookup"><span data-stu-id="05627-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**  

## <a name="syntax"></a><span data-ttu-id="05627-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05627-104">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05627-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="05627-105">Attributes and Elements</span></span>

<span data-ttu-id="05627-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="05627-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="05627-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="05627-107">Attributes</span></span>

|<span data-ttu-id="05627-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="05627-108">Attribute</span></span>|<span data-ttu-id="05627-109">Description</span><span class="sxs-lookup"><span data-stu-id="05627-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="05627-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="05627-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="05627-111">Spécifie si le runtime détecte des déclarations d’appel de code non managé incorrectes et résout automatiquement la pile au moment de l’exécution sur les plateformes 32 bits.</span><span class="sxs-lookup"><span data-stu-id="05627-111">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="05627-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="05627-112">enabled Attribute</span></span>

|<span data-ttu-id="05627-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="05627-113">Value</span></span>|<span data-ttu-id="05627-114">Description</span><span class="sxs-lookup"><span data-stu-id="05627-114">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="05627-115">Le runtime utilise l’architecture de marshaling d’interopérabilité plus rapide introduite dans le .NET Framework 4, qui ne détecte pas et ne corrige pas les déclarations d’appel de code non managé incorrectes.</span><span class="sxs-lookup"><span data-stu-id="05627-115">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="05627-116">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="05627-116">This is the default.</span></span>|
|`1`|<span data-ttu-id="05627-117">Le runtime utilise des transitions plus lentes qui détectent et corrigent les déclarations d’appel de code non managé incorrectes.</span><span class="sxs-lookup"><span data-stu-id="05627-117">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="05627-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="05627-118">Child Elements</span></span>

<span data-ttu-id="05627-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="05627-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="05627-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="05627-120">Parent Elements</span></span>

|<span data-ttu-id="05627-121">Élément</span><span class="sxs-lookup"><span data-stu-id="05627-121">Element</span></span>|<span data-ttu-id="05627-122">Description</span><span class="sxs-lookup"><span data-stu-id="05627-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="05627-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="05627-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="05627-124">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="05627-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="05627-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="05627-125">Remarks</span></span>

<span data-ttu-id="05627-126">Cet élément vous permet d’échanger un marshaling d’interopérabilité plus rapide pour la résilience au moment de l’exécution contre les déclarations d’appel de code non managé incorrectes.</span><span class="sxs-lookup"><span data-stu-id="05627-126">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="05627-127">À partir du .NET Framework 4, une architecture de marshaling d’interopérabilité rationalisée offre une amélioration significative des performances des transitions du code managé vers du code non managé.</span><span class="sxs-lookup"><span data-stu-id="05627-127">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="05627-128">Dans les versions antérieures du .NET Framework, la couche de marshaling a détecté des déclarations d’appel de code non managé incorrectes sur les plateformes 32 bits et a résolu automatiquement la pile.</span><span class="sxs-lookup"><span data-stu-id="05627-128">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="05627-129">La nouvelle architecture de marshaling élimine cette étape.</span><span class="sxs-lookup"><span data-stu-id="05627-129">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="05627-130">Par conséquent, les transitions sont très rapides, mais une déclaration d’appel de code non managé incorrecte peut provoquer un échec de programme.</span><span class="sxs-lookup"><span data-stu-id="05627-130">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="05627-131">Pour faciliter la détection des déclarations incorrectes pendant le développement, l’expérience de débogage de Visual Studio a été améliorée.</span><span class="sxs-lookup"><span data-stu-id="05627-131">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="05627-132">L’Assistant Débogage managé (MDA) [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) vous avertit des déclarations d’appel de code non managé incorrectes lorsque votre application s’exécute avec le débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="05627-132">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="05627-133">Pour traiter les scénarios où votre application utilise des composants que vous ne pouvez pas recompiler et qui ont des déclarations d’appel de code non managé incorrectes, vous pouvez utiliser l' `NetFx40_PInvokeStackResilience` élément.</span><span class="sxs-lookup"><span data-stu-id="05627-133">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="05627-134">L’ajout de cet élément à votre fichier de configuration de l’application avec `enabled="1"` opte dans un mode de compatibilité avec le comportement des versions antérieures du .NET Framework, au détriment des transitions plus lentes.</span><span class="sxs-lookup"><span data-stu-id="05627-134">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="05627-135">Les assemblys qui ont été compilés sur des versions antérieures du .NET Framework sont automatiquement activés dans ce mode de compatibilité et n’ont pas besoin de cet élément.</span><span class="sxs-lookup"><span data-stu-id="05627-135">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="05627-136">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="05627-136">Configuration File</span></span>

<span data-ttu-id="05627-137">Cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="05627-137">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="05627-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="05627-138">Example</span></span>

<span data-ttu-id="05627-139">L’exemple suivant montre comment opter pour une meilleure résilience par rapport aux déclarations d’appel de code non managé incorrectes pour une application, au détriment de transitions plus lentes entre le code managé et le code non managé.</span><span class="sxs-lookup"><span data-stu-id="05627-139">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="05627-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05627-140">See also</span></span>

- [<span data-ttu-id="05627-141">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="05627-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="05627-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="05627-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="05627-143">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="05627-143">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
