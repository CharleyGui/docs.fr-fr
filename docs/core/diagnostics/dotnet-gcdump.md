---
title: outil de diagnostic dotnet-gcdump-CLI .NET
description: Découvrez comment installer et utiliser l’outil CLI dotnet-gcdump pour collecter des vidages de mémoire (garbage collector) de processus .NET en temps réel à l’aide de .NET EventPipe.
ms.date: 11/17/2020
ms.openlocfilehash: 59de1845ada9e5bdd0b24bf4312517283324ce94
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826038"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="8bb81-103">Outil d’analyse de tas (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="8bb81-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="8bb81-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="8bb81-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="8bb81-105">Installer</span><span class="sxs-lookup"><span data-stu-id="8bb81-105">Install</span></span>

<span data-ttu-id="8bb81-106">Il existe deux façons de télécharger et d’installer `dotnet-gcdump` :</span><span class="sxs-lookup"><span data-stu-id="8bb81-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="8bb81-107">**outil Global dotnet :**</span><span class="sxs-lookup"><span data-stu-id="8bb81-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="8bb81-108">Pour installer la dernière version Release du `dotnet-gcdump` [package NuGet](https://www.nuget.org/packages/dotnet-gcdump), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="8bb81-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="8bb81-109">**Téléchargement direct :**</span><span class="sxs-lookup"><span data-stu-id="8bb81-109">**Direct download:**</span></span>

  <span data-ttu-id="8bb81-110">Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="8bb81-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="8bb81-111">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="8bb81-111">OS</span></span>  | <span data-ttu-id="8bb81-112">Plateforme</span><span class="sxs-lookup"><span data-stu-id="8bb81-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="8bb81-113">Windows</span><span class="sxs-lookup"><span data-stu-id="8bb81-113">Windows</span></span> | <span data-ttu-id="8bb81-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [ARM](https://aka.ms/dotnet-gcdump/win-arm) \| [ARM-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="8bb81-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="8bb81-115">macOS</span><span class="sxs-lookup"><span data-stu-id="8bb81-115">macOS</span></span>   | [<span data-ttu-id="8bb81-116">x64</span><span class="sxs-lookup"><span data-stu-id="8bb81-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="8bb81-117">Linux</span><span class="sxs-lookup"><span data-stu-id="8bb81-117">Linux</span></span>   | <span data-ttu-id="8bb81-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [ARM](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="8bb81-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="8bb81-119">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8bb81-119">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="8bb81-120">Description</span><span class="sxs-lookup"><span data-stu-id="8bb81-120">Description</span></span>

<span data-ttu-id="8bb81-121">L' `dotnet-gcdump` outil Global collecte les vidages GC (garbage collector) des processus .net en temps réel à l’aide de [EventPipe](./eventpipe.md).</span><span class="sxs-lookup"><span data-stu-id="8bb81-121">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="8bb81-122">Les dumps GC sont créés en déclenchant un GC dans le processus cible, en activant des événements spéciaux et en régénérant le graphique des racines d’objets à partir du flux d’événements.</span><span class="sxs-lookup"><span data-stu-id="8bb81-122">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="8bb81-123">Ce processus permet de collecter des vidages de mémoire GC pendant que le processus est en cours d’exécution et avec une surcharge minimale.</span><span class="sxs-lookup"><span data-stu-id="8bb81-123">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="8bb81-124">Ces vidages sont utiles pour plusieurs scénarios :</span><span class="sxs-lookup"><span data-stu-id="8bb81-124">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="8bb81-125">Comparaison du nombre d’objets sur le tas à plusieurs points dans le temps.</span><span class="sxs-lookup"><span data-stu-id="8bb81-125">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="8bb81-126">Analyse des racines d’objets (réponse à des questions telles que « qu’est-ce qui a toujours une référence à ce type ? »).</span><span class="sxs-lookup"><span data-stu-id="8bb81-126">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="8bb81-127">Collecte des statistiques générales sur le nombre d’objets sur le tas.</span><span class="sxs-lookup"><span data-stu-id="8bb81-127">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="8bb81-128">Afficher le vidage GC capturé à partir de dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="8bb81-128">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="8bb81-129">Sur Windows, `.gcdump` les fichiers peuvent être affichés dans [PerfView](https://github.com/microsoft/perfview) pour l’analyse ou dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8bb81-129">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="8bb81-130">Actuellement, il n’existe aucun moyen d’ouvrir une `.gcdump` sur des plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="8bb81-130">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="8bb81-131">Vous pouvez collecter plusieurs `.gcdump` s et les ouvrir simultanément dans Visual Studio pour obtenir une comparaison.</span><span class="sxs-lookup"><span data-stu-id="8bb81-131">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="8bb81-132">Options</span><span class="sxs-lookup"><span data-stu-id="8bb81-132">Options</span></span>

- **`--version`**

  <span data-ttu-id="8bb81-133">Affiche la version de l' `dotnet-gcdump` utilitaire.</span><span class="sxs-lookup"><span data-stu-id="8bb81-133">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8bb81-134">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8bb81-134">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="8bb81-135">Collecte un vidage de mémoire GC à partir d’un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8bb81-135">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8bb81-136">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8bb81-136">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="8bb81-137">Options</span><span class="sxs-lookup"><span data-stu-id="8bb81-137">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="8bb81-138">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8bb81-138">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="8bb81-139">ID de processus à partir duquel collecter le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="8bb81-139">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="8bb81-140">Chemin d’accès où les dumps GC collectés doivent être écrits.</span><span class="sxs-lookup"><span data-stu-id="8bb81-140">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="8bb81-141">La valeur par défaut est *. \\ AAAAMMJJ \_ HHMMSS \_ \<pid> . gcdump*.</span><span class="sxs-lookup"><span data-stu-id="8bb81-141">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="8bb81-142">Sortie du journal lors de la collecte du vidage GC.</span><span class="sxs-lookup"><span data-stu-id="8bb81-142">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="8bb81-143">Abandonner la collecte du vidage GC s’il prend plus de temps que ce nombre de secondes.</span><span class="sxs-lookup"><span data-stu-id="8bb81-143">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="8bb81-144">La valeur par défaut est 30.</span><span class="sxs-lookup"><span data-stu-id="8bb81-144">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="8bb81-145">Nom du processus à partir duquel collecter le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="8bb81-145">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="8bb81-146">Répertorie les processus dotnet pour lesquels les dumps GC peuvent être collectés.</span><span class="sxs-lookup"><span data-stu-id="8bb81-146">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8bb81-147">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8bb81-147">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="8bb81-148">Générez un rapport à partir d’un vidage GC précédemment généré ou d’un processus en cours d’exécution, puis écrivez dans `stdout` .</span><span class="sxs-lookup"><span data-stu-id="8bb81-148">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8bb81-149">Synopsis</span><span class="sxs-lookup"><span data-stu-id="8bb81-149">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="8bb81-150">Options</span><span class="sxs-lookup"><span data-stu-id="8bb81-150">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="8bb81-151">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8bb81-151">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="8bb81-152">ID de processus à partir duquel collecter le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="8bb81-152">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="8bb81-153">Type de rapport à générer.</span><span class="sxs-lookup"><span data-stu-id="8bb81-153">The type of report to generate.</span></span> <span data-ttu-id="8bb81-154">Options disponibles : heapstat (par défaut).</span><span class="sxs-lookup"><span data-stu-id="8bb81-154">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="8bb81-155">Dépanner</span><span class="sxs-lookup"><span data-stu-id="8bb81-155">Troubleshoot</span></span>

- <span data-ttu-id="8bb81-156">Il n’y a pas d’informations de type dans le gcdump.</span><span class="sxs-lookup"><span data-stu-id="8bb81-156">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="8bb81-157">Avant .NET Core 3,1, il y avait un problème où un cache de type n’a pas été effacé entre gcdumps lorsqu’il a été appelé avec EventPipe.</span><span class="sxs-lookup"><span data-stu-id="8bb81-157">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="8bb81-158">Cela a entraîné les événements nécessaires pour déterminer les informations de type qui n’ont pas été envoyées pour la deuxième gcdumps et les autres.</span><span class="sxs-lookup"><span data-stu-id="8bb81-158">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="8bb81-159">Ce problème a été résolu dans .NET Core 3,1-preview2.</span><span class="sxs-lookup"><span data-stu-id="8bb81-159">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="8bb81-160">Les types COM et static ne sont pas dans le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="8bb81-160">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="8bb81-161">Avant .NET Core 3,1-preview2, il y avait un problème où les types static et COM n’étaient pas envoyés lorsque le vidage GC était appelé via EventPipe.</span><span class="sxs-lookup"><span data-stu-id="8bb81-161">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="8bb81-162">Ce problème a été résolu dans .NET Core 3,1-preview2.</span><span class="sxs-lookup"><span data-stu-id="8bb81-162">This has been fixed in .NET Core 3.1-preview2.</span></span>
