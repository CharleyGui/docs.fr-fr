---
title: outil de diagnostic dotnet-gcdump-CLI .NET
description: Découvrez comment installer et utiliser l’outil CLI dotnet-gcdump pour collecter des vidages de mémoire (garbage collector) de processus .NET en temps réel à l’aide de .NET EventPipe.
ms.date: 11/17/2020
ms.openlocfilehash: 02e1a7c5d86b582289672a027464aefd67a6f490
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593368"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a>Outil d’analyse de tas (dotnet-gcdump)

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,1 et versions ultérieures

## <a name="install"></a>Installer

Il existe deux façons de télécharger et d’installer `dotnet-gcdump` :

- **outil Global dotnet :**

  Pour installer la dernière version Release du `dotnet-gcdump` [package NuGet](https://www.nuget.org/packages/dotnet-gcdump), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- **Téléchargement direct :**

  Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :

  | Système d''exploitation  | Plateforme |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [ARM](https://aka.ms/dotnet-gcdump/win-arm) \| [ARM-x64](https://aka.ms/dotnet-gcdump/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-gcdump/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [ARM](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64) |

## <a name="synopsis"></a>Synopsis

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a>Description

L' `dotnet-gcdump` outil Global collecte les vidages GC (garbage collector) des processus .net en temps réel à l’aide de [EventPipe](./eventpipe.md). Les dumps GC sont créés en déclenchant un GC dans le processus cible, en activant des événements spéciaux et en régénérant le graphique des racines d’objets à partir du flux d’événements. Ce processus permet de collecter des vidages de mémoire GC pendant que le processus est en cours d’exécution et avec une surcharge minimale. Ces vidages sont utiles pour plusieurs scénarios :

- Comparaison du nombre d’objets sur le tas à plusieurs points dans le temps.
- Analyse des racines d’objets (réponse à des questions telles que « qu’est-ce qui a toujours une référence à ce type ? »).
- Collecte des statistiques générales sur le nombre d’objets sur le tas.

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a>Afficher le vidage GC capturé à partir de dotnet-gcdump

Sur Windows, `.gcdump` les fichiers peuvent être affichés dans [PerfView](https://github.com/microsoft/perfview) pour l’analyse ou dans Visual Studio. Actuellement, il n’existe aucun moyen d’ouvrir une `.gcdump` sur des plateformes non-Windows.

Vous pouvez collecter plusieurs `.gcdump` s et les ouvrir simultanément dans Visual Studio pour obtenir une comparaison.

## <a name="options"></a>Options

- **`--version`**

  Affiche la version de l' `dotnet-gcdump` utilitaire.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## `dotnet-gcdump collect`

Collecte un vidage de mémoire GC à partir d’un processus en cours d’exécution.

> [!WARNING]
> Pour parcourir le tas GC, cette commande déclenche une garbage collection de génération 2 (complète), qui peut interrompre le runtime pendant une longue période, en particulier lorsque le tas GC est volumineux. N’utilisez pas cette commande dans les environnements sensibles aux performances lorsque le tas GC est volumineux.

### <a name="synopsis"></a>Synopsis

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a>Options

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

- **`-p|--process-id <pid>`**

  ID de processus à partir duquel collecter le vidage GC.

- **`-o|--output <gcdump-file-path>`**

  Chemin d’accès où les dumps GC collectés doivent être écrits. La valeur par défaut est *. \\ AAAAMMJJ \_ HHMMSS \_ \<pid> . gcdump*.

- **`-v|--verbose`**

  Sortie du journal lors de la collecte du vidage GC.

- **`-t|--timeout <timeout>`**

  Abandonner la collecte du vidage GC s’il prend plus de temps que ce nombre de secondes. La valeur par défaut est 30.

- **`-n|--name <name>`**

  Nom du processus à partir duquel collecter le vidage GC.

## `dotnet-gcdump ps`

Répertorie les processus dotnet pour lesquels les dumps GC peuvent être collectés.

### <a name="synopsis"></a>Synopsis

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

Générez un rapport à partir d’un vidage GC précédemment généré ou d’un processus en cours d’exécution, puis écrivez dans `stdout` .

### <a name="synopsis"></a>Synopsis

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a>Options

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

- **`-p|--process-id <pid>`**

  ID de processus à partir duquel collecter le vidage GC.

- **`-t|--report-type <HeapStat>`**

  Type de rapport à générer. Options disponibles : heapstat (par défaut).

## <a name="troubleshoot"></a>Dépanner

- Il n’y a pas d’informations de type dans le gcdump.

   Avant .NET Core 3,1, il y avait un problème où un cache de type n’a pas été effacé entre gcdumps lorsqu’il a été appelé avec EventPipe. Cela a entraîné les événements nécessaires pour déterminer les informations de type qui n’ont pas été envoyées pour la deuxième gcdumps et les autres. Ce problème a été résolu dans .NET Core 3,1-preview2.

- Les types COM et static ne sont pas dans le vidage GC.

   Avant .NET Core 3,1-preview2, il y avait un problème où les types static et COM n’étaient pas envoyés lorsque le vidage GC était appelé via EventPipe. Ce problème a été résolu dans .NET Core 3,1-preview2.
