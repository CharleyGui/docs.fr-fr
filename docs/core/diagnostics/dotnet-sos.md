---
title: dotnet-SOS-.NET Core
description: Découvrez comment installer et utiliser l’outil en ligne de commande dotnet-SOS.
ms.date: 08/26/2020
ms.openlocfilehash: ba83105718909038ca56129ed8a5063aeff12e89
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065082"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="b1eba-103">Programme d’installation SOS (dotnet-SOS)</span><span class="sxs-lookup"><span data-stu-id="b1eba-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="b1eba-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b1eba-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-sos"></a><span data-ttu-id="b1eba-105">Installer dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="b1eba-105">Install dotnet-sos</span></span>

<span data-ttu-id="b1eba-106">Pour installer la dernière version Release du `dotnet-sos` [package NuGet](https://www.nuget.org/packages/dotnet-sos), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="b1eba-106">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a><span data-ttu-id="b1eba-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b1eba-107">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="b1eba-108">Description</span><span class="sxs-lookup"><span data-stu-id="b1eba-108">Description</span></span>

<span data-ttu-id="b1eba-109">L' `dotnet-sos` outil Global installe l' [extension de débogueur SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) permettant l' [inspection de l’État .net Core géré](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) à partir de débogueurs natifs tels que WinDbg/CDB sur Windows et lldb sur Linux et MacOS.</span><span class="sxs-lookup"><span data-stu-id="b1eba-109">The `dotnet-sos` global tool installs the [SOS debugger extension](../../framework/tools/sos-dll-sos-debugging-extension.md) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and macOS.</span></span> <span data-ttu-id="b1eba-110">Les versions récentes du débogueur Windows (>= version 10.0.18317.1001 de WinDbg ou CDB) chargent automatiquement SOS à partir de la Galerie d’extensions Microsoft. par conséquent, l’installation de SOS via l' `dotnet-sos` outil est uniquement nécessaire sur Linux et MacOS ou sur Windows si vous utilisez des outils de débogage plus anciens.</span><span class="sxs-lookup"><span data-stu-id="b1eba-110">Recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and macOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="b1eba-111">Options</span><span class="sxs-lookup"><span data-stu-id="b1eba-111">Options</span></span>

- **`--version`**

  <span data-ttu-id="b1eba-112">Affiche des informations sur la version.</span><span class="sxs-lookup"><span data-stu-id="b1eba-112">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b1eba-113">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b1eba-113">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="b1eba-114">installation de dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="b1eba-114">dotnet-sos install</span></span>

<span data-ttu-id="b1eba-115">Installe l' [extension SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) localement pour déboguer les processus .net core.</span><span class="sxs-lookup"><span data-stu-id="b1eba-115">Installs the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="b1eba-116">Sur macOS et Linux, le fichier. lldbinit est mis à jour afin que l’extension se charge automatiquement au démarrage de lldb.</span><span class="sxs-lookup"><span data-stu-id="b1eba-116">On macOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="b1eba-117">Si vous installez SOS sur Windows avec les anciens outils de débogage (< version 10.0.18317.1001), vous devrez charger manuellement l’extension dans WinDbg ou CDB en exécutant `.load %USERPROFILE%\.dotnet\sos\sos.dll` dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="b1eba-117">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b1eba-118">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b1eba-118">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="b1eba-119">désinstallation de dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="b1eba-119">dotnet-sos uninstall</span></span>

<span data-ttu-id="b1eba-120">Désinstalle l' [extension SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) et, si sur Linux ou MacOS, la supprime de la configuration lldb.</span><span class="sxs-lookup"><span data-stu-id="b1eba-120">Uninstalls the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) and, if on Linux or macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b1eba-121">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b1eba-121">Synopsis</span></span>

```console
dotnet-sos uninstall
```
