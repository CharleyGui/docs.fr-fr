---
title: Détection par défaut-.NET Core
description: Vue d’ensemble de la logique de sonde System. Runtime. Loader. AssemblyLoadContext. default de .NET Core pour localiser les dépendances.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 13ce4c7de5f6ce1b76b2e61db810c0f19717540f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608416"
---
# <a name="default-probing"></a><span data-ttu-id="c2dde-103">Détection par défaut</span><span class="sxs-lookup"><span data-stu-id="c2dde-103">Default probing</span></span>

<span data-ttu-id="c2dde-104">L' <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance est chargée de localiser les dépendances d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="c2dde-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="c2dde-105">Cet article décrit la <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> logique de sondage de l’instance.</span><span class="sxs-lookup"><span data-stu-id="c2dde-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="c2dde-106">Propriétés de détection de l’hôte configurées</span><span class="sxs-lookup"><span data-stu-id="c2dde-106">Host configured probing properties</span></span>

<span data-ttu-id="c2dde-107">Lorsque le runtime est démarré, l’hôte de Runtime fournit un ensemble de propriétés de détection nommées qui configurent les <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> chemins d’accès des sondes.</span><span class="sxs-lookup"><span data-stu-id="c2dde-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="c2dde-108">Chaque propriété de détection est facultative.</span><span class="sxs-lookup"><span data-stu-id="c2dde-108">Each probing property is optional.</span></span> <span data-ttu-id="c2dde-109">Si elle est présente, chaque propriété est une valeur de chaîne qui contient une liste délimitée de chemins absolus.</span><span class="sxs-lookup"><span data-stu-id="c2dde-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="c2dde-110">Le délimiteur est « ; » sur Windows et «  : » sur toutes les autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="c2dde-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="c2dde-111">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="c2dde-111">Property Name</span></span>                 |<span data-ttu-id="c2dde-112">Description</span><span class="sxs-lookup"><span data-stu-id="c2dde-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="c2dde-113">Liste des chemins d’accès aux fichiers d’assembly de plateforme et d’application.</span><span class="sxs-lookup"><span data-stu-id="c2dde-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="c2dde-114">Liste des chemins d’accès aux répertoires dans lesquels rechercher les assemblys de ressources satellites.</span><span class="sxs-lookup"><span data-stu-id="c2dde-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="c2dde-115">Liste des chemins d’accès aux répertoires dans lesquels rechercher les bibliothèques non managées (natives).</span><span class="sxs-lookup"><span data-stu-id="c2dde-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="c2dde-116">Liste des chemins d’accès aux répertoires dans lesquels rechercher des assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="c2dde-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="c2dde-117">Liste des chemins d’accès aux répertoires dans lesquels rechercher les images natives des assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="c2dde-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="c2dde-118">Comment les propriétés sont-elles renseignées ?</span><span class="sxs-lookup"><span data-stu-id="c2dde-118">How are the properties populated?</span></span>

<span data-ttu-id="c2dde-119">Il existe deux principaux scénarios pour remplir les propriétés selon que l' \* \<myapp>.deps.jssur\* le fichier existe.</span><span class="sxs-lookup"><span data-stu-id="c2dde-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="c2dde-120">Lorsque le \* \*.deps.jssur\* le fichier est présent, il est analysé pour renseigner les propriétés de détection.</span><span class="sxs-lookup"><span data-stu-id="c2dde-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="c2dde-121">Lorsque le \* \*.deps.jssur\* le fichier n’est pas présent, le répertoire de l’application est supposé contenir toutes les dépendances.</span><span class="sxs-lookup"><span data-stu-id="c2dde-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="c2dde-122">Le contenu du répertoire est utilisé pour remplir les propriétés de détection.</span><span class="sxs-lookup"><span data-stu-id="c2dde-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="c2dde-123">En outre, les \* \*.deps.js\* des fichiers pour les infrastructures référencées sont analysées de la même façon.</span><span class="sxs-lookup"><span data-stu-id="c2dde-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="c2dde-124">Enfin, la variable `ADDITIONAL_DEPS` d’environnement peut être utilisée pour ajouter des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="c2dde-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>  <span data-ttu-id="c2dde-125">`dotnet.exe` contient également un `--additional-deps` paramètre facultatif permettant de définir cette valeur au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="c2dde-125">`dotnet.exe` also contains an `--additional-deps` optional parameter to set this value on application startup.</span></span>

<span data-ttu-id="c2dde-126">Les `APP_PATHS` Propriétés et ne `APP_NI_PATHS` sont pas remplies par défaut et sont omises pour la plupart des applications.</span><span class="sxs-lookup"><span data-stu-id="c2dde-126">The `APP_PATHS` and `APP_NI_PATHS` properties are not populated by default and are omitted for most applications.</span></span>

<span data-ttu-id="c2dde-127">La liste de tous les \* \*.deps.jssur\* les fichiers utilisés par l’application est accessible via `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")` .</span><span class="sxs-lookup"><span data-stu-id="c2dde-127">The list of all *\*.deps.json* files used by the application can be accessed via `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")`.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="c2dde-128">Comment faire consultez les propriétés de détection à partir du code managé ?</span><span class="sxs-lookup"><span data-stu-id="c2dde-128">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="c2dde-129">Chaque propriété est disponible en appelant la <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> fonction avec le nom de la propriété à partir du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="c2dde-129">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="c2dde-130">Comment faire déboguer la construction des propriétés de détection ?</span><span class="sxs-lookup"><span data-stu-id="c2dde-130">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="c2dde-131">L’hôte du Runtime .NET Core génère des messages de trace utiles lorsque certaines variables d’environnement sont activées :</span><span class="sxs-lookup"><span data-stu-id="c2dde-131">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="c2dde-132">Variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="c2dde-132">Environment Variable</span></span>        |<span data-ttu-id="c2dde-133">Description</span><span class="sxs-lookup"><span data-stu-id="c2dde-133">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="c2dde-134">Active le suivi.</span><span class="sxs-lookup"><span data-stu-id="c2dde-134">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="c2dde-135">Effectue le suivi vers un chemin d’accès de fichier au lieu de la valeur par défaut `stderr` .</span><span class="sxs-lookup"><span data-stu-id="c2dde-135">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="c2dde-136">Définit les commentaires de 1 (le plus bas) à 4 (le plus élevé).</span><span class="sxs-lookup"><span data-stu-id="c2dde-136">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="c2dde-137">Détection par défaut de l’assembly managé</span><span class="sxs-lookup"><span data-stu-id="c2dde-137">Managed assembly default probing</span></span>

<span data-ttu-id="c2dde-138">Lors de la détection pour localiser un assembly managé, le se <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> présente dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="c2dde-138">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="c2dde-139">Fichiers correspondant <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> à la dans `TRUSTED_PLATFORM_ASSEMBLIES` (après la suppression des extensions de fichier).</span><span class="sxs-lookup"><span data-stu-id="c2dde-139">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="c2dde-140">Fichiers d’assembly d’images natives dans `APP_NI_PATHS` avec des extensions de fichier courantes.</span><span class="sxs-lookup"><span data-stu-id="c2dde-140">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="c2dde-141">Fichiers d’assembly dans `APP_PATHS` avec des extensions de fichier courantes.</span><span class="sxs-lookup"><span data-stu-id="c2dde-141">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="c2dde-142">Détection d’assembly satellite (ressource)</span><span class="sxs-lookup"><span data-stu-id="c2dde-142">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="c2dde-143">Pour rechercher un assembly satellite pour une culture spécifique, construisez un jeu de chemins d’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="c2dde-143">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="c2dde-144">Pour chaque chemin d’accès dans `PLATFORM_RESOURCE_ROOTS` `APP_PATHS` , puis, ajoutez la <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> chaîne, un séparateur de répertoires, la <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> chaîne et l’extension'. dll'.</span><span class="sxs-lookup"><span data-stu-id="c2dde-144">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="c2dde-145">Si un fichier correspondant existe, essayez de le charger et de le retourner.</span><span class="sxs-lookup"><span data-stu-id="c2dde-145">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="c2dde-146">Détection de bibliothèque non managée (Native)</span><span class="sxs-lookup"><span data-stu-id="c2dde-146">Unmanaged (native) library probing</span></span>

<span data-ttu-id="c2dde-147">Lors de la détection de la localisation d’une bibliothèque non managée, la recherche `NATIVE_DLL_SEARCH_DIRECTORIES` d’une bibliothèque correspondante est effectuée.</span><span class="sxs-lookup"><span data-stu-id="c2dde-147">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
