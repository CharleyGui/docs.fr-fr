---
title: Installer .NET Core sur Linux RHEL 7 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: f17a410ccea1ef4dec32de1d80ef6aac889aa6f3
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836954"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="c0de8-103">RHEL 7 Package Manager-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="c0de8-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="c0de8-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="c0de8-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span> <span data-ttu-id="c0de8-105">.NET Core 3,1 n’est pas encore disponible pour RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="c0de8-105">.NET Core 3.1 is not yet available for RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="c0de8-106">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="c0de8-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="c0de8-107">Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="c0de8-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="c0de8-108">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="c0de8-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="c0de8-109">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="c0de8-109">Install the .NET Core SDK</span></span>

<span data-ttu-id="c0de8-110">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0de8-110">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="c0de8-111">Sur votre terminal, exécutez les commandes suivantes pour activer le canal dotnet RHEL 7 et l’installer.</span><span class="sxs-lookup"><span data-stu-id="c0de8-111">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="c0de8-112">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c0de8-112">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="c0de8-113">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0de8-113">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="c0de8-114">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c0de8-114">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="c0de8-115">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="c0de8-115">Install the .NET Core Runtime</span></span>

<span data-ttu-id="c0de8-116">Après vous être inscrit auprès du gestionnaire d’abonnements, vous êtes prêt à installer et à activer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0de8-116">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="c0de8-117">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c0de8-117">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a><span data-ttu-id="c0de8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0de8-118">See also</span></span>

- [<span data-ttu-id="c0de8-119">Utilisation de .NET Core 3,0 sur Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="c0de8-119">Using .NET Core 3.0 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
