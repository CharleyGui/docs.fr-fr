---
title: outil de diagnostic dotnet-SOS-interface de commande .NET
description: Découvrez comment installer et utiliser l’outil CLI dotnet-SOS pour gérer l’extension de débogueur SOS, qui est utilisée avec les débogueurs natifs sur Windows et Linux.
ms.date: 11/17/2020
ms.openlocfilehash: 09e8228c47bdc632bccf3c9ad2296d55fe420060
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765005"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="4b256-103">Programme d’installation SOS (dotnet-SOS)</span><span class="sxs-lookup"><span data-stu-id="4b256-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="4b256-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="4b256-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="4b256-105">Installer</span><span class="sxs-lookup"><span data-stu-id="4b256-105">Install</span></span>

<span data-ttu-id="4b256-106">Il existe deux façons de télécharger et d’installer `dotnet-sos` :</span><span class="sxs-lookup"><span data-stu-id="4b256-106">There are two ways to download and install `dotnet-sos`:</span></span>

- <span data-ttu-id="4b256-107">**outil Global dotnet :**</span><span class="sxs-lookup"><span data-stu-id="4b256-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="4b256-108">Pour installer la dernière version Release du `dotnet-sos` [package NuGet](https://www.nuget.org/packages/dotnet-sos), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="4b256-108">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- <span data-ttu-id="4b256-109">**Téléchargement direct :**</span><span class="sxs-lookup"><span data-stu-id="4b256-109">**Direct download:**</span></span>

  <span data-ttu-id="4b256-110">Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="4b256-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="4b256-111">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="4b256-111">OS</span></span>  | <span data-ttu-id="4b256-112">Plateforme</span><span class="sxs-lookup"><span data-stu-id="4b256-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="4b256-113">Windows</span><span class="sxs-lookup"><span data-stu-id="4b256-113">Windows</span></span> | <span data-ttu-id="4b256-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [ARM](https://aka.ms/dotnet-sos/win-arm) \| [ARM-x64](https://aka.ms/dotnet-sos/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="4b256-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span></span> |
  | <span data-ttu-id="4b256-115">macOS</span><span class="sxs-lookup"><span data-stu-id="4b256-115">macOS</span></span>   | [<span data-ttu-id="4b256-116">x64</span><span class="sxs-lookup"><span data-stu-id="4b256-116">x64</span></span>](https://aka.ms/dotnet-sos/osx-x64) |
  | <span data-ttu-id="4b256-117">Linux</span><span class="sxs-lookup"><span data-stu-id="4b256-117">Linux</span></span>   | <span data-ttu-id="4b256-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [ARM](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="4b256-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="4b256-119">Synopsis</span><span class="sxs-lookup"><span data-stu-id="4b256-119">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="4b256-120">Description</span><span class="sxs-lookup"><span data-stu-id="4b256-120">Description</span></span>

<span data-ttu-id="4b256-121">L' `dotnet-sos` outil Global installe l' [extension de débogueur SOS](sos-debugging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="4b256-121">The `dotnet-sos` global tool installs the [SOS debugger extension](sos-debugging-extension.md).</span></span> <span data-ttu-id="4b256-122">Cette extension vous permet d’inspecter l’état de .NET Core géré à partir de débogueurs natifs tels que lldb et WinDbg.</span><span class="sxs-lookup"><span data-stu-id="4b256-122">This extension lets you inspect managed .NET Core state from native debuggers like lldb and windbg.</span></span>

> [!NOTE]
> <span data-ttu-id="4b256-123">L’installation de SOS via l' `dotnet-sos` outil est uniquement nécessaire sur Linux ou MacOS.</span><span class="sxs-lookup"><span data-stu-id="4b256-123">Installing SOS via the `dotnet-sos` tool is only needed on Linux or macOS.</span></span>  <span data-ttu-id="4b256-124">Il peut également s’avérer nécessaire sur Windows si vous utilisez des outils de débogage plus anciens.</span><span class="sxs-lookup"><span data-stu-id="4b256-124">It may also be needed on Windows if you're using older debugging tools.</span></span> <span data-ttu-id="4b256-125">Les versions récentes du [débogueur Windows](/windows-hardware/drivers/debugger/debugger-download-tools) (>= version 10.0.18317.1001 de WinDbg ou CDB) chargent SOS automatiquement à partir de la Galerie d’extensions Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4b256-125">Recent versions of the [Windows Debugger](/windows-hardware/drivers/debugger/debugger-download-tools) (>= version 10.0.18317.1001 of WinDbg or cdb) load SOS automatically from the Microsoft extension gallery.</span></span>  

## <a name="options"></a><span data-ttu-id="4b256-126">Options</span><span class="sxs-lookup"><span data-stu-id="4b256-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="4b256-127">Affiche des informations sur la version.</span><span class="sxs-lookup"><span data-stu-id="4b256-127">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4b256-128">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4b256-128">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="4b256-129">installation de dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="4b256-129">dotnet-sos install</span></span>

<span data-ttu-id="4b256-130">Installe l' [extension SOS](sos-debugging-extension.md) localement pour déboguer les processus .net core.</span><span class="sxs-lookup"><span data-stu-id="4b256-130">Installs the [SOS extension](sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="4b256-131">Sur macOS et Linux, le fichier *. lldbinit* est mis à jour afin que l’extension se charge automatiquement au démarrage de lldb.</span><span class="sxs-lookup"><span data-stu-id="4b256-131">On macOS and Linux, the *.lldbinit* file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="4b256-132">Si vous installez SOS sur Windows avec les anciens outils de débogage (antérieurs à la version 10.0.18317.1001), vous devrez charger manuellement l’extension dans WinDbg ou CDB en exécutant `.load %USERPROFILE%\.dotnet\sos\sos.dll` dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="4b256-132">If you're installing SOS on Windows with older debugging tools (prior to version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="4b256-133">Synopsis</span><span class="sxs-lookup"><span data-stu-id="4b256-133">Synopsis</span></span>

```console
dotnet-sos install [--architecture <arch>]
```

### <a name="options"></a><span data-ttu-id="4b256-134">Options</span><span class="sxs-lookup"><span data-stu-id="4b256-134">Options</span></span>

- **`--architecture <arch>`**

  <span data-ttu-id="4b256-135">Spécifie l’architecture de processeur des fichiers binaires SOS à installer.</span><span class="sxs-lookup"><span data-stu-id="4b256-135">Specifies the processor architecture of the SOS binaries to install.</span></span> <span data-ttu-id="4b256-136">Par défaut, `dotnet-sos` installe l’architecture de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="4b256-136">By default, `dotnet-sos` installs the architecture of the host machine.</span></span> <span data-ttu-id="4b256-137">Utilisez cette option lorsque vous souhaitez installer SOS pour une architecture différente de l’architecture d’hôte dotnet.</span><span class="sxs-lookup"><span data-stu-id="4b256-137">Use this option when you want to install SOS for an architecture that's different from the dotnet host architecture.</span></span> <span data-ttu-id="4b256-138">Par exemple, si vous exécutez des binaires Arm32 à partir d’un hôte Arm64, vous devrez installer SOS avec `dotnet-sos install --architecture Arm` .</span><span class="sxs-lookup"><span data-stu-id="4b256-138">For example, if you're running Arm32 binaries from an Arm64 host, you will need to install SOS with `dotnet-sos install --architecture Arm`.</span></span>

  <span data-ttu-id="4b256-139">Les architectures suivantes sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="4b256-139">The following architectures are available:</span></span>

  - `Arm`
  - `Arm64`
  - `X86`
  - `X64`

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="4b256-140">désinstallation de dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="4b256-140">dotnet-sos uninstall</span></span>

<span data-ttu-id="4b256-141">Désinstalle l' [extension SOS](sos-debugging-extension.md) et, sur Linux et MacOS, la supprime de la configuration lldb.</span><span class="sxs-lookup"><span data-stu-id="4b256-141">Uninstalls the [SOS extension](sos-debugging-extension.md) and, on Linux and macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="4b256-142">Synopsis</span><span class="sxs-lookup"><span data-stu-id="4b256-142">Synopsis</span></span>

```console
dotnet-sos uninstall
```
