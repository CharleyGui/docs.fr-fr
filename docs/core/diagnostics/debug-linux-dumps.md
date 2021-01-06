---
title: Déboguer des vidages Linux
description: Dans cet article, vous allez apprendre à collecter et à analyser les vidages des environnements Linux.
ms.date: 08/27/2020
ms.openlocfilehash: e6f2eea3af718853ad7365a5209b397a66035dde
ms.sourcegitcommit: 35ca2255c6c86968eaef9e3a251c9739ce8e4288
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97753599"
---
# <a name="debug-linux-dumps"></a><span data-ttu-id="3fa12-103">Déboguer des vidages Linux</span><span class="sxs-lookup"><span data-stu-id="3fa12-103">Debug Linux dumps</span></span>

<span data-ttu-id="3fa12-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="3fa12-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

## <a name="collect-dumps-on-linux"></a><span data-ttu-id="3fa12-105">Collecter des vidages sur Linux</span><span class="sxs-lookup"><span data-stu-id="3fa12-105">Collect dumps on Linux</span></span>

<span data-ttu-id="3fa12-106">Les deux méthodes recommandées pour collecter des vidages sur Linux sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3fa12-106">The two recommended ways of collecting dumps on Linux are:</span></span>

* <span data-ttu-id="3fa12-107">[`dotnet-dump`](dotnet-dump.md) Outil CLI</span><span class="sxs-lookup"><span data-stu-id="3fa12-107">[`dotnet-dump`](dotnet-dump.md) CLI tool</span></span>
* <span data-ttu-id="3fa12-108">[Variables d’environnement](dumps.md#collecting-dumps-on-crash) qui recueillent des vidages sur les incidents</span><span class="sxs-lookup"><span data-stu-id="3fa12-108">[Environment variables](dumps.md#collecting-dumps-on-crash) that collect dumps on crashes</span></span>

### <a name="managed-dumps-with-dotnet-dump"></a><span data-ttu-id="3fa12-109">Dumps managés avec `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="3fa12-109">Managed dumps with `dotnet-dump`</span></span>

<span data-ttu-id="3fa12-110">L' [`dotnet-dump`](dotnet-dump.md) outil est simple à utiliser et n’a pas de dépendance sur les débogueurs natifs.</span><span class="sxs-lookup"><span data-stu-id="3fa12-110">The [`dotnet-dump`](dotnet-dump.md) tool is simple to use, and does not have a dependency on any native debuggers.</span></span> <span data-ttu-id="3fa12-111">`dotnet-dump` fonctionne sur un large éventail de plates-formes Linux (telles que Alpine ou ARM32/ARM64) où les outils de débogage traditionnels ne sont peut-être pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="3fa12-111">`dotnet-dump` works on a wide variety of Linux platforms (like Alpine or ARM32/ARM64) where traditional debugging tools may not be available.</span></span> <span data-ttu-id="3fa12-112">Toutefois, `dotnet-dump` ne capture que l’état managé afin qu’il ne puisse pas être utilisé pour déboguer des problèmes en code natif.</span><span class="sxs-lookup"><span data-stu-id="3fa12-112">However, `dotnet-dump` only captures managed state so it can't be used for debugging issues in native code.</span></span> <span data-ttu-id="3fa12-113">Les vidages collectés par `dotnet-dump` sont analysés dans un environnement avec le système d’exploitation et l’architecture sur lesquels le dump a été créé.</span><span class="sxs-lookup"><span data-stu-id="3fa12-113">Dumps collected by `dotnet-dump` are analyzed in an environment with the same OS and architecture the dump was created on.</span></span> <span data-ttu-id="3fa12-114">L' [`dotnet-gcdump`](dotnet-gcdump.md) outil peut être utilisé comme alternative qui capture uniquement les informations du tas GC, mais produit des vidages qui peuvent être analysés sur Windows.</span><span class="sxs-lookup"><span data-stu-id="3fa12-114">The [`dotnet-gcdump`](dotnet-gcdump.md) tool can be used as an alternative that only captures GC heap information but produces dumps that can be analyzed on Windows.</span></span>

### <a name="core-dumps-with-createdump"></a><span data-ttu-id="3fa12-115">Vidages principaux avec `createdump`</span><span class="sxs-lookup"><span data-stu-id="3fa12-115">Core dumps with `createdump`</span></span>

<span data-ttu-id="3fa12-116">En guise d’alternative à `dotnet-dump` , qui crée des dumps managés uniquement, [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) est l’outil recommandé pour créer des vidages principaux sur Linux contenant des informations natives et managées.</span><span class="sxs-lookup"><span data-stu-id="3fa12-116">As an alternative to `dotnet-dump`, which creates managed-only dumps, [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) is the recommended tool for creating core dumps on Linux containing both native and managed information.</span></span> <span data-ttu-id="3fa12-117">D’autres outils tels que gdb ou gcore peuvent également être utilisés pour créer des vidages essentiels, mais ils peuvent manquer d’État pour le débogage managé, ce qui entraîne des noms de type ou de fonction « inconnus » lors de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="3fa12-117">Other tools like gdb or gcore can also be used to create core dumps but may miss state needed for managed debugging, resulting in "UNKNOWN" type or function names during analysis.</span></span>

<span data-ttu-id="3fa12-118">L' `createdump` outil est installé avec le Runtime .net Core et se trouve en regard de libcoreclr.so (généralement dans « /usr/share/dotnet/Shared/Microsoft.NETCore.app/[version] »).</span><span class="sxs-lookup"><span data-stu-id="3fa12-118">The `createdump` tool is installed with the .NET Core runtime and can be found next to libcoreclr.so (typically in "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]").</span></span> <span data-ttu-id="3fa12-119">L’outil prend un ID de processus pour collecter un dump à partir de comme son argument principal et peut également accepter des paramètres facultatifs qui spécifient le type de vidage à collecter (un minidump avec segment de mémoire est la valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="3fa12-119">The tool takes a process ID to collect a dump from as its primary argument and can also take optional parameters specifying what kind of dump to collect (a minidump with heap is the default).</span></span> <span data-ttu-id="3fa12-120">Options disponibles :</span><span class="sxs-lookup"><span data-stu-id="3fa12-120">Options include:</span></span>

- **`<input-filename>`**

  <span data-ttu-id="3fa12-121">Fichier de trace d’entrée à convertir.</span><span class="sxs-lookup"><span data-stu-id="3fa12-121">Input trace file to be converted.</span></span> <span data-ttu-id="3fa12-122">La valeur par défaut est *trace. NetTrace*.</span><span class="sxs-lookup"><span data-stu-id="3fa12-122">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="3fa12-123">Options</span><span class="sxs-lookup"><span data-stu-id="3fa12-123">Options</span></span>

- **`-f|--name <output-filename>`**

  <span data-ttu-id="3fa12-124">Fichier dans lequel écrire le vidage.</span><span class="sxs-lookup"><span data-stu-id="3fa12-124">The file to write the dump to.</span></span> <span data-ttu-id="3fa12-125">La valeur par défaut est « /tmp/coredump.%p », où% p est l’ID de processus du processus cible.</span><span class="sxs-lookup"><span data-stu-id="3fa12-125">Default is '/tmp/coredump.%p' where %p is the process ID of the target process.</span></span>

- **`-n|--normal`**

  <span data-ttu-id="3fa12-126">Créez un minidump.</span><span class="sxs-lookup"><span data-stu-id="3fa12-126">Create a minidump.</span></span>

- **`-h|--withheap`**

  <span data-ttu-id="3fa12-127">Créez un minidump avec segment mémoire (par défaut).</span><span class="sxs-lookup"><span data-stu-id="3fa12-127">Create a minidump with heap (default).</span></span>

- **`-t|--triage`**

  <span data-ttu-id="3fa12-128">Créez un minidump de triage.</span><span class="sxs-lookup"><span data-stu-id="3fa12-128">Create a triage minidump.</span></span>

- **`-u|--full`**

  <span data-ttu-id="3fa12-129">Créez un vidage de noyau complet.</span><span class="sxs-lookup"><span data-stu-id="3fa12-129">Create a full core dump.</span></span>

- **`-d|--diag`**

  <span data-ttu-id="3fa12-130">Activez les messages de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="3fa12-130">Enable diagnostic messages.</span></span>

<span data-ttu-id="3fa12-131">La collecte des vidages centraux requiert la `SYS_PTRACE` fonctionnalité ou l' `createdump` exécution avec sudo ou su.</span><span class="sxs-lookup"><span data-stu-id="3fa12-131">Collecting core dumps requires either the `SYS_PTRACE` capability or that `createdump` be run with sudo or su.</span></span>

## <a name="analyze-dumps-on-linux"></a><span data-ttu-id="3fa12-132">Analyser les vidages sur Linux</span><span class="sxs-lookup"><span data-stu-id="3fa12-132">Analyze dumps on Linux</span></span>

<span data-ttu-id="3fa12-133">Les dumps managés collectés avec `dotnet-dump` et les vidages de noyau collectés avec `createdump` peuvent être analysés avec l' `dotnet-dump` outil à l’aide de la `dotnet-dump analyze` commande.</span><span class="sxs-lookup"><span data-stu-id="3fa12-133">Both managed dumps collected with `dotnet-dump` and core dumps collected with `createdump` can be analyzed with the `dotnet-dump` tool using the `dotnet-dump analyze` command.</span></span> <span data-ttu-id="3fa12-134">Le `dotnet dump` requiert que l’environnement qui analyse le dump ait le même système d’exploitation et l’même architecture que l’environnement dans lequel le dump a été capturé.</span><span class="sxs-lookup"><span data-stu-id="3fa12-134">The `dotnet dump` requires that the environment analyzing the dump has the same OS and architecture as the environment the dump was captured in.</span></span>

<span data-ttu-id="3fa12-135">Vous pouvez également utiliser [LLDB](https://lldb.llvm.org/) pour analyser les vidages principaux sur Linux, ce qui permet l’analyse des frames managés et natifs.</span><span class="sxs-lookup"><span data-stu-id="3fa12-135">Alternatively, [LLDB](https://lldb.llvm.org/) can be used to analyze core dumps on Linux, which allows analysis of both managed and native frames.</span></span> <span data-ttu-id="3fa12-136">LLDB utilise l’extension SOS pour déboguer le code managé.</span><span class="sxs-lookup"><span data-stu-id="3fa12-136">LLDB uses the SOS extension to debug managed code.</span></span> <span data-ttu-id="3fa12-137">L' [`dotnet-sos`](dotnet-sos.md) outil CLI peut être utilisé pour installer SOS, qui contient de [nombreuses commandes utiles](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) pour déboguer le code managé.</span><span class="sxs-lookup"><span data-stu-id="3fa12-137">The [`dotnet-sos`](dotnet-sos.md) CLI tool can be used to install SOS, which has [many useful commands](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) for debugging managed code.</span></span> <span data-ttu-id="3fa12-138">Pour analyser les vidages .NET Core, LLDB et SOS requièrent les binaires .NET Core suivants de l’environnement dans lequel le dump a été créé :</span><span class="sxs-lookup"><span data-stu-id="3fa12-138">In order to analyze .NET Core dumps, LLDB and SOS require the following .NET Core binaries from the environment the dump was created in:</span></span>

1. <span data-ttu-id="3fa12-139">libmscordaccore.so</span><span class="sxs-lookup"><span data-stu-id="3fa12-139">libmscordaccore.so</span></span>
2. <span data-ttu-id="3fa12-140">libcoreclr.so</span><span class="sxs-lookup"><span data-stu-id="3fa12-140">libcoreclr.so</span></span>
3. <span data-ttu-id="3fa12-141">dotnet (l’hôte utilisé pour lancer l’application)</span><span class="sxs-lookup"><span data-stu-id="3fa12-141">dotnet (the host used to launch the app)</span></span>

<span data-ttu-id="3fa12-142">Dans la plupart des cas, ces fichiers binaires peuvent être téléchargés à l’aide de l' [`dotnet-symbol`](dotnet-symbol.md) outil.</span><span class="sxs-lookup"><span data-stu-id="3fa12-142">In most cases, these binaries can be downloaded using the [`dotnet-symbol`](dotnet-symbol.md) tool.</span></span> <span data-ttu-id="3fa12-143">Si les fichiers binaires nécessaires ne peuvent pas être téléchargés avec `dotnet-symbol` (par exemple, si une version privée de .net Core générée à partir de la source était en cours d’utilisation), il peut être nécessaire de copier les fichiers listés ci-dessus à partir de l’environnement dans lequel le dump a été créé.</span><span class="sxs-lookup"><span data-stu-id="3fa12-143">If the necessary binaries can't be downloaded with `dotnet-symbol` (for example, if a private version of .NET Core built from source was in use), it may be necessary to copy the files listed above from the environment the dump was created in.</span></span> <span data-ttu-id="3fa12-144">Si les fichiers ne sont pas situés à côté du fichier dump, vous pouvez utiliser la commande LLDB/SOS `setclrpath <path>` pour définir le chemin à partir duquel ils doivent être chargés et `setsymbolserver -directory <path>` pour définir le chemin d’accès à rechercher pour les fichiers de symboles.</span><span class="sxs-lookup"><span data-stu-id="3fa12-144">If the files aren't located next to the dump file, you can use the LLDB/SOS command `setclrpath <path>` to set the path they should be loaded from and `setsymbolserver -directory <path>` to set the path to look in for symbol files.</span></span>

<span data-ttu-id="3fa12-145">Une fois les fichiers nécessaires disponibles, le vidage peut être chargé dans LLDB en spécifiant l’hôte dotnet comme exécutable à déboguer :</span><span class="sxs-lookup"><span data-stu-id="3fa12-145">Once the necessary files are available, the dump can be loaded in LLDB by specifying the dotnet host as the executable to debug:</span></span>

```console
lldb --core <dump-file> <host-program>
```

<span data-ttu-id="3fa12-146">Dans la ligne de commande ci-dessus, `<dump-file>` est le chemin d’accès de l’image mémoire à analyser et `<host-program>` est le programme natif qui a démarré l’application .net core.</span><span class="sxs-lookup"><span data-stu-id="3fa12-146">In the above command line, `<dump-file>` is the path of the dump to analyze and `<host-program>` is the native program that started the .NET Core application.</span></span> <span data-ttu-id="3fa12-147">Il s’agit généralement du `dotnet` binaire, à moins que l’application ne soit autonome, auquel cas il s’agit du nom de l’application sans l’extension dll.</span><span class="sxs-lookup"><span data-stu-id="3fa12-147">This is typically the `dotnet` binary unless the app is self-contained, in which case it is the name of the application without the dll extension.</span></span>

<span data-ttu-id="3fa12-148">Une fois LLDB démarré, il peut être nécessaire d’utiliser la `setsymbolserver` commande pour pointer vers l’emplacement de symbole approprié ( `setsymbolserver -ms` pour utiliser le serveur de symboles de Microsoft ou `setsymbolserver -directory <path>` pour spécifier un chemin d’accès local).</span><span class="sxs-lookup"><span data-stu-id="3fa12-148">Once LLDB starts, it may be necessary to use the `setsymbolserver` command to point at the correct symbol location (`setsymbolserver -ms` to use Microsoft's symbol server or `setsymbolserver -directory <path>` to specify a local path).</span></span> <span data-ttu-id="3fa12-149">Les symboles natifs peuvent être chargés en exécutant `loadsymbols` .</span><span class="sxs-lookup"><span data-stu-id="3fa12-149">Native symbols can be loaded by running `loadsymbols`.</span></span> <span data-ttu-id="3fa12-150">À ce stade, les [commandes SOS](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) peuvent être utilisées pour analyser le vidage.</span><span class="sxs-lookup"><span data-stu-id="3fa12-150">At this point, [SOS commands](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) can be used to analyze the dump.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fa12-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fa12-151">See also</span></span>

- <span data-ttu-id="3fa12-152">[dotnet-SOS](dotnet-sos.md) pour plus d’informations sur l’installation de l’extension SOS.</span><span class="sxs-lookup"><span data-stu-id="3fa12-152">[dotnet-sos](dotnet-sos.md) for more details on installing the SOS extension.</span></span>
- <span data-ttu-id="3fa12-153">[dotnet-Symbol](dotnet-symbol.md) pour plus d’informations sur l’installation et l’utilisation de l’outil de téléchargement de symboles.</span><span class="sxs-lookup"><span data-stu-id="3fa12-153">[dotnet-symbol](dotnet-symbol.md) for more details on installing and using the symbol download tool.</span></span>
- <span data-ttu-id="3fa12-154">[Diagnostics .net Core référentiel](https://github.com/dotnet/diagnostics/blob/master/documentation/) pour plus d’informations sur le débogage, y compris un Forum aux questions utile.</span><span class="sxs-lookup"><span data-stu-id="3fa12-154">[.NET Core diagnostics repo](https://github.com/dotnet/diagnostics/blob/master/documentation/) for more details on debugging, including a useful FAQ.</span></span>
- <span data-ttu-id="3fa12-155">[Installation de LLDB](https://github.com/dotnet/diagnostics/blob/master/documentation/sos.md#getting-lldb) pour obtenir des instructions sur l’installation de LLDB sur Linux ou Mac.</span><span class="sxs-lookup"><span data-stu-id="3fa12-155">[Installing LLDB](https://github.com/dotnet/diagnostics/blob/master/documentation/sos.md#getting-lldb) for instructions on installing LLDB on Linux or Mac.</span></span>
