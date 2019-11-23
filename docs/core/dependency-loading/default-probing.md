---
title: Détection par défaut-.NET Core
description: Vue d’ensemble de la logique de sonde System. Runtime. Loader. AssemblyLoadContext. default de .NET Core pour localiser les dépendances.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031830"
---
# <a name="default-probing"></a><span data-ttu-id="6971f-103">Détection par défaut</span><span class="sxs-lookup"><span data-stu-id="6971f-103">Default probing</span></span>

<span data-ttu-id="6971f-104">L’instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> est chargée de localiser les dépendances d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="6971f-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="6971f-105">Cet article décrit la logique de sondage de l’instance de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6971f-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="6971f-106">Propriétés de détection de l’hôte configurées</span><span class="sxs-lookup"><span data-stu-id="6971f-106">Host configured probing properties</span></span>

<span data-ttu-id="6971f-107">Lorsque le runtime est démarré, l’hôte de Runtime fournit un ensemble de propriétés de détection nommées qui configurent des chemins d’accès de sonde <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6971f-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="6971f-108">Chaque propriété de détection est facultative.</span><span class="sxs-lookup"><span data-stu-id="6971f-108">Each probing property is optional.</span></span> <span data-ttu-id="6971f-109">Si elle est présente, chaque propriété est une valeur de chaîne qui contient une liste délimitée de chemins absolus.</span><span class="sxs-lookup"><span data-stu-id="6971f-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="6971f-110">Le délimiteur est « ; » sur Windows et «  : » sur toutes les autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="6971f-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="6971f-111">Nom de propriété</span><span class="sxs-lookup"><span data-stu-id="6971f-111">Property Name</span></span>                 |<span data-ttu-id="6971f-112">Description</span><span class="sxs-lookup"><span data-stu-id="6971f-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="6971f-113">Liste des chemins d’accès aux fichiers d’assembly de plateforme et d’application.</span><span class="sxs-lookup"><span data-stu-id="6971f-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="6971f-114">Liste des chemins d’accès aux répertoires dans lesquels rechercher les assemblys de ressources satellites.</span><span class="sxs-lookup"><span data-stu-id="6971f-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="6971f-115">Liste des chemins d’accès aux répertoires dans lesquels rechercher les bibliothèques non managées (natives).</span><span class="sxs-lookup"><span data-stu-id="6971f-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="6971f-116">Liste des chemins d’accès aux répertoires dans lesquels rechercher des assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="6971f-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="6971f-117">Liste des chemins d’accès aux répertoires dans lesquels rechercher les images natives des assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="6971f-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="6971f-118">Comment les propriétés sont-elles renseignées ?</span><span class="sxs-lookup"><span data-stu-id="6971f-118">How are the properties populated?</span></span>

<span data-ttu-id="6971f-119">Il existe deux principaux scénarios pour remplir les propriétés selon que le *\<myapp >. DEPS. JSON* existe.</span><span class="sxs-lookup"><span data-stu-id="6971f-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="6971f-120">Quand le fichier *\*. DEPS. JSON* est présent, il est analysé pour renseigner les propriétés de détection.</span><span class="sxs-lookup"><span data-stu-id="6971f-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="6971f-121">Lorsque le fichier *\*. DEPS. JSON* n’est pas présent, le répertoire de l’application est supposé contenir toutes les dépendances.</span><span class="sxs-lookup"><span data-stu-id="6971f-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="6971f-122">Le contenu du répertoire est utilisé pour remplir les propriétés de détection.</span><span class="sxs-lookup"><span data-stu-id="6971f-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="6971f-123">En outre, les fichiers *\*. DEPS. JSON* pour tous les frameworks référencés sont analysés de la même façon.</span><span class="sxs-lookup"><span data-stu-id="6971f-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="6971f-124">Enfin, la variable d’environnement `ADDITIONAL_DEPS` peut être utilisée pour ajouter des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="6971f-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="6971f-125">Comment faire consultez les propriétés de détection à partir du code managé ?</span><span class="sxs-lookup"><span data-stu-id="6971f-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="6971f-126">Chaque propriété est disponible en appelant la fonction <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> avec le nom de la propriété à partir du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="6971f-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="6971f-127">Comment faire déboguer la construction des propriétés de détection ?</span><span class="sxs-lookup"><span data-stu-id="6971f-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="6971f-128">L’hôte du Runtime .NET Core génère des messages de trace utiles lorsque certaines variables d’environnement sont activées :</span><span class="sxs-lookup"><span data-stu-id="6971f-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="6971f-129">Variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="6971f-129">Environment Variable</span></span>        |<span data-ttu-id="6971f-130">Description</span><span class="sxs-lookup"><span data-stu-id="6971f-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="6971f-131">Active le suivi.</span><span class="sxs-lookup"><span data-stu-id="6971f-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="6971f-132">Effectue le suivi vers un chemin d’accès de fichier au lieu du `stderr`par défaut.</span><span class="sxs-lookup"><span data-stu-id="6971f-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="6971f-133">Définit les commentaires de 1 (le plus bas) à 4 (le plus élevé).</span><span class="sxs-lookup"><span data-stu-id="6971f-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="6971f-134">Détection par défaut de l’assembly managé</span><span class="sxs-lookup"><span data-stu-id="6971f-134">Managed assembly default probing</span></span>

<span data-ttu-id="6971f-135">Lors de la détection de la localisation d’un assembly managé, le <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> recherche dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="6971f-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="6971f-136">Fichiers correspondant à la <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dans `TRUSTED_PLATFORM_ASSEMBLIES` (après la suppression des extensions de fichier).</span><span class="sxs-lookup"><span data-stu-id="6971f-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="6971f-137">Fichiers d’assembly d’images natives dans `APP_NI_PATHS` avec des extensions de fichier courantes.</span><span class="sxs-lookup"><span data-stu-id="6971f-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="6971f-138">Fichiers d’assembly dans `APP_PATHS` avec des extensions de fichier courantes.</span><span class="sxs-lookup"><span data-stu-id="6971f-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="6971f-139">Détection d’assembly satellite (ressource)</span><span class="sxs-lookup"><span data-stu-id="6971f-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="6971f-140">Pour rechercher un assembly satellite pour une culture spécifique, construisez un jeu de chemins d’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="6971f-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="6971f-141">Pour chaque chemin d’accès dans `PLATFORM_RESOURCE_ROOTS` puis `APP_PATHS`, ajoutez la chaîne de <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>, un séparateur de répertoires, la chaîne de <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> et l’extension'. dll'.</span><span class="sxs-lookup"><span data-stu-id="6971f-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="6971f-142">Si un fichier correspondant existe, essayez de le charger et de le retourner.</span><span class="sxs-lookup"><span data-stu-id="6971f-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="6971f-143">Détection de bibliothèque non managée (Native)</span><span class="sxs-lookup"><span data-stu-id="6971f-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="6971f-144">Lors de la détection de la localisation d’une bibliothèque non managée, les `NATIVE_DLL_SEARCH_DIRECTORIES` sont recherchés dans la recherche d’une bibliothèque correspondante.</span><span class="sxs-lookup"><span data-stu-id="6971f-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
