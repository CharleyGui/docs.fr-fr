---
title: <requiredRuntime>, élément
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697488"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="e5a4b-102">élément \<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="e5a4b-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="e5a4b-103">Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="e5a4b-104">Cet élément est déconseillé et ne doit plus être utilisé.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="e5a4b-105">L’élément [`supportedRuntime`](supportedruntime-element.md) doit être utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[<span data-ttu-id="e5a4b-106"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="e5a4b-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e5a4b-107">&nbsp;&nbsp;[ **\<de démarrage >** ](startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5a4b-107">&nbsp;&nbsp;[**\<startup>**](startup-element.md)</span></span>  
<span data-ttu-id="e5a4b-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<requiredRuntime >**</span><span class="sxs-lookup"><span data-stu-id="e5a4b-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="e5a4b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5a4b-109">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5a4b-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e5a4b-110">Attributes and elements</span></span>

<span data-ttu-id="e5a4b-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5a4b-112">Attributes</span><span class="sxs-lookup"><span data-stu-id="e5a4b-112">Attributes</span></span>

|<span data-ttu-id="e5a4b-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="e5a4b-113">Attribute</span></span>|<span data-ttu-id="e5a4b-114">Description</span><span class="sxs-lookup"><span data-stu-id="e5a4b-114">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="e5a4b-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e5a4b-116">Valeur de chaîne qui spécifie la version du .NET Framework que cette application prend en charge.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="e5a4b-117">La valeur de chaîne doit correspondre au nom de répertoire trouvé sous la racine d’installation .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="e5a4b-118">Le contenu de la valeur de chaîne n’est pas analysé.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-118">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="e5a4b-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e5a4b-120">Spécifie si le code de démarrage du runtime effectue une recherche dans le registre pour déterminer la version du Runtime.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="e5a4b-121">safemode (attribut)</span><span class="sxs-lookup"><span data-stu-id="e5a4b-121">safemode attribute</span></span>

|<span data-ttu-id="e5a4b-122">Value</span><span class="sxs-lookup"><span data-stu-id="e5a4b-122">Value</span></span>|<span data-ttu-id="e5a4b-123">Description</span><span class="sxs-lookup"><span data-stu-id="e5a4b-123">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="e5a4b-124">Le code de démarrage du runtime recherche dans le registre.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="e5a4b-125">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-125">This is the default value.</span></span>|
|`true`|<span data-ttu-id="e5a4b-126">Le code de démarrage du runtime n’examine pas le registre.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-126">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e5a4b-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e5a4b-127">Child elements</span></span>

<span data-ttu-id="e5a4b-128">Aucune.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-128">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5a4b-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e5a4b-129">Parent elements</span></span>

|<span data-ttu-id="e5a4b-130">Élément</span><span class="sxs-lookup"><span data-stu-id="e5a4b-130">Element</span></span>|<span data-ttu-id="e5a4b-131">Description</span><span class="sxs-lookup"><span data-stu-id="e5a4b-131">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e5a4b-132">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="e5a4b-133">Contient l’élément `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-133">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5a4b-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="e5a4b-134">Remarks</span></span>
 <span data-ttu-id="e5a4b-135">Les applications générées pour prendre en charge uniquement la version 1,0 du Runtime doivent utiliser l’élément `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="e5a4b-136">Les applications générées à l’aide de la version 1,1 ou ultérieure du Runtime doivent utiliser l’élément `<supportedRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="e5a4b-137">Si vous utilisez la fonction [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) pour spécifier le fichier de configuration, vous devez utiliser l’élément `<requiredRuntime>` pour toutes les versions du Runtime.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-137">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="e5a4b-138">L’élément `<supportedRuntime>` est ignoré lorsque vous utilisez [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="e5a4b-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="e5a4b-139">La chaîne d’attribut `version` doit correspondre au nom du dossier d’installation pour la version spécifiée du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="e5a4b-140">Cette chaîne n’est pas interprétée.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-140">This string is not interpreted.</span></span> <span data-ttu-id="e5a4b-141">Si le code de démarrage du runtime ne trouve pas de dossier correspondant, le runtime n’est pas chargé ; le code de démarrage affiche un message d’erreur et se ferme.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="e5a4b-142">Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore l’élément `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="e5a4b-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5a4b-143">Example</span></span>

<span data-ttu-id="e5a4b-144">L’exemple suivant montre comment spécifier la version du runtime dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e5a4b-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e5a4b-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5a4b-145">See also</span></span>

- [<span data-ttu-id="e5a4b-146">Schéma des paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="e5a4b-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e5a4b-147">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="e5a4b-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e5a4b-148">Comment : configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="e5a4b-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
