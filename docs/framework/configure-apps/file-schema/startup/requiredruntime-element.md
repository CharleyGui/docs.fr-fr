---
title: <requiredRuntime> (élément)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: 19fa1561ca3acd845918d952379c5227121465b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174067"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="2bb43-102">\<requiredRuntime>, élément</span><span class="sxs-lookup"><span data-stu-id="2bb43-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="2bb43-103">Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="2bb43-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="2bb43-104">Cet élément est déconseillé et ne doit plus être utilisé.</span><span class="sxs-lookup"><span data-stu-id="2bb43-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="2bb43-105">L' [`supportedRuntime`](supportedruntime-element.md) élément doit être utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="2bb43-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="2bb43-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bb43-106">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2bb43-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2bb43-107">Attributes and elements</span></span>

<span data-ttu-id="2bb43-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2bb43-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2bb43-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="2bb43-109">Attributes</span></span>

|<span data-ttu-id="2bb43-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2bb43-110">Attribute</span></span>|<span data-ttu-id="2bb43-111">Description</span><span class="sxs-lookup"><span data-stu-id="2bb43-111">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="2bb43-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="2bb43-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2bb43-113">Valeur de chaîne qui spécifie la version du .NET Framework que cette application prend en charge.</span><span class="sxs-lookup"><span data-stu-id="2bb43-113">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="2bb43-114">La valeur de chaîne doit correspondre au nom de répertoire trouvé sous la racine d’installation .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bb43-114">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="2bb43-115">Le contenu de la valeur de chaîne n’est pas analysé.</span><span class="sxs-lookup"><span data-stu-id="2bb43-115">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="2bb43-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="2bb43-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2bb43-117">Spécifie si le code de démarrage du runtime effectue une recherche dans le registre pour déterminer la version du Runtime.</span><span class="sxs-lookup"><span data-stu-id="2bb43-117">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="2bb43-118">safemode (attribut)</span><span class="sxs-lookup"><span data-stu-id="2bb43-118">safemode attribute</span></span>

|<span data-ttu-id="2bb43-119">Valeur</span><span class="sxs-lookup"><span data-stu-id="2bb43-119">Value</span></span>|<span data-ttu-id="2bb43-120">Description</span><span class="sxs-lookup"><span data-stu-id="2bb43-120">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="2bb43-121">Le code de démarrage du runtime recherche dans le registre.</span><span class="sxs-lookup"><span data-stu-id="2bb43-121">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="2bb43-122">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2bb43-122">This is the default value.</span></span>|
|`true`|<span data-ttu-id="2bb43-123">Le code de démarrage du runtime n’examine pas le registre.</span><span class="sxs-lookup"><span data-stu-id="2bb43-123">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2bb43-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2bb43-124">Child elements</span></span>

<span data-ttu-id="2bb43-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2bb43-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2bb43-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2bb43-126">Parent elements</span></span>

|<span data-ttu-id="2bb43-127">Élément</span><span class="sxs-lookup"><span data-stu-id="2bb43-127">Element</span></span>|<span data-ttu-id="2bb43-128">Description</span><span class="sxs-lookup"><span data-stu-id="2bb43-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2bb43-129">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bb43-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="2bb43-130">Contient l' `<requiredRuntime>` élément.</span><span class="sxs-lookup"><span data-stu-id="2bb43-130">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2bb43-131">Notes</span><span class="sxs-lookup"><span data-stu-id="2bb43-131">Remarks</span></span>

 <span data-ttu-id="2bb43-132">Les applications générées pour prendre en charge uniquement la version 1,0 du Runtime doivent utiliser l' `<requiredRuntime>` élément.</span><span class="sxs-lookup"><span data-stu-id="2bb43-132">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="2bb43-133">Les applications générées à l’aide de la version 1,1 ou ultérieure du Runtime doivent utiliser l' `<supportedRuntime>` élément.</span><span class="sxs-lookup"><span data-stu-id="2bb43-133">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="2bb43-134">Si vous utilisez la fonction [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) pour spécifier le fichier de configuration, vous devez utiliser l' `<requiredRuntime>` élément pour toutes les versions du Runtime.</span><span class="sxs-lookup"><span data-stu-id="2bb43-134">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="2bb43-135">L' `<supportedRuntime>` élément est ignoré lorsque vous utilisez [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="2bb43-135">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="2bb43-136">La `version` chaîne d’attribut doit correspondre au nom du dossier d’installation pour la version spécifiée du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bb43-136">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="2bb43-137">Cette chaîne n’est pas interprétée.</span><span class="sxs-lookup"><span data-stu-id="2bb43-137">This string is not interpreted.</span></span> <span data-ttu-id="2bb43-138">Si le code de démarrage du runtime ne trouve pas de dossier correspondant, le runtime n’est pas chargé ; le code de démarrage affiche un message d’erreur et se ferme.</span><span class="sxs-lookup"><span data-stu-id="2bb43-138">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="2bb43-139">Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore l' `<requiredRuntime>` élément.</span><span class="sxs-lookup"><span data-stu-id="2bb43-139">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="2bb43-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bb43-140">Example</span></span>

<span data-ttu-id="2bb43-141">L’exemple suivant montre comment spécifier la version du runtime dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="2bb43-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2bb43-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bb43-142">See also</span></span>

- [<span data-ttu-id="2bb43-143">Schéma des paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="2bb43-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2bb43-144">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="2bb43-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2bb43-145">Comment : configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="2bb43-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
