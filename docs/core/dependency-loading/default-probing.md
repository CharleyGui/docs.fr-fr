---
title: Détection par défaut-.NET Core
description: Vue d’ensemble de la logique de sonde System. Runtime. Loader. AssemblyLoadContext. default de .NET Core pour localiser les dépendances.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 1e347c716c2d739a1bd03be056b57fdbda6c678f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859514"
---
# <a name="default-probing"></a><span data-ttu-id="61c68-103">Détection par défaut</span><span class="sxs-lookup"><span data-stu-id="61c68-103">Default probing</span></span>

<span data-ttu-id="61c68-104">L' <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance est chargée de localiser les dépendances d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="61c68-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="61c68-105">Cet article décrit la <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> logique de sondage de l’instance.</span><span class="sxs-lookup"><span data-stu-id="61c68-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="61c68-106">Propriétés de détection de l’hôte configurées</span><span class="sxs-lookup"><span data-stu-id="61c68-106">Host configured probing properties</span></span>

<span data-ttu-id="61c68-107">Lorsque le runtime est démarré, l’hôte de Runtime fournit un ensemble de propriétés de détection nommées <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> qui configurent les chemins d’accès des sondes.</span><span class="sxs-lookup"><span data-stu-id="61c68-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="61c68-108">Chaque propriété de détection est facultative.</span><span class="sxs-lookup"><span data-stu-id="61c68-108">Each probing property is optional.</span></span> <span data-ttu-id="61c68-109">Si elle est présente, chaque propriété est une valeur de chaîne qui contient une liste délimitée de chemins absolus.</span><span class="sxs-lookup"><span data-stu-id="61c68-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="61c68-110">Le délimiteur est « ; » sur Windows et «  : » sur toutes les autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="61c68-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="61c68-111">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="61c68-111">Property Name</span></span>                 |<span data-ttu-id="61c68-112">Description</span><span class="sxs-lookup"><span data-stu-id="61c68-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="61c68-113">Liste des chemins d’accès aux fichiers d’assembly de plateforme et d’application.</span><span class="sxs-lookup"><span data-stu-id="61c68-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="61c68-114">Liste des chemins d’accès aux répertoires dans lesquels rechercher les assemblys de ressources satellites.</span><span class="sxs-lookup"><span data-stu-id="61c68-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="61c68-115">Liste des chemins d’accès aux répertoires dans lesquels rechercher les bibliothèques non managées (natives).</span><span class="sxs-lookup"><span data-stu-id="61c68-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="61c68-116">Liste des chemins d’accès aux répertoires dans lesquels rechercher des assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="61c68-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="61c68-117">Liste des chemins d’accès aux répertoires dans lesquels rechercher les images natives des assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="61c68-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="61c68-118">Comment les propriétés sont-elles renseignées ?</span><span class="sxs-lookup"><span data-stu-id="61c68-118">How are the properties populated?</span></span>

<span data-ttu-id="61c68-119">Il existe deux principaux scénarios pour remplir les propriétés selon que le \* \<fichier MyApp>. DEPS. JSON\* existe ou non.</span><span class="sxs-lookup"><span data-stu-id="61c68-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="61c68-120">Quand le \* \*fichier. DEPS. JSON\* est présent, il est analysé pour remplir les propriétés de détection.</span><span class="sxs-lookup"><span data-stu-id="61c68-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="61c68-121">Quand le \* \*fichier. DEPS. JSON\* n’est pas présent, le répertoire de l’application est supposé contenir toutes les dépendances.</span><span class="sxs-lookup"><span data-stu-id="61c68-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="61c68-122">Le contenu du répertoire est utilisé pour remplir les propriétés de détection.</span><span class="sxs-lookup"><span data-stu-id="61c68-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="61c68-123">En outre, les \* \*fichiers. DEPS. JSON\* pour tous les frameworks référencés sont analysés de la même façon.</span><span class="sxs-lookup"><span data-stu-id="61c68-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="61c68-124">Enfin, la variable `ADDITIONAL_DEPS` d’environnement peut être utilisée pour ajouter des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="61c68-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

<span data-ttu-id="61c68-125">Les `APP_PATHS` propriétés `APP_NI_PATHS` et ne sont pas remplies par défaut et sont omises pour la plupart des applications.</span><span class="sxs-lookup"><span data-stu-id="61c68-125">The `APP_PATHS` and `APP_NI_PATHS` properties are not populated by default and are omitted for most applications.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="61c68-126">Comment faire consultez les propriétés de détection à partir du code managé ?</span><span class="sxs-lookup"><span data-stu-id="61c68-126">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="61c68-127">Chaque propriété est disponible en appelant la <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> fonction avec le nom de la propriété à partir du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="61c68-127">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="61c68-128">Comment faire déboguer la construction des propriétés de détection ?</span><span class="sxs-lookup"><span data-stu-id="61c68-128">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="61c68-129">L’hôte du Runtime .NET Core génère des messages de trace utiles lorsque certaines variables d’environnement sont activées :</span><span class="sxs-lookup"><span data-stu-id="61c68-129">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="61c68-130">Variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="61c68-130">Environment Variable</span></span>        |<span data-ttu-id="61c68-131">Description</span><span class="sxs-lookup"><span data-stu-id="61c68-131">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="61c68-132">Active le suivi.</span><span class="sxs-lookup"><span data-stu-id="61c68-132">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="61c68-133">Effectue le suivi vers un chemin d’accès de `stderr`fichier au lieu de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="61c68-133">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="61c68-134">Définit les commentaires de 1 (le plus bas) à 4 (le plus élevé).</span><span class="sxs-lookup"><span data-stu-id="61c68-134">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="61c68-135">Détection par défaut de l’assembly managé</span><span class="sxs-lookup"><span data-stu-id="61c68-135">Managed assembly default probing</span></span>

<span data-ttu-id="61c68-136">Lors de la détection pour localiser un assembly managé <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> , le se présente dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="61c68-136">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="61c68-137">Fichiers correspondant à <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> la `TRUSTED_PLATFORM_ASSEMBLIES` dans (après la suppression des extensions de fichier).</span><span class="sxs-lookup"><span data-stu-id="61c68-137">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="61c68-138">Fichiers d’assembly d' `APP_NI_PATHS` images natives dans avec des extensions de fichier courantes.</span><span class="sxs-lookup"><span data-stu-id="61c68-138">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="61c68-139">Fichiers d’assembly dans `APP_PATHS` avec des extensions de fichier courantes.</span><span class="sxs-lookup"><span data-stu-id="61c68-139">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="61c68-140">Détection d’assembly satellite (ressource)</span><span class="sxs-lookup"><span data-stu-id="61c68-140">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="61c68-141">Pour rechercher un assembly satellite pour une culture spécifique, construisez un jeu de chemins d’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="61c68-141">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="61c68-142">Pour chaque chemin d' `PLATFORM_RESOURCE_ROOTS` accès dans `APP_PATHS`, puis, <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> ajoutez la chaîne, un séparateur de <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> répertoires, la chaîne et l’extension'. dll'.</span><span class="sxs-lookup"><span data-stu-id="61c68-142">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="61c68-143">Si un fichier correspondant existe, essayez de le charger et de le retourner.</span><span class="sxs-lookup"><span data-stu-id="61c68-143">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="61c68-144">Détection de bibliothèque non managée (Native)</span><span class="sxs-lookup"><span data-stu-id="61c68-144">Unmanaged (native) library probing</span></span>

<span data-ttu-id="61c68-145">Lors de la détection de la localisation d’une bibliothèque non managée, la `NATIVE_DLL_SEARCH_DIRECTORIES` recherche d’une bibliothèque correspondante est effectuée.</span><span class="sxs-lookup"><span data-stu-id="61c68-145">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
