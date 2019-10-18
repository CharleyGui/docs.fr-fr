---
title: Commande dotnet build-server
description: La commande dotnet build-server interagit avec les serveurs démarrés par une build.
ms.date: 04/24/2019
ms.openlocfilehash: 1c6c6dcdb53d779426daf5daa470d2ad0470a7a1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523013"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Cet article s’applique à : ✓** SDK .NET Core 2.1 et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Name

`dotnet build-server` -Interagit avec les serveurs démarrés par une build.

## <a name="synopsis"></a>Résumé

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Commandes

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
