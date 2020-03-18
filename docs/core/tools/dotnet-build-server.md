---
title: Commande dotnet build-server
description: La commande dotnet build-server interagit avec les serveurs démarrés par une build.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503779"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="27aa8-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="27aa8-103">dotnet build-server</span></span>

<span data-ttu-id="27aa8-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="27aa8-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="27aa8-105">Nom</span><span class="sxs-lookup"><span data-stu-id="27aa8-105">Name</span></span>

<span data-ttu-id="27aa8-106">`dotnet build-server` -Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="27aa8-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="27aa8-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="27aa8-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="27aa8-108">Commandes</span><span class="sxs-lookup"><span data-stu-id="27aa8-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="27aa8-109">Arrête les serveurs de builds démarrés à partir de dotnet.</span><span class="sxs-lookup"><span data-stu-id="27aa8-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="27aa8-110">Par défaut, tous les serveurs sont arrêtés.</span><span class="sxs-lookup"><span data-stu-id="27aa8-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="27aa8-111">Options</span><span class="sxs-lookup"><span data-stu-id="27aa8-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="27aa8-112">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="27aa8-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="27aa8-113">Arrête le serveur de builds MSBuild.</span><span class="sxs-lookup"><span data-stu-id="27aa8-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="27aa8-114">Arrête le serveur de builds Razor.</span><span class="sxs-lookup"><span data-stu-id="27aa8-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="27aa8-115">Arrête le serveur de builds du compilateur VB/C#.</span><span class="sxs-lookup"><span data-stu-id="27aa8-115">Shuts down the VB/C# compiler build server.</span></span>
