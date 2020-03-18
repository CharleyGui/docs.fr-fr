---
title: Sondage par défaut - .NET Core
description: Aperçu de la logique de sondage .NET Core’s System.Runtime.Loader.AssemblyLoadContext.Default pour localiser les dépendances.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399090"
---
# <a name="default-probing"></a><span data-ttu-id="1c33b-103">Sondage par défaut</span><span class="sxs-lookup"><span data-stu-id="1c33b-103">Default probing</span></span>

<span data-ttu-id="1c33b-104">L’exemple <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> est responsable de la localisation des dépendances d’une assemblée.</span><span class="sxs-lookup"><span data-stu-id="1c33b-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="1c33b-105">Cet article décrit <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> la logique de sonder de l’instance.</span><span class="sxs-lookup"><span data-stu-id="1c33b-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="1c33b-106">Propriétés de sondage configurées par l’hôte</span><span class="sxs-lookup"><span data-stu-id="1c33b-106">Host configured probing properties</span></span>

<span data-ttu-id="1c33b-107">Lorsque le temps d’exécution est commencé, l’hôte de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> temps d’exécution fournit un ensemble de propriétés de sondage nommées qui configurent les trajectoires de sonde.</span><span class="sxs-lookup"><span data-stu-id="1c33b-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="1c33b-108">Chaque propriété de sondage est facultative.</span><span class="sxs-lookup"><span data-stu-id="1c33b-108">Each probing property is optional.</span></span> <span data-ttu-id="1c33b-109">Si elle est présente, chaque propriété est une valeur de chaîne qui contient une liste délimitée de chemins absolus.</span><span class="sxs-lookup"><span data-stu-id="1c33b-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="1c33b-110">Le délimitant est ';' sur Windows et ':' sur toutes les autres plates-formes.</span><span class="sxs-lookup"><span data-stu-id="1c33b-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="1c33b-111">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="1c33b-111">Property Name</span></span>                 |<span data-ttu-id="1c33b-112">Description</span><span class="sxs-lookup"><span data-stu-id="1c33b-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="1c33b-113">Liste des trajectoires de fichiers de plate-forme et d’assemblage d’applications.</span><span class="sxs-lookup"><span data-stu-id="1c33b-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="1c33b-114">Liste des parcours d’annuaires pour rechercher des assemblages de ressources par satellite.</span><span class="sxs-lookup"><span data-stu-id="1c33b-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="1c33b-115">Liste des parcours d’annuaires à la recherche de bibliothèques (autochtones) non gérantes.</span><span class="sxs-lookup"><span data-stu-id="1c33b-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="1c33b-116">Liste des parcours d’annuaires pour rechercher des assemblages gérés.</span><span class="sxs-lookup"><span data-stu-id="1c33b-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="1c33b-117">Liste des parcours de répertoire pour rechercher des images natives d’assemblages gérés.</span><span class="sxs-lookup"><span data-stu-id="1c33b-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="1c33b-118">Comment les propriétés sont-elles peuplées?</span><span class="sxs-lookup"><span data-stu-id="1c33b-118">How are the properties populated?</span></span>

<span data-ttu-id="1c33b-119">Il existe deux scénarios principaux pour peupler les propriétés selon que le \* \<fichier myapp>.deps.json\* existe.</span><span class="sxs-lookup"><span data-stu-id="1c33b-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="1c33b-120">Lorsque le \* \*fichier .deps.json\* est présent, il est analysé pour remplir les propriétés de sondage.</span><span class="sxs-lookup"><span data-stu-id="1c33b-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="1c33b-121">Lorsque le \* \*fichier .deps.json\* n’est pas présent, l’annuaire de l’application est supposé contenir toutes les dépendances.</span><span class="sxs-lookup"><span data-stu-id="1c33b-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="1c33b-122">Le contenu du répertoire est utilisé pour peupler les propriétés de sondage.</span><span class="sxs-lookup"><span data-stu-id="1c33b-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="1c33b-123">En outre, les \* \*fichiers .deps.json\* pour tous les cadres référencés sont analysés de la même façon.</span><span class="sxs-lookup"><span data-stu-id="1c33b-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="1c33b-124">Enfin, la `ADDITIONAL_DEPS` variable de l’environnement peut être utilisée pour ajouter des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="1c33b-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="1c33b-125">Comment puis-je voir les propriétés de sondage à partir de code géré?</span><span class="sxs-lookup"><span data-stu-id="1c33b-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="1c33b-126">Chaque propriété est disponible <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> en appelant la fonction avec le nom de propriété de la table ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="1c33b-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="1c33b-127">Comment puis-je déboiser la construction des propriétés de sondage?</span><span class="sxs-lookup"><span data-stu-id="1c33b-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="1c33b-128">L’hôte de temps d’exécution .NET Core produira des messages de trace utiles lorsque certaines variables de l’environnement sont activées :</span><span class="sxs-lookup"><span data-stu-id="1c33b-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="1c33b-129">Variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="1c33b-129">Environment Variable</span></span>        |<span data-ttu-id="1c33b-130">Description</span><span class="sxs-lookup"><span data-stu-id="1c33b-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="1c33b-131">Permet le traçage.</span><span class="sxs-lookup"><span data-stu-id="1c33b-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="1c33b-132">Traces à un chemin de `stderr`fichier au lieu de la valeur par défaut .</span><span class="sxs-lookup"><span data-stu-id="1c33b-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="1c33b-133">Définit la verbosité de 1 (plus bas) à 4 (le plus élevé).</span><span class="sxs-lookup"><span data-stu-id="1c33b-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="1c33b-134">Sondage par défaut d’assemblage géré</span><span class="sxs-lookup"><span data-stu-id="1c33b-134">Managed assembly default probing</span></span>

<span data-ttu-id="1c33b-135">Lorsque vous sonder pour <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> localiser un assemblage géré, les regards dans l’ordre à:</span><span class="sxs-lookup"><span data-stu-id="1c33b-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="1c33b-136">Fichiers correspondant <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` à l’in (après la suppression des extensions de fichiers).</span><span class="sxs-lookup"><span data-stu-id="1c33b-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="1c33b-137">Fichiers d’assemblage `APP_NI_PATHS` d’images autochtones avec des extensions de fichiers communes.</span><span class="sxs-lookup"><span data-stu-id="1c33b-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="1c33b-138">Fichiers d’assemblage `APP_PATHS` avec extensions de fichiers communes.</span><span class="sxs-lookup"><span data-stu-id="1c33b-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="1c33b-139">Sondage d’assemblage par satellite (ressources)</span><span class="sxs-lookup"><span data-stu-id="1c33b-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="1c33b-140">Pour trouver un assemblage satellite pour une culture spécifique, construisez un ensemble de pistes de fichiers.</span><span class="sxs-lookup"><span data-stu-id="1c33b-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="1c33b-141">Pour chaque `PLATFORM_RESOURCE_ROOTS` chemin `APP_PATHS`dans et <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> puis , ajouter la chaîne, un séparateur de répertoire, la <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> chaîne, et l’extension '.dll'.</span><span class="sxs-lookup"><span data-stu-id="1c33b-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="1c33b-142">S’il existe un fichier correspondant, essayez de le charger et de le retourner.</span><span class="sxs-lookup"><span data-stu-id="1c33b-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="1c33b-143">Une bibliothèque non gestion (indigène) sondage</span><span class="sxs-lookup"><span data-stu-id="1c33b-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="1c33b-144">Lorsque vous sondez pour localiser une `NATIVE_DLL_SEARCH_DIRECTORIES` bibliothèque non gémanie, les personnes sont recherchées à la recherche d’une bibliothèque assortie.</span><span class="sxs-lookup"><span data-stu-id="1c33b-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
