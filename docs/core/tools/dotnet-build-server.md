---
title: Commande dotnet build-server
description: La commande dotnet build-server interagit avec les serveurs démarrés par une build.
ms.date: 04/24/2019
ms.openlocfilehash: 89d1aba104e2cb07b46766a3768eed68d85a7aa7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117772"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="6543b-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="6543b-103">dotnet build-server</span></span>

<span data-ttu-id="6543b-104">**Cet article s’applique à : ✓** SDK .NET Core 2.1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6543b-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="6543b-105">Name</span><span class="sxs-lookup"><span data-stu-id="6543b-105">Name</span></span>

<span data-ttu-id="6543b-106">`dotnet build-server` -Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="6543b-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6543b-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="6543b-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="6543b-108">Commandes</span><span class="sxs-lookup"><span data-stu-id="6543b-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="6543b-109">Arrête les serveurs de builds démarrés à partir de dotnet.</span><span class="sxs-lookup"><span data-stu-id="6543b-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="6543b-110">Par défaut, tous les serveurs sont arrêtés.</span><span class="sxs-lookup"><span data-stu-id="6543b-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="6543b-111">Options</span><span class="sxs-lookup"><span data-stu-id="6543b-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="6543b-112">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="6543b-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="6543b-113">Arrête le serveur de builds MSBuild.</span><span class="sxs-lookup"><span data-stu-id="6543b-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="6543b-114">Arrête le serveur de builds Razor.</span><span class="sxs-lookup"><span data-stu-id="6543b-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="6543b-115">Arrête le serveur de builds du compilateur VB/C#.</span><span class="sxs-lookup"><span data-stu-id="6543b-115">Shuts down the VB/C# compiler build server.</span></span>
