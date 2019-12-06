---
title: Installer .NET Core sur Linux RHEL 8,1 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 3ef639d5b76e81856ec8370d10e098c455ca8b3d
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836926"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="4583f-103">Gestionnaire de package RHEL 8,1-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="4583f-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="4583f-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="4583f-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span> <span data-ttu-id="4583f-105">.NET Core 3,1 n’est pas encore disponible pour RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="4583f-105">.NET Core 3.1 is not yet available for RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="4583f-106">RHEL 8,0 n’inclut pas .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="4583f-106">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="4583f-107">Utilisez la commande `yum upgrade` pour effectuer une mise à jour vers RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="4583f-107">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="4583f-108">RHEL 8,0 n’inclut pas .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="4583f-108">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="4583f-109">Utilisez la commande `yum upgrade` pour effectuer une mise à jour vers RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="4583f-109">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="4583f-110">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="4583f-110">Register your Red Hat subscription</span></span>

<span data-ttu-id="4583f-111">Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="4583f-111">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="4583f-112">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="4583f-112">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="4583f-113">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="4583f-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="4583f-114">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4583f-114">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="4583f-115">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="4583f-115">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="4583f-116">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4583f-116">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="4583f-117">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4583f-117">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="4583f-118">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="4583f-118">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="4583f-119">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="4583f-119">Install the .NET Core Runtime</span></span>

<span data-ttu-id="4583f-120">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4583f-120">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="4583f-121">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="4583f-121">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="4583f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4583f-122">See also</span></span>

- [<span data-ttu-id="4583f-123">Utilisation de .NET Core 3,0 sur Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="4583f-123">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
