---
title: Installer .NET Core sur Fedora 32-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur Fedora 32.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624965"
---
# <a name="fedora-32-package-manager---install-net-core"></a><span data-ttu-id="385c1-103">Gestionnaire de package Fedora 32-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="385c1-103">Fedora 32 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="385c1-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="385c1-104">This article describes how to use a package manager to install .NET Core on Fedora 32.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

<span data-ttu-id="385c1-105">À compter de Fedora 32, .NET Core 3,1 est disponible dans les référentiels de packages par défaut dans Fedora.</span><span class="sxs-lookup"><span data-stu-id="385c1-105">Starting with Fedora 32, .NET Core 3.1 is available in the default package repositories in Fedora.</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="385c1-106">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="385c1-106">Install the .NET Core SDK</span></span>

<span data-ttu-id="385c1-107">Installez le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="385c1-107">Install the .NET Core SDK.</span></span> <span data-ttu-id="385c1-108">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="385c1-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="385c1-109">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="385c1-109">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="385c1-110">Installez le runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="385c1-110">Install the ASP.NET runtime.</span></span> <span data-ttu-id="385c1-111">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="385c1-111">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="385c1-112">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="385c1-112">Install the .NET Core runtime</span></span>

<span data-ttu-id="385c1-113">Installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="385c1-113">Install the .NET Core runtime.</span></span> <span data-ttu-id="385c1-114">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="385c1-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="385c1-115">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="385c1-115">How to install other versions</span></span>

<span data-ttu-id="385c1-116">Pour installer d’autres versions de .NET Core, installez manuellement [le kit SDK .net Core](sdk.md?pivots=os-linux#download-and-manually-install) ou [le Runtime .net Core](runtime.md?pivots=os-linux#download-and-manually-install).</span><span class="sxs-lookup"><span data-stu-id="385c1-116">To install other versions of .NET Core, manually install [the .NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) or [the .NET Core Runtime](runtime.md?pivots=os-linux#download-and-manually-install).</span></span>
