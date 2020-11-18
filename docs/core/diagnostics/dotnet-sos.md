---
title: outil de diagnostic dotnet-SOS-interface de commande .NET
description: Découvrez comment installer et utiliser l’outil CLI dotnet-SOS pour gérer l’extension de débogueur SOS, qui est utilisée avec les débogueurs natifs sur Windows et Linux.
ms.date: 11/17/2020
ms.openlocfilehash: 59512c42a778f68bb3cd092dc854dcc727fd2881
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825440"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="b542c-103">Programme d’installation SOS (dotnet-SOS)</span><span class="sxs-lookup"><span data-stu-id="b542c-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="b542c-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b542c-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="b542c-105">Installer</span><span class="sxs-lookup"><span data-stu-id="b542c-105">Install</span></span>

<span data-ttu-id="b542c-106">Il existe deux façons de télécharger et d’installer `dotnet-sos` :</span><span class="sxs-lookup"><span data-stu-id="b542c-106">There are two ways to download and install `dotnet-sos`:</span></span>

- <span data-ttu-id="b542c-107">**outil Global dotnet :**</span><span class="sxs-lookup"><span data-stu-id="b542c-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="b542c-108">Pour installer la dernière version Release du `dotnet-sos` [package NuGet](https://www.nuget.org/packages/dotnet-sos), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="b542c-108">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- <span data-ttu-id="b542c-109">**Téléchargement direct :**</span><span class="sxs-lookup"><span data-stu-id="b542c-109">**Direct download:**</span></span>

  <span data-ttu-id="b542c-110">Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="b542c-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="b542c-111">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="b542c-111">OS</span></span>  | <span data-ttu-id="b542c-112">Plateforme</span><span class="sxs-lookup"><span data-stu-id="b542c-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="b542c-113">Windows</span><span class="sxs-lookup"><span data-stu-id="b542c-113">Windows</span></span> | <span data-ttu-id="b542c-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [ARM](https://aka.ms/dotnet-sos/win-arm) \| [ARM-x64](https://aka.ms/dotnet-sos/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="b542c-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span></span> |
  | <span data-ttu-id="b542c-115">macOS</span><span class="sxs-lookup"><span data-stu-id="b542c-115">macOS</span></span>   | [<span data-ttu-id="b542c-116">x64</span><span class="sxs-lookup"><span data-stu-id="b542c-116">x64</span></span>](https://aka.ms/dotnet-sos/osx-x64) |
  | <span data-ttu-id="b542c-117">Linux</span><span class="sxs-lookup"><span data-stu-id="b542c-117">Linux</span></span>   | <span data-ttu-id="b542c-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [ARM](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="b542c-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="b542c-119">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b542c-119">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="b542c-120">Description</span><span class="sxs-lookup"><span data-stu-id="b542c-120">Description</span></span>

<span data-ttu-id="b542c-121">L' `dotnet-sos` outil Global installe l' [extension de débogueur SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) permettant l' [inspection de l’État .net Core géré](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) à partir de débogueurs natifs tels que WinDbg/CDB sur Windows et lldb sur Linux et MacOS.</span><span class="sxs-lookup"><span data-stu-id="b542c-121">The `dotnet-sos` global tool installs the [SOS debugger extension](../../framework/tools/sos-dll-sos-debugging-extension.md) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and macOS.</span></span> <span data-ttu-id="b542c-122">Les versions récentes du débogueur Windows (>= version 10.0.18317.1001 de WinDbg ou CDB) chargent automatiquement SOS à partir de la Galerie d’extensions Microsoft. par conséquent, l’installation de SOS via l' `dotnet-sos` outil est uniquement nécessaire sur Linux et MacOS ou sur Windows si vous utilisez des outils de débogage plus anciens.</span><span class="sxs-lookup"><span data-stu-id="b542c-122">Recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and macOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="b542c-123">Options</span><span class="sxs-lookup"><span data-stu-id="b542c-123">Options</span></span>

- **`--version`**

  <span data-ttu-id="b542c-124">Affiche des informations sur la version.</span><span class="sxs-lookup"><span data-stu-id="b542c-124">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b542c-125">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b542c-125">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="b542c-126">installation de dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="b542c-126">dotnet-sos install</span></span>

<span data-ttu-id="b542c-127">Installe l' [extension SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) localement pour déboguer les processus .net core.</span><span class="sxs-lookup"><span data-stu-id="b542c-127">Installs the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="b542c-128">Sur macOS et Linux, le fichier. lldbinit est mis à jour afin que l’extension se charge automatiquement au démarrage de lldb.</span><span class="sxs-lookup"><span data-stu-id="b542c-128">On macOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="b542c-129">Si vous installez SOS sur Windows avec les anciens outils de débogage (< version 10.0.18317.1001), vous devrez charger manuellement l’extension dans WinDbg ou CDB en exécutant `.load %USERPROFILE%\.dotnet\sos\sos.dll` dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="b542c-129">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b542c-130">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b542c-130">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="b542c-131">désinstallation de dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="b542c-131">dotnet-sos uninstall</span></span>

<span data-ttu-id="b542c-132">Désinstalle l' [extension SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) et, si sur Linux ou MacOS, la supprime de la configuration lldb.</span><span class="sxs-lookup"><span data-stu-id="b542c-132">Uninstalls the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) and, if on Linux or macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b542c-133">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b542c-133">Synopsis</span></span>

```console
dotnet-sos uninstall
```
