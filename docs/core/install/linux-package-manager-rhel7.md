---
title: Installer .NET Core sur Linux RHEL 7 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: cc7865727927eda1406da26e64b89325fd5665a4
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801961"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="3a914-103">RHEL 7 Package Manager-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="3a914-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="3a914-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="3a914-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="3a914-105">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="3a914-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="3a914-106">Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="3a914-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="3a914-107">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="3a914-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="3a914-108">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="3a914-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="3a914-109">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a914-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="3a914-110">Sur votre terminal, exécutez les commandes suivantes pour activer le canal dotnet RHEL 7 et l’installer.</span><span class="sxs-lookup"><span data-stu-id="3a914-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install .</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="3a914-111">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3a914-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="3a914-112">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a914-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="3a914-113">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="3a914-113">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="3a914-114">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="3a914-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="3a914-115">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a914-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="3a914-116">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="3a914-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a><span data-ttu-id="3a914-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a914-117">See also</span></span>

- [<span data-ttu-id="3a914-118">Utilisation de .NET Core 3,0 sur Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="3a914-118">Using .NET Core 3.0 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
