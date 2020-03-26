---
title: Installer .NET Core sur Linux RHEL 7 gestionnaire de paquet - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1f1372b32c7b2471a96492d48aab5533dadb64a
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134202"
---
# <a name="rhel-7-package-manager---install-net-core"></a>RHEL 7 Package Manager - Installer .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur RHEL 7.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Enregistrez votre abonnement Red Hat

Pour installer .NET Core de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du Red Hat Subscription Manager. Si cela n’a pas été fait sur votre système, ou si vous n’êtes pas sûr, consultez la [documentation du produit Red Hat pour .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Installer le kit de développement logiciel (SDK) .NET Core

Après vous être inscrit auprès du Responsable De l’Abonnement, vous êtes prêt à installer et à activer le SDK .NET Core. Dans votre terminal, exécutez les commandes suivantes pour activer le canal pointnet RHEL 7 et installer.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Installer le ASP.NET Core Runtime

Après vous être inscrit auprès du Responsable De l’Abonnement, vous êtes prêt à installer et à activer le ASP.NET Core Runtime. Dans votre terminal, exécutez les commandes suivantes.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a>Installer le .NET Core Runtime

Après vous être inscrit auprès du responsable de l’abonnement, vous êtes prêt à installer et à activer le .NET Core Runtime. Dans votre terminal, exécutez les commandes suivantes.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a>Voir aussi

- [Utilisation de .NET Core 3.1 sur Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
