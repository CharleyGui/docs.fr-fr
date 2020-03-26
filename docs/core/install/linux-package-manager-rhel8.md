---
title: Installer .NET Core sur Linux RHEL 8 package manager - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b564a386eb67b6e414a832ad3bca10d3d09022bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134193"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="8e2f3-103">RHEL 8 Package Manager - Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e2f3-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="8e2f3-104">Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="8e2f3-104">This article describes how to use a package manager to install .NET Core on RHEL 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="8e2f3-105">Enregistrez votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="8e2f3-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="8e2f3-106">Pour installer .NET Core de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du Red Hat Subscription Manager.</span><span class="sxs-lookup"><span data-stu-id="8e2f3-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="8e2f3-107">Si cela n’a pas été fait sur votre système, ou si vous n’êtes pas sûr, consultez la [documentation du produit Red Hat pour .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="8e2f3-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="8e2f3-108">Installer le kit de développement logiciel (SDK) .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e2f3-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="8e2f3-109">Après vous être inscrit auprès du Responsable De l’Abonnement, vous êtes prêt à installer et à activer le SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e2f3-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="8e2f3-110">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="8e2f3-110">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="8e2f3-111">Installer le ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="8e2f3-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="8e2f3-112">Après vous être inscrit auprès du Responsable De l’Abonnement, vous êtes prêt à installer et à activer le ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="8e2f3-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="8e2f3-113">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="8e2f3-113">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="8e2f3-114">Installer le .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="8e2f3-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="8e2f3-115">Après vous être inscrit auprès du responsable de l’abonnement, vous êtes prêt à installer et à activer le .NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="8e2f3-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="8e2f3-116">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="8e2f3-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a><span data-ttu-id="8e2f3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e2f3-117">See also</span></span>

- [<span data-ttu-id="8e2f3-118">Utilisation de .NET Core 3.1 sur Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="8e2f3-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
