---
title: dotnet-gcdump-.NET Core
description: Installation et utilisation de l’outil en ligne de commande dotnet-gcdump.
ms.date: 07/26/2020
ms.openlocfilehash: a7b19f4d7487677b975621e7267a17894dae2e3a
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656649"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="65eb5-103">Outil d’analyse de tas (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="65eb5-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="65eb5-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="65eb5-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install-dotnet-gcdump"></a><span data-ttu-id="65eb5-105">Installer dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="65eb5-105">Install dotnet-gcdump</span></span>

<span data-ttu-id="65eb5-106">Pour installer la dernière version Release du `dotnet-gcdump` [package NuGet](https://www.nuget.org/packages/dotnet-gcdump), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="65eb5-106">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a><span data-ttu-id="65eb5-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="65eb5-107">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="65eb5-108">Description</span><span class="sxs-lookup"><span data-stu-id="65eb5-108">Description</span></span>

<span data-ttu-id="65eb5-109">L' `dotnet-gcdump` outil Global est un moyen de collecter des vidages de mémoire GC (garbage collector) des processus .net en direct.</span><span class="sxs-lookup"><span data-stu-id="65eb5-109">The `dotnet-gcdump` global tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span> <span data-ttu-id="65eb5-110">Il utilise la technologie EventPipe, qui est une alternative multiplateforme à ETW sur Windows.</span><span class="sxs-lookup"><span data-stu-id="65eb5-110">It uses the EventPipe technology, which is a cross-platform alternative to ETW on Windows.</span></span> <span data-ttu-id="65eb5-111">Les dumps GC sont créés en déclenchant un GC dans le processus cible, en activant des événements spéciaux et en régénérant le graphique des racines d’objets à partir du flux d’événements.</span><span class="sxs-lookup"><span data-stu-id="65eb5-111">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="65eb5-112">Ce processus permet de collecter des vidages de mémoire GC pendant que le processus est en cours d’exécution et avec une surcharge minimale.</span><span class="sxs-lookup"><span data-stu-id="65eb5-112">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="65eb5-113">Ces vidages sont utiles pour plusieurs scénarios :</span><span class="sxs-lookup"><span data-stu-id="65eb5-113">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="65eb5-114">Comparaison du nombre d’objets sur le tas à plusieurs points dans le temps.</span><span class="sxs-lookup"><span data-stu-id="65eb5-114">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="65eb5-115">Analyse des racines d’objets (réponse à des questions telles que « qu’est-ce qui a toujours une référence à ce type ? »).</span><span class="sxs-lookup"><span data-stu-id="65eb5-115">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="65eb5-116">Collecte des statistiques générales sur le nombre d’objets sur le tas.</span><span class="sxs-lookup"><span data-stu-id="65eb5-116">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="65eb5-117">Afficher le vidage GC capturé à partir de dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="65eb5-117">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="65eb5-118">Sur Windows, `.gcdump` les fichiers peuvent être affichés dans [PerfView](https://github.com/microsoft/perfview) pour l’analyse ou dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="65eb5-118">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="65eb5-119">Actuellement, il n’existe aucun moyen d’ouvrir une `.gcdump` sur des plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="65eb5-119">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="65eb5-120">Vous pouvez collecter plusieurs `.gcdump` s et les ouvrir simultanément dans Visual Studio pour obtenir une comparaison.</span><span class="sxs-lookup"><span data-stu-id="65eb5-120">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="65eb5-121">Options</span><span class="sxs-lookup"><span data-stu-id="65eb5-121">Options</span></span>

- **`--version`**

  <span data-ttu-id="65eb5-122">Affiche la version de l' `dotnet-gcdump` utilitaire.</span><span class="sxs-lookup"><span data-stu-id="65eb5-122">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="65eb5-123">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="65eb5-123">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="65eb5-124">Collecte un vidage de mémoire GC à partir d’un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="65eb5-124">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="65eb5-125">Synopsis</span><span class="sxs-lookup"><span data-stu-id="65eb5-125">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="65eb5-126">Options</span><span class="sxs-lookup"><span data-stu-id="65eb5-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="65eb5-127">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="65eb5-127">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="65eb5-128">ID de processus à partir duquel collecter le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="65eb5-128">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="65eb5-129">Chemin d’accès où les dumps GC collectés doivent être écrits.</span><span class="sxs-lookup"><span data-stu-id="65eb5-129">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="65eb5-130">La valeur par défaut est *. \\ AAAAMMJJ \_ HHMMSS \_ \<pid> . gcdump*.</span><span class="sxs-lookup"><span data-stu-id="65eb5-130">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="65eb5-131">Sortie du journal lors de la collecte du vidage GC.</span><span class="sxs-lookup"><span data-stu-id="65eb5-131">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="65eb5-132">Abandonner la collecte du vidage GC s’il prend plus de temps que ce nombre de secondes.</span><span class="sxs-lookup"><span data-stu-id="65eb5-132">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="65eb5-133">La valeur par défaut est 30.</span><span class="sxs-lookup"><span data-stu-id="65eb5-133">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="65eb5-134">Nom du processus à partir duquel collecter le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="65eb5-134">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="65eb5-135">Répertorie les processus dotnet pour lesquels les dumps GC peuvent être collectés.</span><span class="sxs-lookup"><span data-stu-id="65eb5-135">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="65eb5-136">Synopsis</span><span class="sxs-lookup"><span data-stu-id="65eb5-136">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="65eb5-137">Générez un rapport à partir d’un vidage GC précédemment généré ou d’un processus en cours d’exécution, puis écrivez dans `stdout` .</span><span class="sxs-lookup"><span data-stu-id="65eb5-137">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="65eb5-138">Synopsis</span><span class="sxs-lookup"><span data-stu-id="65eb5-138">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="65eb5-139">Options</span><span class="sxs-lookup"><span data-stu-id="65eb5-139">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="65eb5-140">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="65eb5-140">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="65eb5-141">ID de processus à partir duquel collecter le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="65eb5-141">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="65eb5-142">Type de rapport à générer.</span><span class="sxs-lookup"><span data-stu-id="65eb5-142">The type of report to generate.</span></span> <span data-ttu-id="65eb5-143">Options disponibles : heapstat (par défaut).</span><span class="sxs-lookup"><span data-stu-id="65eb5-143">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="65eb5-144">Dépanner</span><span class="sxs-lookup"><span data-stu-id="65eb5-144">Troubleshoot</span></span>

- <span data-ttu-id="65eb5-145">Il n’y a pas d’informations de type dans le gcdump.</span><span class="sxs-lookup"><span data-stu-id="65eb5-145">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="65eb5-146">Avant .NET Core 3,1, il y avait un problème où un cache de type n’a pas été effacé entre gcdumps lorsqu’il a été appelé avec EventPipe.</span><span class="sxs-lookup"><span data-stu-id="65eb5-146">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="65eb5-147">Cela a entraîné les événements nécessaires pour déterminer les informations de type qui n’ont pas été envoyées pour la deuxième gcdumps et les autres.</span><span class="sxs-lookup"><span data-stu-id="65eb5-147">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="65eb5-148">Ce problème a été résolu dans .NET Core 3,1-preview2.</span><span class="sxs-lookup"><span data-stu-id="65eb5-148">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="65eb5-149">Les types COM et static ne sont pas dans le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="65eb5-149">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="65eb5-150">Avant .NET Core 3,1-preview2, il y avait un problème où les types static et COM n’étaient pas envoyés lorsque le vidage GC était appelé via EventPipe.</span><span class="sxs-lookup"><span data-stu-id="65eb5-150">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="65eb5-151">Ce problème a été résolu dans .NET Core 3,1-preview2.</span><span class="sxs-lookup"><span data-stu-id="65eb5-151">This has been fixed in .NET Core 3.1-preview2.</span></span>
