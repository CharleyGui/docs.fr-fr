---
title: outil de diagnostic dotnet-gcdump-CLI .NET
description: Découvrez comment installer et utiliser l’outil CLI dotnet-gcdump pour collecter des vidages de mémoire (garbage collector) de processus .NET en temps réel à l’aide de .NET EventPipe.
ms.date: 11/17/2020
ms.openlocfilehash: fe7772eed642daadbd1754627751f58d0ab57b8e
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188567"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="60def-103">Outil d’analyse de tas (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="60def-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="60def-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="60def-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="60def-105">Installer</span><span class="sxs-lookup"><span data-stu-id="60def-105">Install</span></span>

<span data-ttu-id="60def-106">Il existe deux façons de télécharger et d’installer `dotnet-gcdump` :</span><span class="sxs-lookup"><span data-stu-id="60def-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="60def-107">**outil Global dotnet :**</span><span class="sxs-lookup"><span data-stu-id="60def-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="60def-108">Pour installer la dernière version Release du `dotnet-gcdump` [package NuGet](https://www.nuget.org/packages/dotnet-gcdump), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="60def-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="60def-109">**Téléchargement direct :**</span><span class="sxs-lookup"><span data-stu-id="60def-109">**Direct download:**</span></span>

  <span data-ttu-id="60def-110">Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="60def-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="60def-111">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="60def-111">OS</span></span>  | <span data-ttu-id="60def-112">Plateforme</span><span class="sxs-lookup"><span data-stu-id="60def-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="60def-113">Windows</span><span class="sxs-lookup"><span data-stu-id="60def-113">Windows</span></span> | <span data-ttu-id="60def-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [ARM](https://aka.ms/dotnet-gcdump/win-arm) \| [ARM-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="60def-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="60def-115">macOS</span><span class="sxs-lookup"><span data-stu-id="60def-115">macOS</span></span>   | [<span data-ttu-id="60def-116">x64</span><span class="sxs-lookup"><span data-stu-id="60def-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="60def-117">Linux</span><span class="sxs-lookup"><span data-stu-id="60def-117">Linux</span></span>   | <span data-ttu-id="60def-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [ARM](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="60def-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="60def-119">Pour utiliser `dotnet-gcdump` sur une application x86, vous avez besoin d’une version x86 correspondante de l’outil.</span><span class="sxs-lookup"><span data-stu-id="60def-119">To use `dotnet-gcdump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="60def-120">Synopsis</span><span class="sxs-lookup"><span data-stu-id="60def-120">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="60def-121">Description</span><span class="sxs-lookup"><span data-stu-id="60def-121">Description</span></span>

<span data-ttu-id="60def-122">L' `dotnet-gcdump` outil Global collecte les vidages GC (garbage collector) des processus .net en temps réel à l’aide de [EventPipe](./eventpipe.md).</span><span class="sxs-lookup"><span data-stu-id="60def-122">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="60def-123">Les dumps GC sont créés en déclenchant un GC dans le processus cible, en activant des événements spéciaux et en régénérant le graphique des racines d’objets à partir du flux d’événements.</span><span class="sxs-lookup"><span data-stu-id="60def-123">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="60def-124">Ce processus permet de collecter des vidages de mémoire GC pendant que le processus est en cours d’exécution et avec une surcharge minimale.</span><span class="sxs-lookup"><span data-stu-id="60def-124">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="60def-125">Ces vidages sont utiles pour plusieurs scénarios :</span><span class="sxs-lookup"><span data-stu-id="60def-125">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="60def-126">Comparaison du nombre d’objets sur le tas à plusieurs points dans le temps.</span><span class="sxs-lookup"><span data-stu-id="60def-126">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="60def-127">Analyse des racines d’objets (réponse à des questions telles que « qu’est-ce qui a toujours une référence à ce type ? »).</span><span class="sxs-lookup"><span data-stu-id="60def-127">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="60def-128">Collecte des statistiques générales sur le nombre d’objets sur le tas.</span><span class="sxs-lookup"><span data-stu-id="60def-128">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="60def-129">Afficher le vidage GC capturé à partir de dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="60def-129">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="60def-130">Sur Windows, `.gcdump` les fichiers peuvent être affichés dans [PerfView](https://github.com/microsoft/perfview) pour l’analyse ou dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="60def-130">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="60def-131">Actuellement, il n’existe aucun moyen d’ouvrir une `.gcdump` sur des plateformes non-Windows.</span><span class="sxs-lookup"><span data-stu-id="60def-131">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="60def-132">Vous pouvez collecter plusieurs `.gcdump` s et les ouvrir simultanément dans Visual Studio pour obtenir une comparaison.</span><span class="sxs-lookup"><span data-stu-id="60def-132">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="60def-133">Options</span><span class="sxs-lookup"><span data-stu-id="60def-133">Options</span></span>

- **`--version`**

  <span data-ttu-id="60def-134">Affiche la version de l' `dotnet-gcdump` utilitaire.</span><span class="sxs-lookup"><span data-stu-id="60def-134">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="60def-135">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="60def-135">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="60def-136">Collecte un vidage de mémoire GC à partir d’un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="60def-136">Collects a GC dump from a currently running process.</span></span>

> [!WARNING]
> <span data-ttu-id="60def-137">Pour parcourir le tas GC, cette commande déclenche une garbage collection de génération 2 (complète), qui peut interrompre le runtime pendant une longue période, en particulier lorsque le tas GC est volumineux.</span><span class="sxs-lookup"><span data-stu-id="60def-137">To walk the GC heap, this command triggers a generation 2 (full) garbage collection, which can suspend the runtime for a long time, especially when the GC heap is large.</span></span> <span data-ttu-id="60def-138">N’utilisez pas cette commande dans les environnements sensibles aux performances lorsque le tas GC est volumineux.</span><span class="sxs-lookup"><span data-stu-id="60def-138">Don't use this command in performance-sensitive environments when the GC heap is large.</span></span>

### <a name="synopsis"></a><span data-ttu-id="60def-139">Synopsis</span><span class="sxs-lookup"><span data-stu-id="60def-139">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="60def-140">Options</span><span class="sxs-lookup"><span data-stu-id="60def-140">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="60def-141">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="60def-141">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="60def-142">ID de processus à partir duquel collecter le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="60def-142">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="60def-143">Chemin d’accès où les dumps GC collectés doivent être écrits.</span><span class="sxs-lookup"><span data-stu-id="60def-143">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="60def-144">La valeur par défaut est *. \\ AAAAMMJJ \_ HHMMSS \_ \<pid> . gcdump*.</span><span class="sxs-lookup"><span data-stu-id="60def-144">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="60def-145">Sortie du journal lors de la collecte du vidage GC.</span><span class="sxs-lookup"><span data-stu-id="60def-145">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="60def-146">Abandonner la collecte du vidage GC s’il prend plus de temps que ce nombre de secondes.</span><span class="sxs-lookup"><span data-stu-id="60def-146">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="60def-147">La valeur par défaut est 30.</span><span class="sxs-lookup"><span data-stu-id="60def-147">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="60def-148">Nom du processus à partir duquel collecter le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="60def-148">The name of the process to collect the GC dump from.</span></span>

> [!NOTE]
> <span data-ttu-id="60def-149">Sur Linux et macOS, cette commande attend l’application cible et `dotnet-gcdump` partager la même variable d' `TMPDIR` environnement.</span><span class="sxs-lookup"><span data-stu-id="60def-149">On Linux and macOS, this command expects the target application and `dotnet-gcdump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="60def-150">Dans le cas contraire, la commande expire.</span><span class="sxs-lookup"><span data-stu-id="60def-150">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="60def-151">Pour collecter un vidage GC à l’aide de `dotnet-gcdump` , il doit être exécuté en tant que même utilisateur que l’utilisateur qui exécute le processus cible ou en tant que racine.</span><span class="sxs-lookup"><span data-stu-id="60def-151">To collect a GC dump using `dotnet-gcdump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="60def-152">Dans le cas contraire, l’outil ne parviendra pas à établir une connexion avec le processus cible.</span><span class="sxs-lookup"><span data-stu-id="60def-152">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="60def-153">Répertorie les processus dotnet pour lesquels les dumps GC peuvent être collectés.</span><span class="sxs-lookup"><span data-stu-id="60def-153">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="60def-154">Synopsis</span><span class="sxs-lookup"><span data-stu-id="60def-154">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="60def-155">Générez un rapport à partir d’un vidage GC précédemment généré ou d’un processus en cours d’exécution, puis écrivez dans `stdout` .</span><span class="sxs-lookup"><span data-stu-id="60def-155">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="60def-156">Synopsis</span><span class="sxs-lookup"><span data-stu-id="60def-156">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="60def-157">Options</span><span class="sxs-lookup"><span data-stu-id="60def-157">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="60def-158">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="60def-158">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="60def-159">ID de processus à partir duquel collecter le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="60def-159">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="60def-160">Type de rapport à générer.</span><span class="sxs-lookup"><span data-stu-id="60def-160">The type of report to generate.</span></span> <span data-ttu-id="60def-161">Options disponibles : heapstat (par défaut).</span><span class="sxs-lookup"><span data-stu-id="60def-161">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="60def-162">Dépanner</span><span class="sxs-lookup"><span data-stu-id="60def-162">Troubleshoot</span></span>

- <span data-ttu-id="60def-163">Il n’y a pas d’informations de type dans le gcdump.</span><span class="sxs-lookup"><span data-stu-id="60def-163">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="60def-164">Avant .NET Core 3,1, il y avait un problème où un cache de type n’a pas été effacé entre gcdumps lorsqu’il a été appelé avec EventPipe.</span><span class="sxs-lookup"><span data-stu-id="60def-164">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="60def-165">Cela a entraîné les événements nécessaires pour déterminer les informations de type qui n’ont pas été envoyées pour la deuxième gcdumps et les autres.</span><span class="sxs-lookup"><span data-stu-id="60def-165">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="60def-166">Ce problème a été résolu dans .NET Core 3,1-preview2.</span><span class="sxs-lookup"><span data-stu-id="60def-166">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="60def-167">Les types COM et static ne sont pas dans le vidage GC.</span><span class="sxs-lookup"><span data-stu-id="60def-167">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="60def-168">Avant .NET Core 3,1-preview2, il y avait un problème où les types static et COM n’étaient pas envoyés lorsque le vidage GC était appelé via EventPipe.</span><span class="sxs-lookup"><span data-stu-id="60def-168">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="60def-169">Ce problème a été résolu dans .NET Core 3,1-preview2.</span><span class="sxs-lookup"><span data-stu-id="60def-169">This has been fixed in .NET Core 3.1-preview2.</span></span>
