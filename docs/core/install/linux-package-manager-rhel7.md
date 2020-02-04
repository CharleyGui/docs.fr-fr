---
title: Installer .NET Core sur Linux RHEL 7 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 4f85ed3da8a434fcd5b6ee88491daf623c3c8b31
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980182"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="43327-103">RHEL 7 Package Manager-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="43327-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="43327-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="43327-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="43327-105">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="43327-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="43327-106">Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="43327-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="43327-107">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="43327-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="43327-108">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="43327-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="43327-109">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43327-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="43327-110">Sur votre terminal, exécutez les commandes suivantes pour activer le canal dotnet RHEL 7 et l’installer.</span><span class="sxs-lookup"><span data-stu-id="43327-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="43327-111">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="43327-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="43327-112">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="43327-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="43327-113">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="43327-113">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="43327-114">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="43327-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="43327-115">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43327-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="43327-116">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="43327-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a><span data-ttu-id="43327-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43327-117">See also</span></span>

- [<span data-ttu-id="43327-118">Utilisation de .NET Core 3,1 sur Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="43327-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
