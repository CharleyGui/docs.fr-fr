---
title: Installer .NET Core sur Linux RHEL 8 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur RHEL 8.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: 8829e842e920e6abd4184b5140f80bb016acace2
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728241"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="11e07-103">RHEL 8 Package Manager-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="11e07-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="11e07-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Red Hat Enterprise Linux (RHEL) 8.</span><span class="sxs-lookup"><span data-stu-id="11e07-104">This article describes how to use a package manager to install .NET Core on Red Hat Enterprise Linux (RHEL) 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="11e07-105">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="11e07-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="11e07-106">Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="11e07-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="11e07-107">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="11e07-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="11e07-108">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="11e07-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="11e07-109">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11e07-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="11e07-110">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="11e07-110">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="11e07-111">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="11e07-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="11e07-112">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="11e07-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="11e07-113">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="11e07-113">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="11e07-114">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="11e07-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="11e07-115">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11e07-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="11e07-116">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="11e07-116">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="11e07-117">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="11e07-117">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="see-also"></a><span data-ttu-id="11e07-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11e07-118">See also</span></span>

- [<span data-ttu-id="11e07-119">Utilisation de .NET Core 3,1 sur Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="11e07-119">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
