---
title: Commande dotnet build-server
description: La commande dotnet build-server interagit avec les serveurs démarrés par une build.
ms.date: 04/24/2019
ms.openlocfilehash: e77a4d9f49f555ac847bb13380380599eef881b1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734378"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Nom

`dotnet build-server` -Interagit avec les serveurs démarrés par une build.

## <a name="synopsis"></a>Résumé

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Commands

- **`shutdown`**

  Arrête les serveurs de builds démarrés à partir de dotnet. Par défaut, tous les serveurs sont arrêtés.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--msbuild`**

  Arrête le serveur de builds MSBuild.

- **`--razor`**

  Arrête le serveur de builds Razor.

- **`--vbcscompiler`**

  Arrête le serveur de builds du compilateur VB/C#.
