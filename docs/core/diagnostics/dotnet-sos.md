---
title: dotnet-SOS-.NET Core
description: Installation et utilisation de l’outil en ligne de commande dotnet-SOS.
ms.date: 08/26/2020
ms.openlocfilehash: 3ce7ca79bbc2c72958d395e9d312e3001ec9fbf8
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598336"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="3d256-103">Programme d’installation SOS (dotnet-SOS)</span><span class="sxs-lookup"><span data-stu-id="3d256-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="3d256-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="3d256-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-sos"></a><span data-ttu-id="3d256-105">Installer dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="3d256-105">Install dotnet-sos</span></span>

<span data-ttu-id="3d256-106">Pour installer la dernière version Release du `dotnet-sos` [package NuGet](https://www.nuget.org/packages/dotnet-sos), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="3d256-106">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a><span data-ttu-id="3d256-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3d256-107">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="3d256-108">Description</span><span class="sxs-lookup"><span data-stu-id="3d256-108">Description</span></span>

<span data-ttu-id="3d256-109">L' `dotnet-sos` outil Global installe l' [extension de débogueur SOS](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) permettant l' [inspection de l’État .net Core géré](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) à partir de débogueurs natifs tels que WinDbg/CDB sur Windows et lldb sur Linux et MacOS.</span><span class="sxs-lookup"><span data-stu-id="3d256-109">The `dotnet-sos` global tool installs the [SOS debugger extension](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and MacOS.</span></span> <span data-ttu-id="3d256-110">Notez que les versions récentes du débogueur Windows (>= version 10.0.18317.1001 de WinDbg ou CDB) chargent SOS automatiquement à partir de la Galerie d’extensions Microsoft. l’installation de SOS via l' `dotnet-sos` outil est donc uniquement nécessaire sur Linux et MacOS ou sur Windows si vous utilisez des outils de débogage plus anciens.</span><span class="sxs-lookup"><span data-stu-id="3d256-110">Note that recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and MacOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="3d256-111">Options</span><span class="sxs-lookup"><span data-stu-id="3d256-111">Options</span></span>

- **`--version`**

  <span data-ttu-id="3d256-112">Affiche des informations sur la version.</span><span class="sxs-lookup"><span data-stu-id="3d256-112">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="3d256-113">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3d256-113">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="3d256-114">installation de dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="3d256-114">dotnet-sos install</span></span>

<span data-ttu-id="3d256-115">Installe l' [extension SOS localement](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) pour utiliser les processus .net Core de débogage.</span><span class="sxs-lookup"><span data-stu-id="3d256-115">Installs the [SOS extension locally](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) for use debugging .NET Core processes.</span></span> <span data-ttu-id="3d256-116">Sur MacOS et Linux, le fichier. lldbinit est mis à jour afin que l’extension se charge automatiquement au démarrage de lldb.</span><span class="sxs-lookup"><span data-stu-id="3d256-116">On MacOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="3d256-117">Si vous installez SOS sur Windows avec les anciens outils de débogage (< version 10.0.18317.1001), vous devrez charger manuellement l’extension dans WinDbg ou CDB en exécutant `.load %USERPROFILE%\.dotnet\sos\sos.dll` dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="3d256-117">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="3d256-118">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3d256-118">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="3d256-119">désinstallation de dotnet-SOS</span><span class="sxs-lookup"><span data-stu-id="3d256-119">dotnet-sos uninstall</span></span>

<span data-ttu-id="3d256-120">Désinstalle l' [extension SOS](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) et, si sur Linux ou MacOS, la supprime de la configuration lldb.</span><span class="sxs-lookup"><span data-stu-id="3d256-120">Uninstalls the [SOS extension](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) and, if on Linux or MacOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="3d256-121">Synopsis</span><span class="sxs-lookup"><span data-stu-id="3d256-121">Synopsis</span></span>

```console
dotnet-sos uninstall
```
