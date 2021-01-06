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
# <a name="sos-installer-dotnet-sos"></a>Programme d’installation SOS (dotnet-SOS)

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="install"></a>Installer

Il existe deux façons de télécharger et d’installer `dotnet-sos` :

- **outil Global dotnet :**

  Pour installer la dernière version Release du `dotnet-sos` [package NuGet](https://www.nuget.org/packages/dotnet-sos), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- **Téléchargement direct :**

  Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :

  | Système d’exploitation  | Plateforme |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [ARM](https://aka.ms/dotnet-sos/win-arm) \| [ARM-x64](https://aka.ms/dotnet-sos/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-sos/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-sos/linux-x64) \| [ARM](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64) |

## <a name="synopsis"></a>Synopsis

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a>Description

L' `dotnet-sos` outil Global installe l' [extension de débogueur SOS](sos-debugging-extension.md). Cette extension vous permet d’inspecter l’état de .NET Core géré à partir de débogueurs natifs tels que lldb et WinDbg.

> [!NOTE]
> L’installation de SOS via l' `dotnet-sos` outil est uniquement nécessaire sur Linux ou MacOS.  Il peut également s’avérer nécessaire sur Windows si vous utilisez des outils de débogage plus anciens. Les versions récentes du [débogueur Windows](/windows-hardware/drivers/debugger/debugger-download-tools) (>= version 10.0.18317.1001 de WinDbg ou CDB) chargent SOS automatiquement à partir de la Galerie d’extensions Microsoft.  

## <a name="options"></a>Options

- **`--version`**

  Affiche des informations sur la version.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="dotnet-sos-install"></a>installation de dotnet-SOS

Installe l' [extension SOS](sos-debugging-extension.md) localement pour déboguer les processus .net core. Sur macOS et Linux, le fichier *. lldbinit* est mis à jour afin que l’extension se charge automatiquement au démarrage de lldb. Si vous installez SOS sur Windows avec les anciens outils de débogage (antérieurs à la version 10.0.18317.1001), vous devrez charger manuellement l’extension dans WinDbg ou CDB en exécutant `.load %USERPROFILE%\.dotnet\sos\sos.dll` dans le débogueur.

### <a name="synopsis"></a>Synopsis

```console
dotnet-sos install [--architecture <arch>]
```

### <a name="options"></a>Options

- **`--architecture <arch>`**

  Spécifie l’architecture de processeur des fichiers binaires SOS à installer. Par défaut, `dotnet-sos` installe l’architecture de l’ordinateur hôte. Utilisez cette option lorsque vous souhaitez installer SOS pour une architecture différente de l’architecture d’hôte dotnet. Par exemple, si vous exécutez des binaires Arm32 à partir d’un hôte Arm64, vous devrez installer SOS avec `dotnet-sos install --architecture Arm` .

  Les architectures suivantes sont disponibles :

  - `Arm`
  - `Arm64`
  - `X86`
  - `X64`

## <a name="dotnet-sos-uninstall"></a>désinstallation de dotnet-SOS

Désinstalle l' [extension SOS](sos-debugging-extension.md) et, sur Linux et MacOS, la supprime de la configuration lldb.

### <a name="synopsis"></a>Synopsis

```console
dotnet-sos uninstall
```
