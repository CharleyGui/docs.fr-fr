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
# <a name="dotnet-build-server"></a><span data-ttu-id="03544-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="03544-103">dotnet build-server</span></span>

<span data-ttu-id="03544-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="03544-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="03544-105">Name</span><span class="sxs-lookup"><span data-stu-id="03544-105">Name</span></span>

<span data-ttu-id="03544-106">`dotnet build-server` -Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="03544-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="03544-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="03544-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="03544-108">Commands</span><span class="sxs-lookup"><span data-stu-id="03544-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="03544-109">Arrête les serveurs de builds démarrés à partir de dotnet.</span><span class="sxs-lookup"><span data-stu-id="03544-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="03544-110">Par défaut, tous les serveurs sont arrêtés.</span><span class="sxs-lookup"><span data-stu-id="03544-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="03544-111">Options</span><span class="sxs-lookup"><span data-stu-id="03544-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="03544-112">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="03544-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="03544-113">Arrête le serveur de builds MSBuild.</span><span class="sxs-lookup"><span data-stu-id="03544-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="03544-114">Arrête le serveur de builds Razor.</span><span class="sxs-lookup"><span data-stu-id="03544-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="03544-115">Arrête le serveur de builds du compilateur VB/C#.</span><span class="sxs-lookup"><span data-stu-id="03544-115">Shuts down the VB/C# compiler build server.</span></span>
