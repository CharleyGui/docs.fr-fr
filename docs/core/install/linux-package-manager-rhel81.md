---
title: Installer .NET Core sur Linux RHEL 8,1 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 20fb3e9e517858b9cc5d6e9c1bd97bf949558843
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800741"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="1c8dd-103">Gestionnaire de package RHEL 8,1-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8dd-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="1c8dd-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="1c8dd-105">RHEL 8,0 n’inclut pas .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-105">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="1c8dd-106">Utilisez la commande `yum upgrade` pour effectuer une mise à jour vers RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-106">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="1c8dd-107">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="1c8dd-107">Register your Red Hat subscription</span></span>

<span data-ttu-id="1c8dd-108">Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-108">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="1c8dd-109">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="1c8dd-109">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="1c8dd-110">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8dd-110">Install the .NET Core SDK</span></span>

<span data-ttu-id="1c8dd-111">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-111">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="1c8dd-112">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-112">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="1c8dd-113">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8dd-113">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="1c8dd-114">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-114">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="1c8dd-115">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-115">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="1c8dd-116">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="1c8dd-116">Install the .NET Core Runtime</span></span>

<span data-ttu-id="1c8dd-117">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-117">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="1c8dd-118">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="1c8dd-118">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="1c8dd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c8dd-119">See also</span></span>

- [<span data-ttu-id="1c8dd-120">Utilisation de .NET Core 3,0 sur Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="1c8dd-120">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
