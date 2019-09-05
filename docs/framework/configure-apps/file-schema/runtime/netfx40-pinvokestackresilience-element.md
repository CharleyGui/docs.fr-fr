---
title: <NetFx40_PInvokeStackResilience>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f4dffe5428ccb7541055fa4f3f335f57deaf2ec
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252428"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="10e54-102">\<NetFx40_PInvokeStackResilience >, élément</span><span class="sxs-lookup"><span data-stu-id="10e54-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="10e54-103">Indique si le runtime corrige automatiquement les déclarations incorrectes d’appel de code non managé à l’exécution, au prix de transitions plus lentes entre le code managé et le code non managé.</span><span class="sxs-lookup"><span data-stu-id="10e54-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

<span data-ttu-id="10e54-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="10e54-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="10e54-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="10e54-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="10e54-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx40_PInvokeStackResilience >**</span><span class="sxs-lookup"><span data-stu-id="10e54-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="10e54-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10e54-107">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10e54-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="10e54-108">Attributes and Elements</span></span>

<span data-ttu-id="10e54-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="10e54-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="10e54-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="10e54-110">Attributes</span></span>

|<span data-ttu-id="10e54-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="10e54-111">Attribute</span></span>|<span data-ttu-id="10e54-112">Description</span><span class="sxs-lookup"><span data-stu-id="10e54-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="10e54-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="10e54-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="10e54-114">Spécifie si le runtime détecte des déclarations d’appel de code non managé incorrectes et résout automatiquement la pile au moment de l’exécution sur les plateformes 32 bits.</span><span class="sxs-lookup"><span data-stu-id="10e54-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="10e54-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="10e54-115">enabled Attribute</span></span>

|<span data-ttu-id="10e54-116">`Value`</span><span class="sxs-lookup"><span data-stu-id="10e54-116">Value</span></span>|<span data-ttu-id="10e54-117">Description</span><span class="sxs-lookup"><span data-stu-id="10e54-117">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="10e54-118">Le runtime utilise l’architecture de marshaling d’interopérabilité plus rapide introduite dans le .NET Framework 4, qui ne détecte pas et ne corrige pas les déclarations d’appel de code non managé incorrectes.</span><span class="sxs-lookup"><span data-stu-id="10e54-118">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="10e54-119">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="10e54-119">This is the default.</span></span>|
|`1`|<span data-ttu-id="10e54-120">Le runtime utilise des transitions plus lentes qui détectent et corrigent les déclarations d’appel de code non managé incorrectes.</span><span class="sxs-lookup"><span data-stu-id="10e54-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="10e54-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="10e54-121">Child Elements</span></span>

<span data-ttu-id="10e54-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="10e54-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10e54-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="10e54-123">Parent Elements</span></span>

|<span data-ttu-id="10e54-124">Élément</span><span class="sxs-lookup"><span data-stu-id="10e54-124">Element</span></span>|<span data-ttu-id="10e54-125">Description</span><span class="sxs-lookup"><span data-stu-id="10e54-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="10e54-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10e54-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="10e54-127">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="10e54-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="10e54-128">Notes</span><span class="sxs-lookup"><span data-stu-id="10e54-128">Remarks</span></span>

<span data-ttu-id="10e54-129">Cet élément vous permet d’échanger un marshaling d’interopérabilité plus rapide pour la résilience au moment de l’exécution contre les déclarations d’appel de code non managé incorrectes.</span><span class="sxs-lookup"><span data-stu-id="10e54-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="10e54-130">À partir du .NET Framework 4, une architecture de marshaling d’interopérabilité rationalisée offre une amélioration significative des performances des transitions du code managé vers du code non managé.</span><span class="sxs-lookup"><span data-stu-id="10e54-130">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="10e54-131">Dans les versions antérieures du .NET Framework, la couche de marshaling a détecté des déclarations d’appel de code non managé incorrectes sur les plateformes 32 bits et a résolu automatiquement la pile.</span><span class="sxs-lookup"><span data-stu-id="10e54-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="10e54-132">La nouvelle architecture de marshaling élimine cette étape.</span><span class="sxs-lookup"><span data-stu-id="10e54-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="10e54-133">Par conséquent, les transitions sont très rapides, mais une déclaration d’appel de code non managé incorrecte peut provoquer un échec de programme.</span><span class="sxs-lookup"><span data-stu-id="10e54-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="10e54-134">Pour faciliter la détection des déclarations incorrectes pendant le développement, l’expérience de débogage de Visual Studio a été améliorée.</span><span class="sxs-lookup"><span data-stu-id="10e54-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="10e54-135">L’Assistant Débogage managé (MDA) [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) vous avertit des déclarations d’appel de code non managé incorrectes lorsque votre application s’exécute avec le débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="10e54-135">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="10e54-136">Pour traiter les scénarios où votre application utilise des composants que vous ne pouvez pas recompiler et qui ont des déclarations d’appel de code `NetFx40_PInvokeStackResilience` non managé incorrectes, vous pouvez utiliser l’élément.</span><span class="sxs-lookup"><span data-stu-id="10e54-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="10e54-137">L’ajout de cet élément à votre fichier de `enabled="1"` configuration de l’application avec opte dans un mode de compatibilité avec le comportement des versions antérieures du .NET Framework, au détriment des transitions plus lentes.</span><span class="sxs-lookup"><span data-stu-id="10e54-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="10e54-138">Les assemblys qui ont été compilés sur des versions antérieures du .NET Framework sont automatiquement activés dans ce mode de compatibilité et n’ont pas besoin de cet élément.</span><span class="sxs-lookup"><span data-stu-id="10e54-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="10e54-139">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="10e54-139">Configuration File</span></span>

<span data-ttu-id="10e54-140">Cet élément peut être utilisé uniquement dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="10e54-140">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="10e54-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="10e54-141">Example</span></span>

<span data-ttu-id="10e54-142">L’exemple suivant montre comment opter pour une meilleure résilience par rapport aux déclarations d’appel de code non managé incorrectes pour une application, au détriment de transitions plus lentes entre le code managé et le code non managé.</span><span class="sxs-lookup"><span data-stu-id="10e54-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="10e54-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10e54-143">See also</span></span>

- [<span data-ttu-id="10e54-144">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="10e54-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="10e54-145">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="10e54-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="10e54-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="10e54-146">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
