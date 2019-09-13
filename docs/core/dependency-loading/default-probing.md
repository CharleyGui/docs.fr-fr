---
title: Détection par défaut-.NET Core
description: Vue d’ensemble de la <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> logique de sondage de .net Core pour localiser les dépendances.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 2fa8a13bcb08a767fa965621f95bec8619aea5cc
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926405"
---
# <a name="default-probing"></a><span data-ttu-id="8bc53-103">Détection par défaut</span><span class="sxs-lookup"><span data-stu-id="8bc53-103">Default probing</span></span>

<span data-ttu-id="8bc53-104">L' <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance est chargée de localiser les dépendances d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="8bc53-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="8bc53-105">Cet article décrit la <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> logique de sondage de l’instance.</span><span class="sxs-lookup"><span data-stu-id="8bc53-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="8bc53-106">Propriétés de détection de l’hôte configurées</span><span class="sxs-lookup"><span data-stu-id="8bc53-106">Host configured probing properties</span></span>

<span data-ttu-id="8bc53-107">Lorsque le runtime est démarré, l’hôte de Runtime fournit un ensemble de propriétés de détection nommées <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> qui configurent les chemins d’accès des sondes.</span><span class="sxs-lookup"><span data-stu-id="8bc53-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="8bc53-108">Chaque propriété de détection est facultative.</span><span class="sxs-lookup"><span data-stu-id="8bc53-108">Each probing property is optional.</span></span>  <span data-ttu-id="8bc53-109">Si elle est présente, chaque propriété est une valeur de chaîne qui contient une liste délimitée de chemins absolus.</span><span class="sxs-lookup"><span data-stu-id="8bc53-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="8bc53-110">Le délimiteur est « ; » sur Windows et «  : » sur toutes les autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="8bc53-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="8bc53-111">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="8bc53-111">Property Name</span></span>                 |<span data-ttu-id="8bc53-112">Description</span><span class="sxs-lookup"><span data-stu-id="8bc53-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="8bc53-113">Liste des chemins d’accès aux fichiers d’assembly de plateforme et d’application.</span><span class="sxs-lookup"><span data-stu-id="8bc53-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="8bc53-114">Liste des chemins d’accès aux répertoires dans lesquels rechercher les assemblys de ressources satellites.</span><span class="sxs-lookup"><span data-stu-id="8bc53-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="8bc53-115">Liste des chemins d’accès aux répertoires dans lesquels rechercher les bibliothèques non managées (natives).</span><span class="sxs-lookup"><span data-stu-id="8bc53-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="8bc53-116">Liste des chemins d’accès aux répertoires dans lesquels rechercher des assemblys managés</span><span class="sxs-lookup"><span data-stu-id="8bc53-116">List of directory paths to search for managed assemblies</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="8bc53-117">Liste des chemins d’accès aux répertoires dans lesquels rechercher les images natives des assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="8bc53-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="8bc53-118">Comment les propriétés sont-elles renseignées ?</span><span class="sxs-lookup"><span data-stu-id="8bc53-118">How are the properties populated?</span></span>

<span data-ttu-id="8bc53-119">Il existe deux principaux scénarios pour remplir les propriétés selon que le `<myapp>.deps.json` fichier existe ou non.</span><span class="sxs-lookup"><span data-stu-id="8bc53-119">There are two main scenarios for populating the properties depending on whether the `<myapp>.deps.json` file exists.</span></span>

- <span data-ttu-id="8bc53-120">Quand le `*.deps.json` fichier est présent, il est analysé pour renseigner les propriétés de détection.</span><span class="sxs-lookup"><span data-stu-id="8bc53-120">When the `*.deps.json` file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="8bc53-121">Lorsque le `*.deps.json` fichier n’est pas présent, le répertoire de l’application est supposé contenir toutes les dépendances.</span><span class="sxs-lookup"><span data-stu-id="8bc53-121">When the `*.deps.json` file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="8bc53-122">Le contenu du répertoire est utilisé pour remplir les propriétés de détection.</span><span class="sxs-lookup"><span data-stu-id="8bc53-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="8bc53-123">En outre, les `*.deps.json` fichiers de toutes les infrastructures référencées sont analysés de la même façon.</span><span class="sxs-lookup"><span data-stu-id="8bc53-123">Additionally, the `*.deps.json` files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="8bc53-124">Enfin, la variable `ADDITIONAL_DEPS` d’environnement peut être utilisée pour ajouter des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="8bc53-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="8bc53-125">Comment faire consultez les propriétés de détection à partir du code managé ?</span><span class="sxs-lookup"><span data-stu-id="8bc53-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="8bc53-126">Chaque propriété est disponible en appelant la <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> fonction avec le nom de la propriété à partir du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="8bc53-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="8bc53-127">Comment faire déboguer la construction des propriétés de détection ?</span><span class="sxs-lookup"><span data-stu-id="8bc53-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="8bc53-128">L’hôte du Runtime .NET Core génère des messages de trace utiles lorsque certaines variables d’environnement sont activées :</span><span class="sxs-lookup"><span data-stu-id="8bc53-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="8bc53-129">Variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="8bc53-129">Environment Variable</span></span>        |<span data-ttu-id="8bc53-130">Description</span><span class="sxs-lookup"><span data-stu-id="8bc53-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="8bc53-131">Active le suivi.</span><span class="sxs-lookup"><span data-stu-id="8bc53-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="8bc53-132">Effectue le suivi vers un chemin d’accès de `stderr`fichier au lieu de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="8bc53-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="8bc53-133">Définit les commentaires de 1 (le plus bas) à 4 (le plus élevé).</span><span class="sxs-lookup"><span data-stu-id="8bc53-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="8bc53-134">Détection par défaut de l’assembly managé</span><span class="sxs-lookup"><span data-stu-id="8bc53-134">Managed assembly default probing</span></span>

<span data-ttu-id="8bc53-135">Lors de la détection pour localiser un assembly managé <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> , le se présente dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="8bc53-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="8bc53-136">Fichiers correspondant à <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> la `TRUSTED_PLATFORM_ASSEMBLIES` dans (après la suppression des extensions de fichier).</span><span class="sxs-lookup"><span data-stu-id="8bc53-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="8bc53-137">Fichiers d’assembly d' `APP_NI_PATHS` images natives dans avec des extensions de fichier courantes.</span><span class="sxs-lookup"><span data-stu-id="8bc53-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="8bc53-138">Fichiers d’assembly dans `APP_PATHS` avec des extensions de fichier courantes.</span><span class="sxs-lookup"><span data-stu-id="8bc53-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="8bc53-139">Détection d’assembly satellite (ressource)</span><span class="sxs-lookup"><span data-stu-id="8bc53-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="8bc53-140">Pour rechercher un assembly satellite pour une culture spécifique, construisez un jeu de chemins d’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="8bc53-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="8bc53-141">Pour chaque chemin d' `PLATFORM_RESOURCE_ROOTS` accès dans `APP_PATHS`, puis, <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> ajoutez la chaîne, un séparateur de <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> répertoires, la chaîne et l’extension'. dll'.</span><span class="sxs-lookup"><span data-stu-id="8bc53-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="8bc53-142">Si un fichier correspondant existe, essayez de le charger et de le retourner.</span><span class="sxs-lookup"><span data-stu-id="8bc53-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="8bc53-143">Détection de bibliothèque non managée (Native)</span><span class="sxs-lookup"><span data-stu-id="8bc53-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="8bc53-144">Lors de la détection de la localisation d’une bibliothèque non managée, la `NATIVE_DLL_SEARCH_DIRECTORIES` recherche d’une bibliothèque correspondante dans est effectuée.</span><span class="sxs-lookup"><span data-stu-id="8bc53-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library,</span></span>
