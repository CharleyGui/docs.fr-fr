---
title: dotnet-symbol-.NET Core
description: Installation et utilisation de l’outil en ligne de commande dotnet-symbol.
ms.date: 08/26/2020
ms.openlocfilehash: 5a96306fc96525b00e57eda089a45b730a7e3e8c
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679186"
---
# <a name="symbol-downloader-dotnet-symbol"></a><span data-ttu-id="bf5a2-103">Téléchargeur de symboles (dotnet-Symbol)</span><span class="sxs-lookup"><span data-stu-id="bf5a2-103">Symbol downloader (dotnet-symbol)</span></span>

<span data-ttu-id="bf5a2-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bf5a2-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-symbol"></a><span data-ttu-id="bf5a2-105">Installer dotnet-Symbol</span><span class="sxs-lookup"><span data-stu-id="bf5a2-105">Install dotnet-symbol</span></span>

<span data-ttu-id="bf5a2-106">Pour installer la dernière version Release du `dotnet-symbol` [package NuGet](https://www.nuget.org/packages/dotnet-symbol), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="bf5a2-106">To install the latest release version of the `dotnet-symbol` [NuGet package](https://www.nuget.org/packages/dotnet-symbol), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-symbol
```

## <a name="synopsis"></a><span data-ttu-id="bf5a2-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="bf5a2-107">Synopsis</span></span>

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a><span data-ttu-id="bf5a2-108">Description</span><span class="sxs-lookup"><span data-stu-id="bf5a2-108">Description</span></span>

<span data-ttu-id="bf5a2-109">L' `dotnet-symbol` outil Global télécharge les fichiers (symboles, DAC, modules, etc.) nécessaires pour le débogage des vidages et des minidumps principaux.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-109">The `dotnet-symbol` global tool downloads files (symbols, DAC, modules, etc.) needed for debugging core dumps and minidumps.</span></span> <span data-ttu-id="bf5a2-110">Cela peut être utile lors du débogage des vidages capturés sur un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-110">This can be useful when debugging dumps captured on another machine.</span></span> <span data-ttu-id="bf5a2-111">`dotnet-symbol` peut télécharger les modules et les symboles nécessaires pour analyser le vidage.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-111">`dotnet-symbol` can download modules and symbols needed to analyze the dump.</span></span>

## <a name="options"></a><span data-ttu-id="bf5a2-112">Options</span><span class="sxs-lookup"><span data-stu-id="bf5a2-112">Options</span></span>

- **`--microsoft-symbol-server`**

  <span data-ttu-id="bf5a2-113">Ajoutez le http://msdl.microsoft.com/download/symbols chemin d’accès du serveur de symboles' ' (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="bf5a2-113">Add 'http://msdl.microsoft.com/download/symbols' symbol server path (default).</span></span>

- **`--server-path <symbol server path>`**

  <span data-ttu-id="bf5a2-114">Ajoutez un serveur de symboles au chemin d’accès du serveur.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-114">Add a symbol server to the server path.</span></span>

- **`authenticated-server-path <pat> <server path>`**

  <span data-ttu-id="bf5a2-115">Ajoutez un serveur de symboles authentifié au chemin d’accès du serveur à l’aide d’un jeton d’accès personnel (PAT).</span><span class="sxs-lookup"><span data-stu-id="bf5a2-115">Add an authenticated symbol server to the server path using a personal access token (PAT).</span></span>

- **`--cache-directory <file cache directory>`**

  <span data-ttu-id="bf5a2-116">Ajoute un répertoire de cache.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-116">Adds a cache directory.</span></span>

- **`--recurse-subdirectories`**

  <span data-ttu-id="bf5a2-117">Traitez les fichiers d’entrée dans tous les sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-117">Process input files in all subdirectories.</span></span>

- **`--host-only`**

  <span data-ttu-id="bf5a2-118">Téléchargez uniquement le programme hôte (c’est-à-dire dotnet) dont lldb a besoin pour charger les vidages principaux.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-118">Download only the host program (i.e. dotnet) that lldb needs for loading core dumps.</span></span>

- **`--symbols`**

  <span data-ttu-id="bf5a2-119">Télécharger les fichiers de symboles (. pdb,. dbg,. nain).</span><span class="sxs-lookup"><span data-stu-id="bf5a2-119">Download symbol files (.pdb, .dbg, .dwarf).</span></span>

- **`--modules`**

  <span data-ttu-id="bf5a2-120">Téléchargez les fichiers de module (. dll,. so,. dylib).</span><span class="sxs-lookup"><span data-stu-id="bf5a2-120">Download the module files (.dll, .so, .dylib).</span></span>

- **`--debugging`**

  <span data-ttu-id="bf5a2-121">Téléchargez les modules de débogage spéciaux (DAC, DBI, SOS).</span><span class="sxs-lookup"><span data-stu-id="bf5a2-121">Download the special debugging modules (DAC, DBI, SOS).</span></span>

- **`--windows-pdbs`**

  <span data-ttu-id="bf5a2-122">Forcez le téléchargement des fichiers PDB Windows lorsque des fichiers PDB portables sont également disponibles.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-122">Force the downloading of the Windows PDBs when Portable PDBs are also available.</span></span>

- **`-o, --output <output directory>`**

  <span data-ttu-id="bf5a2-123">Définissez le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-123">Set the output directory.</span></span> <span data-ttu-id="bf5a2-124">Sinon, écrivez en regard du fichier d’entrée (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="bf5a2-124">Otherwise, write next to the input file (default).</span></span>

- **`-d, --diagnostics`**

  <span data-ttu-id="bf5a2-125">Activez la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-125">Enable diagnostic output.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bf5a2-126">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-126">Shows command-line help.</span></span>

## <a name="download-symbols"></a><span data-ttu-id="bf5a2-127">Télécharger des symboles</span><span class="sxs-lookup"><span data-stu-id="bf5a2-127">Download symbols</span></span>

<span data-ttu-id="bf5a2-128">S’exécuter `dotnet-symbol` sur un fichier dump, par défaut, télécharge tous les modules, les symboles et les fichiers DAC/DBI nécessaires pour déboguer le dump, y compris les assemblys managés.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-128">Running `dotnet-symbol` against a dump file will, by default, download all the modules, symbols, and DAC/DBI files needed to debug the dump including the managed assemblies.</span></span> <span data-ttu-id="bf5a2-129">Dans la mesure où SOS peut télécharger des symboles si nécessaire, la plupart des vidages noyau Linux peuvent être analysés à l’aide de lldb avec uniquement les modules d’hôte (dotnet) et de débogage.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-129">Because SOS can now download symbols when needed, most Linux core dumps can be analyzed using lldb with only the host (dotnet) and debugging modules.</span></span> <span data-ttu-id="bf5a2-130">Pour obtenir ces fichiers nécessaires au diagnostic d’un vidage de base avec lldb, exécutez :</span><span class="sxs-lookup"><span data-stu-id="bf5a2-130">To get these files necessary for diagnosing a core dump with lldb run:</span></span>

```console
dotnet-symbol --host-only --debugging <dump file path>
```

## <a name="troubleshoot"></a><span data-ttu-id="bf5a2-131">Dépanner</span><span class="sxs-lookup"><span data-stu-id="bf5a2-131">Troubleshoot</span></span>

- <span data-ttu-id="bf5a2-132">404 introuvable lors du téléchargement des symboles.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-132">404 Not Found while downloading symbols.</span></span>

   <span data-ttu-id="bf5a2-133">Le téléchargement de symboles n’est pris en charge que pour les versions officielles du Runtime .NET Core acquises par le biais de canaux officiels tels que [le site Web officiel](https://dotnet.microsoft.com/download/dotnet-core) et les [sources par défaut dans les scripts d’installation dotnet](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="bf5a2-133">Symbol download is only supported for official .NET Core runtime versions acquired through official channels such as [the official web site](https://dotnet.microsoft.com/download/dotnet-core) and the [default sources in the dotnet installation scripts](../tools/dotnet-install-script.md).</span></span> <span data-ttu-id="bf5a2-134">Une erreur 404 lors du téléchargement des fichiers de débogage peut indiquer que le dump a été créé avec un Runtime .NET Core à partir d’une autre source, telle que celle générée à partir de la source localement ou pour un distribution Linux particulier, ou à partir de sites de la communauté tels que Archlinux.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-134">A 404 error while downloading debugging files may indicate that the dump was created with a .NET Core runtime from another source, such as one built from source locally or for a particular Linux distro, or from community sites like archlinux.</span></span> <span data-ttu-id="bf5a2-135">Dans ce cas, le fichier nécessaire pour le débogage (dotnet, libcoreclr.so et libmscordaccore.so) doit être copié à partir de ces sources ou de l’environnement dans lequel le fichier de vidage a été créé.</span><span class="sxs-lookup"><span data-stu-id="bf5a2-135">In such cases, file necessary for debugging (dotnet, libcoreclr.so, and libmscordaccore.so) should be copied from those sources or from the environment the dump file was created in.</span></span>
