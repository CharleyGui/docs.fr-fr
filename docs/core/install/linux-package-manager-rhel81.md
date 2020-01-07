---
title: Installer .NET Core sur Linux RHEL 8,1 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 8674b5d9d0f0ee384ca6798a7ea699bad67c5e5e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341180"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="414bb-103">Gestionnaire de package RHEL 8,1-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="414bb-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="414bb-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="414bb-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span> <span data-ttu-id="414bb-105">.NET Core 3,1 n’est pas encore disponible pour RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="414bb-105">.NET Core 3.1 is not yet available for RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="414bb-106">RHEL 8,0 n’inclut pas .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="414bb-106">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="414bb-107">Utilisez la commande `yum upgrade` pour effectuer une mise à jour vers RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="414bb-107">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="414bb-108">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="414bb-108">Register your Red Hat subscription</span></span>

<span data-ttu-id="414bb-109">Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="414bb-109">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="414bb-110">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="414bb-110">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="414bb-111">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="414bb-111">Install the .NET Core SDK</span></span>

<span data-ttu-id="414bb-112">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="414bb-112">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="414bb-113">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="414bb-113">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="414bb-114">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="414bb-114">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="414bb-115">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="414bb-115">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="414bb-116">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="414bb-116">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="414bb-117">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="414bb-117">Install the .NET Core Runtime</span></span>

<span data-ttu-id="414bb-118">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="414bb-118">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="414bb-119">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="414bb-119">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="414bb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="414bb-120">See also</span></span>

- [<span data-ttu-id="414bb-121">Utilisation de .NET Core 3,0 sur Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="414bb-121">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
