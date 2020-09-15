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
# <a name="sos-installer-dotnet-sos"></a>Programme d’installation SOS (dotnet-SOS)

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="install-dotnet-sos"></a>Installer dotnet-SOS

Pour installer la dernière version Release du `dotnet-sos` [package NuGet](https://www.nuget.org/packages/dotnet-sos), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a>Synopsis

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a>Description

L' `dotnet-sos` outil Global installe l' [extension de débogueur SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) permettant l' [inspection de l’État .net Core géré](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) à partir de débogueurs natifs tels que WinDbg/CDB sur Windows et lldb sur Linux et MacOS. Les versions récentes du débogueur Windows (>= version 10.0.18317.1001 de WinDbg ou CDB) chargent automatiquement SOS à partir de la Galerie d’extensions Microsoft. par conséquent, l’installation de SOS via l' `dotnet-sos` outil est uniquement nécessaire sur Linux et MacOS ou sur Windows si vous utilisez des outils de débogage plus anciens.

## <a name="options"></a>Options

- **`--version`**

  Affiche des informations sur la version.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="dotnet-sos-install"></a>installation de dotnet-SOS

Installe l' [extension SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) localement pour déboguer les processus .net core. Sur macOS et Linux, le fichier. lldbinit est mis à jour afin que l’extension se charge automatiquement au démarrage de lldb. Si vous installez SOS sur Windows avec les anciens outils de débogage (< version 10.0.18317.1001), vous devrez charger manuellement l’extension dans WinDbg ou CDB en exécutant `.load %USERPROFILE%\.dotnet\sos\sos.dll` dans le débogueur.

### <a name="synopsis"></a>Synopsis

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a>désinstallation de dotnet-SOS

Désinstalle l' [extension SOS](../../framework/tools/sos-dll-sos-debugging-extension.md) et, si sur Linux ou MacOS, la supprime de la configuration lldb.

### <a name="synopsis"></a>Synopsis

```console
dotnet-sos uninstall
```
